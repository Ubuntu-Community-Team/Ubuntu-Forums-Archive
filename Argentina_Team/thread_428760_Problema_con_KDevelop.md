---
title: "Problema con KDevelop"
date: 2007-04-30
forum: Argentina Team
---

### Post by Shot on 2007-04-30
Necesito ayuda cada vez que trato de compilar un proyecto en C++ con el kdevelop me da este error:

make: aclocal: Command not found
make: *** [all] Error 127
*** Exited with status: 2 ***

---

### Post by Al_maverick on 2007-04-30
lo mas probable es que no tengas esa libreria/paquete instalada en tu maquina.

Las veces que vi errores similares, es porque no encuentra el header de una libreria (me faltan los paquetes -devel de algo).

---

### Post by Shot on 2007-04-30
gracias pero como puedo descubrir que paquete me falta?

---

### Post by javier.der on 2007-04-30
Instalando el paquete build-essential

sudo aptitude install build-essential

ese paquete tiene todo lo normalmente necesario para compilar.

---

### Post by Al_maverick on 2007-05-01
Probablemente te falte el paquete automake. Mi google-fu me dice que aclocal es parte de ese paquete ;)
Fijate porque hay varias versiones de ese paquete. Puede que esa aplicacion necesite una version en particular.

---

