---
title: "[SOLVED] Pregunta"
date: 2008-01-12
forum: Argentina Team
---

### Post by pep0_0 on 2008-01-12
[FONT="Comic Sans MS"][SIZE="4"][COLOR="YellowGreen"]


Queria preguntar si alguien sabe, Si Instalo Ubuntu 7.10 en el segundo disco de mi maquina (en el primero Windows) sin el GRUB, Puedo iniciar Ubuntu seleccionando el disco desde el Bios o, si o si necesito el Grub ?

Gracias.[/FONT][/SIZE][/COLOR]

---

### Post by erginemr on 2008-01-12
Buenos Días,

No, lo siento pero debe instalar Grub. BIOS no puede hacerlo. Sin embargo, no teme de instalar Grub, el va reconocerá Windows y hacer ajustes en el menú Grub en consecuencia.

Más tarde, cuando se sienta suficiente en Linux, puede instalar y ajustar gfxboot con magníficos boot-menús, como figura en las capturas de pantalla adjuntas.

---

### Post by tzulberti on 2008-01-12
No estoy totalmente seguro de que sea necesario instalar el Grub. Supongo que cuando te referis instalar el Grub te referis instalarlo en el MBR. No estoy seguro de que pasaria si le decis que lo instale en el mismo disco en donde esta instalado Ubuntu (esta opcion solo te la daria el alternative)...

---

### Post by pablo0469 on 2008-01-13
> **pep0_0 said:**
> [FONT=Comic Sans MS][SIZE=4][COLOR=YellowGreen]


Queria preguntar si alguien sabe, Si Instalo Ubuntu 7.10 en el segundo disco de mi maquina (en el primero Windows) sin el GRUB, Puedo iniciar Ubuntu seleccionando el disco desde el Bios o, si o si necesito el Grub ?

Gracias.[/COLOR][/SIZE][/FONT]


Si, Pep, lo podes hacer, y de hecho asi tengo mi PC, y el Win XP juntando polvo en un DR que ya ni me acuerdo que tengo :). Cuando ocasionalmente debo hacer algo con el XP, me paso de disco desde la BIOS.

Con GRUB vas a tener la PC en arranque dual, algo que ya no necesito pues uso Ubuntu el 99.9% de las veces que la prendo.

Saludos.

---

### Post by facundocorradini on 2008-01-13
Sí, tranquilamente podés tener un sistema en cada rígido y elegir desde la bios cual correr.

---

### Post by vk-cdg on 2008-01-14
En primer lugar, tu BIOS debería tener la opción de elegir de que disco querés arrancar. Si eso existe en tu BIOS si que se puede. 
Tendrías que desconectar el disco de Windows cuando hagas la instalación y listo.

---

### Post by Mafber on 2008-01-14
Si podes, yo tengo instalado los SO en distintos discos y puedo iniciar uno u otro cambiando la bios.
Ese proceso lo puedes hacer de forma más fácil. Leyendo en el manual de la mother, fijate si te da la opción de elegir de donde bootear sin necesidad de entrar al setup. En mi caso tengo que apretar "F11" y puedo elegir cualquier dispositivo (discos rígidos, lectores, disquettera, etc) que quiera utilizar para bootear.

---

### Post by pep0_0 on 2008-01-16
[SIZE="4"][COLOR="DimGray"]

Muchas Gracias a todos por Responder y tratar de ayudarme, me sirvio elejir que disco desde el Bios asiq ahora me anda todo bien :)

Gracias! Salute!

[/SIZE][/COLOR]

---

### Post by vk-cdg on 2008-01-16
Otra forma de agradecer es hacer un click sobre la estrellita que aparece abajo del post de la persona a la que querés agradecer (justo al lado del botón quote)

---

