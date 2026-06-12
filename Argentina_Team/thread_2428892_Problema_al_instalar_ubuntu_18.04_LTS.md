---
title: "Problema al instalar ubuntu 18.04 LTS"
date: 2019-10-10
forum: Argentina Team
---

### Post by axlhissam on 2019-10-10
Estoy tratando de instalar Ubuntu 18.04, la imagen la tengo en una memoria usb, todo va normal hasta que selecciono la forma de instalación, como el disco duro es nuevo, selecciono borrar e instalar ubuntu, todo parece que va bien ya que el cursos cambia a la ruedita que gira pero por mas tiempo que espere no avanza, el led que indica si se está escribiendo algo en el disco duro está apagado, trato de darle atras y no pasa nada, trato de cerrar la ventana de instalación y aparece una ventana diciendo que la instalación no responde, con cualquier tipo de instalación que seleccione pasa lo mismo, espero me puedan ayudar con este problema.

Uso una laptop HP 15-bs011la

---

### Post by mörgæs on 2019-10-12
Hi, since noone answered in Spanish I hope it's OK that I do in English. Google Translate did a good job. I am aware that the main language here of course is Spanish.

Your HP is fairly new. Have you tried booting Ubuntu 19.04 or 19.10?

---

### Post by fedeavila2 on 2019-11-18
Buenas! Yo tengo una laptop HP Pavilion Power y me sucedía que luego de la instalación se congelaba el sistema. La reiniciaba, (Ubuntu o cualquier derivado de Debian) se instalaba OK, pero cuando iniciaba nuevamente se volvía a congelar... Aparentemente existe algún hardware que no le gusta a Linux. Lo pude resolver agregando la línea noapic acpi=noirq nolapic en Grub. Luego con instalar los drivers privativos de Nvidia andaba sin problemas. Info: [https://askubuntu.com/questions/149745/system-freeze-after-adding-noapic-acpi-noirq-nolapic](https://askubuntu.com/questions/149745/system-freeze-after-adding-noapic-acpi-noirq-nolapic)

---

