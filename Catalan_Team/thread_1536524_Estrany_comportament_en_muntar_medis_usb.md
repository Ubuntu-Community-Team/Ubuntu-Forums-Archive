---
title: "Estrany comportament en muntar medis usb"
date: 2010-07-22
forum: Catalan Team
---

### Post by Daerun on 2010-07-22
A veure si algú em pot explicar com és que em passa el següent: tinc un disc dur extern usb, i no em dóna cap problema "normal", però fa cosa d'un mes vaig voler fer copia de seguretat de les dades amb un script de l'rsync i em va donar error. El problema era que les dues particions que tinc, en comptes de muntar-se a "/media/portatil" i "/media/traspas" que era on s'havien muntat fins aleshores, es muntaven a "/media/portatil_" i "/media/traspas_". Bé, amb resignació vaig canviar el script per afegir-hi la barra baixa aquesta... i l'altre dia ho torno a provar i ara resulta que se'm munten a "portatil__" i a "traspas__"... dues barres baixes! :shock:

Us juro que no he tocat res; com és que passa aquest canvi?

Edito: he comprovat que em passa el mateix amb el pendrive que faig servir habitualment: abans se'm muntava a "/media/PENDRIVE" i ara es munta a "media/PENDRIVE_".

---

### Post by wgarcia on 2010-07-22
Mira primer els permisos a /media (ls -l) per veure si hi ha directoris "portatil" i "traspas" que siguin propietat de "root". En cas que siguin directoris reals i estiguin a nom de root, amb "sudo" remou aquests directoris (i els altres amb un "_" que se t'han creat) i tornar a muntar els discos usb a veure si s'arregla.

---

### Post by Daerun on 2010-07-25
Sí senyor, arreglat: les carpetes corresponents ja apareixen sense la barra baixa i en sóc el propietari, en comptes de root. Gràcies :D

Cal dir que he hagut de reiniciar, perquè en acabar de fer el què m'has dit no reconeixia el disc dur quan l'he conectat :P

---

