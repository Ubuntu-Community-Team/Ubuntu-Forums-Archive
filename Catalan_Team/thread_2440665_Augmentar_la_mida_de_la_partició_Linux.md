---
title: "Augmentar la mida de la partició Linux"
date: 2020-04-13
forum: Catalan Team
---

### Post by bielfiol on 2020-04-13
Vaig instal·lar la Ubuntu 19.10 al meu portàtil nou (que venia amb Windows) i vaig reservar 75 Gb per a la partició del sistema Linux. 
Voldria fer més gran la partició on tenc el Linux i reduir la de Windows. Pràcticament no faig servir Windows.
No tenc problemes en com reduir la partició Windows. Però crec que moure l'inici de partició de Linux pot fer que el sistema ni s'inicii correctament.

Com he dit tenc Ubuntu 19.10 i el detall de les particions és el següent:

[https://paste.ubuntu.com/p/277yQKbNgw/](https://paste.ubuntu.com/p/277yQKbNgw/)

Gràcies!

---

### Post by jmaspons on 2020-04-14
Com que no es poden redimensionar particions que estan muntades, hauràs de fer-ho des d'una distribució live, per exemple arrencant des de l'USB que vas utilitzar per fer la instal·lació de linux. Després caldrà suprimir i  redimensionar les particions segons les teves preferències usant el [partition manager]("https://kde.org/applications/system/org.kde.partitionmanager") o similar.

```

/dev/nvme0n1p1      2048    534527    532480   260M EFI System
/dev/nvme0n1p2    534528    567295     32768    16M Microsoft reserved
/dev/nvme0n1p3    567296 337594367 337027072 160,7G Microsoft basic data
/dev/nvme0n1p4 499077120 500105215   1028096   502M Windows recovery environment
/dev/nvme0n1p5 337594368 341594111   3999744   1,9G Intercanvi Linux
/dev/nvme0n1p6 341594112 499077119 157483008  75,1G Linux filesystem

Partition table entries are not in disk order.


Disk /dev/sda: 931,53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: TOSHIBA MQ04ABF1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: E516B46D-91D4-48B3-BA8C-CE5D7D955C28

Dispositiu Start      Final    Sectors   Size Tipus
/dev/sda1   2048 1953523711 1953521664 931,5G Microsoft basic data

```

Sembla que les particions de Windows són /dev/nvme0n1p1 fins a /dev/nvme0n1p4 més la /dev/sda1. Cal que t'asseguris que la partició d'arrencada és la del linux i si no tens clar si utilitza UEFI, millor no tocar la partició /dev/nvme0n1p1.

Fes còpia de seguretat pel que pugui ser

---

### Post by bielfiol on 2020-04-14
Vaig instal·lar el sistema amb UEFI. Actualment tenc el Secure Boot desactivat per poder utlitzar una dockstation (si no, no funciona).

El sistema Linux està a la partició /dev/nvme0n1p6

El portàtil té un SSD de 250 Gb (/dev/nvme0n1) i un altre disc mecànic /dev/sda. Aquest darrer el tenc amb NTFS per compartir les dades entre Linux i Windows.

El meu dubte està en si reduint l'espai de la patrició /dev/nvme0n1p3 puc assignar l'espai lliure a la partició /dev/nvme0n1p6 i, en cas de poder fer-ho, he de fer alguna passa més per tal que el sistema arrenqui sense problemes. Era per tenir-ho tot en compte i no perdre dades... si és molt complicat en sortir la 20.04 reinstal·laré el sistema i reparticionaré. Reduiré la partició de Windows i refaré les de Linux.

---

### Post by jmaspons on 2020-04-15
Com que /dev/nvme0n1p3 i /dev/nvme0n1p6 no són particions contigües, diria que no pots reduir la primera i aprofitar l'espai per ampliar la segona. Per fer això caldria que les particions estiguessin en [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm). Podries reduïr la partició de Windows i crear-ne una de nova a l'espai buit però no se si et serveix

---

### Post by bielfiol on 2020-04-16
> **jmaspons said:**
> Com que /dev/nvme0n1p3 i /dev/nvme0n1p6 no són particions contigües, diria que no pots reduir la primera i aprofitar l'espai per ampliar la segona. Per fer això caldria que les particions estiguessin en [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm). Podries reduïr la partició de Windows i crear-ne una de nova a l'espai buit però no se si et serveix
Voldria ampliar la partició de sistema sencera, no fer-ne dues parts. Però gràcies.

Amb el gparted veig que les particions són contigües. Tal i com es pot veure a la imatge:

[ATTACH=CONFIG]285536[/ATTACH]

Bé, entra la de windows i la de Linux hi ha la Swap. Però aquesta no em preocupa esborrar-la i tornar-la crear al lloc que sia.

No sé si aprofitar que surt la 20.04 i tornar a instal·lar-ho tot... Tal vegada intenti abans fer els canvis i si la cosa no tira bé tornaré a instal·lar el sistema de bell nou amb la ubuntu 20.04.

---

### Post by ffp on 2020-04-16
Bona tarda.
Jo crec que si pots reduir la partició /dev/nvme0n1p3, i augmentar la /dev/nvme0n1p6. Es tracta de reduir amb un ubuntu live i gparted, la partició /dev/nvme0n1p3 cap a l'esquerra a la mida que vulguis: 100GB per exemple, i executar-ho, una vegada acabat mous cap l'esquerra la partició swap (l'hauràs de desmuntar abans, amb el mateix gparted) finalment amplies la partició /dev/nvme0n1p6 a tope cap l'esquerra i ho executes, trigará una bona estona.
Reiniciar i comprovar que tot funciona.

---

### Post by slickymaster on 2020-04-16
@bielfiol:

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by wgarcia on 2020-04-17
@bielfol: El que et diu slickymaster és que no incrustis imatges grans als missatges, sinó que facis servir l'eina d'adjunts, perquè hi ha gent amb connexions lentes que poden tenir problemes quan volen llegir el missatge.

---

### Post by bielfiol on 2020-04-19
> **wgarcia said:**
> @bielfol: El que et diu slickymaster és que no incrustis imatges grans als missatges, sinó que facis servir l'eina d'adjunts, perquè hi ha gent amb connexions lentes que poden tenir problemes quan volen llegir el missatge.
Deman disculpes :oops:

---

### Post by jmaspons on 2020-04-20
És estrany que al gparted no surti la partició /dev/nvme0n1p4. Ja ens explicaràs com ha anat l'experiment

---

### Post by bielfiol on 2020-09-15
Bon dia, 
disculpes per no haver contestat abans. 

Fa mesos vaig provar d'augmentar la partició de linux.
Primer, des de Windows, vaig reduir la mida de la partició del sistema Windows. Amb això no hi va haver cap problema.
Després, iniciant Linux des d'un llapis de memòria vaig esborrar la swap i la vaig tornar a crear tot seguit de la partició Windows. Finalment vaig canviar la mida de la partició Linux.
Durant el procés no es va mostrar cap error. 
Vaig reiniciar l'ordinador i va aparèixer el grub. Però en iniciar Linux apareixia error i no l'iniciava. Vaig poder entrar a Windows, seleccionant l'opció al grub, sense cap problema.

Al final vaig decidir començar la instal·lació des de zero. Quan ho vaig fer em vaig donar compte que durant el procés de canviar les mides de les particions de Linux m'havia fet alguna cosa estranya, perquè les mides que m'apareixien ara no eren exactament les que havia definit (variaven poc, en un o dos Mb la partició de swap). Pareixia que entre la partició de sistema i la de swap hi havia un mínim espai sense particionar. Vaig esborrar les dues particions de linux (swap i sistema) i les vaig tornar a crear. 

Bé, la instal·lació del nou sistema va anar sense problemes (vaig aprofitar per instal·lar la versió 20.04) i tenc les particions modificades.

---

### Post by wgarcia on 2020-09-16
Perfecte, doncs, si no t'importa, marca el primer missatge com a "Solved" així es veu que ha quedat solucionat per si algú ho vol consultar en el futur.

---

