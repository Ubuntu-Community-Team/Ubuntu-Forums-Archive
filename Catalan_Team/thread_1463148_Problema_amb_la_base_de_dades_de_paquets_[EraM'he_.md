---
title: "Problema amb la base de dades de paquets [Era:M'he carregat el synaptic]"
date: 2010-04-26
forum: Catalan Team
---

### Post by pelai21 on 2010-04-26
Hola companys,

He tingut el següent problema: mentre instal·lava un programa a través del synaptic, l'ordinador ha quedat penjat (per culpa d'un altre programa). No hi havia manera de fer-lo tornar en si, i al final he optat per reiniciar. I ara, quan intento instal·lar o desinstal·lar qualsevol programa, m'apareix el següent missatge:

> E: gaupol: el subprocés installed post-installation script retornà el codi d'eixida d'error 2
E: python-chardet: el subprocés installed post-installation script retornà el codi d'eixida d'error 2
E: python-enchant: el subprocés installed post-installation script retornà el codi d'eixida d'error 2

Pel que sembla hi ha tres programets que em fan la guitza: Gaupol (el programa que intentava instal·lar la primera vegada), python-chardet i python-enchant. He provat de deinstal·lar-los, però el synaptic no em respon. Alguna idea?

---

### Post by papapep on 2010-04-26
Se't pot haver quedat malmesa la base de dades de paquets, però difícilment el Synaptic. Jo provaria fent:

```
sudo apt-get -f install
```

i un cop estigui, fer:

```
sudo dpkg --configure --pending
```

Un cop estiguin les dues ordres torna a provar a fer alguna cosa amb els paquets, a veure si hi ha algun canvi positiu.

---

### Post by pelai21 on 2010-04-27
Seguim igual, amb el primer codi m'apareix això:

> S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
Els paquets següents s'instal·laren automàticament i ja no són necessaris:
  sp-auth libvlccore-dev libvlc-dev lib32stdc++5
Empreu «apt-get autoremove» per a suprimir-los.
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 0 no actualitzats.
3 no instal·lats o suprimits completament.
Després d'aquesta operació s'empraran 0B d'espai en disc addicional.
S'està configurant gaupol (0.15-1ubuntu1) ...
dpkg (subprocés): no es pot executar installed post-installation script: Exec format error
dpkg: s'ha produït un error en processar gaupol (--configure):
 el subprocés installed post-installation script retornà el codi d'eixida d'error 2
S'està configurant python-chardet (1.0.1-1.1) ...
dpkg (subprocés): no es pot executar installed post-installation script: Exec format error
dpkg: s'ha produït un error en processar python-chardet (--configure):
 el subprocés installed post-installation script retornà el codi d'eixida d'error 2
S'està configurant python-enchant (1.5.3-1) ...
dpkg (subprocés): no es pot executar installed post-installation script: Exec format error
dpkg: s'ha produït un error en processar python-enchant (--configure):
 el subprocés installed post-installation script retornà el codi d'eixida d'error 2
S'han trobat errors en processar:
 gaupol
 python-chardet
 python-enchant
E: Sub-process /usr/bin/dpkg returned an error code (1)
i amb el segon:

> S'està configurant python-chardet (1.0.1-1.1) ...
dpkg (subprocés): no es pot executar installed post-installation script: Exec format error
dpkg: s'ha produït un error en processar python-chardet (--configure):
 el subprocés installed post-installation script retornà el codi d'eixida d'error 2
S'han trobat errors en processar:
 python-chardet

Alguna idea?

---

### Post by papapep on 2010-04-27
Sembla clar que el problema el tens al paquet [Gaupol]("http://packages.ubuntu.com/karmic/gaupol") i les seves dependències. Jo provaria a eliminar-lo del tot:

```
sudo aptitude purge gaupol python-chardet python-enchant
```

a veure si et deixa.

Si et deixa, tornaria a fer les dues ordres d'abans per acabar de "fer net".

---

### Post by pelai21 on 2010-04-27
Res a fer: 

> S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
Els paquets següents se suprimiran:
  gaupol{p} lib32stdc++5{u} libvlc-dev{u} libvlccore-dev{u} 
  python-chardet{p} python-enchant{ap} sp-auth{u} 
