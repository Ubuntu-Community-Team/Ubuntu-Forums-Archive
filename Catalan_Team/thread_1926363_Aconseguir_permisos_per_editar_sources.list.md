---
title: "Aconseguir permisos per editar sources.list"
date: 2012-02-16
forum: Catalan Team
---

### Post by Urfe on 2012-02-16
Hola.

He escrit malament un respositori en sources.list i ara no puc fer actualitzacions.

Provo d'editar l'arxiu però em diu que com que no soc l'autor no el puc modificar.

He provat amb:

echo "nombreusuario ALL=(ALL) ALL" >> /etc/sudoers

i tampoc he pogut.

Alguna suggerència? Moltes gràcies.

---

### Post by prostata on 2012-02-16
mira aquesta pàgina, creec que et pot anar bé...

Salut

[http://www.ubuntuhispano.org/wiki/editar-archivo-etcsudoers](http://www.ubuntuhispano.org/wiki/editar-archivo-etcsudoers)

---

### Post by wgarcia on 2012-02-16
A veure, li poses "sudo" endavant de la comanda per editar "sources.list"? Una altra alternativa és entrar "gksudo gedit /etc/apt/sources.list" des d'una terminal.

També pots deshabilitar la fons de programari sospitosa obrint el Centre de Programari Ubuntu amb el menú "Fons de programari" que crec que està a "Editar".

---

### Post by kimet on 2012-02-16
Per modificar sources.list ho pots fer amb nano per ex.:
```
sudo nano /etc/apt/sources.list
```

Modificar /etc/sudoers amb aquests ordres(echo "nombreusuario ALL=(ALL) ALL" >> /etc/sudoers) Estaries donant permisos absoluts al teu usuari, poc recomanable. En tot cas verifica si el teu usuari pertany al grup sudo.

Salut.

Edito, no havia vist el post d'en w.:)

---

### Post by wgarcia on 2012-02-16
El problema és que si ha perdut la capacitat d'executar "sudo" no pot modificar "sudoers" per tornar-se a donar permís per executar "sudo", un peix que es mossega la cua, o un argument "recursiu", com els agrada dir als informàtics.

---

