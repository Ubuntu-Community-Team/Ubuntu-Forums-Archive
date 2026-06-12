---
title: "Amule no em funciona bé (xarxa KAD bloquejada?) :("
date: 2009-12-10
forum: Catalan Team
---

### Post by kukat on 2009-12-10
No hi ha manera de que em vaja bé l'Amule. He provat a fer de tot: Tornar a insta&#320;lar Amule, esborrar totalment Firestarter, canviar els ports del 2662 i 2672 i 2665 que he gastat sempre, als que es veuen en la imatge. Canviar el kernel en el GRUB, per altre més antic (en tinc 3), obrir els ports mitjançant IPtables(veure fitxer adjunt)....Però res. 

Tinc IP alta, i el KAD "Connectat" i al cap d'una estona -entre 15 minuts o més - (sense que començe a baixar-se res) , em posa "KAD darrere de tallafocs". 

El router és un Xavi 7968 de Timofònica 
Tinc el Karmic Koala.
Em vaig canviar a Timofònica fa una setmana i pico. Va arribar a baixar-me a 250 Kbps o més.
S'ha actualitzat el Kernel sinó estic equivocat durant eixe temps.....
La pujada va perfectament, a 15 kbps que li he posat...
:(

**Configuracions i registres de l'Amule:**


**Connexions Amule:**
[http://img130.imageshack.us/img130/8876/connexioamule.png](http://img130.imageshack.us/img130/8876/connexioamule.png)

**Pagina de Descarregues (estic baixant coses amb moltes fonts!)**
[http://img130.imageshack.us/img130/1784/descarregues.png](http://img130.imageshack.us/img130/1784/descarregues.png)

**Xarxa ED2k amb ID alta:**
[http://img23.imageshack.us/img23/6532/ed2k.png](http://img23.imageshack.us/img23/6532/ed2k.png)

**Iptables al Reiniciar l'equip:**
[http://img23.imageshack.us/img23/7614/iptables.png](http://img23.imageshack.us/img23/7614/iptables.png) 

Al reiniciar, i estant el tallafocs.sh en el "init.d" , em surt açò al posar la comanda iptables -F -n. Si execute manualment el fitxer, ja m'ix com a que estan oberts.....

**Xarxa Kad:**
[http://img23.imageshack.us/img23/2667/kadd.png](http://img23.imageshack.us/img23/2667/kadd.png)

**Registre Amule:**
[http://img23.imageshack.us/img23/9001/registreamule.png](http://img23.imageshack.us/img23/9001/registreamule.png)

**Pestanya "Seguretat":**
[http://img526.imageshack.us/img526/3811/seguretatamule.png](http://img526.imageshack.us/img526/3811/seguretatamule.png)

**Pestanya "Servidors"**
[http://img526.imageshack.us/img526/3454/servidorsamule.png](http://img526.imageshack.us/img526/3454/servidorsamule.png)

**Configuració Router Xavi:**
[http://img526.imageshack.us/img526/6244/routerd.png](http://img526.imageshack.us/img526/6244/routerd.png)


***I de sobte , bloquejat: ***
[http://img526.imageshack.us/img526/3367/bloquejat.png](http://img526.imageshack.us/img526/3367/bloquejat.png)

Si algú li ha passat alguna cosa semblant, seria una gran ajuda!

Gràcies!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

PD: no se que ha passat, que m'ha tocat fer el post una altra vegada.... :(

---

### Post by kukat on 2009-12-10
Esborreu l'altre ;) 
No se que li ha passat a la web (veig que teniu problemes...) però abans no em sortien els posts!!!!

Salutacions!

---

### Post by kukat on 2009-12-13
Pareix que és un problema de l'Amule......Però l'esborre completament (carpeta ".amule" inclosa), i el torne a insta&#320;lar i res de res. No funciona......

Que he fet al final??????

[http://www.guia-ubuntu.org/index.php?title=EMule](http://www.guia-ubuntu.org/index.php?title=EMule)

Insta&#320;lar l'emule amb el WINE!!! :)
I pareix que vaja de meravella!!!

Aquesta nit veuré com han anat les baixades i ho acabaré de confirmar....
però de moment funciona, i el KAD no es bloqueja, que és el que compta! :)

[[img]http://img101.imageshack.us/img101/4050/capturat.th.png[/img]](http://img101.imageshack.us/i/capturat.png/)

---

### Post by kukat on 2009-12-14
Tot i que consumeix un poc massa recursos, va de meravella!!!!

---

