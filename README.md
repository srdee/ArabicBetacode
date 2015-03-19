# Arabic betaCode

## Some updates to the scheme (2015-03-09:10-21)

Done to avoid issues with Alpheios translation alignment, which automatically splits supplied texts into words. Essentially, combinations with "." and ":" are replaced with "\*" and "=" respectively.

* **=t** is *tāʾ marbūṭaŧ*
* **\*s** is *ṣād* (and the same for other letters transliterated with dots)

<center>[a better formatted version](http://maximromanov.github.io/2015/02-07.html)</center>

 Although both Windows and Mac OS now support Arabic, it is still quite difficult to type and edit Arabic texts. It is particularly frustrating to edit and manipulate fully vocalized texts, since most fonts either render “short vowels” (*ḥarakāt*) invisible, or do not render them properly. Because of the “stacking,” i.e. “short vowels” being placed on top of letters and on top of each other, it becomes impossible to *edit* texts and one is often forced to go into delete-and-retype mode (and there is still no guarantee, because of visual issues, that all the letters and “short vowels” will actually be in the right order). **betaCode** can make it easy to type fully-vocalized Arabic texts on any machine through the use of simple character combinations and automatic rendering into various transliteration schemes and the Arabic script (scroll below for examples). 

**betaCode** is first converted into a one-to-one transliteration scheme, which combines conventions from various academic transliteration schemes. Such scheme is necessary, since none of the existing academic schemes (American/Library of Congress, British, French, German, etc.) allow representing Arabic text unambiguously for computational purposes. Arabic **betaCode** transliteration can be then converted into any transliteration convention. At the moment the following schemes are implemented:

* Library of Congress Romanization of Arabic
* Simplified transliteration (LOC without diacritics)
* Arabic script (the rules of *ḥamzaŧ* orthography are implemented, but may require some additional testing)

**NB:** The idea of **betaCode** is borrowed from the Classicists who developed ["a method of representing, using only ASCII characters, characters and formatting found in ancient Greek texts"](http://en.wikipedia.org/wiki/Beta_Code). The current **betaCode** is inspired by, and is therefore quite similar to, the [arabTex scheme](http://www2.informatik.uni-stuttgart.de/ivi/bs/research/arab_e.htm). Linguists working with Arabic are commonly using [Buckwalter transliteration](http://en.wikipedia.org/wiki/Buckwalter_transliteration), which is very similar to the current betaCode, but less readable. 

## betaCode and One-To-One Transliteration

| betacode | translit | Arabic letter |
|----------|-----------------|---------------|
| **\_a** | ā | *alif* |
| **b** | b | *bāʾ* |
| **t** | t | *tāʾ* |
| **\_t** | ṯ | *thāʾ* |
| **^g, j** | ǧ | *jīm* |
| **\*h** | ḥ | *ḥāʾ* |
| **\_h** | ḫ | *khāʾ* |
| **d** | d | *dāl* |
| **\_d** | ḏ | *dhāl* |
| **r** | r | *rā’* |
| **z** | z | *zayn* |
| **s** | s | *sīn* |
| **^s** | š | *shīn* |
| **\*s** | ṣ | *ṣād* |
| **\*d** | ḍ | *ḍād* |
| **\*t** | ṭ | *ṭāʾ* |
| **\*z** | ẓ | *ẓāʾ* |
| **`** | ʿ | *‘ayn* |
| **\*g** | ġ | *ghayn* |
| **f** | f | *fāʾ* |
| **\*k, q** | ḳ | *qāf* |
| **k** | k | *kāf* |
| **l** | l | *lām* |
| **m** | m | *mīm* |
| **n** | n | *nūn* |
| **h** | h | *hā’* |
| **w** | w | *wāw* |
| **\_u** | ū | *wāw* |
| **y** | y | *yāʾ* |
| **\_i** | ī | *yāʾ* |

## Non-alphabetic letters
| **betacode** | translit | Arabic |
|----------|-----------------|---------------|
| **'** | ʾ | *ḥamzaŧ* |
| **/a** | á | *alif maqṣūraŧ* |
| **=t** | ŧ | *tāʾ marbūṭaŧ* |

## Vowels

| **betacode** | translit | Arabic |
|----------|-----------------|---------------|
| **~a** | ã | *dagger alif* |
| **u** | u | *ḍammaŧ* |
| **i** | i | *kasraŧ* |
| **a** | a | *fatḥaŧ* |
| **\*n** | ȵ | *n* of *tanwīn* |
| **\*a** | å | *silent alif* |
| **\*w** | ů | *silent wāw* |
| **?u** | ủ | final *ḍammaŧ* \* |
| **?i** | ỉ | final *kasraŧ* \* |
| **?a** | ả | final *fatḥaŧ* \* |

\* “finals” are those final vowels that are usually dropped in transliteration and pronounciation (i.e., *al-kitāb*, instead of *al-kitābủ*, *al-kitābỉ*, *al-kitābả*), vs those that are not (*huwa*, *hiyya*, *ḏãlika*, *tilka*).

## Basic principles:
Every Arabic letter is betaCoded with its one-letter equivalent,
preceded (if necessary) with a technical character that is similar to a diacritical mark in the transliterated version. Thus, most common symbols are as follows:

#### *General*
* **\_** (underscore), if a letter can be transliterated with *macron*/*breve* below or above (*ā*, *ṯ*, *ḫ*, *ḏ*, *ū*, *ī*)
* **\*** (asterisk), if a letter can be transliterated transliterated with *dot* below or above (*ḥ*, *ṣ*, *ḍ*, *ṭ*, *ẓ*, *ġ*, *ḳ*)
* **^** (caret), if a letter can be transliterated with *caron* (*ǧ*, *š*)

#### *Specifics*
* attached prepositions/conjunctions and pronominal suffixes must be separated with “-” (mostly relevant for text alignment, treebanking,  and general readability):
	* ``` fa-_dahaba ```
* add “?” before “optional” final vowels that are usually dropped in transliteration and pronounciation (mostly relevant  for transliteration):
	* ``` bi-Llah?i  ```, but not:
	* ``` fa-_dahaba ```	
* *tāʾ marbūṭaŧ*: add “+” after *tāʾ marbūṭaŧ*, if the first word of *iḏāfaŧ* (mostly relevant for transliteration):
	* ``` `_amma:t+u Ba.gd_ada ```, but:
	* ``` al-`_amma:tu f_i Ba.gd_ada ```
* transliterating *tanwīn*:
	* ```*n```
		* ```?u*n```
		* ```?i*n```
		* ```?a*n```
* silent *wāw* and *alif*:
	* `*w` (`Amr?u*n*w`, for <span="arabic">عَمْرٌو</span>)
	* `*a` (```wa-fa`al_u*a```, for <span="arabic">وَفَعَلُوا</span>)

## Running the converter
* (Python 3.xx must be installed on the machine)
* clone [git repository](https://github.com/PerseusDL/ArabicBetacode)
* save texts that must be transliterated (i.e., the text is in English, but has some Arabic terms that must be transliterated) into ```./to_translit/``` (follow the format given in the example file).
* save texts that must be fully transliterated or/and converted into Arabic script (i.e., the entire texts is in Arabic) into ```./to_arabic/``` (follow the format given in the example file).
* run the script `_generateBetaCode.py` (in Mac terminal: ```python3 _generateBetaCode.py```; on Windows: double-click on the script should work).
* converted texts (in all available modes of conversion) will be appended to the file.
* if you need to make any changes, edit your initial betaCode text and run the script again, converted results will be replaced with relevant updated versions.

# Examples 

### betaCode Example

**NB**: These are examples of converting betaCode to full transliteration and Arabic script. The very last paragraph showcases conversion of *ḥamzaŧ* in different positions.

q\_ala 'ab\_u Mas\`\_ud?i\*n :: 'an\_a qad sami\`tu h~a\_d\_a min ras\_ul?i All~ah?i ( \*sl\`m )

\*hadda\_ta-n\_a \`Amr?u\*w bn?u R\_afi\`?i\*n , \*hadda\_ta-n\_a \`Abd?u All~ah?i bn?u al-Mub\_arak?i , \`an Mu\*hammad?i bn?i 'Is\*h\_aq?a , \`an Mu\*hammad?i bn?i ^Ga\`far?i\*n , \`an \`Ubayd?i All~ah?i bn?i \`Abd?i All~ah?i bn?i \`Umar?a , \`an 'Ab\_i-hi , \`an?i al-Nabiyy?i ( \*sl\`m ) na\*hwa-hu

'a\_hbara-n\_a Qutayba:t?u q\_ala , \*hadda\_ta-n\_a Sufy\_an?u , \`an Ya\*hy/a bn?i Sa\`\_id?i\*n , \`an 'Ab\_i Bakr?i bn?i Mu\*hammad?i\*n , \`an \`Umar?a bn?i \`Abd?i al-\`Az\_iz?i , \`an 'Ab\_i Bakr?i bn?i \`Abd?i al-Ra\*hm~an?i bn?i al-\*H\_ari\_t?i bn?i Hi^s\_am?i\*n , \`an 'Ab\_i Hurayra:t?a mi\_tla-hu

**Ta\*hw\_il?u al-\*hamza:t?i ( kalim\_at?u\*n mufrada:t?u\*n )**

'amr?u\*n 'uns?u\*n 'ins?u\*n '\_im\_an?u\*n
'\_aya:t?u\*n '\_amana mas'ala:t?u\*n sa'ala ra's?u\*n qur'\_an?u\*n ta'\_amara
\_di'b?u\*n as'ila:t?u\*n q\_ari'i-hi su'l?u\*n mas'\_ul?u\*n
tak\_afu'u-hu su'ila q\_ari'i-hi \_di'\_ab?u\*n ra'\_is?u\*n
bu'isa ru'\_uf?u\*n ra'\_uf?u\*n su'\_al?u\*n mu'arri\_h?u\*n
abn\_a'a-hu abn\_a'u-hu abn\_a'i-hi ^say'?a\*n \_ha\*t\_i'a:t?u\*n
\*daw'u-hu \*d\_u'u-hu \*daw'a-hu \*daw'i-hi mur\_u'a:t?u\*n
'abn\_a'i-hi bar\_i'u-hu s\_u'ila f\_il?u\*n f\_ann?u\*n f\_unn?u\*n
s\_a'ala fu'\_ad?u\*n ^surak\_a'u-hu ri'\_asa:t?u\*n tahni'a:t?u\*n
daf\_a'a:t?u\*n \*taff\_a'a:t?u\*n ta'r\_i\_h?u\*n fa'r?u\*n
^say'?u\*n ^say'?i\*n ^say'?a\*n  \*daw'?u\*n \*daw'?i\*n \*daw'?a\*n
juz'?u\*n  juz'?i\*n  juz'?a\*n mabda'?u\*n mabda'?i\*n mabda'?a\*n
naba'a q\_ari'?u\*n tak\_afu'?u\*n tak\_afu'?i\*n tak\_afu'?a\*n
abn\_a'u abn\_a'i abn\_a'a jar\_i'?u\*n maqr\_u'?u\*n \*daw'?u\*n ^say'?u\*n juz'?u\*n
\`ulam\_a'u al-\`ulam\_a'i al-\`ulam\_a'a \`Amr?u\*n\*w wa-fa\`al\_u\*a

## betaCode converted into one-to-one translit

ḳāla ʾabū Masʿūdỉȵ :: ʾanā ḳad samiʿtu hãḏā min rasūlỉ Allãhỉ ( ṣlʿm )

ḥaddaṯa-nā ʿAmrủů bnủ Rāfiʿỉȵ , ḥaddaṯa-nā ʿAbdủ Allãhỉ bnủ al-Mubārakỉ , ʿan Muḥammadỉ bnỉ ʾIsḥāḳả , ʿan Muḥammadỉ bnỉ Ǧaʿfarỉȵ , ʿan ʿUbaydỉ Allãhỉ bnỉ ʿAbdỉ Allãhỉ bnỉ ʿUmarả , ʿan ʾAbī-hi , ʿanỉ al-Nabiyyỉ ( ṣlʿm ) naḥwa-hu

ʾaḫbara-nā Ḳutaybaŧủ ḳāla , ḥaddaṯa-nā Sufyānủ , ʿan Yaḥyá bnỉ Saʿīdỉȵ , ʿan ʾAbī Bakrỉ bnỉ Muḥammadỉȵ , ʿan ʿUmarả bnỉ ʿAbdỉ al-ʿAzīzỉ , ʿan ʾAbī Bakrỉ bnỉ ʿAbdỉ al-Raḥmãnỉ bnỉ al-Ḥāriṯỉ bnỉ Hišāmỉȵ , ʿan ʾAbī Hurayraŧả miṯla-hu

**Taḥwīlủ al-ḥamzaŧỉ ( kalimātủȵ mufradaŧủȵ )**

ʾamrủȵ ʾunsủȵ ʾinsủȵ ʾīmānủȵ
ʾāyaŧủȵ ʾāmana masʾalaŧủȵ saʾala raʾsủȵ ḳurʾānủȵ taʾāmara
ḏiʾbủȵ asʾilaŧủȵ ḳāriʾi-hi suʾlủȵ masʾūlủȵ
takāfuʾu-hu suʾila ḳāriʾi-hi ḏiʾābủȵ raʾīsủȵ
buʾisa ruʾūfủȵ raʾūfủȵ suʾālủȵ muʾarriḫủȵ
abnāʾa-hu abnāʾu-hu abnāʾi-hi šayʾảȵ ḫaṭīʾaŧủȵ
ḍawʾu-hu ḍūʾu-hu ḍawʾa-hu ḍawʾi-hi murūʾaŧủȵ
ʾabnāʾi-hi barīʾu-hu sūʾila fīlủȵ fānnủȵ fūnnủȵ
sāʾala fuʾādủȵ šurakāʾu-hu riʾāsaŧủȵ tahniʾaŧủȵ
dafāʾaŧủȵ ṭaffāʾaŧủȵ taʾrīḫủȵ faʾrủȵ
šayʾủȵ šayʾỉȵ šayʾảȵ  ḍawʾủȵ ḍawʾỉȵ ḍawʾảȵ
ǧuzʾủȵ  ǧuzʾỉȵ  ǧuzʾảȵ mabdaʾủȵ mabdaʾỉȵ mabdaʾảȵ
nabaʾa ḳāriʾủȵ takāfuʾủȵ takāfuʾỉȵ takāfuʾảȵ
abnāʾu abnāʾi abnāʾa ǧarīʾủȵ maḳrūʾủȵ ḍawʾủȵ šayʾủȵ ǧuzʾủȵ
ʿulamāʾu al-ʿulamāʾi al-ʿulamāʾa ʿAmrủȵů wa-faʿalūå

### betaCode converted into arabic script

<p class="arabic">
	
قَالَ أَبُو مَسْعُودٍ :: أَنَا قَدْ سَمِعْتُ هٰذَا مِنْ رَسُولِ الـلّٰـهِ ( صْلْعْمْ )

</p>
<p class="arabic">
حَدَّثَنَا عَمْرُو بْنُ رَافِعٍ ، حَدَّثَنَا عَبْدُ الـلّٰـهِ بْنُ الْمُبَارَكِ ، عَنْ مُحَمَّدِ بْنِ إِسْحَاقَ ، عَنْ مُحَمَّدِ بْنِ جَعْفَرٍ ، عَنْ عُبَيْدِ الـلّٰـهِ بْنِ عَبْدِ الـلّٰـهِ بْنِ عُمَرَ ، عَنْ أَبِيهِ ، عَنِ النَّبِيِّ ( صْلْعْمْ ) نَحْوَهُ
</p>
<p class="arabic">
أَخْبَرَنَا قُتَيْبَةُ قَالَ ، حَدَّثَنَا سُفْيَانُ ، عَنْ يَحْيٰى بْنِ سَعِيدٍ ، عَنْ أَبِي بَكْرِ بْنِ مُحَمَّدٍ ، عَنْ عُمَرَ بْنِ عَبْدِ الْعَزِيزِ ، عَنْ أَبِي بَكْرِ بْنِ عَبْدِ الرَّحْمٰنِ بْنِ الْحَارِثِ بْنِ هِشَامٍ ، عَنْ أَبِي هُرَيْرَةَ مِثْلَهُ
</p>
<p class="arabic">
<b>
تَحْوِيلُ الْحَمْزَةِ ( كَلِمَاتٌ مُفْرَدَةٌ )
</b>
</p>
<p class="arabic">
أَمْرٌ أُنْسٌ إِنْسٌ إِيمَانٌ
آيَةٌ آمَنَ مَسْأَلَةٌ سَأَلَ رَأْسٌ قُرْآنٌ تَآمَرَ
ذِئْبٌ أَسْئِلَةٌ قَارِئِهِ سُؤْلٌ مَسْؤُولٌ
تَكَافُؤُهُ سُئِلَ قَارِئِهِ ذِئَابٌ رَئِيسٌ
بُئِسَ رُؤُوفٌ رَؤُوفٌ سُؤَالٌ مُؤَرِّخٌ
أَبْنَاءَهُ أَبْناؤُهُ أَبْنائِهِ شَيْئًا خَطِيئَةٌ
ضَوْءُهُ ضُوؤُهُ ضَوْءَهُ ضَوْئِهِ مُرُوءَةٌ
أَبْنائِهِ بَرِيؤُهُ سُوئِلَ فِيلٌ فَانٌّ فُونٌّ
سَاءَلَ فُؤَادٌ شُرَكاؤُهُ رِئَاسَةٌ تَهْنِئَةٌ
دَفَاءَةٌ طَفّاءَةٌ تَأْرِيخٌ فَأْرٌ
شَيْءٌ شَيْءٍ شَيْئًا  ضَوْءٌ ضَوْءٍ ضَوْءًا
جُزْءٌ  جُزْءٍ  جُزْءًا مَبْدَأٌ مَبْدَأٍ مَبْدَأً
نَبَأَ قَارِئٌ تَكَافُؤٌ تَكَافُؤٍ تَكَافُؤًا
أَبْناءُ أَبْناءِ أَبْناءَ جَريءٌ مَقْروءٌ ضَوْءٌ شَيْءٌ جُزْءٌ
عُلَماءُ الْعُلَماءِ الْعُلَماءَ عَمْرٌو وَفَعَلُوا
</p>

## betaCode into Translit

### betaCode in English text

NB: This is an example of the English text with terms, names and toponyms given in betaCode and automatically converted into different transliteration flavors (exerpts are from Brill’s *Encyclopaedia of Islam*).

Dima^s\*k, Dima^s\*k al-^S\_am or simply al-^S\_am , (Lat. Damascus, Fr. Damas) is the largest city of Syria. It is situated ... very much at the same latitude as Ba\*gd\_ad and F\_as, at an altitude of nearly 700 metres, on the edge of the desert at the foot of ^Gabal \*K\_asiy\_un.

al-\_Dahab\_i, ^Sams al-D\_in Ab\_u \`Abd All~ah Mu\*hammad b. \`U\_tm\_an b. \*K\_aym\_a\*z b. \`Abd All~ah al-Turkum\_an\_i al-F\_ari\*k\_i al-Dima^s\*k\_i al-^S\_afi\`\_i, an Arab historian and theologian, was born at Damascus or at Mayy\_afari\*k\_in on 1 or 3 Rab\_i\` II (according to al-Kutub\_i, in Rab\_i\` I) 673/5 or 7 October 1274, and died at Damascus, according to al-Subk\_i and al-Suy\_u\*t\_i, in the night of Sunday-Monday on 3 \_D\_u al-\*Ka\`da:t 748/4 February 1348, or, according to A\*hmad b. \`Iy\_as, in 753/1352-3. He was buried at the B\_ab al-\*Sa.g\_ir.

### betaCode converted into one-to-one translit

Dimašḳ, Dimašḳ al-Šām or simply al-Šām , (Lat. Damascus, Fr. Damas) is the largest city of Syria. It is situated ... very much at the same latitude as Baġdād and Fās, at an altitude of nearly 700 metres, on the edge of the desert at the foot of Ǧabal Ḳāsiyūn.

al-Ḏahabī, Šams al-Dīn Abū ʿAbd Allãh Muḥammad b. ʿUṯmān b. Ḳāymāẓ b. ʿAbd Allãh al-Turkumānī al-Fāriḳī al-Dimašḳī al-Šāfiʿī, an Arab historian and theologian, was born at Damascus or at Mayyāfariḳīn on 1 or 3 Rabīʿ II (according to al-Kutubī, in Rabīʿ I) 673/5 or 7 October 1274, and died at Damascus, according to al-Subkī and al-Suyūṭī, in the night of Sunday-Monday on 3 Ḏū al-Ḳaʿdaŧ 748/4 February 1348, or, according to Aḥmad b. ʿIyās, in 753/1352-3. He was buried at the Bāb al-Ṣaġīr.

### betaCode converted into the Library of Congress scheme

Dimashq, Dimashq al-Shām or simply al-Shām , (Lat. Damascus, Fr. Damas) is the largest city of Syria. It is situated ... very much at the same latitude as Baghdād and Fās, at an altitude of nearly 700 metres, on the edge of the desert at the foot of Jabal Qāsiyūn.

al-Dhahabī, Shams al-Dīn Abū ʿAbd Allāh Muḥammad b. ʿUthmān b. Qāymāẓ b. ʿAbd Allāh al-Turkumānī al-Fāriqī al-Dimashqī al-Shāfiʿī, an Arab historian and theologian, was born at Damascus or at Mayyāfariqīn on 1 or 3 Rabīʿ II (according to al-Kutubī, in Rabīʿ I) 673/5 or 7 October 1274, and died at Damascus, according to al-Subkī and al-Suyūṭī, in the night of Sunday-Monday on 3 Dhū al-Qaʿda 748/4 February 1348, or, according to Aḥmad b. ʿIyās, in 753/1352-3. He was buried at the Bāb al-Ṣaghīr.

### betaCode converted into a searcheable string (diacritics removed)

Dimashq, Dimashq al-Sham or simply al-Sham , (Lat. Damascus, Fr. Damas) is the largest city of Syria. It is situated ... very much at the same latitude as Baghdad and Fas, at an altitude of nearly 700 metres, on the edge of the desert at the foot of Jabal Qasiyun.

al-Dhahabi, Shams al-Din Abu Abd Allah Muhammad b. Uthman b. Qaymaz b. Abd Allah al-Turkumani al-Fariqi al-Dimashqi al-Shafii, an Arab historian and theologian, was born at Damascus or at Mayyafariqin on 1 or 3 Rabi II (according to al-Kutubi, in Rabi I) 673/5 or 7 October 1274, and died at Damascus, according to al-Subki and al-Suyuti, in the night of Sunday-Monday on 3 Dhu al-Qada 748/4 February 1348, or, according to Ahmad b. Iyas, in 753/1352-3. He was buried at the Bab al-Saghir.
