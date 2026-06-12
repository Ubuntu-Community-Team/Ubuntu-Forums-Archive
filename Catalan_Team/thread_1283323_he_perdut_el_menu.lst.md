---
title: "he perdut el menu.lst"
date: 2009-10-05
forum: Catalan Team
---

### Post by knuss on 2009-10-05
Hola a tothom!!
 
Be , o millor dit , malament,,, resulta que per accident vaig enviar el menu.lst del grub
a la paperera i ara no hi ha qui arranqui el xubuntu per arreglar-ho.He provat amb el super grup disc  i com que no el troba em diu que no el pot arrencar , tambe he intentat seguir aquest manual en castella [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)
pero tampoc m´en surto  i ja no se com  fer-ho. Hi ha alguna manera d´arrencar amb el livecd i accedir als arxius del meu dis dur ? es que ja no se que provar. He llegit 
tambe que si començo una instalacio nova i la tallo  al principi m´arregla el grub pero   em sembla massa bestia,,,,
 
A veure si em podeu orientar una mica.
 
Gracies per endavant.
 
Cesc

---

### Post by anna_marti_gomez on 2009-10-05
Hola Cesc,

he estat mirant i aquí van tenir el mateix problema: [HTML]http://ubuntuforums.org/showthread.php?t=1280060&highlight=grub+menu.lst[/HTML]
Es tracta de posar un Live-CD i montar la partició i repares el fitxer.

Potser algú més té una idea més brillant...

Adeu,
anna

---

### Post by anna_marti_gomez on 2009-10-05
M'havia equivocat de tags...:confused:
Ara sí,

[http://ubuntuforums.org/showthread.php?t=1280060&highlight=grub+menu.lst]("http://ubuntuforums.org/showthread.php?t=1280060&highlight=grub+menu.lst")

---

### Post by knuss on 2009-10-08
hola a tothom!!

Be en primer lloc vull donar les gracies a la Anna per la seva resposta. També dir que no ho he fet abans perquè no aconseguia arreglar el problema de la pèrdua del menú.lst i esperava a solventar-ho.

Explico de nou el problema i la sol.lució que al final he trobat per si algú si trobés en el mateix cas. Vull avisar que jo soc bastant novell amb el linux i potser no es massa ortodoxe  i  aquí la solució que he fet servir.

Primer el problema:

Vaig esborrar el menu .lst del  Boot/grub/menu.lst i aleshores no hi havia manera d'arrencar. Vaig probar de fer servir el Super Disk Grub per arrencar però suposso que al no trobar el fitxer doncs no el podia arreglar i fer que s'inicies el Xubuntu.Total que  vaig intentar fer-ho amb un  live cd  (Xubuntu 8.04)
 Aleshores vaig començar a intentar seguir els manuals que he posat al link del primer post i els del que va posar Anna però sempre en un punt o altre no em funcionaven o perque no sabia muntar la partició o perque no tenia permisos en fi un desastre.

Al final la solucio que he trobat es de lo mes senzill., i m'explico:

1 Carrego el Live Cd
2 Arrenco Aplicacions>Sistema>Partition Editor 
3 Com el Xubuntu fa un backup del menu.lst  (menu.lst.backup) entro a la terminal i (en el meu cas)
 restauro el backup         

```
cp media/disk/boot/grub/menu.lst.backup  media/disk/boot/grub/menu.lst
```

4 Reinicio i llestos !!

Bé potser es una parida però a mi m'ha funcionat . Aixo si he estat un munt d'hores de proves ,,,,

Suposso que deu funcionar amb altres distros jo faig  servir Xubuntu 9.04 i potser a algú li serveixi ,,,,

Be perdoneu el totxo

Gràcies de nou a tothom >> Cesc

---

