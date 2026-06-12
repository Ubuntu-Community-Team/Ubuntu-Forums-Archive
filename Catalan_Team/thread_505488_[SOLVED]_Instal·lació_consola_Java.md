---
title: "[SOLVED] Instal·lació consola Java"
date: 2007-07-20
forum: Catalan Team
---

### Post by pablinsfc on 2007-07-20
Hola companys!! Sempre he sigut un usuari de sang Windows, però poc a poc el cuquet Linux ha anat quallant en mi (Firefox, OpenOffice...) , doncs la informàtica m'encanta i sempre he investigat en tots els camps. Fa tot just un dia que he decidit instal·lar Ubuntu al PC petit de casa i n'estic molt content!!! El que passa és que no en tinc ni fava...

El problema concret que tinc és que no puc instal·lar Java a l'ordinador. Per veure segons quines web me'l demana però no me'l baixa automàticament com a complement del Firefox. Les instruccions són en anglès que em patina una mica i estic en un cul de sac. 

Jo entenc que haig d'obrir el Terminal i escriure "su", el pasword d'administrador (el de la meva sessió, no?) i seguir endavant, però això ja no em funciona. Us enganxo dues captures amb les instruccions i el que em surt realment.

Us agrairia una petita ajuda.

[IMG]http://www.matafaluga.com/captura1.png[/IMG]
[IMG]http://www.matafaluga.com/captura2.png[/IMG]

Moltissimes gràcies!!!

---

### Post by argggg on 2007-07-20
Has d'activar els repositoris 'multiverse'

sudo aptitude install sun-java6-plugin  

Si ho vols fer tal i com surt a les captures, diria que enlloc de fer el su, has de posar sudo davant de totes les instrucions que surten (menys el su que no l'has de fer), tot i que es millor fer servir els paquets d'ubuntu, aixi tindràs les actualitzacions i tal.
Salut!

---

### Post by pablinsfc on 2007-07-20
Merci company!

De moment ho he fet com ho has dit i s'ha instal·lat perfectament. Però ja que ho comentes, on puc trobar aquests paquets??

Una altra dubte que tinc és com personalitzar els escriptoris. He vist captures de pantalles realment molt guapes, però no en tinc ni idea de com fer-ho. Tampoc sé si aquest és el millor lloc per preguntar-ho.

Merci per tot!

---

### Post by papapep on 2007-07-20
"su " serveix per a canviar d'usuari i passar a ser, en aquest cas, el superusuari "root". 
És més aconsellable utilitzar "sudo", el qual significa que demanes per a executar una comanda com a superusuari sense ser-ho. Apart, com has vist, Ubuntu no et deixa passar a ser el superusuari perquè aquest usuari per defecte no té contrassenya.

Els paquets d'Ubuntu que demanes on són, els tens disponibles als dipòsits de programari que hi ha a internet, dels quals t'has descarregat, per exemple, el paquet de java.

Respecte el tema de personalitzar l'escriptori jo no et puc ajudar gaire, però t'asseguro que a aquests fòrum es pot fer  qualsevol pregunta (o gairebé qualsevol)  ;)

---

### Post by RainCT on 2007-07-20
> **pablinsfc said:**
> Però ja que ho comentes, on puc trobar aquests paquets??

Ves a Sistema -> Administració -> Gestor de Paquets Synaptic :D

---

### Post by pablinsfc on 2007-07-20
Ei, gràcies a tots per l'ajuda!! Això amb gent com vosaltres és bastant més fàcil. Respecte al tema dels paquets, em surt el això:


S'ha produït un error
Es proveeixen els detalls següents:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i com podeu comprendre, no entenc res de res... :S

Salut! i merci de nou!

---

### Post by papapep on 2007-07-21
Després de quina ordre t'ha sortit aquest missatge?

Dins el mateix missatge tens la teòrica solució al problema:

> : dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

o sigui, tecleja a un terminal:

```
sudo dpkg --configure -a
```

---

### Post by pablinsfc on 2007-07-21
Em sortia tant sols intentar entrar al gestor de paquets. He fet el que comentes s'han executat aquestes ordres. He tancat el Terminal i he pogut accedir al gestor de paquets. Segueixo investigant... :P

Gràcies per tot!

Salut!

---

