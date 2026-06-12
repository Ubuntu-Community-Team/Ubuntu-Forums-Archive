---
title: "Actualització a firefox 18 el deixa en anglés"
date: 2013-01-10
forum: Catalan Team
---

### Post by fvilaubi on 2013-01-10
Ahir vaig acceptar les actualitzacions sobre Ubuntu 12.10
Entre d'altres venia el Firefox 18, va actualitzar normalment, com estava usant el firefox, em va sortir el missatge sota la barra de que cal reiniciar. El reinicio i el deixa en anglés.

A about:config tinc el "general.useragent.locale" a en-US i l'he posat a "ca".

Si vaig a "paràmetres del sistema > Suport d'idioma" no em falta cap (si esborro el català, amb el centre de programari, ho detecta i m'el torna a carregar)

El més extrany es que a "tools > add-ons > languages" NO tinc el català!

Alguna idea més?

---

### Post by wgarcia on 2013-01-10
A "Paràmetres de sistema -> suport d'idioma " a veure si et diu si falta alguna cosa instal·lar dels idiomes que tens instal·lats.

---

### Post by merles on 2013-01-10
Tinc el mateix problema i he intentat baixar-me el paquet de català que el firefox intenta instal·lar directament i diu que el paquet està corrupte. Potser realment el problema és del paquet que no és vàlid. 

> **wgarcia said:**
> A "Paràmetres de sistema -> suport d'idioma " a veure si et diu si falta alguna cosa instal·lar dels idiomes que tens instal·lats.

Aquí a paràmetres del sistema no em diu que tingui cap problema, tot i així gràcies

---

### Post by jordicoma on 2013-01-10
Tinc el mateix problema. Però no se si he trobat la causa.
Si mires amb l'apt-file (diu els fitxers del paquet) :
apt-file search firefox-locale-ca
firefox-locale-ca: /usr/share/doc/firefox-locale-ca/changelog.Debian.gz
firefox-locale-ca: /usr/share/doc/firefox-locale-ca/copyright
.
Com es pot veure sembla que els  paquets d'idioma estan buits, només hi ha informació, no la traducció.
S'ha de penjar com a bug això, segurament no és l'únic idioma que té problemes ara.

Per cert, la versió oficial del firefox (descarregat des de la web), si que té versió català.

---

### Post by ffp on 2013-01-10
Doncs a mi també m'ha passat el mateix.
Ahir vaig reinstal·lar el paquet firefox-locale-ca, sense resultat.

---

### Post by jordicoma on 2013-01-10
Sembla que els paquets de localització del prepositori estan malmesos.
Una solució temporal és descarregar el paquet de localització català(valencià) de la pagina de firefox.
[https://addons.mozilla.org/en-US/firefox/addon/valencian-catalan-languag-9702/](https://addons.mozilla.org/en-US/firefox/addon/valencian-catalan-languag-9702/)
Aquest tira.

---

### Post by Darent on 2013-01-10
Si vos baixeu el paquet en valencià-català, assegureu-vos de que vos baixeu el que està fet per la AVL. L'altre marcat com myspell és una atrocitat feta per algun blaver.

Només cal veure alguns dels comentaris a la web del complement:

"
moltes gracies
una proposta es que lleven lo de catala i mos posem com lo que son una llengua independent i diferenciada.
gracies
                                   **                       "**

No és que em fie molt des l'AVL (Acadèmia Valenciana de la Llengua) però comparat en l'altre segueix prou la normativa.

I després d'això, esperar a que el mantenidor del paquet de llenguatge se n'adone i l'actualitze, no hauria de tardar molt.

En fi, quin país...

---

### Post by arakelov on 2013-01-10
A mi em passa el mateix; esperem que ho arreglin aviat.

Salut

---

### Post by elmeunick9 on 2013-01-10
A mi em passa el mateix, he instal·lat el paquet en valencià i va perfecte. Potser no ho consideren català, però m'és igual, es llegeix idèntic. Es una molt bona solució provisional. ;)

Per cert, soc nou al foro, Hola ):P. En aquest foro hi ha un apartat en català o estan els post desordenats? Salut!

---

### Post by Txaume on 2013-01-10
A mi també m'ha passat el mateix, a primera vista veig que el valencià no deu ser molt diferent del català !! ;-)

---

### Post by fvilaubi on 2013-01-10
> **wgarcia said:**
> A "Paràmetres de sistema -> suport d'idioma " a veure si et diu si falta alguna cosa instal·lar dels idiomes que tens instal·lats.

Si vaig a "centre de programari", busco firefox, i clico el link "mostra el nnn links tècnics", ensenya els "packs d'idioma".
Llavors desinstalo el pack de català, i vaig a parametrització de sistema > suport d'idiomes. Aqui al entrar m'avisa que hi ha un paquet d'idioma que no tinc.... Fantàstic, ho ha vist, l'instala... però queda igual.

Gràcies Walter.

---

### Post by fvilaubi on 2013-01-10
Sembla que hi ha un bug reconegut. Fora bó que tots els que estem afectats hi anéssim i cliquem "estic afectat per aquest bug" així el farem pujar de prioritat.
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098312](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098312)

