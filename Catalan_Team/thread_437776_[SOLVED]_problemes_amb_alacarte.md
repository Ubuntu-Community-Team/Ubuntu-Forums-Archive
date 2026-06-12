---
title: "[SOLVED] problemes amb alacarte"
date: 2007-05-09
forum: Catalan Team
---

### Post by xavier22 on 2007-05-09
Benvolguts:

Primer de tot presentar-me. Fa dues setmanes he descobert Ubuntu 7.04 i estic entusiasmat. ho he instal·lat pràcticament tot la wifi, el so el vídeo, només tinc problemes amb bluetouth i amb la Palm. Però he instal·lat Beryl i és fantàstic, gDesklets, etc. A més del programari OpenOffice, Firefox o Audacity. Fisn ara usaba Suse però la dificultat d'instal·lar la tarja wifi em va aborrir fins al punt que ja pensava abandonar Línux després de 14 anys. Finalment Ubuntu 7 va venir en el meu ajut.

Bé el cas es que ara no puc editar el Menú Principal a Sistema > Preferències>Menú Principal. he descobert que l'ordre que l'executa és alacarte des de la consola i el missatge que em dona és:

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 441, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 373, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: ca_AD

He reinstalat alcarte, python i res continua donant-me el mateix missatge i l'editor de menús no funciona.

Algú té alguna idea?

Gràcies
Xavier

---

### Post by papapep on 2007-05-09
Si et fixes en el missatge d'error, sembla que tinguis algun problema amb els locales i l'idioma, ca_AD, que has definit (t'ho repeteix vàries vegades).

Podries provar:

```
sudo dpkg-reconfigure locales
```

Si tot i això segueix fallant, podries provar a ficar, per exemple, l'anglès com a idioma del sistema i veure si així s'executa correctament des del menú. T'ajudarà a intentar delimitar el problema.

A veure com et va.

---

### Post by xavier22 on 2007-05-09
Hola Pep:

doncs he fet el
sudo dpkg-reconfigure locales

i em segueix donant el problema. També he provat de reconfigurar a un altre idioma  a Sistema>Adminstració>Suport d'Idioma i trio English Unitet States. Aleshores he tornat a entrar a gnome i "bingo" apareix el main menu. Ara modifico les entrades torno a canviar a idioma Catalan Esapña -abans tenia Català Andorra- surto de gnome i torno a entrar i ara si que funciona.
Potser estava "com encallat".

Gràcies

---

### Post by eselma on 2007-05-10
No sé on està el problema exactament, però usant l'opció "Andorra" com a *locale *(a part d'instal·lar-te els teclats "espanyol" i AZERTY ) és fàcil tenir dificultats. Segurament caldria polir quelcom. Recordo uns problemes amb la Dapper (6.06) que es van resoldre quan vaig optar per *ca_ES* en lloc de *ca_AD*. Concretament, el teclat no reconeixia els caràcters *doble-stroke*, bàsicament els accentuats: à. è, á, é, etc. malgrat acceptar la Ç i la Ñ normalment. 

La veritat, l'opció "Andorra" és una temptació molt forta per molts, i potser no a tothom li ha anat malament. Alguna experiència des del Principat (de les Valls)?

---

### Post by EnricPV on 2008-01-03
Salutacions des del País Valencià:

A mi m'està succeint el mateix que al Xavier. Vaig a provar a seguir els mateixos passos i vore si funciona.

La temptació d'escollir Andorra és directament proporcional a l'esperança de tindre un estat propi per tots els catalans.

Au cacau

---

### Post by EnricPV on 2008-01-03
Hola un altre viatge:

Amb més esforç del previst però ja ho tinc. En primer lloc, no sabia reiniciar el gnome amb la combinació de tecles Ctrl+Alt+Retrocés (una altra cosa apresa hui). En segon lloc no sabia que després de seleccionar l'anglès, anglès EUA per exemple, a Sistema > Administració > Suport d'idioma, havia de tornar a triar-la a l'entrada al gnome (més coses apreses hui). En eixe punt el sistema m'ha dit que la meua llengua per defecte era el català d'Andorra (veges tu qui me mana a mi ser independentista!) i que si volia canviar-la a l'anglès EUA. Conteste afirmativament i faig la mateixa jugada però a l'inrevés, aquesta volta triant català d'Ej-pania (com Déu i els Borbons manen!) i ara ja em funciona l'edició de menús amb alacarte.

Encara em passa poc, tota la vida sentint-ho (Ejpaña, Ejpaña y nadie más) i peim! jo cabut trie Andorra.

Au a rebentar de salut

Enric

---

### Post by Curial on 2008-01-03
Em sembla que els que tenim el síndrome d'Andorra en som uns quants...

:)

Salut

---

