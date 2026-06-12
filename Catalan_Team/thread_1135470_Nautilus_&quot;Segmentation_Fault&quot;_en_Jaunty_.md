---
title: "Nautilus &quot;Segmentation Fault&quot; en Jaunty Jackalope"
date: 2009-04-24
forum: Catalan Team
---

### Post by kukat on 2009-04-24
Bé, per si algú més del Catalan Team li està passant açò (ja que es una mica estrany), he obert aquest fil. 

Aquí també es comenta el mateix problema: [http://ubuntuforums.org/showthread.php?t=1133799](http://ubuntuforums.org/showthread.php?t=1133799)

Però la veritat, la solució d'insta&#320;lar el k3b no em pareix de moment satisfactòria. 

En resum: Si fiquem un CD en blanc, desapareixen les icones de l'escriptori, i no es pot accedir a cap disc dur, ni a la carpeta /home, ni a res de res (des de la consola si)

Si posem "nautilus" a la consola (tant en root com amb un usuari normal)
ens tira el següent:

kukat@kukatmaulet:~$ nautilus
Segmentation fault

root@kukatmaulet:/home/kukat# nautilus
Segmentation fault

De moment no gravarem cap CD! jejeje :)

Salutacions!

---

### Post by narcisgarcia on 2009-04-30
A mi aquesta instrucció en un Terminal m'ha funcionat:
```

sudo chmod a-r /usr/lib/nautilus/extensions-2.0/libnautilus-brasero-extension.so

```

[http://blog.ibeentoubuntu.com/2009/04/awful-nautilus-brasero-bug-in-jaunty.html](http://blog.ibeentoubuntu.com/2009/04/awful-nautilus-brasero-bug-in-jaunty.html)

Això només et salva el poder obrir l'explorador de carpetes Nautilus com a usuari normal, però no soluciona la gravació de discs amb Brasero.

---

### Post by kukat on 2009-04-30
Si, ara puc entrar al /home i tot això....però desapareixen les icones de l'escriptori, estiga el CD buit o no......no se....molt estranY! jejeje
Però gràcies! almenys ara puc entrar al /home!!!

---

### Post by PatrickVogeli on 2009-04-30
obrint el brasero tampoc pots gravar? i si t'instal·les el gnomebaker?

---

### Post by narcisgarcia on 2009-05-01
Kukat, has reiniciat l'entorn gràfic o l'ordinador després d'aplicar el petit remei?

---

### Post by kukat on 2009-05-02
Exacte!!!!!

Gràcies, era això, feia falta reiniciar.....
Ara ja funciona correctament!!!

Moltes gràcies!!!
Ja es pot marcar com a resolt, supose! (si es poguera)

---

### Post by narcisgarcia on 2009-05-02
El problema jo no el veig ben bé resolt, doncs estem parlant d'un remei que només esquiva l'error.

Suposo que cal estar pendent de la incidència que hi ha oberta:
[https://bugs.launchpad.net/ubuntu/+bug/355970](https://bugs.launchpad.net/ubuntu/+bug/355970)

---

### Post by kukat on 2009-05-04
Si, la veritat es que és un remei d'aquestos.......per tapar un poc...jejejeje
A veure que passa amb açò

---

### Post by kukat on 2009-05-06
Si no estic equivocat, AVUI al gestor d'actualitzacions es corregeix aquesta errada....
Salut!

---

### Post by narcisgarcia on 2009-05-06
No ho he provat amb una instal·lació neta, però he aplicat les actualitzacions d'avui, he desinstal·lat K3B i tornat a instal·lar Brasero, i em funciona tot bé (Nautilus i gravació de CD)

---

