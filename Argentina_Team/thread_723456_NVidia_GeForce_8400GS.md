---
title: "NVidia GeForce 8400GS"
date: 2008-03-13
forum: Argentina Team
---

### Post by santiagoward2000 on 2008-03-13
Hola gente!
Hace poco me compré una compu nueva y estaba con ganas de instalarle Xubuntu. Primero quise probar cómo andaba todo, y probé el LiveCD. Tuve un problema con la placa GeForce 8400GS. Instalé los drivers, y cuando traté de cerrar la sesión, se reinició la compu (y obviamente perdí lo que había bajado). Después probé de nuevo, cerrando con Ctrl+Alt+Backspace y pasó lo mismo.
Después, medio improvisando, traté con ```
sudo killall -u ubuntu
```.Esta vez no se reinició, pero cuando entré de nuevo, me saltó una ventana que decía que estaba en **"low graphics mode"**. Traté de buscar los drivers en esa ventana, pero igual no andaba.
Mi pregunta es si alguien probó con esa placa y me puede decir cómo le anduvo todo, y si alguien sabe cómo puedo hacer para probarla en el LiveCD.
Saludos!

---

### Post by Apokalyptica79 on 2008-03-13
Hola encontré algo espero que te sirva.
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")
[http://www.nvidia.com/object/linux_display_amd64_169.04.html]("http://www.nvidia.com/object/linux_display_amd64_169.04.html")
Saludos

---

### Post by Mauro22 on 2008-03-13
Que yo sepa en la version LiveCD no podes bajar nada... :(


Al reiniciar fue...



:guitar:

---

### Post by Apokalyptica79 on 2008-03-13
Hola, cualquier cambio o arreglo que hagas usando ubuntu como live lo vas a perder porque no lo tenes instalado.
Saludos

---

### Post by Hei Ku on 2008-03-13
Perdon por "robar" la thread. Mi hermano se compró hace poco una NVidia GEForce 8000GS. Alguien tuvo suerte con esta placa?

---

### Post by Cripton on 2008-03-13
yo la tengo andando la 8400gs, al principio solo con los VESA, pero después la logré hacer andar, creo que no me reconocia bien el refresco del monitor, instalé el sistema en modo texto y modifiqué el xorg

---

### Post by santiagoward2000 on 2008-03-14
> **Mauro22 said:**
> Que yo sepa en la version LiveCD no podes bajar nada... :(


Al reiniciar fue...

Jeje, sí, ya sé que cuando se reinicia pierdo todo. Yo lo que quiero hacer es cerrar solo la sesión, y después volver a entrar. Cuando tenía antes una GeForce 4000MX podía hacerlo sin problema. Tocaba Ctrl+Alt+Backspace, volvía a entrar y podía usar la placa con los drivers y ver si andaba Compiz.
El problema es que con los drivers de la 8400GS se reinicia en lugar de cerrar la sesión.

---

### Post by niko_3100 on 2008-03-14
Es una placa bastante nueva pero supongo que linux la debe de soportar. Lo mejor seria instalar el SO y instalar los drivers restringidos de nvidia.

---

### Post by santiagoward2000 on 2008-03-14
> **niko_3100 said:**
> Es una placa bastante nueva pero supongo que linux la debe de soportar. Lo mejor seria instalar el SO y instalar los drivers restringidos de nvidia.

Si, yo también supuse que los debe soportar, pero quería estar seguro. Medio que me asusté cuando me entró a **Low graphics mode** después de instalar los drivers. :lolflag:

---

