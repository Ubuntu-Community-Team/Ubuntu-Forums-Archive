---
title: "Problemes amb taula de particions"
date: 2011-07-03
forum: Catalan Team
---

### Post by sianeu on 2011-07-03
Després de reinstal·lar windows 7, dues particions ext4 de dades (particions lògiques) van desapareixer. Des de windows7 apareixia com espai lliure, des d'Ubuntu amb Gparted (desprès de recuperar grub2) tot el disc semblava no particionat. Vaig recuperar les particions amb Testdisk des de Dos (Hiren's boot) reescribint la taula de particions. Peró Gparted (tant des d'Ubuntu com des de LiveCD) segueix sense veure les particions.

Deixo uns anàlisis:

1- TESTDISK. Aquí tot sembla correcte:
> TestDisk 6.11, Data Recovery Utility, April 2009

Christophe GRENIER <grenier@cgsecurity.org>

[http://www.cgsecurity.org](http://www.cgsecurity.org)





Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63

Current partition structure:

     Partition                  Start        End    Size in sectors



 1 * Linux                    0  32 33  5736 209 41   92160000

 2 P HPFS - NTFS           5736 209 42 10198 177 27   71680000

 3 P Linux Swap           10198 209 60 10326  77 39    2047984

 4 E extended LBA         10326  78  1 60801 254 63  810892026

 5 L Linux                10326 110 25 23457  22 53  210944000 [EXTRA]

 6 L Linux                23457  55 23 36970  16 38  217083904 [GUARDA]

 7 L HPFS - NTFS          36970  49  8 60801  80 15  382846976 [CALAIXERA]





2- FDISK
a)Aquí dues particions semblen sortir de mare (negreta):
> sianeu@unicorn:~$ sudo fdisk -l /dev/sda



Disc /dev/sda: 500.1 GB, 500107862016 octets

255 cabezas, 63 sectores/pista, **60801 cilindros**

Unidades = cilindres de 16065 * 512 = 8225280 bytes

Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes

Identificador de disco: 0x0001e626



Dispositiu Arrenc.   Inici         Final    Blocs         Id  Sistema

/dev/sda1   *                  1         5737    46080000   83  Linux

/dev/sda2                  5737       10199    35840000    7  HPFS/NTFS

/dev/sda3                 10199       10327     1023992   82  Intercanvi Linux / Solaris

/dev/sda4                 10327     **  60802  ** 405446013    f  W95 Estesa (LBA)

/dev/sda5                  10327       23458   105472000   83  Linux

/dev/sda6                  23458       36971   108541952   83  Linux

/dev/sda7                   36971       **60802**   191423488    7  HPFS/NTFS
 

b)Aquí només l'estesa (sda4) sembla que pasa el límit, sda7 sembla que no:
> sianeu@unicorn:~$ sudo fdisk -lu



Disc /dev/sda: 500.1 GB, 500107862016 octets

255 cabezas, 63 sectores/pista, 60801 cilindros, total** 976773168 sectors**

Unidades = sectors de 1 * 512 = 512 bytes

Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes

Identificador de disco: 0x0001e626



Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema

/dev/sda1   *        2048       92162047    46080000   83  Linux

/dev/sda2        92162048   163842047    35840000    7  HPFS/NTFS

/dev/sda3       163844096   165892079     1023992   82  Intercanvi Linux / Solaris

/dev/sda4       165892104   **976784129**   405446013    f  W95 Estesa (LBA)

/dev/sda5       165894144   376838143   105472000   83  Linux

/dev/sda6       376840192   593924095   108541952   83  Linux

/dev/sda7       593926144   976773119   191423488    7  HPFS/NTFS



3-SFDISK. Aquí detecta un altre error:
> sianeu@unicorn:~$ sudo sfdisk -d

Avís: [B]la partició estesa no comença al límit d'un cilindre.

El DOS i Linux interpretaran el contingut de manera diferent.
[/B]
# partition table of /dev/sda

unit: sectors



/dev/sda1 : start=     2048, size= 92160000, Id=83, bootable

/dev/sda2 : start= 92162048, size= 71680000, Id= 7

/dev/sda3 : start=163844096, size=  2047984, Id=82

/dev/sda4 : start=165892104, size=810892026, Id= f

/dev/sda5 : start=165894144, size=210944000, Id=83

/dev/sda6 : start=376840192, size=217083904, Id=83

/dev/sda7 : start=593926144, size=382846976, Id= 7

4-PARTED. Sembla referir-se a algun dels problemes detectat per fdisk:

> sianeu@unicorn:~$ sudo parted

GNU Parted 2.3

Utilitzant /dev/sda

¡Bienvenido/a a GNU Parted! Teclee «help» para ver la lista de órdenes.

(parted) print                                                            

Error: No es pot fer una partició fora del disc!                          

(parted) 


5-CFDISK. Igual que Parrted i fdisk:
> sianeu@unicorn:~$ sudo cfdisk /dev/sda

 ERROR FATAL: Partició primària incorrecta 3: La partició acaba despres de la fí del disc

                                                     Premeu una tecla per a sortir del cfdisk


6- La &#8220;utilitat de discs&#8221; de Natty es capaç de veure be totes les particions i no senyala cap problema, però al final del disc hi col·loca un altre partició que gràficament no es més gran que la swap i la defineix com  &#8220;espai no ubicat&#8221; amb &#8220;capacitat:18446744TB (-5612544 bytes).

7-Com ja he comentat Gparted no detecta cap partició i Win7 les detecta totes normalment (si entenem com a &#8220;normal&#8221; que col·loqui sda5 i sda6 fora de la partició estesa i que seria imposible que hi hagués 6 particions primaries, però tinc entès que això ja es normal en aquest SO) 

Dir que puc entrar a ambdós sistemes sense cap problema aparent, i totes les particions semblen respondre correctament. Però evidentment temo que en qualsevol moment tot faci crash, tot i que ja tinc copia del mes important.

No se si te sol·lució, sobretot per la disparitat en els tests. I si no la te, voldria saber quina seria la millor manera de formatar tot el disc de manera que no es reproduís el problema.

Salut (perdoneu el totxo)

---

