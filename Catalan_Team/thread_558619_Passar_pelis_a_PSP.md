---
title: "Passar pelis a PSP"
date: 2007-09-24
forum: Catalan Team
---

### Post by xoldy on 2007-09-24
Bones tardes a tots,
voldria saber si algú de vosaltres ha tingut l'oportunitat de passar-se pelis a la PSP de Sony. He estat llegint algun fòrum per la xarxa, però allò que he llegit no m'ha molat molt.
Em refio més dels meus compatriotes.

Com podeu imaginar no és un tema vital per l'existència humana, però fa passar l'estona...

Moltes gràcies, com sempre a tots els que feu que tingui cada vegada més ganes d'oblidar les finestres pay per use.
De fet, ja no tinc l'engegada dual güindous-Ubuntu, sinò que tinc l'engegada Ubuntu Feisty UOC distro - Ubunty Gutsy (que te molt bona pinta per cert)

Siau

---

### Post by CarlesOriol on 2007-09-24
Per els que no tenim PSP si ens dones una pista de quin format usa igual et podem ajudar.

---

### Post by xoldy on 2007-09-25
Perdoneu, de vegades m'oblido del que es fonamental. El format de pelis els mp4 i la resolució màxima que permet és 480x272 que és la mida de la pantalla.

He vist pels fòrums un programet que es diu pspvc però no m'acabo de refiar.

Moltes gràcies

---

### Post by CarlesOriol on 2007-09-25
> **xoldy said:**
> Perdoneu, de vegades m'oblido del que es fonamental. El format de pelis els mp4 i la resolució màxima que permet és 480x272 que és la mida de la pantalla.
s

A veure si això funciona:

mencoder -vf scale=480:272 -ovc lavc -lavcopts vcodec=mpeg4:threads=2:vbitrate=350 -oac mp3lame -lameopts mode=1:cbr:br=48 entra.avi -o surt.psp.av

(canvia entra.avi i surt.psp.avi al teu gust)

---

### Post by xoldy on 2007-09-25
Per passar pelis de DVD a divx per exemple quin programa utilitzes?
Merci

---

### Post by xoldy on 2007-09-29
Bones a tots cercant i rebuscant, he aconseguit amb el wine i amb la darrera actualització a Gutsy, que em funcioni una bonica versió de programari que es diu DVDFab platinum per aquell sistema lleig i antic, de la que m'agradaria conèixer la versió per a Linux (no existeix de moment).
Et fa la conversió directa a format PSP, etc.
Només us ho volia fer saber per si és útil a algú.
M'agradaria anar a la GrescaGutsy, però tinc panorama familiar complicat per cangurs, etc..
Espero que tot vagi molt bé.
Cada vegada em trobo més de gust en aquesta comunitat que pel nom no pots jutjar mai (LoCo Team) ;-)
Siau

---

### Post by papapep on 2007-09-29
> en aquesta comunitat que pel nom no pots jutjar mai (LoCo Team)

Això ho dius perquè encara no ens has vist en acció.... :-D

---

### Post by pixatintes on 2007-10-01
Jo faig servir aquesta utilitat, [PSP Video Converter]("http://pspvc.sourceforge.net/").

Es només per això, els format h264 no m'els reconeix, pero els mpeg4 si.
Has de mirar de marcar bé el format i despres passes el video a la carpeta video. (Jo tinc el firm 3.40 OE)

Sort,
pixatintes

---

### Post by CarlesOriol on 2007-10-01
Aquest programa és una interficie gràfica al ffmpeg. 
Vigila ja que l'arxiu que ofereixen per descarregar inclou una versió estàtica del ffmpeg i pot donar-te conflictes amb altres programes a la llarga.

---

### Post by xoldy on 2007-10-01
Moltes gràcies a tots tres, em poso mans a l'obra amb el programa pspvc. Com que tinc una distro instal·lada per anar "jugant" doncs no em fa por anar fent proves.

Salut per tots

---

