---
title: "Dual boot - problemas al instalar Ubuntu"
date: 2008-04-15
forum: Argentina Team
---

### Post by Kabezon on 2008-04-15
Buenas :) Les cuento cortita y al pie:

Estoy intentando instalar Windows y Ubuntu en dos particiones distintas: una de 70GB para Windows y una de 300GB para Ubuntu. Con el CD de XP formatie totalmente el HDD, cree ambas particiones, e instale Windows en la de menor capacidad. Ahora, cuando arranco Ubuntu con el Live CD, todo parece ir perfecto, selecciono ocupar los 300GB restantes, le doy al Install pero... maso al 70% se cuelga, diciendome que hay un problema al copiar los archivos y que la causa normalmente es que estas usando una mala copia de Ubuntu, que tu lectora esta sucia, o que el HDD esta fallando... 

Bueno, el CD no es, ya voy sacando 3 copias y con distintos quemadores :P La lectora de la PC tampoco, la PC es relativamente nueva y sigue estando igual que  cuando la saque de la caja. Supongo que el problema entonces son mis particiones?

Otro dato creo importante es que logre instalar Kubuntu una vez, se me dio por intentar con Kubuntu... Pero se instalo mal, todo andaba mal mal, la lista de sources estaba re incompleta, no podia correr ningun programa por falta de dependencias. Cuando arregle esto de la sources.list, igual todo seguia funcionando mal, aun despues de instalar lo que faltaba o.o Entonces tire restart a ver que onda... Bueno, ya no me dejo loggearme :P Pongo mi password, le doy enter, se pone todo en negro y vuelve a la pantalla de login O.O!!

Hoy volvi a intentar con Ubuntu... Ahora el instalador se para sin previo aviso en los 70% tambien, no dice nada, simplemente desaparece... La verdad que me estoy impacientando :S!! Windows lo puse por 2 juegos, nada mas, no me cabe usarlo para nada mas!! Pero tampoco quiero tener solo Ubuntu y no poder jugar online con mis amiguitos u.u! Mmmm... S.O.S :S

PD: Ah, y otra cosa: mi CPU, por el ruido que hace, aparenta estar en constante esfuerzo de salir adeltante :S

---

### Post by ToySouljah on 2008-04-15
Lamentable si este es confuso. Uso a un traductor ya que digo el inglés. :) Entran en su BIOS y ven si usted inicializa en el HDD con Ubuntu instalado primero y Windows como la segunda opción ... o bastante tercer... Yo tenía el mío paseo de DVD, Ubuntu (hda1), y luego Windows (sda1).

---

### Post by leo_rockway on 2008-04-15
Podrías intentar usar un cd alternate que dan menos problemas.

---

### Post by Kabezon on 2008-04-15
> **ToySouljah said:**
> Lamentable si este es confuso. Uso a un traductor ya que digo el inglés. :) Entran en su BIOS y ven si usted inicializa en el HDD con Ubuntu instalado primero y Windows como la segunda opción ... o bastante tercer... Yo tenía el mío paseo de DVD, Ubuntu (hda1), y luego Windows (sda1).

I'm bilingual xD I think I get your Spanish :P

Soy bilingue, medio torcido, pero creo entender lo que dice :P

---

### Post by faktorqm on 2008-04-16
Hola, para que pusiste 70gb para windows? si con 20 gb te alcanza te sobra y te archivas espacio por las dudas? :P:P 

Yo te recomendaria lo siguiente, mete el cd de xp, borra todas las particiones, crea una sola de 20 o 30gb, y el resto dejalo asi. Instala windows y despues mete el cd de ubuntu y elegi particionado manual. hacete una de 15gb para el /, el resto hasta el final (acordate de dejar 2gb para swap) para el /home y fijate ahi que pasa.

te tiene que quedar algo asi (con lujo de detalles) :P

partición número 1: primaria - bootflag on - activa - ntfs - 20 ó 30 gb - windows
partición número 2: primaria - bootflag on - activa - ext3 - 10 ó 15gb - linux (sistema)
partición número 3: primaria - bootflag off - ext3 ó reiserFS - 300 y algo - linux (datos)
partición número 4: primaria - bootflag off - swap - 2gb mas o menos - linux (intercambio)

Salu2!!

---

### Post by Kabezon on 2008-04-17
faktorqm, me puse 70GB porque uno de los juegos come 5GB y el otro casi 2GB, ponele que se me de por jugar alguna otra cosa, o bajarme alguno ripeado, je, teniendo en cuenta que un tanto de MP3 voy a meter o alguno que otro video, con 20 no me aclanzaria :P Dudo llegar alguna vez a los 70, pero creo que no es una cifra muy alta considerando el tamaño del HDD. Además, mejor prevenir que curar; nuinca se sabe xP 

Gracias por la idea, yo lo habia hecho asi antes... pero cree solo 2 particiones, sin contar el swap. Creo que el problema es el CD, me recomendaron grabarlo a x2, que asi se asegura sacar una copia sin fallas... y bueno, cuando termine de escribir este papel para la escuela me pongo a laburar de nuevo en este asunto. Pregunta: qué gano con tene el sistema y los datos de Linux aparte? o.O

---

### Post by leo_rockway on 2008-04-17
> **Kabezon said:**
> Pregunta: qué gano con tene el sistema y los datos de Linux aparte? o.O

Respuesta: que perdés? jaja.

Respuesta real: si tenés tu home por separado podés realizar un fresh install cuando quieras / cuando lo consideres necesario y no perdés tus oggs [0], ni tus tuneos de escritorio, ni tus archivos de configuración de todos tus programas (eso incluye bookmarks de FF), etc.

Es más, podés compartir tu ~ con distintas distros que tengas instaladas (aunque ahí se complica un poco y se arma lindo lío... pero es posible hacerlo hasta cierto punto).

[0]: mp3, si odias la libertad...

---

### Post by Kabezon on 2008-04-17
Ta, piola, eo me salio lo villa xD  Este papel me esta dando dolores de cabeza mal!! No termino mas! Y ya me harto estar en Windows >.<! Ubu, te extraño u.u! Bueno, a ver si sale instalar Ubuntu esta madrugada y comparto mi experiencia :O! Gracias =]

---

