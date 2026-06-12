---
title: "Conectar a proxy amb autentifiacció i contrasenya"
date: 2011-10-14
forum: Catalan Team
---

### Post by vilaseca11 on 2011-10-14
Hola a tots.

Sóc nou en la plataforma d'ubuntu (L'he instal·lat avui de fet)  i m'he traobat amb el problema que a la hora de instal·lar plugins, programes... no puc ja que no em detecta l'internet. Si algú em pogues ajudar li estaria molt agrait. I de pas si teniu algun conssell per a un principiant...

P.D. El nevegador si que l'he pogut configurar i puc navegar.

Edit: tinc el sistema operatiu en català.. però pel que veig falten moltes coses per traduir, ho puc solucionar?

Salutacions...:D

---

### Post by CarlesOriol on 2011-10-14
Quina versió de l'ubuntu has insta&#320;lat?

---

### Post by wgarcia on 2011-10-15
vilaseca11, anem per parts, com deia l'amic Jack.

1) Sembla que tens connexió a Internet, oi, perquè amb el navegador pots navegar, valga la redundància.

2) No et deixa instal·lar més programes? Quin procediment vas fer servir per instal·lar programes i quin error veus?

3) Si se soluciona el tema d'instal·lar més programes, es pot mirar si tens instal·lades totes les traduccions, tot i que també pot ser que alguna coseta encara no estigui traduïda, tot i que el percentatge és ben alt, i van arribant actualitzacions que completen les traduccions.

---

### Post by vilaseca11 on 2011-10-15
Primer de tot gràcies per respondre.

> 1) Sembla que tens connexió a Internet, oi, perquè amb el navegador pots navegar, valga la redundància.Doncs si, l'internet l'he aconseguit fer funcionar.

> 2) No et deixa instal·lar més programes? Quin procediment vas fer servir per instal·lar programes i quin error veus?Primer de tot he intentat "ubuntu software center" però al intentar descarregar el problema em saltava aquest error:

407  Proxy Authentication Required

I per això demanava com puc posar usuari i contrasenya per poderme conectar.

Despres vaig intentar descarregar paquets debian, però alguns també necessitaven internet per acabar  de descarregar algua cosa.

> 3) Si se soluciona el tema d'instal·lar més programes, es pot mirar si  tens instal·lades totes les traduccions, tot i que també pot ser que  alguna coseta encara no estigui traduïda, tot i que el percentatge és  ben alt, i van arribant actualitzacions que completen les traduccionsQuan vaig iniciar ubuntu, ja em va preguntar per actualitzar el paquet de traduccions... però per culpa em va donar error al mirar actualitzacions.

Edit: he trobat això però no sé com fer-ho... si algú em pot ajudar!!!!
[http://danjared.wordpress.com/2011/03/09/configurar-el-proxy-en-ubuntu/]("http://http://danjared.wordpress.com/2011/03/09/configurar-el-proxy-en-ubuntu/")

---

### Post by wgarcia on 2011-10-15
Tens tots els paràmetres del teu proxy, és a dir l'usuari i la clau, i el port pel qual es connecta?

---

### Post by vilaseca11 on 2011-10-15
si això no és problema els tinc tots!!! nomès em falta saber com fer-ho.. si pot ser explicat pas a pas que encara no sé ben bé com funciona del tot ubuntu.

Gràcies per respondre!!!

---

### Post by wgarcia on 2011-10-15
Et passo les instruccions, però amb la cautela que no les he provades i no estic a darrere d'un proxy, i per tant no sé si funcionen. 

1) Entra la combinació de tecles ALT F2

2) A la finestra que s'obre entra 
```
gksudo gedit /etc/apt/apt.conf
```

3) Després d'entrar la teva clau, s'obrirà un editor on has d'escriure 

```

Acquire::http::Proxy "http://usuari:clau@proxy.domini:port/";
Acquire::https::Proxy "https://usuari:clau@proxy.domini:port/";

```
on "usuari", "clau", "proxy.domini" i "port" els has de substituir pels teus paràmetres. 

Desa el fitxer.

4) Reinicia el sistema

Si no funcionés, convindria esborrar aquest fitxer que has creat, i ho pots fer entrant un altre cop la combinació ALT F2 i a la finestra entrant

```
sudo rm /etc/apt/apt.conf
```

---

### Post by vilaseca11 on 2011-10-15
Ho he acabat de fer i ja puc descarregar programes i codecs.....

Moltíssimes gràcies wgarcia per la teva ajuda gràcies a tu ho he aconseguit!!!! i seguiré en aquest forum per poder ajudar a altra gent.

Una cosa, apratant alt +F2 el menu que surt que és exactament??

Salutacions.. i moltíssimes gràcies de nou!!!

---

### Post by wgarcia on 2011-10-15
ALT F2 et deixa executar alguna instrucció que entris a l'ordinador, cosa que també pots fer obrint una terminal i entrant aquestes instruccions a la terminal. És també el que es diu treballar des de la "línia de comandes", cosa que amb les interfícies gràfiques anem oblidant de poc a poc però que fa no tants anys es feia molt sovint.

---

