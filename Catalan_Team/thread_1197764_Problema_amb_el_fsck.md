---
title: "Problema amb el fsck"
date: 2009-06-26
forum: Catalan Team
---

### Post by akyra on 2009-06-26
Hola a tothom

M'ha aparegut un problema a l'arrancar el ubuntu fa 5 minuts.
Quan es disposava a fer el checkdisk que fa de tant en tant quan arrenca, m'ha surtit un fallo. i m'ha dit que executi el fsck de forma manual cosa que he fet, i que mirés el /var/log/checkfs. El que hi ha en el log és el segUent:
> 
Log of fsck -C3 -R -A -a 
Fri Jun 26 20:30:22 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda5 contains a file system with errors, check forced.
/dev/sda5: Duplicate or bad block in use!
/dev/sda5: Multiply-claimed block(s) in inode 4448547: 17826272 17826273 17826274 17826275 17826276 17826277 17826278 17826279 17826280 17826281 17826282 17826283 17826284 17826285 17826286 17826287 17826288
/dev/sda5: Multiply-claimed block(s) in inode 4450989: 17826272 17826273 17826274 17826275 17826276 17826277 17826278 17826279 17826280 17826281 17826282 17826283 17826284 17826285 17826286 17826287 17826288
/dev/sda5: (There are 2 inodes containing multiply-claimed blocks.)

/dev/sda5: File /marilen/.mozilla/firefox/r5fuxlo9.default/urlclassifier3.sqlite (inode #4448547, mod time Thu Jun 25 21:11:33 2009) 
  has 17 multiply-claimed block(s), shared with 1 file(s):
/dev/sda5: 	/marilen/.gconfd/saved_state (inode #4450989, mod time Thu Jun 25 21:11:33 2009)
/dev/sda5: 

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Fri Jun 26 20:32:48 2009
----------------

Bé, després he tornat a engegar i m'ha tornat a sortir el mateix fallo.

He tornat a parar i no he fet l'escaneig del disc i m'ha entrat normalment.
Algú em pot donar un cop de mà.

Moltes gracies.

---

### Post by akyra on 2009-06-26
He tornat a arrencar i no ha sortit cap error. Com no estava conforme he arrancat amb el recovery mode, després he fet umount /dev/sda5 (era la que tenia problemes) i després he el fsck /dev/sda5, i m'ha surtit:
> 
Log of fsck -C3 -R -A -a 
Fri Jun 26 21:56:48 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda5: clean, 74057/4694016 files, 10252214/18753871 blocks

Fri Jun 26 21:56:49 2009
----------------

Suposo que això vol dir que està bé, oi?

A que  es deuen aquests errors? És per saber una mica més

Salutacions.

---

