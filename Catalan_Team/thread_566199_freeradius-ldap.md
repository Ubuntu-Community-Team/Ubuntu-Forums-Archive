---
title: "freeradius-ldap"
date: 2007-10-03
forum: Catalan Team
---

### Post by josepmacia on 2007-10-03
Hola a tothom.

estic instalant un pdc i tinc els següents problemes.
a part de pdc també vull aprofitar el servidor LDAP per fer validacios dels usuaris wifi i per a fer aixo he pensat en utilitzar el freeradius. ja he configurat el radiusd.conf per a que el servidor radius faci les validacions contra el ldap del pdc. el cas es que quan faig:

radtest usuari password localhost sharedsecret port 

hem rebutja el paquet:  (acces-reject)

no sé si es el comportament normal i tampoc se si vaig bé a l'hora d'administrar els diferents servidors. he probat amb debian sarge i també amb ubuntu server i sempre em trobo amb el mateix problema. 
a veure si algú pot postejar   la part del radiusd.conf que fa referencia a l'autenticació ldap.
també estic provant amb el freebsd (pfense) però no acaba de ser el que voldria.

salutacions.
ubuntu power!!!

josep

---

