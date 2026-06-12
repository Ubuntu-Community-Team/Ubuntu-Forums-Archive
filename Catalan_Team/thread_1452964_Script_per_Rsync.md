---
title: "Script per Rsync"
date: 2010-04-12
forum: Catalan Team
---

### Post by Daerun on 2010-04-12
Normalment faig servir Grsync per a les còpies de seguretat dels meus directoris a un disc dur extern usb, però com que fer-ho manualment pot arribar a ser una mica tediós, m'agradaria a veure si algú em pogués dir com podria -o a on podria llegir com es fa- crear un script per l'Rsync que en executar-lo actualitcés automáticament totes les carpetes.

---

### Post by wgarcia on 2010-04-13
Aquest és el meu script, que vaig agafar fa molts anys i sempre m'ha funcionat molt bé, per fer còpies de seguretat "snapshot" a un disc que tinc muntat a /mnt/Backup, i dins d'aquí a una carpeta que es diu Work. No sé si es més del que vols, però és la millor manera de fer-ho, i és com ho fan sistemes de còpies més sofisticats. 

Aquest script actualitza una carpeta que es diu "hourly.0", i mou l'últim hourly.0 a hourly.1, l'últim hourly.1 a hourly.2, i per últim, l'últim hourly.2 a hourly.3. El corre un cron cada 4 hores, amb la qual cosa tinc una fotografia dels meus arxius cada 4 hores. També corro uns scripts cada dia, cada setmana i cada mes, aquest simplement fan còpies incrementals d'hourly.3, amb la qual cosa conservo fotografies fins a tres dies enrere, de les quatre últimes setmanes i dels últims 12 mesos. Hi ha també unes exclusions que s'especifiquen en un arxiu extern, si vols el format d'això també te'l puc passar. 

El tamany del disc que es necessita per fer aquestes fotografies és únicament el doble de l'espai que estiguis ocupant amb els teus arxius. perquè les fotografies són sols incrementals, és a dir es diferencien únicament en les coses que hagin canviat. 

Aquí està el script, té alguns comentaris però si tens dubtes de com funciona, pots preguntar. El rsync concret està sobre el final, perquè també fa que la còpia sigui sols lectura, i com el corro com a superusuari és una mesura de protecció addicional per si se'm compromet el sistema. 

```
#!/bin/bash
# ----------------------------------------------------------------------
# mikes handy rotating-filesystem-snapshot utility
# ----------------------------------------------------------------------
# this needs to be a lot more general, but the basic idea is it makes
# rotating backup-snapshots of /home whenever called
# ----------------------------------------------------------------------
#
# Adapted for wgarcia on February 2006
#

unset PATH	# suggestion from H. Milz: avoid accidental use of $PATH

# ------------- system commands used by this script --------------------
ID=/usr/bin/id;
ECHO=/bin/echo;

MOUNT=/bin/mount;
RM=/bin/rm;
MV=/bin/mv;
CP=/bin/cp;
TOUCH=/bin/touch;
CHMOD=/bin/chmod;

RSYNC=/usr/bin/rsync;


# ------------- file locations -----------------------------------------

SNAPSHOT_RW=/mnt/Backup/Work;
EXCLUDES=/home/wgarcia/jobs/backup_exclude;

# ------------- the script itself --------------------------------------

# make sure we're running as wgarcia
# if (( `$ID -u` != 2001 )); then { $ECHO "Sorry, must be wgarcia.  Exiting...";
 exit; } fi

# attempt to make the directory writable; else abort
$CHMOD -R u+rw $SNAPSHOT_RW;
 if (( $? )); then
  {
	$ECHO "snapshot: could not make $SNAPSHOT_RW readwrite";
	exit;
 }
 fi;


# rotating snapshots of /home (fixme: this should be more general)

# step 1: delete the oldest snapshot, if it exists:
if [ -d $SNAPSHOT_RW/hourly.3 ] ; then			\
$RM -rf $SNAPSHOT_RW/hourly.3 ;				\
fi ;

# step 2: shift the middle snapshots(s) back by one, if they exist
if [ -d $SNAPSHOT_RW/hourly.2 ] ; then			\
$MV $SNAPSHOT_RW/hourly.2 $SNAPSHOT_RW/hourly.3 ;	\
fi;
if [ -d $SNAPSHOT_RW/hourly.1 ] ; then			\
$MV $SNAPSHOT_RW/hourly.1 $SNAPSHOT_RW/hourly.2 ;	\
fi;

# step 3: make a hard-link-only (except for dirs) copy of the latest snapshot,
# if that exists
if [ -d $SNAPSHOT_RW/hourly.0 ] ; then			\
$CP -al $SNAPSHOT_RW/hourly.0 $SNAPSHOT_RW/hourly.1 ;	\
fi;

# step 4: rsync from the system into the latest snapshot (notice that
# rsync behaves like cp --remove-destination by default, so the destination
# is unlinked first.  If it were not so, this would copy over the other
# snapshot(s) too!
$RSYNC								\
        -av --delete                                            \
        --delete-excluded                                       \
        --exclude-from=/home/wgarcia/jobs/backup_exclude        \
        /etc                                                    \
        /home/wgarcia     			         	\
        /usr/local                                              \
        /var/spool/../mail                                      \
        /var/www/html                                           \
        /var/lib/mysql                                          \
        /usr/local/share/bases                                  \
        $SNAPSHOT_RW/hourly.0 ;

# step 5: update the mtime of hourly.0 to reflect the snapshot time
$TOUCH $SNAPSHOT_RW/hourly.0 ;

# and thats it for home.

# now make the RW snapshot mountpoint as readonly

 $CHMOD -R a-w $SNAPSHOT_RW ;
 if (( $? )); then
 {
 	$ECHO "snapshot: could not make $SNAPSHOT_RW readonly";
 exit;
 }
 fi;
```

---

### Post by oriolsbd on 2010-04-13
Hola,

Quan executes un backup amb el Grsync, si mires les traces que et deixa, just al principi t'escriu quina és la sentència exacta de "rsync" que utilitza. Pots fer-la servir per a generar el teu script.

Salut!

---

### Post by Daerun on 2010-04-13
Ah, gràcies! La veritat és que no necessito res tan complicat. Sencillament cada pocs dies faig una còpia al disc extern "per si de cas", y com que en faig de cuatre o cinc carpetes, volia fer un script que m'ho facilités, y ho fés solet d'uan tacada :D
També val a dir que no tinc idea de scripts :P però vaig llegir -crec recordar que en un article de SomGNU-, això que em comentes, Oriol :D

---

