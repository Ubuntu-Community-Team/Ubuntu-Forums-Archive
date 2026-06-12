---
title: "Jaunty Jackalope s'em penja de forma exagerada"
date: 2009-05-05
forum: Catalan Team
---

### Post by kukat on 2009-05-05
Hola!!!
Hui a sigut una cosa exagerada la de vegades que he tingut que reiniciar l'ordinador. Si dic que l'he reiniciat 15 vegades no estaré exagerant. Si estic escoltant música, es queda com si fos música màquina (:)) i si no, passa com quan he vingut d'estudiar, que m'he deixat l'amule funcionant...i el PC s'ha quedat completament sec...en l'estalvi de pantalla!!!

He llevat els efectes d'escriptori....i ja van dues vegades les que he reiniciat. I l'únic que tenia obert era el Pidgin, el Firefox....i ja està!!! 

Hi ha alguna forma de veure quines son les errades?? A "Sistema" "Administració" "Visualitzador de registres" pareix que hi haja alguna cosa, però.....es que no se per on començar.

Moltíssimes gràcies... Espere que siga algun error de hardware i em lleve el "susto" de damunt!

---

### Post by papapep on 2009-05-05
Prova amb alguna versió anterior del nucli que tinguis instal·lada. Avui crec haver vist que hi havia una actualització.

---

### Post by kukat on 2009-05-05
Com ho faig per a fer això¿?:confused:

---

### Post by papapep on 2009-05-05
Doncs a l'arrencada, quan surt a dalt a l'esquerra "Grub..." prems Esc, i t'haurien de sortir els nuclis que tens instal·lats i configurats al Grub, amb els que pots arrencar.

---

### Post by kukat on 2009-05-06
Per molt que prem "esc" no em surt res.......Serà per què solament tinc un nucli?

---

### Post by SiscoGarcia on 2009-05-06
> **kukat said:**
> Per molt que prem "esc" no em surt res.......Serà per què solament tinc un nucli?

Per comprovar-ho pots obrir un terminal i escriure-hi "uname -r", sense cometes, clar ;)

---

### Post by kukat on 2009-05-06
> **SiscoGarcia said:**
> Per comprovar-ho pots obrir un terminal i escriure-hi "uname -r", sense comentes, clar ;)

Si, crec que solament tinc un nucli:

kukat@kukatmaulet:~$ uname -r
2.6.28-11-generic

Bé, avui a part d'unes actualitzacions del Brasero i alguna cosa més, he netejat tot l'ordinador (per dins, la targeta gràfica, la font d'alimentació i tal...:)). A veure si era alguna cosa de la targeta gràfica, de moment no s'he m'ha penjat! Però ja dic...ahir va ser exagerat. 

Seguiré informant! :)
Gràcies!

---

### Post by kukat on 2009-05-06
Doncs déu ser que la targeta gràfica...no se...no estaria ben subjecta? tendria massa pols?? :confused:

Solament dir que he fet la barbaritat d'obrir tots aquestos programes (veure fitxer adjunt del comandament **ps lax**) i no ha passat res! es més, anava prou ràpid...i de penjar-se...res de res...:confused:

Misteris de la electrònica...

---

### Post by kukat on 2009-05-07
:(
Avui se m'ha penjat dues vegades! :(

I anit una!!! Però no li vaig donar tanta importància....
Anit:
1.Estava escoltant Catalunya Ràdio (La retransmissió del Puyal)...i quan va marcar l'Iniesta, vaig engegar l'Amarok per a escoltar l'himne del barça dels Lax N Busto (tanta emoció!:) ) i es va quedar penjat.

2. Avui: Estava escoltant l'Amarok (una peça del meu disc dur). Acabava d'insta&#320;lar el "Shiretoko"(el Firefox3.5), i he obert "Llocs" "Carpeta d'inici", per a copiar l'arxiu per a tindre'l en català, i s'ha quedat penjat.

3. Segona vegada: Només engegar l'ordinador, he posat el Pidgin i he obert l'OpenOffice. He obert l'Amarok (que tarda a obrir-se, supose per el Jamendo) i també s'ha quedat penjat....(sense estar escoltant res)

En un principi vaig pensar que igual era alguna cosa del so, però ja no se que pensar....L'ext4, la targeta gràfica, el so...ni idea. Algún programa que està donant problemes....ufff....no se...

Ahir estava escoltant amb l'amarok (el 2.0, ja que l'altre el vaig llevar per si era això el problema), les cançons de Jamendo, i no va passar res, com podeu comprovar en l'arxiu de dalt.....:confused:

