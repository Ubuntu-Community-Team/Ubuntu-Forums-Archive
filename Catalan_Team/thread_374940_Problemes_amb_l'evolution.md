---
title: "Problemes amb l'evolution"
date: 2007-03-03
forum: Catalan Team
---

### Post by Syzygia on 2007-03-03
Hola.

Sóc usuari d'Ubuntu des de fa poc, tot i que ja porto algun temps usant altres distribucions de Linux. Això sí, és la primera vegada que sóc *root* del sistema.

Tinc dos problemes amb el gestor de correus evolution:

Quan feia servir només el gpg per controlar la part criptogràfica, no tenia cap problema. Però fa uns dies em vaig descarregar el seahorse, i des de llavors, quan provo d'enviar un mail signat o encriptat, em dóna el següent error:

[INDENT]
No s'ha pogut crear el missatge.

Because "can't connect to `/home/ignasi/.gnome2/seahorse-YGnPiw/S.gpg-agent': Connection refused
gpg: no s'ha pogut connectar amb «/home/ignasi/.gnome2/seahorse-YGnPiw/S.gpg-agent»: connect failed
gpg: s'està escrivint en «-»
gpg: DSA/SHA1 signature from: "*el correu que usi*"
", you may need to select different mail options.
[/INDENT]

Abans de tenir el seahorse sí que podia enviar mails. Algú sap què passa?

L'altre problema és amb la signatura (no digital, sinó la frase que es posa al final de cada e-mail). Em vaig fer una signatura HTML. En aquella sessió, tots els mails que vaig enviar van anar perfecte. Però el següent cop que vaig obrir Evolution, la signatura se'm havia transformat en una cosa de l'estil:
[INDENT]
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 TRANSITIONAL//EN">
<HTML>
<HEAD>
  <META HTTP-EQUIV="Content-Type" CONTENT="text/html; CHARSET=UTF-8">
  <META NAME="GENERATOR" CONTENT="GtkHTML/3.10.3">
</HEAD>
...
[/INDENT]
És a dir, en el codi html. Si torno a editar la signatura, durant aquella sessió em funciona bé, però no a les següents. Faig alguna cosa malament?

Agrairé qualsevol consell. Gràcies a tots.

---

### Post by CarlesOriol on 2007-03-07
Inicia seahorse-daemon abans del evolution.

---

### Post by Syzygia on 2007-03-08
Moltes gràcies, ara em funciona.

---

### Post by CarlesOriol on 2007-03-08
Crec que hi ha hagut algun problema en alguna actualització.

Fins que no s'aclareixi el tema pots posar el seahorse-daemon a l'inici de sessió a sistema->Preferencies -> sessions

---

