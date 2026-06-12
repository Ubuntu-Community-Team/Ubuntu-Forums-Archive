---
title: "No puc entrar a Windows després de formatejar"
date: 2007-04-09
forum: Catalan Team
---

### Post by _61_ on 2007-04-09
Hola a tots,

He enviat aquest missatge al forum anglès, però em sembla que tindré més sort si ho envïo aquí.

Tinc el Windows en una partició a /media/hda1/.

Tinc una còpia de seguretat de /media/hda1/ en un disc dur extern.

He volgut formatejar aquesta partició a ext3 i aleshores he restaurat els arxius des de la còpia. No he pogut arrencar el Windows.

Ara he tornat a formatejar en Fat32 i he tornat a restaurar els arxius... Però encara no puc arrencar Windows :( Es queixa de que el disc no és "a bootable disc"

Algú em pot ajudar?

---

### Post by CarlesOriol on 2007-04-09
Engega amb el disc d'inici del windows en mode de consola de recuperació i executes:
fixmbr i fixboot

---

### Post by _61_ on 2007-04-09
Moltes gràcies Carles Oriol,

Com que ja ho he arreglat, explico el que he fet...

Els del fòrum anglès m'han donat el mateix consell que tu. El que passa és que al fer la còpia de seguretat, només he copiat els arxius, i al formatejar m'he carregat el sector d'inici de la partició, a part dels arxius. (Això és el que m'han dit i ho explico per si algú curiós vol saber què passava. Jo de vegades llegeixo els problemes d'altra gent per aprendre...)

He intentat fer això que dius, però el Cd de recovery que em venia amb l'ordinador només tenia la opció de recuperar lordinador tal com el vaig comprar (tinc el windows que em venia quan vaig comprar l'ordinador).

Quin remei. He restaurat el Windows que em venia de la botiga i després he restaurat la meva còpia de seguretat a sobre. La cosa sembla que ha funcionat bé.

Moltes gràcies de totes formes. Repeteixo el que he dit en el fòrum anglès , "You are the best!"

---

### Post by orestesmas on 2007-04-09
> **_61_ said:**
> Moltes gràcies Carles Oriol,

Com que ja ho he arreglat, explico el que he fet...



Anava a ficar-hi cullerada, però ara que ja ho has arreglat només se m'acut dir que d'antuvi quan he vist el títol del fil ("No puc entrar a Windows després de formatejar") he pensat: Contesta-li que ara és l'ocasió per deixar el windows definitivament... :-D

---

### Post by _61_ on 2007-04-10
De fet, la única raó per la que volia recuperar el Windows és perquè de moment, la declaració d'iva i la declaració de la renta i aquestes coses, no m'he atrevit a fer-ho amb el Linux. Les altres coses les faig totes en Linux...

De totes formes, els moments en que la meva dona i jo vam pensar que havíem perdut el Windows per sempre més va servir per adonar-nos que no passa res. En realitat, potser l'enviarem a pastar fang voluntariament... En aquest cas, també haurà estat veritat allò de que no valores de veritat una cosa fins que la perds... ;)

---

### Post by CarlesOriol on 2007-04-10
Mestre 61.

Els forums son una gran eïna però per "angoixes" com la teva el proper cop et recomano que t'instal·lis el xchat i et conectis al **IRC** #**ubuntu**-cat de **freenode**. Allà sempre hi ha algú (si no pots anar a #**ubuntu** - en angles-). 

T'haguessim pogut ajudar més directament.

El consell de l'Orestes és realment bó... quan acabis de perdre la por a l'ubuntu i t'hi sentis segur veuras que aquest sistema que ara tens si l'elimines guanyes molt d'espai al disc. ;-)

---

