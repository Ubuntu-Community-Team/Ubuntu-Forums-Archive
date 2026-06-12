---
title: "Dispositius grab'n'go i compatibilitat amb GNU/Linux"
date: 2007-08-25
forum: Catalan Team
---

### Post by giorgiograppa on 2007-08-25
Perdoneu si la pregunta és massa elemental, però abans de "regalar-me" un d'aquests discos durs externs que reprodueixen música, vídeo i fotos sense necessitat d'ordinador, voldria assegurar-me que no donen problemes, és a dir, que el meu Ubuntu (6.06.1) els reconeixerà només connectar-los (no conec ningú que en tinga un, i la publicitat no indica si són o no compatibles amb el pingüí, catxis la mar). En principi, hauria de ser així, perquè, pel que he llegit en algun llibre d'instruccions (Conceptronic), en connectar-los a l'ordinador es comporten com un dispositiu USB nomal i corrent.

Pel que fa al model concret, de moment em crida l'atenció el CMEDPLUS de Conceptronic de 500 GB; ara bé, no porta pantalla de display, necessites un televisor per saber quin arxiu (d'àudio, se sobreentén) vas a reproduir.
Supose que el fet que porte un disc IDE o SATA (segons siga un model més antic o més recent) tampoc no hauria de ser gaire important (o sí?).

He llegit pestes dels Woxter, i sembla que els Conceptronic van millor, algú m'ho pot confirmar?

No sé fins a quin punt és important, però els discos del Conceptronic han d'estar formatats en FAT32, i sembla que a alguns usuaris els preocupa la limitació d'aquest sistema a una mida màxima de fitxer de 4 GB. En quins casos podria ser un problema?

L'ús que li vull donar crec que és el normal: escoltar àudio connectat a un amplificador (ací notaré a faltar una pantalleta, supose) i reproduir pel·lícules, siga en el televisor, en la pantalla de l'ordinador o en el projector. Sempre ús domèstic, res de professional ni en públic.

Gràcies pels comentaris i, insistisc, perdoneu si la pregunta és massa elemental.

---

### Post by CarlesOriol on 2007-08-25
La principal limitació del format FAT32 és que no és tolerable a fallades.

Jo no tinc ap dispositiu d'aquests però si 3 adaptadors conceptronic 1 SATA  2'5, 1 ATA 2'5 i 1 ATA 3,5 (amb transformador). En l'ubuntu no he tingut mai cap problema amb cap d'ells. Però si amb la playstation 2 on els adaptadors conceptronic no funionen.

---

### Post by PellRoja on 2007-08-25
Actualment m' he comprat una caixa de disc dur extern, i li he posat un disc dur intern SATA 200GB. i amb Ubuntu i NTFS vaig tindre problemes, no em deixava escriure. Vaig passar la unitat a FAT32, pero no em fa molta gracia.

Si no fos per que es per fer copies de mon pare i meves, me la haves formatat a ext3, pero mon pare te windows i no se si el driver [http://www.fs-driver.org/](http://www.fs-driver.org/) me la detectarà.

---

### Post by lluisanunez on 2007-08-25
A mi em van regalar un Conceptronic d'aquests, l'Ubuntu el reconeix sense problemes, però perquè funcioni amb la TV cal mantenir el format FAT32 i els seus programes propietaris (cosa que no m'agrada), per altra banda la TV no obre bé algunes pelis que sí que s'obren amb Ubuntu... estic per reformatejar-lo i que només faci de disc.

---

### Post by pespin on 2007-08-25
Jo el fs-driver el tinc instal·lat i em detecta la partició ext3 sense problemes :)

---

### Post by PellRoja on 2007-08-25
> **pespin said:**
> Jo el fs-driver el tinc instal·lat i em detecta la partició ext3 sense problemes :)


La partició està en un disc USB?

---

### Post by pespin on 2007-08-25
No, partició al mateix disc :lolflag:

---

### Post by giorgiograppa on 2007-08-25
Ala, quanta informació! :-)

**CarlesOriol**, tens raó amb el tema de les fallades en FAT32, no recordava aquest detall.
No sé a què et refereixes quan parles d'adaptadors, m'hauré de tornar a mirar la web de Conceptronic a veure què és això.

