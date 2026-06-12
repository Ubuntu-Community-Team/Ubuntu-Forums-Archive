---
title: "Ubuntu mig en català mig en anglès"
date: 2007-05-14
forum: Catalan Team
---

### Post by Aljullu on 2007-05-14
M'he instal·lat l'Ubuntu 7.04, durant la instal·lació ja li vaig dir en català, però utilitzant el SO moltes coses em surten en anglès (la gran majoria), fins i tot el Firefox. Però per exemple, la data, em surt en català.

A què és degut? Què puc fer per a sol·lucionar-ho? Gràcies.

---

### Post by PellRoja on 2007-05-14
hola aljullu :P

doncs has de anar a sistema administració> suport d 'idioma i afegir de suport, el català.

---

### Post by patrickfromspain on 2007-05-14
sudo apt-get install language-support-ca

---

### Post by Aljullu on 2007-05-15
> **PellRoja said:**
> hola aljullu :P

doncs has de anar a sistema administració> suport d 'idioma i afegir de suport, el català.

Quan hi vaig em diu:
[INDENT]
Only one software management tool is allowed to run at the same time

Please close the other application e.g. "Update Manager", "aptitude" or "Synaptic" at first.[/INDENT]

Si entro al "Add/Remove..." de "Applications", escolleixo un programa i li dic "Apply" em diu:
[INDENT]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/INDENT]

Aquest mateix missatge em surt només obrir el "Gestor de paquest Synaptic".

És que, com bé sabràs Pell Roja, no porto ni tres dies a l'Ubuntu.

> sudo apt-get install language-support-ca
:confused: Què és això? S'ha de posar al terminal?:( 

Gràcies.

---

### Post by Aljullu on 2007-05-15
Problema sol·lucionat. Tot i això "Applications", "Places" i "System" surten en anglès. És normal?

Gràcies.

---

### Post by PellRoja on 2007-05-15
> **Aljullu said:**
> Problema sol·lucionat. Tot i això "Applications", "Places" i "System" surten en anglès. És normal?

Gràcies.

has reiniciat? a mi fins que no vaig reiniciar crec que em seguia sortin applications system i places

;)

---

### Post by muleta on 2007-08-25
A mi no em funciona el consell de Patrickfromspain.

Fins i tot he instal·lat un altre programa del repositori que fa suport de llenguatge. 

També he anat canviant d'idioma, n'he descarregat d'altres, reiniciant cada vegada que canviaba i res. Al final ja començo a aprendre el britànic i li agafaré "carinyo".

---

### Post by muleta on 2007-08-25
Mireu què diu:

---

### Post by pespin on 2007-08-25
Com diu al screenshot, ja el tens instal·lat. El que passa que segurament deus tindre activat el anglès o té és prioritat que altres idiomes. Això es canvia toquetejant per **administració> suport d 'idioma** em sembla, no t'ho pucn dir segur perquè no tinc un Gnome a mà

---

### Post by muleta on 2007-08-25
Sí, és el primer que he fet. Tenia posat el català com a llenguatge per defecte. Potser perque ho havia indicat en fer la instal·lació.

He baixat el suport per a altres idiomes i també per al català, he canviat el per defecte, he reiniciat...

Com que em tornava a sortir en anglès, tot i que déia que tenia configurat el català per defecte, he seguit el consell de Patrickfromspain, he reiniciat, he canviat per l'italià, he reiniciat... i m'ha tornat a sortir mig en anglès.

Provaré l'spanish...

---

### Post by muleta on 2007-08-25
Arreglat: tinc instal·lat el català d'Andorra.

---

### Post by CarlesOriol on 2007-08-26
El català ca_AD, ca_IT i ca_FR té problemes que han estat corretgits per en Toni Hermoso i que podrem usar a la propera versió (gutsy). De moment si no vols problemes (en kde per exemple) cal que posis ca_ES. (no em fot p. gràcia però sinó no funciona bé).

Per cert amb la primera suggerencia d'en Pellroja n'hi hauria d'haver prou.

------------------------------------------------------

Al servidor de caliu podeu trobar una versió feta pel loco pre-catalanitzada per que en properes insta&#320;lacions us funcioni en català totalment de bon començament.

[IMG]https://wiki.ubuntu.com/CatalanTeam/ApprovalApplication?action=AttachFile&do=get&target=feistycat.jpg[/IMG]

---

### Post by oostap on 2007-08-26
Bones!!!

Jo vaig fer l'instal·lació en castellà i per passar a català vaig instal·lar els següents paquets:
aspell-ca language-pack-ca language-pack-ca-base language-pack-gnome-ca language-pack-gnome-ca-base language-support-ca mozilla-firefox-locale-ca myspell-ca openoffice.org-l10n-ca thunderbird-locale-ca

Per jo diria que només amb mozilla-firefox-locale-ca i openoffice.org-l10n-ca el teu problema es te que solucionar...

---

### Post by Aljullu on 2007-10-19
Bé, ara que torno a passar-me per aquests fòrums, i veient que no havia tornat a respondre (ho sento) dir-vos que sí, que al final teníeu raó i ara ja està tot en català!

Moltes gràices!

---

### Post by muleta on 2007-10-20
> **Aljullu said:**
>  ara ja està tot en català!


Vols dir que amb el Gutsy està tot traduït? Tot, tot i tot, absolutament?.

---

### Post by Aljullu on 2007-10-20
> **Aljullu said:**
> Bé, ara que torno a passar-me per aquests fòrums, i veient que no havia tornat a respondre (ho sento) dir-vos que sí, que al final teníeu raó i ara ja està tot en català!

Moltes gràices!
El Gusty és el 7.04?

Bé, tot tot no, però la major part sí.

---

### Post by SiscoGarcia on 2007-10-24
Ja tinc instal·lat el Gutsy de forma dual (amb el finestres) en dues màquines a partir del Feisty i ara l'he instal·lat des de CD (de nou) en una màquina vella només el Gutsy i he aconseguit tenir-lo només en català.
Havia començat anit i només havia aconseguit que se m'instal·lés mig en català mig en anglès, El que havia fet llavors és consultar el fòrum i fer allò que ja havia pensat (sistema/administració/suport d'idioma i també fer servir l'apt...), però no me'n sortia; el tornava a reinstal·lar i tornava a passar-me el mateix. Havia pensat d'instal·lar Feisty i després actualitzar-me a Gutsy, però em sabia greu anar així, i aquest matí he pensat deredimensionar el disc dur amb el GParted i desfer-lo tot, per tal d'instal·lar-hi després només l'ubuntu Gutsy. Aquest cop me n'he sortit. No sé si pot ser útil a algú, espero que sí.

---