I'm confused....

---

### Post by Urfe on 2009-05-08
Hola, Kukat.

Jo tinc el mateix problema i des d'Argentina Team m'han recomanat que vigili la temperatura del processador. Em diuen que si arriba a 85-90 Cº és un indici de problemas.

Encara estic fent comprovacions però podria ser aquest el problema.

He instal·lat sensors-applet i lm-sensors.

sudo apt-get install sensors-applet lm-sensors

Salut.

---

### Post by kukat on 2009-05-08
Doncs la veritat es que és una possibilitat, ja que estic rallant-me. Avui no se m'ha penjat, i ahir va ser solament dues vegades de bon matí....insta&#320;laré també això!
Gracies!

---

### Post by quitus on 2009-05-08
just després de de la "penjada" en iniciar l'ordinador, fes una ullada al registre del sitema , com comentaves al principi del fil, encara no has fet cap referencia al error exacte, i la informació que has donat no es gaire útil.

salut

---

### Post by kukat on 2009-05-17
mmm.....
estava passant unes fotografies a altre disc dur (en format NTFS), i se m'ha penjat...

El Registre:(kern.log)

May 17 22:34:58 kukatmaulet kernel: [42825.463192] [drm] Num pipes: 1
May 17 22:34:58 kukatmaulet kernel: [42825.463201] [drm] writeback test succeeded in 1 usecs
May 17 22:37:34 kukatmaulet kernel: [42981.684022] end_request: I/O error, dev fd0, sector 0
May 17 22:37:34 kukatmaulet kernel: [42981.708032] end_request: I/O error, dev fd0, sector 0
May 17 22:37:48 kukatmaulet kernel: [42995.784068] end_request: I/O error, dev fd0, sector 0
May 17 22:37:48 kukatmaulet kernel: [42995.816071] end_request: I/O error, dev fd0, sector 0

Es de les poques coses que he vist que poden ser un error...però te pinta de ser de hardware, veritat?  no se...o alguna cosa del ext4


EDITO:

Aquest es d'aquest matí: 

(auth.log)

May 18 10:31:48 kukatmaulet dbus-daemon: Rejected send message, 4 matched rules; type="error", sender=":1.11" (uid=0 pid=2804 comm="/sbin/wpa_supplicant -u -f /var/log/wpa_supplicant") interface="(unset)" member="(unset)" error name="fi.epitest.hostap.WPASupplicant.InvalidInterface" requested_reply=0 destination=":1.9" (uid=0 pid=2799 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))
May 18 10:31:58 kukatmaulet gdm[2777]: pam_unix(gdm:session): session opened for user kukat by (uid=0)
May 18 10:31:58 kukatmaulet gdm[2777]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0

(sys.log)
May 18 10:29:45 kukatmaulet kernel: [40199.689946] __ratelimit: 3 callbacks suppressed
May 18 10:29:45 kukatmaulet kernel: [40199.689954] ext4: find_group_flex failed, fallback succeeded dir 117070
May 18 10:29:48 kukatmaulet kernel: [40202.207240] ext4: find_group_flex failed, fallback succeeded dir 23012
May 18 10:30:01 kukatmaulet /USR/SBIN/CRON[21201]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 18 10:30:05 kukatmaulet kernel: [40219.916324] ext4: find_group_flex failed, fallback succeeded dir 117070
May 18 10:30:07 kukatmaulet kernel: [40221.447385] ext4: find_group_flex failed, fallback succeeded dir 117070
May 18 10:30:09 kukatmaulet kernel: [40223.322399] ext4: find_group_flex failed, fallback succeeded dir 117070
May 18 10:30:09 kukatmaulet kernel: [40223.704579] ext4: find_group_flex failed, fallback succeeded dir 117070
May 18 10:30:10 kukatmaulet kernel: [40225.003180] ext4: find_group_flex failed, fallback succeeded dir 117070
May 18 10:30:11 kukatmaulet kernel: [40225.400936] ext4: find_group_flex failed, fallback succeeded dir 117070
May 18 10:30:11 kukatmaulet kernel: [40225.402175] ext4: find_group_flex failed, fallback succeeded dir 117070
May 18 10:30:11 kukatmaulet kernel: [40225.667096] ext4: find_group_flex failed, fallback succeeded dir 117070
May 18 10:31:42 kukatmaulet syslogd 1.5.0#5ubuntu3: restart.

