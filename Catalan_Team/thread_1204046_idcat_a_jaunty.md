---
title: "idcat a jaunty"
date: 2009-07-04
forum: Catalan Team
---

### Post by climent on 2009-07-04
Acabo de fer una instal·lació neta del Jaunty i, a l'hora de voler instal·lar l'IDCAT, puc fer tot el procés, però quan faig "firefox-install-pkcs11.sh" em respòn -no es pot afegir el mòdul-. He seguit pas a pas tot el procés, però segueixo igual. Algú s'hi ha trobat?

---

### Post by climent on 2009-07-04
Ah, me n'oblidava. No he fet cap actualització, llevat de la d'idioma. La versió del Firefox és la de la distro

---

### Post by Tomàs M. on 2009-07-05
Sento no haver actualitzat el post, però juraria que no canvia gaire respecte de la 8.10: [http://www.tomi.cat/2008/10/i-avui-idcat.html](http://www.tomi.cat/2008/10/i-avui-idcat.html)

Salut!

---

### Post by akyra on 2009-07-06
Hola, a mi també em pasa el mateix

El problema el tinc en el Firefox, que quan visitu la pàgina [http://www.catcert.cat/web/cat/6_3_prova.jsp](http://www.catcert.cat/web/cat/6_3_prova.jsp) i poso un texter a certificar, en surt al recuadre de signatura: error:noMatchingCert.

Jo ja l'havia instal·lat abans amb el Firefox 3.0 i i amb jaunty i m'havia funcionat, però ara al formatajar la partició i tornar-lo a instal·lar m'ha succeit això.

No trobo gaire informació d'això en el google.

Adeu

---

### Post by akyra on 2009-07-06
Perdó Climent,

Jo si que l'he pogut instal·lar, però després no em funciona.

---

### Post by akyra on 2009-07-06
Hola Climent

Jo m'he instal·lat el idcat i com ja he dit tinc el problema en el firefox, però tinc instal·lat el mòdul.

També em va pasar que no podia instal·lar el mòdul.
Intenta fer això a veure que et surt:
/etc/init.d/clos restart

Si està correctament instal·lat, el clos es tornarà a engegar, i si no el problema segurament estarà en el "libCRYPTOWrap.so.0", i es podria solucionar amb fent:
  **export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib/**

Jo ho he hagut de fer des de la consola pero fent abans un "sudo su"

Si s'engegat correctament fes:
  **exit**
i després tornar a fer:
  **firefox-install-pkcs11.sh**

Jo he fet un petit script, que recull tots els passos que he anat recollint (llibreries i pasos a instal·lar), si t'interesa te'l puc enviar o posar en el forum.

Ja diràs con va.

Salutacions

---

### Post by climent on 2009-07-07
[SOLVED]
Bé, el cert és que ja tinc el mòdul activat. La instal·lació era correcte, i l'expressió "export..." també l'havia posada. La qüestió és que després de dues .../clos restart i un reinici de l'ordinador va funcionar.

I la prova de text a la pròpia pàgina d'idcat sempre m'ha donat error, però el llapis funciona en d'altres serveis (el meu ajuntament, hisenda, la Seg Social).
Gràcies a tothom

---