0 paquets a actualitzar, 0 a instal·lar, 7 a suprimir i 0 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'alliberaran 7848kB.
Esteu segur de voler continuar? [Y/n/?] y
S'està escrivint la informació d'estat estesa... Fet
(S'està llegint la base de dades ... hi ha 229411 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant gaupol ...
dpkg (subprocés): no es pot executar installed pre-removal script: Exec format error
dpkg: s'ha produït un error en processar gaupol (--purge):
 el subprocés installed pre-removal script retornà el codi d'eixida d'error 2
dpkg (subprocés): no es pot executar installed post-installation script: Exec format error
dpkg: s'ha produït un error en netejar:
 el subprocés installed post-installation script retornà el codi d'eixida d'error 2
S'està desinstal·lant python-chardet ...
dpkg (subprocés): no es pot executar installed pre-removal script: Exec format error
dpkg: s'ha produït un error en processar python-chardet (--purge):
 el subprocés installed pre-removal script retornà el codi d'eixida d'error 2
S'està desinstal·lant python-enchant ...
dpkg (subprocés): no es pot executar installed pre-removal script: Exec format error
dpkg: s'ha produït un error en processar python-enchant (--purge):
 el subprocés installed pre-removal script retornà el codi d'eixida d'error 2
S'han trobat errors en processar:
 gaupol
 python-chardet
 python-enchant
E: Sub-process /usr/bin/dpkg returned an error code (1)
S'ha produït un error en la instal·lació del paquet. S'està intentant restablir.
S'està llegint la llista de paquets... Fet           
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet

---

### Post by papapep on 2010-04-27
Doncs prova amb un:

```
sudo dpkg --configure -a
```

si tampoc va, prova un:

```
sudo apt-get dselect-upgrade
```

Quan posis el resultat de les ordres, copia i enganxa també al capdamunt la ordre que has picat, si us plau. Ja suposo que ho fas bé, però és per no deixar cap opció sense considerar ;)

---

### Post by pelai21 on 2010-04-27
La primera ordre sembla que s'ha dut a terme, però després tampoc podia eliminar o reinstal·lar els 3 paquets problemàtics. La segona ordre em dóna aquest resultat:

> S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 0 no actualitzats.
1 no instal·lats o suprimits completament.
Es necessita obtenir 0B/172kB d'arxius.
Després d'aquesta operació s'empraran 0B d'espai en disc addicional.
Voleu continuar [S/n]? s
(S'està llegint la base de dades ... hi ha 229412 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar python-chardet 1.0.1-1.1 (fent servir .../python-chardet_1.0.1-1.1_all.deb) ...
dpkg (subprocés): no es pot executar seqüència de «pre-removal» antiga: Exec format error
dpkg: warning: seqüència de «pre-removal» antiga returned error exit status 2
dpkg - s'està provant la seqüència del paquet nou en el seu lloc...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2196, in <module>
    main()
  File "/usr/bin/pycentral", line 2190, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1645, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 381, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 414, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: s'ha produït un error en processar /var/cache/apt/archives/python-chardet_1.0.1-1.1_all.deb (--unpack):
 el subprocés seqüència pre-removal nova retornà el codi d'eixida d'error 1
dpkg (subprocés): no es pot executar installed post-installation script: Exec format error
dpkg: s'ha produït un error en netejar:
 el subprocés installed post-installation script retornà el codi d'eixida d'error 2
S'han trobat errors en processar:
 /var/cache/apt/archives/python-chardet_1.0.1-1.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Curiosament, el programa Gaupol, el que instal·lava quan se'm penjà l'ordinador, funciona sense problemes. Crec que el problema ve del python-chardet, ja que quan intento eliminar-lo completament em diu el següent:

> E: python-chardet: El paquet està en un estat molt dolent e inconsistent - el tindreu que  reinstal·lar abans d'intentar desinstal·lar-lo.

Però quan intento reinstal·lar-lo, em surt el següent missatge d'error:

> E: /var/cache/apt/archives/python-chardet_1.0.1-1.1_all.deb: el subprocés seqüència pre-removal nova retornà el codi d'eixida d'error 1

---