---

### Post by kukat on 2009-05-18
Per cert, la temperatura és

41ºC -- Disc dur Maxtor
39ºC -- Disc dur secundari
41ºC -- temp1
54ºC -- temp2 (supose que serà el processador)

Salut!

---

### Post by indiosincracia on 2009-05-18
En la linea d'en papapep, provaria d'instal·lar un kernel anterior i provar si es penja.

---

### Post by CarlesOriol on 2009-05-18
has fet un memtest a l'iniciar l'ordinador??

---

### Post by kimet on 2009-05-18
Hola.

Jo descartaria que fos un problema de hardware si tens altres sistemes funcionant be.

Per el que havia llegit en algún forum, desde el kernel 2.6.27 és donava suport a ext4 però no s'aconsellava fins al 2.6.30.... puc estar equivocat (el meu anglés és molt bàsic)](*,)

I, si poses l'error que et surt al log i el busques al google: 

ext4: find_group_flex failed, fallback succeeded [http://www.google.es/search?q=ext4:+find_group_flex+failed,+fallback+succeeded&hl=ca&start=0&sa=N]("http://www.google.es/search?q=ext4:+find_group_flex+failed,+fallback+succeeded&hl=ca&start=0&sa=N") sembla que està reportat com a bug..(el meu anglés és extremadament dolent)](*,)](*,)

O sigui: ext4 està molt verd encara.

):P

---

### Post by CarlesOriol on 2009-05-18
> **kimet said:**
> Jo descartaria que fos un problema de hardware si tens altres sistemes funcionant be.

ui, no, no... ni de conya. No et pots imaginar la quantitat d'ordinadors que van "bé" pel mon amb problemes aleatoris per culpa de la memòria. (de fet el guindous es menja molts d'aquests marrons :-D ) 

> Per el que havia llegit en algún forum, desde el kernel 2.6.27 és donava suport a ext4 però no s'aconsellava fins al 2.6.30.... 

L'ext4 va de conya. xaxi piruli i pilonguins.

