---
title: "Problemes actualització 7.10 wifi conceptronic"
date: 2007-10-28
forum: Catalan Team
---

### Post by xavier22 on 2007-10-28
Benvolguts amics:

Fa dies que vaig actualitzar a 7.10 i no he aconseguit que funcioni la xarxa wifi. Anteriorment amb el 7.04 anva perfecte i ara la connexió comença a funcionar quan vol i es perd sovint. El cas és que ni puc buscar una sol3lució des de Linux i he d'escriure aquest post des de windows!!

He buscat la solució de fa dies també i no he trobat encara una resposta a d'altres Forums clara. Resulta que utilitzo una tarja Concetronic cr54i i va amb un modul que segons sembla a Gutsi és erroni. Per canviar-lo he llegit que cal col·locar-lo a la blacklist i instal·lar el nou modul:

make
strip rt61.ko
sudo make install


Per fer-ho he de descarregar l'última versió des de serialmonkey i després fer make i make install i aquí hi ha el problema, el make install em dona un error:

sudo make install
*** Install module in /lib/modules/2.6.22-14-generic/extra ...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
INSTALL /home/xavier/Desktop/rt61-cvs-2007102416/Module/rt61.ko
DEPMOD 2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
/sbin/depmod -a
WARNING: Couldn't find symtab and strtab in module /lib/modules/2.6.22-14-generic/extra/rt61.ko

Penso que l'error deu ser perquè no hi ha intal·lat el source kernel però no en tinc la seguretat.

Algú de vosaltres sabeub que vol dir aquest error a'lhora de fer el make isntall?

Salutacions

---

### Post by Ferri on 2007-10-28
Crec que tu mateix ja has posat la resposta. Estàs intentant afegir un mòdul a la kernel, però per fer-ho necessites els "kernel-sources".

---

### Post by xavier22 on 2007-10-29
Bé però el cas és que no se com instal·lar el source kernell. Com que no puc connectar a Internet des de Ubuntu he baixat dos arxius linux-source i linux-headers, els he instal·lat i continua donants el mateix missatge.

---

### Post by Ferri on 2007-10-29
En principi, amb això n'hi hauria d'haver prou, si és que aquest és el problema:
```
sudo apt-get install linux-headers build-essential gcc
```

---

### Post by xavier22 on 2007-11-02
Doncs ho he fet i continuu sense sortir-me'n. La veritat és que estic desesperat. No sé que me´s fer.
He aconseguit connexió durant una estona i s'ha carregat el linux-headers-generic, també he intal3lat linux-source i res ara em diu que no troba el directori /lib/linux-headers tot i que està instal·lat i a mig fer, es perd la connexió a Internet.

En f que estic per fer una instal·lació nova de Suse per exemple a verure si m'ho soluciona.

---

### Post by Nescafi on 2008-02-07
You must must use the -S switch in the *strip* command
```
$ strip -S rt61.ko
```
if not used all the symbols are removed from the file.

I had the same problem and this solved it for me.

---

