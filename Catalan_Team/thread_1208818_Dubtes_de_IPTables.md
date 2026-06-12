---
title: "Dubtes de IPTables"
date: 2009-07-09
forum: Catalan Team
---

### Post by akyra on 2009-07-09
Hola a tothom

Tinc un petit problema amb la configuració del iptables, i és que em talla las conexions dels meu disc dur multimedia, que és un dispositiu upnp i dlna.

El meu ordinador el pot veure mitjançant conexió samba, però el disc dur, quan tinc el iptables activat, no el veu.

M'agradaria saber quina regla m'ho impedeix, o quin port hauria d'obrir per poder comunicar.

Us deixo el fitxer per si algu li vol donar un cop d'ull.

Salutacions

---

### Post by papapep on 2009-07-09
[SMB]("http://ca.wikipedia.org/wiki/Samba_(inform%C3%A0tica)") fa servir, sense ser massa exhaustiu, el ports 137, 138, 139 i 445, tots quatre [TCP]("http://ca.wikipedia.org/wiki/TCP"). 

Com que l'script que fas servir per aixecar el tallafocs és restrictiu, els tanca de manera predeterminada.

Línia 28 de l'script:
> #Politica general.Cerramos todo.Dejamos entrar lo solicitado y salir todo


Hauries de provar a obrir-los explícitament. Però, ja saps on et fiques? iptables no és especialment simple. No et surtiria més a compte, i que no senti precedent aquest consell per part meva :D, fer servir l'[ufw]("http://packages.ubuntu.com/search?keywords=ufw&searchon=names&suite=jaunty&section=all") (una capa que simplifica l'iptables, tot i que el fa servir) i la seva interfície gràfica (gufw)? crec que et seria molt més simple de gestionar.

Es pot veure una extensa relació de ports i el seu protocol associat habitual fent:

```
less /etc/services
```

---

### Post by akyra on 2009-07-09
Gracies pels ports de smb.

Els obriré a veure que succeix.
La política és restrictiva per l'entrada, crec que per això són els tallafocs :p, però permisiva en les sortides.

Ho faig servir des de la versió 7.04, i he anat llegint exemples trobats per internet, i fins ara m'ha anat força bé, el problema són els dispòsitius que es volen connectar al propi ordinador, ja que al ser les entrades restrictives has de saber els ports que utilitzen.

Jo pensava que amb l'opcio de permetre el tràfic de la xarxa interna:

> #Permitimos todo el trafico de la LAN de nuestro router Belkin 
iptables -A INPUT -s 192.168.2.1/100 -j ACCEPT

però dec està confós.


El que té una gran ventatge per a mí, que quan faig un formateig del disc per instalar una nova versió d'ubuntu només haig de copiar aquest fitxer en el directori corresponent, sempre està engegat independentment de l'usuari que el faci servir (això no ho he lograt amb el firestarter) i ocupa una miseria.

D'altra banda haig de confesar que és una mica dificil d'utilitzar, sobre tot al principi.

Per cert has fet servir el firestarter? Has lograt que s'engegui automàticament independenment de l'usuari que inici sessió?

Salutacions.

---

### Post by akyra on 2009-07-10
Pots fer cinc cènctims de com funciona el GUFW?

Veig que és una interfaz gràfica de ufw.
Suposo que deu crear regles de iptables i les deu guardar en un arxiu, i no és necessari tenir el gufw engegat sempre.

Les regles són comuns per a tots els usuaris de l'ordinador?
Aplica polítiques per defecte?

Entre el firestarter i el gufw quin et quedes?

Salutacions

---

### Post by papapep on 2009-07-10
[http://lmgtfy.com/?q=gufw+tutorial](http://lmgtfy.com/?q=gufw+tutorial)

---