Aqui tens un enlaç que comenta precisament això: [http://ubuntuforums.org/showpost.php?p=7303547&postcount=18](http://ubuntuforums.org/showpost.php?p=7303547&postcount=18)

---

### Post by kimet on 2009-05-18
A veure CarlesOriol, si tens dos sistemes operatius en el mateix ordinador i uns d'ells te falades i l'altre no, el mes logic és que no sigui problema de ferralla...Em sembla a mi... Però és clar si en Carles Oriol i Margarit diu que no, haurem de callar:-#

Ps. Noi, has de tenir l'ego molt alt per posar un enllaç al teu propi comentari...:mrgreen::mrgreen:

---

### Post by kimet on 2009-05-18
O potser volies dir aquest enllaç:

[http://www.vivalinux.com.ar/distros/kubuntu-con-ext4-pierde-datos.html]("http://www.vivalinux.com.ar/distros/kubuntu-con-ext4-pierde-datos.html")

Salud.

---

### Post by kukat on 2009-05-18
Estic content amb el ext4...espere que no tinga res a veure....
Bé, anava a comentar el que he fet, i se m'ha quedat penjat....jajajaj (començe a pensar que es el Firefox.....no crec....)

Bé, he fet el memtest i m'ha posat:

"Pass complete, no errors...."


Solament tinc el Debian que vaig insta&#320;lar fa poc, però tampoc l'he provat massa. Podria provar a veure si falla amb el Debian també per comprovar.....


Ara he trobat açò, en el Kernel Log

May 18 22:00:20 kukatmaulet kernel: [ 1596.800865] end_request: I/O error, dev sr1, sector 0
May 18 22:00:20 kukatmaulet kernel: [ 1596.800881] Buffer I/O error on device sr1, logical block 0
May 18 22:00:20 kukatmaulet kernel: [ 1596.800895] Buffer I/O error on device sr1, logical block 1
May 18 22:00:20 kukatmaulet kernel: [ 1596.800899] Buffer I/O error on device sr1, logical block 2
May 18 22:00:20 kukatmaulet kernel: [ 1596.800903] Buffer I/O error on device sr1, logical block 3
May 18 22:00:20 kukatmaulet kernel: [ 1596.856121] end_request: I/O error, dev sr1, sector 0
May 18 22:00:20 kukatmaulet kernel: [ 1596.856137] Buffer I/O error on device sr1, logical block 0
May 18 22:12:37 kukatmaulet kernel: Inspecting /boot/System.map-2.6.28-11-generic
May 18 22:12:37 kukatmaulet kernel: Cannot find map file.
May 18 22:12:38 kukatmaulet kernel: Loaded 52143 symbols from 47 modules.

No se m'ocurreix res mes.....
a no ser que siga alguna cosa del disc dur....?¿?¿?


EDITO: EN el Syslog, he vist açó

May 18 21:49:44 kukatmaulet ntpdate[3928]: can't find host ntp.ubuntu.com 
May 18 21:49:44 kukatmaulet ntpdate[3928]: no servers can be used, exiting
May 18 21:50:01 kukatmaulet /USR/SBIN/CRON[3937]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 18 22:00:01 kukatmaulet /USR/SBIN/CRON[4399]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
May 18 22:00:01 kukatmaulet /USR/SBIN/CRON[4413]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 18 22:00:20 kukatmaulet kernel: [ 1596.800865] end_request: I/O error, dev sr1, sector 0
May 18 22:00:20 kukatmaulet kernel: [ 1596.800881] Buffer I/O error on device sr1, logical block 0
May 18 22:00:20 kukatmaulet kernel: [ 1596.800895] Buffer I/O error on device sr1, logical block 1
May 18 22:00:20 kukatmaulet kernel: [ 1596.800899] Buffer I/O error on device sr1, logical block 2
May 18 22:00:20 kukatmaulet kernel: [ 1596.800903] Buffer I/O error on device sr1, logical block 3
May 18 22:00:20 kukatmaulet kernel: [ 1596.856121] end_request: I/O error, dev sr1, sector 0
May 18 22:00:20 kukatmaulet kernel: [ 1596.856137] Buffer I/O error on device sr1, logical block 0
May 18 22:04:06 kukatmaulet noip2[2560]: invisigoth.sytes.net set to 85.59.50.72
May 18 22:09:01 kukatmaulet /USR/SBIN/CRON[4614]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
May 18 22:10:01 kukatmaulet /USR/SBIN/CRON[4694]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
May 18 22:12:37 kukatmaulet syslogd 1.5.0#5ubuntu3: restart.




Que deu ser quan estava connectant-me per escriure al fòrum....

Salut!

---

### Post by kimet on 2009-05-18
Per comprovar/reparar l'estat del disc dur hi ha el comand "fsck", però t'ho sol fer al arrencar cada x vegades. Pots provar de veure el funcionament amb "man fsck" o buscar un tutorial del seu funcionament al google. La veritat és que no sé si funciona amb ext4.

---

### Post by marteljorge on 2009-05-19
marteljorge@marteljorge-server:~$ ext4fsck
bash: ext4fsck: command not found
marteljorge@marteljorge-server:~$ fsck
fsck           fsck.ext2      fsck.ext4      fsck.minix     fsck.nfs       fsck.vfat      
fsck.cramfs    fsck.ext3      fsck.ext4dev   fsck.msdos     fsck.reiserfs  
Se supossa que sí funciona, però, no ho sé. Jo refrigeo amb pots de vidre plens de sal i aigua congelats a ~-19ºC, i el meu uname -r diu:
marteljorge@marteljorge-server:~$ uname -r
2.6.28-12-server
i Jo només tinc problemes amb els sensors(no els trobo) i fglrx(no carrega el módul del kernel), al PC. Preò al portàtil falla fins i tot el wifi i el disc dur(potser tingui que veure el fet que el ventall no li funciona del tot).
Per cert, no facis el fsck a una partició muntada en rw.

---

### Post by kukat on 2009-05-20
Descartats els problemes de hadware: Els tests a les memòries RAM i als Discs Durs no han donat cap errada...Seguirem informant :)
El meu uname -r: 

kukat@kukatmaulet:~$ uname -r
2.6.28-11-generic


Anant amb Papapep i el del Kernel...insta&#320;le un de superior (el 30???) o un d'inferior??  
Es bo insta&#320;lar un kernel distint, o sol donar problemes?

Salut!

---

### Post by CarlesOriol on 2009-05-20
> **kukat said:**
> 
May 18 22:00:20 kukatmaulet kernel: [ 1596.800881] Buffer I/O error on device sr1, logical block 0

Si el hdd t'ho permet fes un test (llarg) amb les smart tools (smartmontools).

A veure que t'explica el disc dur.

---

### Post by CarlesOriol on 2009-05-20
> **kimet said:**
> Ps. Noi, has de tenir l'ego molt alt per posar un enllaç al teu propi comentari...:mrgreen::mrgreen:

Nops... és RECURSIVITAT.

Poden passar 3 coses:

1. Treus una conculsio' i surts de la indentacio'

2. Un stack overflow error com una casa de pages (i de les grans incloent bèsties i masovera)

3. Si no exiteix un bon control el codi de l'stack i aquest es mescla amb el codi del heap executant dades en lloc del programa. (tècnica molt usada fa temps per petar aquell sistema de redmon)

---

### Post by kimet on 2009-05-20
> Nops... és RECURSIVITAT

=D>=D> No hi havia caigut... Es que se t'ha oblidat el tracte amb els humans...

Si em vols fer petar només m'has de banejar home, l'unic que pot passar és que et quedis tot solet ()
:---) 

