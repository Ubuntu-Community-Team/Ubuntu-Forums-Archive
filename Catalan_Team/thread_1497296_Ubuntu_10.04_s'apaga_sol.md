---
title: "Ubuntu 10.04 s'apaga sol"
date: 2010-05-30
forum: Catalan Team
---

### Post by albertdelleida on 2010-05-30
Hola a tots i totes,

sembla que aviat tindré el meu estimat Ubuntu 10.04 llest del tot i una part molt important és gràcies a vosaltres :D

Ara petit dubte: el meu ordinador (un HP Pavilion dv5) es tanca sol des de que tinc instal·lat l'Ubuntu 10.04. Amb l'Ubuntu 9.10 ni amb la partició de Windows em passa. 

Les vegades que es tanca coincideix sempre en que la temperatura de l'ordinador és molt elevada i normalment em passa quan estic jugant o fa moltes hores que tinc encés l'ordenador. 

El que em sembla estrany és que abans això no em passava. La pregunta és: sabeu si això pot ser conseqüència directa d'usar el 10.04? He arribat a pensar que en aquesta versió, quan l'ordinador es sobrecalenta, l'Ubuntu l'apaga automàticament. És possible?

Altre cop moltes gràcies a tots, m'esteu ajudant a millorar molt la meua primera experiència amb l'Ubuntu :)

---

### Post by kukat on 2010-05-30
doncs la veritat és que poden ser moltes coses!! 

Però de moment, podries passar-nos uns "logs" del sistema???? 

quan tornes a encendre'l pots fer la següent ordre:

**tail -n 20 /var/log/syslog **

Açò traurà les 20 últimes línies del registre del sistema. 

a veure si ens diu alguna cosa...:)

També pots insta&#320;lar:
**sudo apt-get install sensors-applet lm-sensors**
Que et diuen la temperatura del Processador, per si te a veure amb la temperatura.

---

### Post by albertdelleida on 2010-05-30
Ara m'instal·lo l'aplicació per veure la temperatura. Ja us ho dic, segur que s'apaga quan la temperatura és alta, però podria obligar a que no ho fes?

Pel que fa als "logs"... Com ho faig per veure'ls? Quan haig d'escriure 
*tail -n 20 /var/log/syslog*?Potser són preguntes molt obvies però sóc molt novell... :P

---

### Post by papapep on 2010-05-30
> Ja us ho dic, segur que s'apaga quan la temperatura és alta, però podria obligar a que no ho fes?

Si tens una caixa de processadors per anar-los substituïnt a mida que es vagin fregint, cap problema :)

Ara seriosament, els sistemes tenen un procediment de protecció que quan pugen excessivament de temperatura fa que s'aturin, abans de cremar-se. S'apaga per la temperatura, no per que l'Ubuntu l'apagui. La pregunta, doncs, és què causa que es descontroli tant la temperatura. No es posa en marxa el ventilador? potser el dissipador de la gràfica, si en té, o del processador no fa bon contacte? Busca al fòrum fils antics que van parlar llarg i estès del tema, repetits cops.

---

### Post by kukat on 2010-05-30
Si, tens que anar a "Aplicacions", "Accesoris", "Terminal", i escriure la línia:


**tail -n 20 /var/log/syslog** i copiar el resultat.... 

o bé:

**tail -n 20 /var/log/syslog > /home/EL_TEU_USUARI/resultat.txt**

Per a dirigir el resultat a un fitxer de text!!!

---

### Post by albertdelleida on 2010-05-31
Hola de nou,

aquí us adjunto els "logs" del sistema:
[I]
May 31 09:16:28 lordinadordelalbert NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
May 31 09:16:28 lordinadordelalbert NetworkManager: <info>  Policy set 'Auto WLAN_7C' (wlan0) as default for routing and DNS.
May 31 09:16:28 lordinadordelalbert NetworkManager: <info>  Activation (wlan0) successful, device activated.
May 31 09:16:28 lordinadordelalbert NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
May 31 09:16:28 lordinadordelalbert ntpdate[1575]: adjust time server 91.189.94.4 offset 0.192115 sec
May 31 09:16:36 lordinadordelalbert kernel: [   35.140072] wlan0: no IPv6 routers present
May 31 09:17:01 lordinadordelalbert CRON[1676]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 31 09:17:25 lordinadordelalbert AptDaemon: INFO: Initializing daemon
May 31 09:23:25 lordinadordelalbert AptDaemon: INFO: Quiting due to inactivity
May 31 09:23:25 lordinadordelalbert AptDaemon: INFO: Shutdown was requested
May 31 09:39:47 lordinadordelalbert dhclient: DHCPREQUEST of 192.168.1.36 on wlan0 to 192.168.1.1 port 67
May 31 09:39:47 lordinadordelalbert dhclient: DHCPACK of 192.168.1.36 from 192.168.1.1
May 31 09:39:47 lordinadordelalbert NetworkManager: <info>  DHCP: device wlan0 state changed bound -> renew
May 31 09:39:47 lordinadordelalbert NetworkManager: <info>    address 192.168.1.36
May 31 09:39:47 lordinadordelalbert NetworkManager: <info>    prefix 24 (255.255.255.0)
May 31 09:39:47 lordinadordelalbert NetworkManager: <info>    gateway 192.168.1.1
May 31 09:39:47 lordinadordelalbert NetworkManager: <info>    nameserver '80.58.61.250'
May 31 09:39:47 lordinadordelalbert NetworkManager: <info>    nameserver '80.58.61.254'
May 31 09:39:47 lordinadordelalbert NetworkManager: <info>    domain name 'local.lan'
May 31 09:39:47 lordinadordelalbert dhclient: bound to 192.168.1.36 -- renewal in 1420 seconds.[/I]

