---
title: "Como modifico el Grub?"
date: 2007-08-12
forum: Argentina Team
---

### Post by SSNova on 2007-08-12
Buenas

 Como hago para dejar predefinida la opción de Windows en ves de Ubuntu en Grub? Gracias!!

---

### Post by Hei Ku on 2007-08-12
Tenes que editar el archivo /boot/grub/menu.lst. Dentro de ese archivo tenes una linea que dice default, tendrias que setear ahi el default para que tome la entrada de Windows. Es un número de la lista, empezando de 0. O sea  que si tu Windows aparece como el cuarto en la lista, deberias poner default 3.

 Despues de eso, tendrías que hacer un update-grub, para que tome estos cambios.

En resumen:

```
sudo kate /boot/grub/menu.lst
```

editar la linea que dice:

```
default 0

```
y cambiarla por el número de la entrada de windows en el menu (Recorda que la lista empieza a contar desde cero)

Guarda el archivo, y pone:

```
sudo update-grub
```

OJO, si nunca editaste este archivo, o tenes dudas, pregunta antes de tocarlo. Y como siempre, HACE BACKUP DE ESTE ARCHIVO. :D

---

### Post by HalcónMaltés on 2007-08-13
Ojo con la línea "Otros sistemas operativos" porque grub la cuenta como entrada válida. Si Windows figura debajo de ella, sumále uno a la cuenta. Pffff.

---

### Post by ZipoTe on 2007-08-13
De todas formas, el propio menu.lst te proporciona la informacion necesaria de como modificarlo. Si te entretienes en leerlo un rato seguro que aprendes a manejarte con el :D

---