també hi ha el primer bug incomplert obert:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098296](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098296)

i aquest es el post que he obert a Ubuntu updates:
[http://ubuntuforums.org/showthread.php?p=12449179#post12449179](http://ubuntuforums.org/showthread.php?p=12449179#post12449179)

---

### Post by Margaret Dumont on 2013-01-11
Hola,

Jo ja m'hi he registrat també. 

Per cert, si a part d'apuntar-te a l'error com a afectat també t'hi subscrius, en comptes de pujar la flameta d'importància 4 punts per usuari en puja 6. La veritat és que no sé quin cas li fan a això però, vaja, no costa gaire.   :)

Per cert, ningú no té ni idea de quant solen trigar aquestes coses?

A reveure!

              Margaret

---

### Post by lpargemi on 2013-01-11
A mi també m'ha deixat penjat. Falla al descarregar el paquet i dóna aquest error:
```

Install Additional Language : Catalan
Download from ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/18.0/linux-x86_64/xpi/ca.xpi
Download Started
Downloading, progress = 1%
Downloading, progress = 1%
Downloading, progress = 2%
Downloading, progress = 3%
Downloading, progress = 5%
(...)
Downloading, progress = 90%
Downloading, progress = 91%
Downloading, progress = 99%
Downloading, progress = 100%
Download Failed : undefined undefined

```

M'he apuntat a la pàgina del bug, a veure si es resol aviat

---

