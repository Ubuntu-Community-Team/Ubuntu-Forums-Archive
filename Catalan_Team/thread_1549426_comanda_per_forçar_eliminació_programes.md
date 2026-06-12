---
title: "comanda per forçar eliminació programes?"
date: 2010-08-09
forum: Catalan Team
---

### Post by pserra on 2010-08-09
Hola,
el meu problema es que quan faig el sudo apt-get upgrade o actualitzo sempre em surt el mateix error:
(adjunto darreres linees)
> rmdir: no s’ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/ZLe»: No such file or directory
rmdir: no s’ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/ZLeFB»: No such file or directory
rmdir: no s’ha pogut eliminar «/usr/local/Brother/sane/GrayCmData»: No such file or directory
rmdir: no s’ha pogut eliminar «/usr/local/Brother/sane»: No such file or directory
dpkg: s'ha produït un error en processar brscan (--remove):
 el subprocés installed post-removal script retornà el codi d'eixida d'error 1
S'han trobat errors en processar:
 brscan
E: Sub-process /usr/bin/dpkg returned an error code (1)

des de el synaptic si escolleixo opció eliminar completament els paquets no em soluciona el problema... 
COM HO PUC SOLUCIONAR?

Merci

---

### Post by wgarcia on 2010-08-10
Això se soluciona creant aquestes carpetes que el sistema et diu que no existeixen, i després donant l'ordre:

sudo apt-get remove --purge brscan

---

### Post by pserra on 2010-08-11
> **wgarcia said:**
> Això se soluciona creant aquestes carpetes que el sistema et diu que no existeixen, i després donant l'ordre:

sudo apt-get remove --purge brscan

merci wgarcia, encara es resisteix... et passo els errors de terminal:
> pere@pere-laptop:~$ sudo apt-get remove --purge brscan
[sudo] password for pere: 
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet
Els paquets següents s'instal·laren automàticament i ja no són necessaris:
  xsane-common
Empreu «apt-get autoremove» per a suprimir-los.
Es SUPRIMIRAN els paquets següents:
  brscan
0 actualitzats, 0 nous a instal·lar, 1 a suprimir i 49 no actualitzats.
1 no instal·lats o suprimits completament.
Després d'aquesta operació s'empraran 0B d'espai en disc addicional.
Voleu continuar [S/n]? S
(S'està llegint la base de dades ... hi ha 255114 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant brscan ...
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/BHL»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/BHL2»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/BHL2FB»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/BHLFB»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/BHMFB»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/BHminiFB»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/YL4»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/YL4FB»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/ZL2»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/ZL2FB»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/ZLe»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData/ZLeFB»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane/GrayCmData»: No such file or directory
rmdir: no s&#8217;ha pogut eliminar «/usr/local/Brother/sane»: No such file or directory
dpkg: s'ha produït un error en processar brscan (--remove):
 el subprocés installed post-removal script retornà el codi d'eixida d'error 1
S'han trobat errors en processar:
 brscan
E: Sub-process /usr/bin/dpkg returned an error code (1)
pere@pere-laptop:~$ 


i si faig apt-get autoremove brscan o xsane-common em surten els mateixos errors....

---

### Post by pserra on 2010-08-15
Merci,
al final ja he pogut solventar el problema seguint el consell de wgarcia, era ben fàcil...
per crear els  paquets ho he fet amb la comanda:
$ sudo touch /usr/local/Brother/sane/GrayCmData/ZLe
per aquest paquet i per cada paquet trencat i després ja permet fer els updates sense cap problema..
Merci

---

