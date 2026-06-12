---
title: "No recordo la contrasenya de root"
date: 2011-07-03
forum: Catalan Team
---

### Post by dmolner on 2011-07-03
Hola,

Quan vaig instal.lar linux 11.04 no recordo quina contrasenya vaig posar per a root, no se si vaig posar cap.

Ara necessito posar una contrasenya com a su al terminal.

Com ho puc fer?

Gracies.

---

### Post by lncoll on 2011-07-03
Al Ubuntu el compter de root está deshabilitat.
Per a fer tarees d'administració cal usar sudo.
Et recomane lligir asó [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dmolner on 2011-07-03
Hola,

Gràcies per la resposta.
Però ara no tinc clar si el problema es el que he dit o un altre.

Si al terminal escric su per poder fer alguna cosa hem demana la contrasenya però si li poso la que jo faig servir per les actualitzacions hem dona error.
Jo soc administrador del sistema i així ho tinc a Paràmetres de usuari.

Per aclarir el tema:
Que haig de fer per al escriure su al terminal posar la contrasenya (ja dic que escric la que tinc com administrador i no funciona).

Gràcies.

---

### Post by epileg on 2011-07-03
l'ordre "su" és correcte que no et funcioni per defecte. pel que ja t'ha explicat en/na lncoll.
Si vols entrar com a root, et cal fer:
$ sudo su
i després escriure la contrasenya del teu usuari.
Si el que vols fer és executar una ordre concreta com a usuari root, només has de fer:
$ sudo ordre

Salut,

---

### Post by dmolner on 2011-07-03
Moltes gràcies.

Ara ja puc fer el que necessito.

Gràcies.

Per cert això es nou o es que m'he oblidat de com anava,

---

