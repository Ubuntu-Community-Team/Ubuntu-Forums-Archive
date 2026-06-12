---
title: "Titan mp3 2gb"
date: 2007-08-25
forum: Argentina Team
---

### Post by Apipote on 2007-08-25
Es un reproductor de mp3 generico con chip sigmatel.
Xubuntu lo reconoce, pero no puedo borrar nada. Esto me sale:

Failed to open "/media/disk/.Trash-1000/info/Talking_Heads-The_Best_Of_The_Talking_Heads-2004-CNS.trashinfo" for writing.

Tampoco se como formatearlo, y luego meter musica nueva.
En definitiva, querria tener domino total del pen drive como hacia con el explorador de windows.
He leido algo de "automount" y el comando "dmesg" en la consola, pero no entiendo nada de lo que ahi me sale. 
Que hago?
Gracias.

---

### Post by undiaperfecto on 2007-08-25
a lo mejor tenes la papelera llena o algo asi.
proba en el menu ver, mostrar los archivos ocultos, y ahi entras a tu papelera y la vacias.
a mi me pasaba eso con uno generico.

---

### Post by Apipote on 2007-08-26
Hermano sos un campeón. Funciona!!
Ahora por favor explicame, porque?
Saludos.

---

### Post by Hei Ku on 2007-08-26
porque no tenes espacio, y el dispositivo no lo maneja bien. 

Alguien sabe si hay forma de evitar el comportamiento de "papelera de reciclaje" para un dispositivo determinado?
Es decir, que directamente elimine los archivos en vez de mandarlos a la papelera, pero sólo para ciertos dispositivos?

---

### Post by por100pre1 on 2007-08-26
> **Apipote said:**
> Hermano sos un campeón. Funciona!!
Ahora por favor explicame, porque?
Saludos.

Eso se debe a que cuando mueves un material a la papelera, Nautilus crea una carpeta de papelera en el medio donde el material esta ubicado y mueve el archivo a dicha papelera. El mandar esa carpeta de papelera "a la papelera" significa borrarla por completo.

---

### Post by por100pre1 on 2007-08-26
> **Hei Ku said:**
> porque no tenes espacio, y el dispositivo no lo maneja bien. 

Alguien sabe si hay forma de evitar el comportamiento de "papelera de reciclaje" para un dispositivo determinado?
Es decir, que directamente elimine los archivos en vez de mandarlos a la papelera, pero sólo para ciertos dispositivos?

Existe la opción de borrado permanente pero hay que habilitarla. Vamos abrir el editor de configuración de Gnome:

```
gconf-editor
```

Busquen en:
/
   apps
          nautilus
                    preferences

y marquen la opción **enable_delete**

Lean la advertencia al proceder... :)

---

### Post by Hei Ku on 2007-08-26
Si, realmente no es algo que quiera tener siempre habilitado. Pero estaria bueno tener una opcion en el fstab para decirle que, por ejemplo en los dispositivos USB, haga un borrado permanente, pero solo para esos dispositivos.

Obviamente el fstab no es el lugar para eso, porque el borrado logico es algo del entorno de escritorio, pero quizas gnome o kde tengan una opcion x dispositivo.

---

### Post by Tinchio on 2007-08-29
Para evitar el comportamiento tipo papelera en los pendrive borren directamente los archivos, en vez de borrarlos con la tecla "supr" borren con "shift"+"supr" y borrara directamente sin mandar a la papelera

---

### Post by niko_3100 on 2007-08-29
Iba a decirte lo mismo "shift" + "supr" eso es re de windows pero ubuntu tambien funciona.

---

### Post by undiaperfecto on 2007-08-29
Si esto fuera un foro de windows, la idea general seria que al dispositivo le incluyan las teclas shift + delete jajajaja.
La verdad, antes de toquetear tanto el fstab, creo que es mejor vaciarla manualmente, al menos con mi experiencia en romper todo cada vez que edito algo delicado.

---

### Post by niko_3100 on 2007-08-30
mmm... si a full cuantas veces me mande mocos en ubuntu borrando cosas y tube que recurrir al viejo truco de la papelera de restauracion y me salvo y eso que llevo solo 2 meses y dias con ubuntu jeje!!! Lo mejor es vaciarla manualmente viendo que las cosas que tenes ahi adentro realmente ya no te sean utiles. Una idea que tube hace un tiempito fue hacer un back up de la papelera de reciclaje jajajjaj!!!! bueniiiiiiiisimo!!

---

### Post by por100pre1 on 2007-08-30
El borrado en GNOME es una opcion fuerte. Por eso deje esta advertencia:

> **por100pre1 said:**
> Lean la advertencia al proceder... :)

Esta es la advertencia:

> Si se establece a «true», entonces Nautilus tendrá una opción que le permitirá borrar un archivo inmediatamente en lugar de moverlo a la papelera. Esta característica puede ser peligrosa, así que úsela con cuidado.

---

### Post by Apipote on 2007-08-30
Soy conservador, me quedo con el metdodo manual, que me funcionó de 10.
Gracias

---

