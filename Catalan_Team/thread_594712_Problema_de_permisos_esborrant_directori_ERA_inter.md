---
title: "Problema de permisos esborrant directori ERA: interpet de commandes d'en papapep"
date: 2007-10-28
forum: Catalan Team
---

### Post by prostata on 2007-10-28
Segons la doc. d'en papapep i per tal de practica una mica, vull esborrar un directori determinat, el qual en te unes determinades caracterìstiques de permissos, suposso.

De forma que us adjuntu la resposta per terminal per tal de veure si em podeu ajudar a interpretar on és l'error i com deuria tractar-lo per fer-lo bé.

gràcies.

josep@josep-desktop:~$ cd aplicacions
josep@josep-desktop:~/aplicacions$ cd descarregues
josep@josep-desktop:~/aplicacions/descarregues$ rm -r fusioninstaller
rm: ¿descender al directorio protegido contra escritura `fusioninstaller'? (s/n) s
rm: ¿borrar el archivo regular `fusioninstaller/execute.py'  protegido contra escritura? (s/n) s
rm: no se puede borrar `fusioninstaller/execute.py': Permiso denegado
rm: ¿descender al directorio protegido contra escritura `fusioninstaller/images'? (s/n) s
rm: ¿borrar el archivo regular `fusioninstaller/images/CompizFusion.png'  protegido contra escritura? (s/n) s
rm: no se puede borrar `fusioninstaller/images/CompizFusion.png': Permiso denegado
rm: ¿borrar el archivo regular `fusioninstaller/images/build.png'  protegido contra escritura? (s/n) s
rm: no se puede borrar `fusioninstaller/images/build.png': Permiso denegado
rm: ¿borrar el archivo regular `fusioninstaller/images/download.png'  protegido contra escritura? (s/n) s
rm: no se puede borrar `fusioninstaller/images/download.png': Permiso denegado
rm: ¿borrar el archivo regular `fusioninstaller/images/install.png'  protegido contra escritura? (s/n) S
rm: no se puede borrar `fusioninstaller/images/install.png': Permiso denegado
rm: ¿borrar el archivo regular `fusioninstaller/images/optional.png'  protegido contra escritura? (s/n) s
rm: no se puede borrar `fusioninstaller/images/optional.png': Permiso denegado
rm: ¿borrar el archivo regular `fusioninstaller/images/update.png'  protegido contra escritura? (s/n) s
rm: no se puede borrar `fusioninstaller/images/update.png': Permiso denegado
rm: ¿borrar el archivo regular `fusioninstaller/install.py'  protegido contra escritura? (s/n) s
rm: no se puede borrar `fusioninstaller/install.py': Permiso denegado
rm: ¿borrar el archivo regular `fusioninstaller/installfusion.glade'  protegido contra escritura? (s/n) s
rm: no se puede borrar `fusioninstaller/installfusion.glade': Permiso denegado
josep@josep-desktop:~/aplicacions/descarregues$

---

### Post by papapep on 2007-10-28
Si us plau, poseu uns títols als fils que expliquin què intenteu solucionar. És MOLT important.

Com que et diu que no tens prou permisos, és clar que els has d'assolir d'alguna manera. Abans però, serà interessant veure qui n'és el propietari:

```
ls -la /camí_al_directori_que_conté_els_fitxers_que_vols_eliminar
```

A fi d'esborrar-ho tot plegat (molt de compte de no ficar un directori que no sigui el que vols, no hi ha possibilitat de tornar enrera!):

```
sudo rm -r /el_directori_pare_del_contingut_que_vols_esborrar
```

---

### Post by prostata on 2007-10-28
[QUOTE=papapep;3652522]Si us plau, poseu uns títols als fils que expliquin què intenteu solucionar. És MOLT important.

**Si, tens raó,disculpes.....i gràcies**

---