### Post by fvilaubi on 2013-01-11
Pel que he entès sembla que ja han trobat el problema, hi ha un fitxer "install.rdf" que comença amb dues línies en blanc, això fa que el gestionador de complements no el sap carregar. ho podeu seguir al Bugzilla 
[https://bugzilla.mozilla.org/show_bug.cgi?id=829246](https://bugzilla.mozilla.org/show_bug.cgi?id=829246)

---

### Post by jordicoma on 2013-01-12
Amb aquesta versó del Install.rdf funciona. canviar amb la del que hi ha al xpi. (copiar el que hi ha entre ")
"
<?xml version="1.0"?>
<!--

-->

<RDF xmlns="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
     xmlns:em="http://www.mozilla.org/2004/em-rdf#">
  <Description about="urn:mozilla:install-manifest"
               em:id="langpack-ca@firefox.mozilla.org"
               em:name="Català Language Pack"
               em:version="18.0"
               em:type="8"
               em:creator="Mozilla.org / Softcatalà">
    <em:contributor>Softcatalà</em:contributor>

    <em:targetApplication>
      <Description>
        <em:id>{ec8030f7-c20a-464f-9b0e-13a3a9e97384}</em:id>
        <em:minVersion>18.0</em:minVersion>
        <em:maxVersion>18.0.*</em:maxVersion>
      </Description>
    </em:targetApplication>
  </Description>
</RDF>
"

---

### Post by Curial on 2013-01-13
Re: Actualització a firefox 18 el deixa en anglés
Sembla que els paquets de localització del prepositori estan malmesos.
Una solució temporal és descarregar el paquet de localització català(valencià) de la pagina de firefox.
[https://addons.mozilla.org/en-US/fir...-languag-9702/](https://addons.mozilla.org/en-US/fir...-languag-9702/)
Aquest tira.



Gràcies.
Amb això ha estat fàcil i ràpid.
Estic a la 12.04 d'Ubuntu i des de la última actualització se'm va passar a l'anglès.
En quant a la llengua no he trobat cap animalada blavera. :-)
Una abraçada als germans valencians!
Salut.

---

### Post by alpc360 on 2013-01-13
Un altre que ha clicat ):P a la espera de updates.

PD: el FIX del idioma valencià funciona a la perfecció

---

### Post by arakelov on 2013-01-14
> **jordicoma said:**
> Amb aquesta versó del Install.rdf funciona. canviar amb la del que hi ha al xpi. (copiar el que hi ha entre ")
"
On ha d'anar aquest fitxer? En el meu equip apareix en diversos llocs:

```
/home/arakelov/.mozilla/firefox/uzo1tumb.default/extensions/ca@dictionaries.addons.mozilla.org/install.rdf
/home/arakelov/.mozilla/firefox/uzo1tumb.default/extensions/es-es@dictionaries.addons.mozilla.org/install.rdf
/usr/share/xul-ext/ubufox/install.rdf
/usr/lib/firefox-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/firefox-addons/extensions/globalmenu@ubuntu.com/install.rdf
/usr/lib/thunderbird-addons/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/thunderbird-addons/extensions/globalmenu@ubuntu.com/install.rdf
```

Merci, salut

---

### Post by alpc360 on 2013-01-15
arakelov

Utilitza aquest enllaç i fes clic a "Add to Firefox" és català valencià però sembra que quasi tot es igual.

[https://addons.mozilla.org/en-US/firefox/addon/valencian-catalan-languag-9702/](https://addons.mozilla.org/en-US/firefox/addon/valencian-catalan-languag-9702/)

---

### Post by jordicoma on 2013-01-15
modifica (en una copia) el xpi de català.
[EMAIL="langpack-ca@firefox.mozilla.org.xpi"]langpack-ca@firefox.mozilla.org.xpi[/EMAIL]
que es troba dintre /usr/lib/firefox-addons/extensions.
El pots obrir amb l'ark si vols sense problemes.
Substitueixes el Install.rdf (treguent les 2 linies que hi ha blanques al principi), tal com he posat en l'altre post.
Segurament no el podras modificar directament per falta de permisos, pots treballar amb una copia i després copiar-ho amb el sudo.

Aquí hi ha el problema resolt(per ff19) (treu l'extensió zip, el ubuntuforums no l'hi agrada el xpi). copia-ho amb sudo al directory /usr/lib/firefox-addons/extensions i reinicia firefox.

---

### Post by fvilaubi on 2013-01-16
alpc360

si no ho tinc mal entès, el la traducció d'Ubuntu es pròpia i no aprofita les traduccions que es fan per cadascuna de les aplicacions. 

Fixat que l'idioma es fa des de "Paràmetres del sistema > Suport d'idioma" i no des de cada aplicació (firefox, thunderbird, ....)

Llavors el que no sé es que passarà amb les properes actualitzacions?
  - tornarà a usar el estàndard d'Ubuntu ?
  - com que tens un complement d'idioma NO Ubuntu, l'actualitzarà des de Mozilla?

He provat el pack que recomanes, em funciona, però l'he desinstalat precisament per aquests dubtes, tot i esperant la solució al bug des d'Ubuntu.

Hi ha algú que em pugui confirmar aquesta reflexió?

---

### Post by fvilaubi on 2013-01-16
Seguint les indicacions d'en jordicoma, aqui us deixo el [email]**langpack-ca@firefox.mozilla.org.xpi**[/email] per la versió 18 de FireFox

Traieu l'extensió .zip no feu res més amb el fitxer i poseu-lo a **/usr/lib/firefox-addons/extensions**  
(haureu de ser, o tenir permisos de root)

Reinicieu el FireFox.

---

### Post by Lotiopep on 2013-01-16
Moltes gràcies! Ha funcionat a la perfecció. Feia dies que li donava voltes al tema fins que he trobat aquest fil.

---

### Post by pumukyb on 2013-01-17
Merci per la informació proporcionada. Funciona de meravella

---

### Post by alpc360 on 2013-01-17
Ho acabo de provar en el portàtil i funciona a la perfecció. :popcorn:

Ara ho provaré en els altres equips treien el Catala(Valencia)

Una question, quan Ubuntu actualitzi no hi haurà cap problema no ?

Gracies !!

---

### Post by fvilaubi on 2013-01-17
> **alpc360 said:**
> 

Una question, quan Ubuntu actualitzi no hi haurà cap problema no ?



D'entrada el que busquem, substituint aquest fitxer xpi, es ser poc "invasius" en la solució. Es el mateix fitxer d'idioma que usa el Firefox al Ubuntu, i estem fent la mateixa correcció que proposen al fil del Bugzilla, que suposo entrarà d'aquí uns dies.

Es molt important haver deixat els permisos i la propietat del xpi igual que el que hem substituït, per tal que no falli l'actualització del paquet quan entri.

---

### Post by vila-seca on 2013-01-18
> **fvilaubi said:**
> Seguint les indicacions d'en jordicoma, aqui us deixo el **langpack-ca@firefox.mozilla.org.xpi** per la versió 18 de FireFox

Traieu l'extensió .zip no feu res més amb el fitxer i poseu-lo a **/usr/lib/firefox-addons/extensions**  
(haureu de ser, o tenir permisos de root)

Reinicieu el FireFox.

Gràcies per la solució. Jo he hagut de fer un petit canvi al fitxer de install.rdf per posar-hi enlloc de 19.0 ...18.0 si no el firefox m'el deshabilitava :)

---

### Post by fvilaubi on 2013-01-18
> **vila-seca said:**
> Gràcies per la solució. Jo he hagut de fer un petit canvi al fitxer de install.rdf per posar-hi enlloc de 19.0 ...18.0 si no el firefox m'el deshabilitava :)

Vila-seca pot ser et confons de post amb el #21 ?
precisament em va passar com a tu (tinc el ff18) i el fitxer ja ho diu en jordi es pel 19. Així que vaig fer la modificació i vaig publicar-la al #23. 

Resumint:
FireFox versió 18 usar descarga del post #23
FireFox        19                   post #21

---

### Post by ffp on 2013-01-18
A mi tambè m'ha funcionat perfectament en firefox 18 ( i el fitxer del post #21). Recomano desinstal·lar el addon del català (valencià) previament (post #6)

---

### Post by alpc360 on 2013-01-18
> **ffp said:**
> A mi tambè m'ha funcionat perfectament en firefox 18 ( i el fitxer del post #21). Recomano desinstal·lar el addon del català (valencià) previament (post #6)


Com diu ffp, també recomano treure el català (valencià)):P

---

### Post by llopdeferro on 2013-01-18
> **jordicoma said:**
> modifica (en una copia) el xpi de català.
[EMAIL="langpack-ca@firefox.mozilla.org.xpi"]langpack-ca@firefox.mozilla.org.xpi[/EMAIL]
que es troba dintre /usr/lib/firefox-addons/extensions.
El pots obrir amb l'ark si vols sense problemes.
Substitueixes el Install.rdf (treguent les 2 linies que hi ha blanques al principi), tal com he posat en l'altre post.
Segurament no el podras modificar directament per falta de permisos, pots treballar amb una copia i després copiar-ho amb el sudo.

Gracies per la solució!!! Tenia el mateix problema. ):P

---

### Post by alpc360 on 2013-01-23
Acabo d'actualitzar l'Ubuntu i ja te l'actualització d'idioma ;) ):P

---

### Post by fvilaubi on 2013-01-23
Amb la darrera actualització de paquets, avui m'acaben d'entrar els paquets d'idioma a versió 18.0.1 i m'ha funcionat perfecte!

---

### Post by Margaret Dumont on 2013-01-27
Fvilaubi (o moderadors),

Donat que ja hi ha una solució que funciona i que el problema està resolt, no s'haurien de marcar tant aquest fil com [aquest altre]("http://ubuntuforums.org/showthread.php?t=2103418") com a [Resolts]?

A reveure,

            Margaret

---

### Post by wgarcia on 2013-01-28
Sí Margaret, però sols ho poden fer els que van iniciar les converses, és a dir els autors del primer missatge de cada fil. Bé, suposo que també els moderadors del fòrum ho poden fer.

---

