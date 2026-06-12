---
title: "Canvi de PC"
date: 2012-03-07
forum: Catalan Team
---

### Post by dmolner on 2012-03-07
Hola,

He comprat un nou PC i voldria traslladar tot el que tenim els usuaris al PC vell al nou.
Es possible fer-ho per xarxa?
Ho dic per estalviar la copia de seguretat i demés.

Gràcies,
David.

---

### Post by akyra on 2012-03-08
Hola,
Entenc que tens els dos PC's en xarxa, si es així, sí que sería posible compartint carpetes en cas de windows, o donat permisos d'accés en cas d'Ubuntu, sempre en el PC vell.

Després només hauries de copiar el que et calgués en una carpeta del nou Pc.

Espero haver-te ajudat, però si dones més informació ens aniria millor.

Salutacions

---

### Post by dmolner on 2012-03-08
Hola,

Els dos PC's tenen Ubuntu i son a la mateixa xarxa.
Dos usuaris al PC vell dels que vull passar tot al nou.
Suposo que ho podria copiar a DVD's però si ho puc fer per Xarxa copiant tot el directori o com sigui dons millor.

Gràcies,
David.

---

### Post by kimet on 2012-03-08
Si la conexió es segura pots usar NFS, si no sshfs o ssh + fish.
Has d'instalar un client i un servidor, hi molts manuals a internet.

Salut.

---

### Post by akyra on 2012-03-09
Hola,

Crec que compartint la carpeta de l'ordinador vell i donant permisos a tothom per accedir i llegir. Després des de Nautilus i posant "//ip_pc_vell//nom_carpeta_compartida" ja podriem accedir.

També es podria fer compartint la carpeta tal com hem dit, i anant al Nautilus i la icona "Xarxa". T'apareixeria el PC_vell i podries accedir a la carpeta compartida.

Espero que això funcioni.

Recorda que en el teu directori hi ha carpetes ocultes (CTRL+H per veure-les.
Quan estigui copiat has de mirar a quin usuari pertanyen les noves carpetes copiades.

També et deixo un link per fer copies de la carpeta /home, ja diràs que tal et va.
[http://ubuntu-cosillas.blogspot.com/2011/11/exportar-cuentas-de-usuario.html]("http://ubuntu-cosillas.blogspot.com/2011/11/exportar-cuentas-de-usuario.html")

NFS no sé com funciona.

Sautacions.

---

### Post by dmolner on 2012-03-10
Miraré de fer el que diu akyra, sembla el més fàcil de fer.
Si no ja provaré les altres opcions.

Gràcies a tots.

---

### Post by dmolner on 2012-03-13
Fet!

M'ha funcionat molt be tal i com ha dit akyra.

Gràcies a tots per la ajuda.

---

### Post by akyra on 2012-03-13
Perfecte.

Salutacions

---

