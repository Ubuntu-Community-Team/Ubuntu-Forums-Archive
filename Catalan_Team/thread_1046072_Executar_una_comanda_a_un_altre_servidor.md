---
title: "Executar una comanda a un altre servidor"
date: 2009-01-21
forum: Catalan Team
---

### Post by open-pitu on 2009-01-21
Bones!
Primer de tot us situo, a la feina desenvolupem una web de meteorolgia on informem del event climatològics de Catalunya. Doncs bé, per no usar SVG que molts navegadors no funcionen bé per manca de pluguins estem passant els .svg a jpg sota demanda. Això ho fem amb un script en php. El tema es que ara volem passar la creació d'imatges a un altre servidor.

Per recollir la imatge, no hi ha problemes, hem montat la carpeta de l'script al servidor web i així podem accedir fàcilment a les imatges. El problema està en la creació de la imatge. Manualment per provar-ho, utilitzem ssh per a crear les imatges però aquest script s'ha d'executar a un altre servidor.

No sé si ho faig massa complicat a l'hora d'explicar, però en resumides contes el què necessitem és:

Des de 192.168.0.2 fer que s'executi a 192.168.0.4 la comanda:
```
$ php script.php
```

Alguna idea nois? Merci per endavant, si trobem com fer-ho ja ho comentaré.

---

### Post by marcoil on 2009-01-21
Heu provat passant-li la comanda a l'ssh?

```
$ ssh 192.168.04 php script.php
```

---

### Post by papapep on 2009-01-21
> Alguna idea nois? 

I exportar per NFS el directori on tens els SVG's al servidor web i que aquest executi l'script?

---

### Post by open-pitu on 2009-01-22
El problema és que el servidor on hi ha la web no pot crear les imatges, per recollir-les si que no tenim fet com dius papapep.

Ahir vaig estar treballant amb ssh per a que s'executés, però el problema és que des de la terminal funciona correctament però el navegador al intentar-se connectar no es connecta.

Avui provarem de que qui es connecti sigui l'usuari www, aviam si funciona. Tot i així serà una solució temporal lo del ssh, i el que farem serà crear un webservice.

---

### Post by papapep on 2009-01-22
> El problema és que el servidor on hi ha la web no pot crear les imatges,

I perquè no pot? Si dius que ja teniu algun directori exportat al servidor web per NFS, quin problema té en executar aquest script en PHP? la càrrega de cpu?

---

### Post by open-pitu on 2009-01-22
No ho podem fer des del servidor web. Tots els servidors menys el web són amb Ubuntu i no ens donen problemes en la creació d'imatges. El servidor públic però, és amb Suse (el volen passar a Ubuntu, però de moment no és així). Per generar les imatges a partir d'un svg, utilitzem inskape i aquest dóna problemes amb Suse.

---

### Post by papapep on 2009-01-22
Amb l'inskcape?? curiós....no heu provat amb l'imagemagick?

---

### Post by open-pitu on 2009-01-22
Que jo sàpiga no, podem fer el mateix que amb l'inksape? és a dir, d'un fitxer .svg crear un png (que després ja passem a .JPG per temes d'espai)? Ja m'ho miraré i ja comentaré.

Merci!

---

### Post by papapep on 2009-01-22
"convert", que és una ordre, de les vàries que té, de l'imagemagick, permet convertir directament svg's a jpg's, gif's i molts més formats. El que sí que he sentit, és que no es porta bé amb _tots_ els svg's. O sigui que seria qüestió de fer la prova amb els vostres fitxers, a veure què tal.

Amb un simple:

```
convert fitxer.svg fitxer.jpg
```

tens el fitxer convertit.

No sé si l'imagemagick ja és a la instal·lació de paquets predeterminada de l'ubuntu, però de no ser així, ja saps, un simple:

```
sudo aptitude install imagemagick
```

arregla el problema.  :-D

---

### Post by open-pitu on 2009-01-22
L'SVG dóna molt problemes però és molt potent al mateix moment. No sabia que convert en formava part, sabent això ja puc contestar, convert l'utilitzem per convertir el PNG a JPG després, sinó ho fem directament és perquè no es porta bé amb eels nostres SVG.

Avui hem trobat php-curl i l'hem instal·lat, demà porvaré aviam què tal però no les tinc totes. Permet fer includes d'altrers servidors, però per això mateix diria que no anirà perquè s'executarà des del servidor web.

Segur que hi ha d'haver alguna comanda php que ho faci i npo haguem de montar un webservice a l'altre servidor, però no trobem massa informació al respecte.

Merci per tot, mantenim el contacte!!

---

### Post by papapep on 2009-01-22
Jo no soc programador, però crec que amb [passthru()]("http://es.php.net/manual/en/function.passthru.php") o [exec()]("http://es.php.net/manual/en/function.exec.php"), combinat amb rsh (ssh) hauria de funcionar.

---

### Post by open-pitu on 2009-01-23
És el primer que vaig provar. El tema està que com dius funciona des del terminal, perquè ho executa el teu usuari. En canvi des del navegador ho executa el dimonmi d'apache i ja no pot connectar-se. Vam intentar fer-ho que ho fes l'usuari de l'apache, però el servidor no ens deixa fer aquesta suplantació d'identitat.

Ara em disposo a provar php_curl.

---

### Post by open-pitu on 2009-01-29
Ei nanus! Ja ho he resolt, com vaig anunciar és amb php_curl, aquí us deixo un codi d'exemple de com funciona

 ```

$url = "http://192.168.0.4/aca/createPNG_sD.php?PRODUCT=".$product."&PLUVIOTIME=".$pluvio_time."&EPOCH=".$epoch;
$ch = curl_init( $url );
curl_setopt($ch, CURLOPT_USERAGENT, $_SERVER['HTTP_USER_AGENT']);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, $array_post);
curl_setopt($ch, CURLOPT_COOKIE, "cookie[0]=dario;cookie[1]=ocles;hola=mundo;");
$postResult = curl_exec($ch);

echo $postResult;

if (curl_errno($ch)) {
    print curl_error($ch);
}

curl_close($ch);

```

En aquest cas cridem una @ privada però ho podem fer amb qualsevol web. Com veieu, podeu passar-hi variables per la url, un dia d'aquests penjaré un manual de com utilitzar-ho a [open-pitu]("http://open-pitu.webcindario.com").

Merci per l'ajuda nanus!

---