(falten icones...);)

---

### Post by kukat on 2009-05-21
Li he passat el Hiren's Boot CD, i li vaig passar el HDD Regenerator (o com es digui), que va tardar quasi 24 hores a fer el disc dur de 250GB.

L'altre disc dur de 80GB li vaig passar altre programa del Hiren's (era solament de tipus "test", no com el Regenerator, que tarda 10 vegades més...) i tampoc va donar cap error....

Bé, de totes formes, vaig a veure si li passe també el que em comentes, i així ja el conec també per a altres ocasions.

EDITO:

Li he passat aquesta comanda: sudo smartctl -t long /dev/sda | zenity --text-info --width 640 --height 480
que he trobat per ahí.....jjeje

---

### Post by Urfe on 2009-05-26
Per moments he tingut la sensació que el kukat i jo potser havíem fet alguna cosa malament o directament estavem bojos.

Però buscant al mon anglosaxó he trobat un fil amb 34 pàgines de comentaris sobre les penjades del Jaunty Jackalope.

[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

És estrany però em sento millor amb la troballa, coses de l'ésser humà, suposso.

Espero que no us sàpiga greu si dic que la meva decepció amb el Jaunty Jackalope és inmensa.

Salut.

---

### Post by jaume69 on 2009-05-26
A mi amb **ext4** també de tan en tan s´em penja i queda tot congelat.
I a més quan el poso en mode **Suspensió**,al reactivar-lo perd l´escriptori i passa a mode gràfic,amb tot un seguit de llistats de comprovacions indefinit.

---

### Post by kukat on 2009-05-26
Vaig perdut. No se si és el ext4, o vejes tu a saber....Però no se...de moment anirem tirant a veure si algún dia m'ix alguna idea....jjejeje 

Es que es tan intermitent...Igual estic una setmana sense que em pase res, que estic un parell de dies que es penja unes quantes vegades! :(

...
Ni idea....

---

### Post by papapep on 2009-05-26
> No se si és el ext4, o vejes tu a saber....

Doncs reinstal·la reformatant a ext3, i sortiràs de dubtes... :)

Per cert, quina placa mare tens?

---

### Post by kukat on 2009-05-26
Tinc la Asrock K7S41GX!! :)

Tindre 10.000 cansons y l'amarok amb el MYSQL, no tindrà res a veure, veritat??? jajaja Es que algunes vegades crec que s'ha parat amb l'amarok funcionant.......però clar...igual te a veure també tot açò amb l'ext4....vejes tu a saber....
:/

---

### Post by papapep on 2009-05-26
Per poder ser, posats a no trobar-ho, poden ser multitud de coses. Ara bé, si no estàs executant l'amarok el 100% del temps i el 100% de cops que se't penja, doncs no...
Probablement seria interessant fer un cop d'ull als registres del sistema dins /var/log, immediatament després de que petés, a veure si ha quedat alguna pista interessant.

---

### Post by kukat on 2009-05-26
Ja, però....quin arixu puc mirar??? es que hi ha tants! Jo anava a "Sistema", "Administració", "Visualitzador de registres"....però...per més que mirava sempre trobava coses com les que ja he dit abans....que igual tampoc te res a veure....Ufff...bé

la pròxima vegada que em passe ho veuré, però moltes vegades crec que és al manipular arxius. Si no ho fa l'amarok actualitzant la biblioteca, ho faig jo copiant arixus...no se...pot ser que siga alguna cosa així....Hui encara no m'ha passat res, i ahir tampoc! :)

---

