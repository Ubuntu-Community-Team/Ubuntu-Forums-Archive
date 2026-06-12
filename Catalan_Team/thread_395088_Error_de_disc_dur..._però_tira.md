---
title: "Error de disc dur... però tira"
date: 2007-03-27
forum: Catalan Team
---

### Post by cortsenc on 2007-03-27
Be gent, fa temps que al carregar el meu Ubuntu em surt un error que atribueixo al disc dur. Fins ara no em preocupava perquè la cosa es seguia carregant però cada cop triga més a engegar-se perquè surten més repeticions del mateix error.

L'error en qüestió apareix en el punt de carregar el FSCK.

[INDENT][17179932.**104000**] Buffer I/O error o device hda, logical block (**2097147**)[/INDENT]

La numeració amb negreta es canviant, però el missatge es el mateix i es repeteix un munt de vegades.

Més endavant surt un altre missatge d'error

[INDENT][171...] Codec_read: codec 0 is not valid[/INDENT]

Tot el procés fa que l'ordinador trigui uns 15 minuts a carregar-se, quant normalment en triga 2. Cal dir que aquest 15 minuts han anat augmentant aquestes dues setmanes.

Per on puc començar? Algun arxiu on es guardin els problemes amb l'fsck?

---

### Post by ChAoS.ct on 2007-03-29
Pots fer un fsck manualment a veure què et diu?

---

### Post by cortsenc on 2007-03-30
> **ChAoS.ct said:**
> Pots fer un fsck manualment a veure què et diu?

oriol@desktop:~$ sudo fsck
Password:
fsck 1.39 (29-May-2006)
e2fsck 1.39 (29-May-2006)
/dev/evms/sda1: recovering journal
Clearing orphaned inode 263416 (uid=0, gid=0, mode=0100644, size=2127216)
Clearing orphaned inode 261654 (uid=0, gid=0, mode=0100644, size=6667672)
/dev/evms/sda1: clean, 132692/3646496 files, 901988/7279445 blocks
e2fsck 1.39 (29-May-2006)
/dev/evms/sda3: recovering journal
/dev/evms/sda3: clean, 54437/17874944 files, 30136360/35734584 blocks
e2fsck 1.39 (29-May-2006)
/dev/evms/sda4: recovering journal
/dev/evms/sda4: clean, 114883/3057824 files, 1179944/6108716 blocks

---

### Post by ChAoS.ct on 2007-03-30
Doncs si no es queixa quan fas el fsck manualment  llavors no sé què pot ser...
A mi em donava fa temps un error semblant en un antic perntium2 i al final vaig veure que era un símptoma de que el disc dur estava fet malbé.

A mi el que també em passava era que a part dels missatgets, amb transferències ràpides de gran quantitat d'informació em petava l'ordinador (se'm reiniciava)

Al final vaig canviar de disc dur i apa, tot correcte.

---

### Post by orestesmas on 2007-03-31
Però es queixa... té (tenia) el sistema de fitxers malament, com si hagués apagat la màquina sense desmuntar les particions.

---

### Post by cortsenc on 2007-03-31
> **orestesmas said:**
> Però es queixa... té (tenia) el sistema de fitxers malament, com si hagués apagat la màquina sense desmuntar les particions.

Correcte Orestes, fa uns dies s'en va anar la llum. Però no relacionava els dos casos perquè l'error no va ser instantani (vull dir que el primer cop que va sortir no deuria afectar el rendiment perquè no el vaig notar), però ahir va trigar 4 hores a carregar-se i ja no l'he tornat a apagar.
Com es poden corregir aquests errors de disc?

---

### Post by cortsenc on 2007-04-01
Fa dues hores he tornat a encendre l'ordinador (s'havia penjat el Gnome) i ara m'ha sortit això...

> 
* Checking file systems...
fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve "UUID=0a3c7ce2-c256-43b3-9ec7-44586cdd66a0"
/dev/evms/sda3: clean, 54552/17874944 files, 31742503/35734584 blocs
fsck died with exit status 8

*File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.

*A maintence shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: groups: command not found
bash: lesspipe: command not fount
bash: dircolors: command not found


---

### Post by cortsenc on 2007-04-11
Ei, algú em pot ajudar amb això?

L'altre dia vaig provar de fer funcionar l'**smart-notifier** però no m'en vaig sortir, algú la fet servir?

Com puc arreglar aquest problema de disc abans de que peti tot?

---

### Post by ChAoS.ct on 2007-04-14
> Com puc arreglar aquest problema de disc abans de que peti tot?
Pinta molt malament, jo de tu provaria a arrencar des d'un cd bootable i intentar recuperar totes les dades possibles des d'allí.
Llavors pots fer un fsck manualment i k arregli els problemes si cal.

---

### Post by moxiot on 2007-04-15
intenta flashear les bios del teu ordinador. informat be per que tel podries carregar, pero es l'unic que sem passa pes cap. si vols diguem quin ordinador tens i te ajudare tot el que pugui amb el proces

---

