---
title: "intal.lacio a notebook amb disc sata"
date: 2009-09-27
forum: Catalan Team
---

### Post by abosch on 2009-09-27
Acabo d'instal.lar la versió 9.04 en un notebook però acabo de sortir-me'n.

He fet instal.lació a partir de USB, al disc complert i separant la /home. He fet primer la partició arrel, llavors la swap i finalment la /home. EL disc dur és SATA. 

Després de la pantalla d'ubuntu carregant es queda la pantalla negra i presenta 
/dev/disk by ....i un munt de missatges

llavors presenta errors 
65.81703 ata1.00 : status: {ARD}
96.816116 ata1.00 : exception Emask 0x0 (...)
96.816181 ata1.00 : Cmd 60/08 (...)

(...)

tallant amb el retorn apareix
(initramfs)

Ara mateix que acabo de fer un reinici, després de l'animació d'entrada-ubuntu la pantalla se'm queda negra ... :(

gràcies

---

### Post by abosch on 2009-09-28
em sembla que ja ho he trobat, simplement cal entrar a la bios i canviar en el menú
 
main>SATA mode  ... passar a IDE mode

Em funciona però desconec si pot tenir algun 'efecte/dany colateral'. 


Ara estava llegint per la Viqui i segons entenc no és que el disc sigui SATA,IDE o SCSI són les connexions entre el disc i la placa ?

O sigui fent una intalació, marquem un sector d'arrencada (és el que gestiona el Grub?) a partir del que "s'engega" tot el sistema.


! volia modificar el title original però no m'ha sortit.

---

### Post by papapep on 2009-09-28
> 
Ara estava llegint per la Viqui i segons entenc no és que el disc sigui SATA,IDE o SCSI són les connexions entre el disc i la placa ?

Les dues coses han de ser coherents. Disc [IDE]("http://es.wikipedia.org/wiki/Integrated_Drive_Electronics") (també conegut com a PATA) ha d'anar amb sistema de comunicacions (connectors, xips, etc..) compatible amb IDE. Així mateix, els [SCSI]("http://ca.wikipedia.org/wiki/SCSI") tenen el seu propi sistema i els SATA (que són una evolució dels PATA (IDE) el mateix. 
Una altra cosa és que les [BIOS]("http://ca.wikipedia.org/wiki/Bios") suportin diferents sistemes i que les plaques tinguin simultàniament diversos connectors per a diferents tipus de discs. Però no es poden barrejar nous i castanyes, en aquest cas :)

---

