---
title: "Ayudenme con esta idea de particion"
date: 2007-02-03
forum: Argentina Team
---

### Post by bichopro on 2007-02-03
Saludos...

el asunto es simple, tengo un disco duro de 80 en el cual tengo instalado ubuntu en una particion de 13 gigas y una swap de 1 giga, el resto es una particion ntfs para wintendo.

wintendo hace de almacen de mis archivos pero ya me aburri de no poder modificarlos directamente desde ubuntu y en vez de instalar soporte de escritura para ntfs pense...

¿que tal si dejos dos particiones de 15 para cada os y una particion en fat 32 para almacenar mis archivos?

ademas de poder escribir desde los dos OS(*) y ademas podre formatear tranquilo cuando para variar wintendo falle o para arreglar algun error que cometiera en ubuntu reinstalando.

alguien ha hecho algo parecido...o alguien nota alguna desventaja?

mi actual instalacion de ubuntu con tooodos los programas que necesito y mas esta pesando cerca de 6 gigas solamente y la de xp algo como 11gigas pero con varias cosas de mas que voy a borrar en esa futura instalacion...
opiniones por favor

---

### Post by beuno on 2007-02-03
No veo nada mal con la idea.
Yo lo maneje asi un tiempo, pero finalmente estaba el 99% del tiempo en Linux, asi que pase todo a la particion de Linux porque es mas rapida el acceso a ext2/3 que a fat32.

---

### Post by Tinchio on 2007-02-03
> **beuno said:**
> No veo nada mal con la idea.
Yo lo maneje asi un tiempo, pero finalmente estaba el 99% del tiempo en Linux, asi que pase todo a la particion de Linux porque es mas rapida el acceso a ext2/3 que a fat32.

lo mismo me paso y ahora que estoy el 100% del tiempo en kubuntu tengo la FAT para almacenar, pero caundo instale Feity saco la FAT a la mier..

---

### Post by bichopro on 2007-02-03
entiendo ...yo tb estoy a cien en linux...pero comparto el pc con gente que necesita xp.
gracias por las respuestas

---

### Post by Tinchio on 2007-02-03
> **bichopro said:**
> entiendo ...yo tb estoy a cien en linux...pero comparto el pc con gente que necesita xp.
gracias por las respuestas

claro por eso como decis lo de la FAT es una buena opcion, dale palante nomas

---

### Post by BlackHero on 2007-02-04
yo tengo un drama parecido tengo mi disco de 40 gb y aparte tengo un carry usb sata de 320 gb el tema es que xfce no me lo reconoce muy bien por ahi lo toma y por ahi me dijeron que en ubuntu funca bien el drama es que lo quiero formatear y esas cosas y nada instal gparted para formatearlo lo formatee en ext3 pero por ahi cuando lo prendo no anda 
ahora lo estoy provando en una maquina con windows y anda bien estuve viendo que onda en ubuntu el sata mas usb pero dicen que anda bien de hecho lo hize andar pero no muy bien que digamos :)

---

### Post by Nemesis Teufel on 2007-02-04
Otra pregunta del mismo tema:
Que es mas rapido para Ubuntu? Un disco FAT32 para compartir archivos con wintendo, o con NTFS con soporte de lectura y escritura?

---

### Post by QUASAR_FREAK on 2007-02-05
es, lo mismo ya ke estas limitado siempre por la velocidad de la red al kompartir, el kuello de botella es ahi y no en la makina lokal, lo ke si excepto ke necesites archivos mas grandes de 3gb yo usaria fat32, ya ke ntfs suele pincharse de formas extrañas (en win) y las herramientas de rekuperacion son mas dificiles de konseguir.

---

### Post by bichopro on 2007-02-05
Les cuento...

Todo bien con la idea...

Parti instalando el wintendo como dije con 15 gigas y el resto lo deje sin partición.
Luego desde el livecd de ubuntu edite manual la particiones dejando 14 para ubuntu y 1 giga de swap, el resto lo formatie en fat32.
Eso me costo por lo de las particiones lógicas o extendidas pero al final se instalo.

Cuando volvi a abrir xp el problema fue que me veia la partición fat32 pero le aparecía sin formato y wintendo solo me dejaba formatearlo en ntfs asi que opte por instalar un programa para formatear y listo ya quedo perfecta.

Luego pase mis archivos que tenia respaldado en otro pc y entre a ubuntu

una vez ahí ubuntu me leia mi particion de wintendo en ntfs solo de lectura como yo quería y solo me quedo montar la nueva partición fat32 con mis archivos.

y...chaaa chaaa channnnn

estoy en gnome con beryl y todo salio perfecto, espero la experiencia le sirva a alguien mas y gracias por las opiniones.
:)

---

