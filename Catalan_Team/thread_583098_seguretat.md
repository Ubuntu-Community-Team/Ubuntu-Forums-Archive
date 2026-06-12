---
title: "seguretat"
date: 2007-10-20
forum: Catalan Team
---

### Post by muleta on 2007-10-20
El gestor d'actualitzacions m'ha notificat que ja existeix la versió 7.10 i m'ha preguntat si vull actualitzar. Ho he intentat unes 12 vegades peró, cap al final, s'interromp el procés perque m'indica que falta espai en el disc, concretament a "/".

He anat eliminant programes i aplicacions fins a deixar-hi només el sistema operatiu (Feisty Fawn), però es torna a interrompre. El meu disc és de 120 Gb i trobo molt estrany que no hi hagi prou espai.

Penso que potser vaig fer malament les particions, que potser hi va quedar alguna cosa de Windows, tot i que la instal·lació d'ubuntu em va dir que formataria HD.

Intueixo que també hi pot haver quedat algun error causat per tota la porqueria que el primer SO havia introduït en el meu pc. També he sospitat sempre que hi pugui haver algun error de hardware.

Penso que seria bó formatejar-lo i instal·lar el Gutsy Gibbon en un entorn net.

Coneixeu alguna eina que em permeti netejar bé el disc i optimitzar-lo abans de la nova instal·lació?.

---

### Post by papapep on 2007-10-20
> Penso que potser vaig fer malament les particions,

Això ens ha passat a tots algun dia. Enganxa el /etc/fstab.

> Intueixo que també hi pot haver quedat algun error causat per tota la porqueria que el primer SO havia introduït en el meu pc.


Ves a Administració > Partition Editor i passan's una captura de pantalla amb el que hi surti.

---

### Post by muleta on 2007-10-20
> **papapep said:**
>  Enganxa el /etc/fstab.



Què és això?.

Aquí teniu la captura de l'editor de particions:

---

### Post by papapep on 2007-10-20
És el fitxer *fstab* que és dins el directori */etc*.

Si fas :

```
cat /etc/fstab
```

Podràs visualitzar el seu contingut i enganxar-lo.

Respecte el particionat, t'has adonat que tens dues particions de swap??

Respecte la capacitat del teu disc dur, encara que sigui de 120 Gb si en dediques 95 Gb al home, i la resta al punt de muntatge arrel, swap i demés, doncs és probable que si, a més,  instal·les moltes aplicacions faci's curt d'espai a /usr/bin o /usr/local/bin o a /opt que és on gairebé sempre s'instal·len.

---

### Post by muleta on 2007-10-20
No entenc res d'això que surt:

---

### Post by papapep on 2007-10-20
Això que has enganxat del /etc/fstab, són els punts de muntatge que té definits el teu ordinador. Dit d'altra manera, a quina partició correspon ser la arrel, per exemple, o quina serà la swap (no només per que la creïs al particionar el sistema operatiu li assigna aquesta tasca, cal que li diguis a aquest fitxer) o amb quina ha d'intentar arrencar el grub, quina serà la swap, si seran només llegibles o també hi podràs escriure, etc.

Com t'he dit abans, tens problemes d'espai al directori arrel (on tens el sistema operatiu excepte el directori /home) perquè només li has deixat 4 Gb d'espai. Aquesta mida, si no instal·les massa coses no és poc, però si fas el contrari doncs es queda curt aviat.

Ah, oblida el tema de que et quedi "porqueria que el primer SO havia introduït en el meu pc". No tens cap partició NTFS ni FAT32, amb el qual ja no tens res d'allò.

---

### Post by muleta on 2007-10-21
Sí, noi, hi tinc un bon embolic pero, ara no trobo la manera d'arreglar-ho. He d'arreglar això de les particions quan actualitzi a 7.10?. Em donarà l'opció guiada de redistribuir l'espai?.

És que he consultat tots els tutorials que vaig descarregar i imprimir de linux bàsic però no m'hi entenc tant bé com quan m'ho expliqueu vosaltres.

---

### Post by sianeu on 2007-10-21
Durant l'instal·laciò, quan et demani còm vols fer les particions, escolleig "manualment". Et sortirà un gràfic semblant al que tu has postejat. Fent clic amb el botò dret sobre les particions o espais del rectangle que simbolitza el disc dur, podras anar crean o destruint particions al teu gust.

Tal com ho tens, una manera sencilla seria:
1- Borrar la primera particiò. Això et deixerà un espai sense asignar de més de 10Gb.

2- Utilitzar aquest espai per a crear una particiò (primaria, ext3) per instal.lar el sistema (punt de muntatge: "/").

3- Eliminar les dues particions swap.

4- Crear una swap de 1Gb (en tens de sobres)

5- Amb l'espai restant crea un altre particiò (ext3 o FAT32)

6- Si vols que la particiò gran sigui la /home només l'has de editar i dir-li (punt de muntatje: /home). Si no et deixarà el /home dins la particiò principal (/) i aquesta particiò gran et quedaria com a particiò de dades.

Salut

---

### Post by muleta on 2007-10-21
Gràcies però no ho acabo d'entendre. Em parles de refer les particions quan faci l'instal·lació, no durant l'actualització.

Això vol dir que no les puc modificar abans i actualitzar?. Que no hi ha un accés a actualitzar reparant l'error de particions?.

---

### Post by patrickfromspain on 2007-10-21
aixo t'ho va fer l'insta&#322;lador tot sol? O tu hi vas fer alguna cosa??

Si ho va fer l'insta&#322;lador sol... hem sembla que es un bug bastant clar no? xD

---

### Post by muleta on 2007-10-21
Doncs, ja no ho recordo perque em marejo quan intento evocar aquella disbauxa del meu dramàtic pas de windows a ubuntu sense haver-ne sentit parlar mai ni haver conegut linux ni de vista.

Vaig començar instal·lant l'alternate i, com que no entenia res, ho vaig fer intuïtivament i vaig buscar suport en espanyol, tota enrabiada. Com és natural, amb la meva càrrega de dubtes i agressivitat, no vaig ser ben rebuda. Només vaig descobrir que existia una opció gràfica més comprensible. Però vaig tornar a cometre l'errror d'instal·lar la versió per a AMD 64, perque és el meu ordinador.

Des d'aquí em vau ajudar a comprendre que era més fàcil començar amb el de 32 bits i el vaig canviar. Amb tantes modificacions sense saber-ne, és possible que fes moltes coses malament. De manera que no culpis el pobre SO.

Amb aquests precedents, penso que potser és més interessant fer un formatejat total i instal·lació nova.

Hi ha la possibilitat de que es particioni automàticament i d'una manera correcta?.

---

### Post by muleta on 2007-10-21
Ja està. Ho he fet: He formatejat el disc i he instal·lat el Gutsy Gibbon en net utilitzant tot el disc, automàticament.

L'amule funciona perfectament, en català, amb servidors ed2k i kad. De moment, no es tanca sol ni fa les coses estranyes que féia abans.

La impressora s'ha autodetectat i m'ha avisat que estava llesta per funcionar, com si es tractés del Plug&Play de Windows.

També s'ha autoinstal·lat el pluggin JAVA sense problemes.

He reinstal·lat les altres aplicacions que ja tenia, sense cap dificultat.

Trobo una gran diferència positiva de funcionament respecte al Feisty Fawn.:D=D>

---

### Post by CarlesOriol on 2007-10-23
Son genials els posts positius! :-)

---

