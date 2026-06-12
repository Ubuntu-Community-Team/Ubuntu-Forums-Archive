---
title: "Onboard amb el locale ca_ES"
date: 2012-07-08
forum: Catalan Team
---

### Post by AlbertJB on 2012-07-08
Hola bona nit,

Començo a estar una mica preocupat perquè ja fa moltes setmanes que espero poder utilitzar l'onboard i la veritat és que no rebo actualitzacions per solucionar el problema. Sé que hi havia un ticket obert com a bug, però d'això en fa unes quantes setmanes. A algú li funciona, a l'Ubuntu 12.04 en català? 

Gràcies per endavant.

---

### Post by AlbertJB on 2012-07-09
Perdoneu, ara he vist a [https://bugs.launchpad.net/ubuntu-translations/+bug/999155](https://bugs.launchpad.net/ubuntu-translations/+bug/999155) que han solucionat el bug, però per a la versió 12.10 d'Ubuntu, no pas per la 12.04. 

El "workaround" que em proposa en Josep P. no em funciona. Utilitzo el gnome classic sense efectes, o sigui metacity. L'error que em dóna en executar onboard és el mateix de sempre:

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/Onboard/OnboardGtk.py", line 86, in do_activate
    self.init()
  File "/usr/lib/python2.7/dist-packages/Onboard/OnboardGtk.py", line 101, in init
    config.init()
  File "/usr/lib/python2.7/dist-packages/Onboard/Config.py", line 256, in init
    self.apply_theme()
  File "/usr/lib/python2.7/dist-packages/Onboard/Config.py", line 547, in apply_theme
    theme_filename = self.theme_filename
  File "/usr/lib/python2.7/dist-packages/Onboard/Config.py", line 519, in get_theme_filename
    "." + Theme.extension()))
  File "/usr/lib/python2.7/dist-packages/Onboard/ConfigUtils.py", line 275, in _get_user_sys_filename_gs
    system_filename_func)
  File "/usr/lib/python2.7/dist-packages/Onboard/ConfigUtils.py", line 318, in _get_user_sys_filename
    .format(description=description, filepath=filepath))
KeyError: u'filename'

Perdoneu la insistència, però és que és una aplicació que necessito. Algú altre em va proposar una aplicació de teclat virtual per a Linux però no em funcionava tampoc :(

---

### Post by wgarcia on 2012-07-09
Si justifiques bé, es pot demanar un SRU, que vol dir Stable Release Update, és a dir que apliquin la correcció de l'error a la versió estable (l'actual). S'explica en aquesta pàgina:

[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Bàsicament s'ha de demostrar que l'aplicació de la correcció d'error no té perill de generar alguna regressió a la versió estable, i justificar perquè és important aplicar-ho. S'ha de fer en anglès perquè ho entenguin els desenvolupadors.

---

### Post by AlbertJB on 2012-07-09
Gràcies wgarcia, intentaré fer això que em dius, tot i que ho trobo complicat. Com demostro que la correcció d'error no té perill de generar alguna regressió a la versió estable? Bé, crec que em tocarà llegir la guia que m'has passat. En qualsevol cas és força descoratjador aquest episodi per mi, humilment trobo que onboard és una aplicació destacable a Ubuntu, tot i que un bug en aquesta aplicació no sigui crítica, sí important. M'ha estranyat força que no s'hagi solucionat després de tantes setmanes, però entenc que hi ha altres paquets més importants i segurament ningú ha tingut el temps per esmenar l'error. 

Ho dic amb tota la bona fe, de veritat, no sóc ningú per criticar que no arreglin bugs en un projecte de programari lliure, simplement m'ha sobtat una mica. Sóc novell en Ubuntu i de vegades em costa entendre els processos formals en projectes grans com Ubuntu. 

En fi, gràcies pel consell. Bona nit.

---

### Post by wgarcia on 2012-07-10
> **Gosset Inofensiu said:**
> Gràcies wgarcia, intentaré fer això que em dius, tot i que ho trobo complicat

No és tan complicat, s'han de posar els cinc punts que està a la secció Procedure 2. i subscriure a l'equip SRU.

> **Gosset Inofensiu said:**
> Com demostro que la correcció d'error no té perill de generar alguna regressió a la versió estable?

Si es tracta d'un error que sembla senzill, i l'arreglo és molt precís i fitat, hi ha poca probabilitat que generi regressions. A més si no és un paquet que està a la base del sistema operatiu el potencial de generar un impacte si s'introdueix una regressió també és menor.

> **Gosset Inofensiu said:**
> En qualsevol cas és força descoratjador aquest episodi per mi, humilment trobo que onboard és una aplicació destacable a Ubuntu, tot i que un bug en aquesta aplicació no sigui crítica, sí important. M'ha estranyat força que no s'hagi solucionat després de tantes setmanes, però entenc que hi ha altres paquets més importants i segurament ningú ha tingut el temps per esmenar l'error.

S'hauria de veure com es mantén aquest paquet, no tinc ni idea. També si hi ha un manteniment "upstream", és a dir que es manté per una comunitat més gran que Ubuntu, en aquest cas s'hauria d'entrar l'informe d'error al seu lloc d'errors (per exemple de Debian, o de Gnome, o a vegades hi ha llocs específics com Firefox, etc.). Un cop entrat l'informe "upstream" s'ha d'enllaçar amb l'informe al launchpad. 

> **Gosset Inofensiu said:**
>  Ho dic amb tota la bona fe, de veritat, no sóc ningú per criticar que no arreglin bugs en un projecte de programari lliure, simplement m'ha sobtat una mica. Sóc novell en Ubuntu i de vegades em costa entendre els processos formals en projectes grans com Ubuntu. 

I... l'única garantia que s'arreglin els errors és posar-se un mateix a remenar el codi, si es tenen els coneixements, perquè a part d'això ningú no té l'obligació de dedicar el seu temps lliure en les coses que necessitem nosaltres. Per una altra part els desenvolupadors contractats per Canonical no són tants i han de prioritzar molt bé el temps que dediquen a cada paquet.

---

### Post by AlbertJB on 2012-07-10
Gràcies wgarcia pels teus comentaris.

Finalment he aconseguit fer-lo funcionar amb el workaround de "env LANGUAGE=en onboard"; m'equivocava a l'hora d'executar la comanda... Sóc novell, demano comprensió ;)

---