**PellRoja**, la caixa de què parles és només per muntar el disc extern o també és un reproductor multimèdia? No m'ha quedat clar...

Gràcies, **Lluisanunez**, eixa era la part que més em preocupava, saber si l'Ubuntu el reconeix correctament com a simple disc dur extern.
Supose que les pel·lícules que no s'obrin quan el tens connectat a la tele és perquè estan en formats que el dispositiu (el firmware?) no sap gestionar, mentre que en Ubuntu sí que hi deus tindre instal·lats tots els còdecs que hi puguen caldre; per tant, supose que mentre les actualitzacions no incloguen més còdecs, aqueixos vídeos continuaran sense poder ser reproduïts sense l'ordinador.

**Pespin**, això del fs-driver (primera volta que ho escolte nomenar, no havia entés a què es referia PellRoja) m'interesa molt. Pel que acabe de llegir en la pàgina de fs-driver, es tracta d'un driver (?) per a Windows; com s'instal·la en el dispositiu de Conceptronic? S'ha de copiar en algun directori concret i ja està? (Val, em miraré amb més calma les FAQ, tens raó.) I el resultat, segons dius, és que et reconeix la partició ext3 i el seu contingut quan funciona com a reproductor connectat a la tele, sense que hi intervinga el PC.
Això vol dir, a més, que, com a mínim, hi tens dues particions, una en FAT32 (que supose que és indispensable perquè el sistema puga funcionar) i una altra en ext3. Mmm... això soluciona el problema que apuntava CarlesOriol, supose.

Doncs moltes a gràcies a tots! (I a totes, i a totes... fa goig trobar alguna ubuntaire de tant en tant.) Continuaré investigant, però ja m'ho heu aclarit molt.

---

### Post by pespin on 2007-08-25
No he aprofundit en el tema del fs-driver. L'únic que sé és que a l'instal·lació del driver t'ensenya les particions ext2 i 3 i particions SWAP i et permet assignar-li una lletra d'unitat com pots tindre C:, D:, etc. Desprtés al MiPC o explorer pots accedir-hi com si fos una partició ntfs o fat32 de tota la vida :)

---

### Post by giorgiograppa on 2007-08-26
És a dir, **Pespin**, que quan utilitzes la unitat com un disc dur extern connectat a un **PC funcionant amb Windows**, és Windows el que reconeix les particions ext2 i ext3 que puga haver-hi, tant a aquesta unitat com sobre altres discos durs?

Però, aquesta unitat, quan funciona com a reproductor multimèdia autònom, **sense** estar connectada a cap PC, sinó només a un televisor o a un amplificador, arriba reconéixer particions ext2 o ext3? Perquè açò sí que seria interessant (vull dir, interessant per a l'ús concret que vull donar-li a aquest grab'n'go, reproduir vídeo i àudio sense estar connectat al PC).

(Tot i que gairebé ja no utilitze el Windows per a res, vaig a baixar-me el driver i a instal·lar-li'l, encara que només siga per veure com funciona.)

---

### Post by CarlesOriol on 2007-08-26
> **giorgiograppa said:**
> Ala, quanta informació! :-)

**CarlesOriol**, tens raó amb el tema de les fallades en FAT32, no recordava aquest detall.
No sé a què et refereixes quan parles d'adaptadors, m'hauré de tornar a mirar la web de Conceptronic a veure què és això.
.

Aquests. Son sols adaptadors, no sistemes multimèdia com el que comentaves tu i per això ho remarcava.

CHD2U - ATA 2'
[IMG]http://mkcomputers.axelero.net/chd2u-1b.jpg[/IMG]

CHD3U - ATA 3'5
[IMG]http://mkcomputers.axelero.net/chd3u-1b.jpg[/IMG]

---

### Post by giorgiograppa on 2007-08-26
Ja està clar, **Carles**: caixes buides on claves el teu disc dur i ja el pots connectar per USB. El cas és que en tinc una (d'una altra marca que ara no recorde); però, en efecte, no és el que estic buscant ara.

---

