---
title: "com ho escric...."
date: 2011-01-29
forum: Catalan Team
---

### Post by esviel on 2011-01-29
He trobat un post per fer còpies ràpides d' arxius, pero no l' acabo d' entendre,proposa una instrucció com aquesta:

 sudo cp /etc/bind/named.conf.local{,.original}

he fet alguna prova amb arxius de la carpeta d'usuari i no em funciona,suposant que volés fer-ho amb un "arxiu.odt"de la carpeta de l'usuari,¿qué haria de posar dintre de les claus ?¿ només funciona amb el sudo ?
     Gracies.

---

### Post by wgarcia on 2011-01-29
No està clar què vols fer, no sé a què et refereixes amb "còpia ràpida", la velocitat de còpia (o d'escriptura al disc) no depèn que ho facis des del gestor "Nautilus" per exemple, o clicant i pegant des de l'escriptori o amb la línia de comandes. Depèn de la velocitat del teu sistema, simplement.

Ara bé, per copiar des de la línia de comandes un arxiu de la carpeta on estàs a la carpeta B, suposant que la carpeta B existeix, la instrucció és:

cp elmeuarxiu B

Aquesta instrucció té moltes variants perquè es pot especificar tot el camí tant per al fitxer d'origen com el de destí de la còpia.

No es necessita "sudo" a no ser que la carpeta B sigui una carpeta on el teu usuari no tingui permisos, en general no et cal escriure a carpetes del sistema que serien carpetes on el teu usuari no té permisos.

---