Pel que fa a l'aplicació de la temperatura, m'instal·lo el que em comentes i quan afegeixo al quadre em surt "No sensors found!"

A veure si em podeu donar un cop de mà.

Merci :)

---

### Post by indiosincracia on 2010-05-31
Hola,

tema temperatura:
és cert que quan un ordinador d'escalfa molt es penja, el que passa és que no és normal, vull dir, que els ordinadors poden estar endollats 24h sobre els 365 dies que té l'any, si el dissipador i el ventilador funciona correctament no es penja.

com diu kukat, desde la consola:

$sudo apt-get install lm-sensors sensors-applet

despres:

$sudo sensors-detect

normalment es respon "yes" a tot, reiniciar l'ordinador
un altre cop desde la consola:

$sensors

si la temperatura és correcta, reinicia l'ordinador amb un kernel anterior.
vinga sort.

---

### Post by kukat on 2010-05-31
Ahhhh....ho senc, mea culpa. 

Tindràs que passar-me tot el contingut de "syslog". Perquè en les últimes 20 línies no puc veure-ho...hehe. 

o siga:

cat /var/log/syslog >> /home/USUARI/sortida_syslog.txt

I ja que estem, també el de "messages":

cat /var/log/messages >> /home/USUARI/sortida_messages.txt


I si a papapep se li ocurreix alguna cosa més.... :D

I els penjes ací, adjuntat com a ".txt"

;)

---

### Post by albertdelleida on 2010-05-31
Hola de nou. He intentat penjar els arxius .txt però pesen massa? Que faig? Us els envio o ho escric tot aquí? Es que és una mica llarg...

Pel que fa a l'aplicació de la temperatura, ara entenc perquè no funcionava. Vaig respondre No. Ara ho tornaré a provar. 

Merci a tots! :)

---

### Post by papapep on 2010-05-31
Comprimeix-los i adjunta l'arxiu comprimit.

---

### Post by albertdelleida on 2010-05-31
Fet, aquí els teniu!

---

### Post by kukat on 2010-06-02
No hi veig res estrany als arxius.....la veritat.

He vist alguna cosa semblant, però a Fedora, [URL="http://forums.fedoraforum.org/archive/index.php/t-243620.html"]ací[/URL (problemes de reinici).

Crec que (a falta de confirmació de papapep :)) el problema passa per provar amb altre Kernel(nucli) distint. 

Al fer "uname -r" al terminal, et diu quin Kernel tens. Quin tens?

Jo tinc aquest: **2.6.32-22-generic**

Si el teu es inferior, prova a fer:

**sudo aptitude update && sudo aptitude safe-upgrade**

Ja que el meu es va instal.lar en una actualització fa unes setmanes!!

;)

---

### Post by wgarcia on 2010-06-02
Un altre suggeriment potser tonto és provar una estona sense efectes gràfics per veure si el problema desapareix, per descartar que no sigui un sobreescalfament provinent de la targeta gràfica, ja que dius que notes que es tanca quan fas ús de jocs (suposo que a una màquina virtual potser).

---

### Post by albertdelleida on 2010-06-02
Hola de nou,

pel que fa al kernel, tinc el** 2.6.32-22-generic**, així que aquesta opció la podem descartar.

Pel que fa al tema dels efectes gràfics, seria una possibilitat ja que estic usant els efectes visuals extra, mentre que amb l'Ubuntu 9.10 usava l'opció més baixa (cap). Però això també és curiós, perquè amb l'Ubuntu 9.10, si intentava usar els efectes visuals normals l'ordinador s'alentia molt, en canvi amb l'Ubuntu 10.04 no tinc cap mena de problema (la qual cosa m'encanta, tot quedi dit :) ).

---

### Post by kukat on 2010-06-02
Prova ha desactivar els efectes d'escriptori, que molt bé ha dit wgarcia.

Si el problema persisteix, i abans d'instal·lar el Lucid Lynx, t'anava bé, no estaria mal instal·lar un Kernel _inferior_ al que tens. De totes formes, pots escollir-lo al Grub  ;)

