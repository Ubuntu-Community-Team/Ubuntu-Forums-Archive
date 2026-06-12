---
title: "Msi a68hm-e33 v2 (ms-7721) lpqtp"
date: 2019-01-06
forum: Argentina Team
---

### Post by Hadso on 2019-01-06
Buenas gente. Feliz año. 
Tuve la pèsima idea de comprar una PC medio pelo para la oficina, sin chequear previamente que la misma tenga hardware compatible con GNU/Linux. 
Actualmente estoy corriendo Ubuntu 18.04 LTS y anda para la mierda. 
Entiendo que el problema son los drivers de la placa madre MSI A68HM-E33 V2 (MS-7721). 
Vale decir, la PC anda 10 puntos, pero se ve todo mal, es un dolo de cabeza usarla. 
Estuve buscando soluciones por todos lados sin èxito. 
Hasta trate de instalar Windows 10, pero es màs complicado que instalar Ubuntu. 
Que solucion proponen? 
Saben de algun driver libre que funcione o se adapta?
Les dejo mis especificaciones. Gracias!

Equipo
Resumen
Equipo
Procesador	AMD A4-4000 APU with Radeon(tm) HD Graphics
Memoria	3291MB (1852MB usados)
Tipo de equipo	PC Escritorio
Sistema operativo	Ubuntu 18.04.1 LTS
Nombre de usuario	lucas (Lucas)
Fecha/Hora	dom 06 ene 2019 14:59:28 -03
Pantalla
Resolución	1280x1024 pixels
Renderizador OpenGL	(desconocido)
Proveedor X11	The X.Org Foundation
Dispositivos de audio
Adaptador de audio	HDA-Intel - HDA ATI HDMI
Adaptador de audio	HDA-Intel - HD-Audio Generic
Discos SCSI
ATA TOSHIBA DT01ACA1	
Sistema operativo
Versión
Núcleo	Linux 4.15.0-43-generic (x86_64)
Versión	#46-Ubuntu SMP Thu Dec 6 14:45:28 UTC 2018
Biblioteca C	Libreria C GNU / (Ubuntu GLIBC 2.27-3ubuntu1) 2.27
Distribución	Ubuntu 18.04.1 LTS
Sesión actual
Nombre del equipo	lucas-MS-7721
Nombre de usuario	lucas (Lucas)
Idioma	es_AR.UTF-8 (es_AR:es)
Directorio personal	/home/lucas
Otras
Activo	14 minutos
Promedio de carga	0,74, 1,59, 1,48
Entropía disponible en /dev/random	3880 bits (saludable)
Procesador
Processors
Package Information
AMD A4-4000 APU with Radeon(tm) HD Graphics	0	0:0	3000,00 MHz
AMD A4-4000 APU with Radeon(tm) HD Graphics	1	0:1	3000,00 MHz

---

### Post by jesusenigma on 2019-02-23
hola, podrias ayudarme como llegastes a instalar ubuntu en esta placa, estoy rompiendomke la cabeza y no logro instalarlo.gracias (como deboconfigurar la eufi)

---

### Post by Hadso on 2019-02-25
Hola. Lo instalé sin problemas desde CD.
Otras distro fueron imposibles.
Pero Ubuntu fue sin problemas. El tema es que anda muy mal

---

### Post by matute75 on 2019-09-23
Instalé Ubuntu 18, Lubuntu 16 y Zorin (todos 64 bits) usando la mother en cuestión, el detalle fundamental es desactivar el arranque seguro.

En el setup:

**Settings - Advanced - Windows 8/8.1/10 Configuration**
- Desactivar Windows 8/8.1/10 Feature

**Settings - Boot**
- Establecer Boot Mode Select en "LEGACY+UEFI"
Estando acá, se puede establecer el orden de arranque deseado o bien pulsar F11 durante el encendido para elegir alternativas por única vez.

Descargué los archivos ISO y los procesé con Rufus para crear unidades USB (pendrives), otro detalle (de compatibilidad más que nada) es conectar el pendrive en los puertos traseros negros (USB2), no los azules (USB3).

(Comentario marginal, no espero respuesta, voy a colgar una pregunta apuntando específicamente a este inconveniente):
Todo esto funcionó perfectamente con un monitor conectado al puerto HDMI, no logro ver la pantalla de ingreso después
de instalar cuando la hago arrancar con un monitor conectado al puerto VGA, sí veo el logo de la mother y la portada de inicio.

---

### Post by nicolasgmatonti on 2020-04-22
Les queria consultar, tengo el mismo problema, probé todo lo que dicen uds y nada. En otras notebooks probé los instaladores y van como piña. Estoy con el Kali y el Peppermint. Ambos me funcionan bien en otras PCs pero en la mía. que tiene le mismo mother que uds dicen no va. ¿Alguna otra recomendación a tener en cuenta? En el error me tira:

AMD-V1: [Firmware Bug]: : No southbridge IOAPIC found
AMD-V1: Disabling interrupt remapping


> **matute75 said:**
> Instalé Ubuntu 18, Lubuntu 16 y Zorin (todos 64 bits) usando la mother en cuestión, el detalle fundamental es desactivar el arranque seguro.

En el setup:

**Settings - Advanced - Windows 8/8.1/10 Configuration**
- Desactivar Windows 8/8.1/10 Feature

**Settings - Boot**
- Establecer Boot Mode Select en "LEGACY+UEFI"
Estando acá, se puede establecer el orden de arranque deseado o bien pulsar F11 durante el encendido para elegir alternativas por única vez.

Descargué los archivos ISO y los procesé con Rufus para crear unidades USB (pendrives), otro detalle (de compatibilidad más que nada) es conectar el pendrive en los puertos traseros negros (USB2), no los azules (USB3).

(Comentario marginal, no espero respuesta, voy a colgar una pregunta apuntando específicamente a este inconveniente):
Todo esto funcionó perfectamente con un monitor conectado al puerto HDMI, no logro ver la pantalla de ingreso después
de instalar cuando la hago arrancar con un monitor conectado al puerto VGA, sí veo el logo de la mother y la portada de inicio.

---