---

### Post by albertdelleida on 2010-06-02
Ok, provaré a veure que passa. Però igualment amb el kernel anterior també em passava el mateix així que...

En tot cas, moltes gràcies a tots :)

---

### Post by JosepF on 2010-06-02
El nostre problema (a mi també em passa) es molt greu i em sembla haver llegit tot sobre el tema i no tinc cap sol·lució bona. Pel que he vist, hi ha dues solucions possibles: una potinera i una altre encara mes. Per salvar el teu ordinador i que no es fregeixi mentre algú no troba la sol·lució definitiva pots intentar actualitzar la BIOS, clar has de tenir el güindous. I l'altre i es la que jo utilitzo es engegar l'ordinador i un cop està tot a lloc, posar-lo en suspens i després tornar-lo a la vida i miraculosament ens ventiladors (fans, ja) tornen a funcionar. Jo segueixo investigant per trobar la sol·lució fina i elegant. Alguna cosa entre el kernel i el grub2 no va com hauria.

---

### Post by albertdelleida on 2010-06-02
Veig que no sóc l'únic que té aquest problema. En tot cas, els meus ventiladors si que funcionen (crec). Com puc fer-ho per comprovar-ho? Algú m'ho podria dir? Merci

---

### Post by papapep on 2010-06-02
JosepF, l'opció d'actualitzar la Bios pot ser una put***, però no és una opció "potinera" :) Si s'ha d'actualitzar deu ser per que alguna cosa de la versió que hi ha instal·lada no va a l'hora.

Albert, pel tema dels ventiladors poca cosa més fàcil: te'ls mires per veure si funcionen o no (és un portàtil o un fix?). Si és un portàtil, ho podràs veure posant la mà per on tenen la sortida d'aire, hauries de notar el ventet.
Si és un fix, també caldria verificar si els dissipadors estan ben colocats i fan la seva feina i si la pasta conductora que solen portar entre el difusor metàl·lic i el xip a refredar és en bon estat. En un portàtil tot això és bastant més complicat, per desgràcia...

---

### Post by JosepF on 2010-06-02
Papapep, si he d'instal·lar el güindows, per a mi es "potinera":P. No estic prou capacitat per fer-ho a la manera linux (m'acollona) i es l'últim que em falta per fer.

---

### Post by albertdelleida on 2010-06-02
:oops: perdoneu... no hi havia caigut...  que ruc que sóc...

sí que funcionen! ;)

---

### Post by kimet on 2010-06-03
Podria ser que algun procés es quedi consumint tota la CPU i això provoqui l'escalfament i posterior reinici del sistema?
Instal·la alguna eina que et permeti monitoritzar l'us de cpu. P.E. conky.

@Josepf El teu problema es diferent, (pot ser hauries d'obrir ul altre fil) pot estar relacionat els processos d'inici.

Salut.

---

### Post by JosepF on 2010-06-03
Jo ho veig. Ja he obert un fil pel tema, però un problema lingüistic :( l'ha enterrat al final del forum.

---

### Post by albertdelleida on 2010-06-04
Hola. Ja m'he instal·lat el conky però no el trobo :confused: on el tinc instal·lat?

---

### Post by kukat on 2010-06-07
si utilitzes el comandament "conky" en la terminal, no s'engega????

---

### Post by albertdelleida on 2010-06-08
Ara sí! Es que no sabia com engegar-lo :P En principi ara tot rutlla bé. Cap programa supera el 10% de la CPU i en total arriba a un 15%. Què us sembla?

Merci a tots un altre cop :)

---

### Post by kukat on 2010-06-09
L'opció de desactivar els efectes d'escriptori, com ha quedat???? :popcorn:

---

### Post by albertdelleida on 2010-06-14
Ho he provat i desactivant els efectes d'escriptori el problema desapareix, però a mi m'agradaria continuar tenint els efectes activats :P

---

### Post by albertdelleida on 2010-06-27
Bé nois, després d'estar fent diferents proves he arribat a la conclusió que el problema és el sobreescalfament del portàtil. L'Ubuntu només s'apaga quan el portàtil fa moltes hores que està encès i treballant i ha pujat molt la temperatura. He provat amb altres sistemes operatius i també passa el mateix! Hauré d'acostumar-me a deixar-lo descansar una mica més :)

Merci a totes!

---

### Post by PatrickVogeli on 2010-06-27
o netejar la merda dels disipadors no?

---

### Post by albertdelleida on 2010-06-27
també és una bona idea xD

---

