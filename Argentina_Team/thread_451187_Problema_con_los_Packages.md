---
title: "Problema con los Packages"
date: 2007-05-22
forum: Argentina Team
---

### Post by natanzuelo on 2007-05-22
Soy 100% nuevo en linux, me acabo de instalar Kubuntu en un disco... en el otro tengo Windows XP.
Tengo una conexión con Arnet y mi modem es el Huawei SmartAX MT810. Para poder instalarlo en Linux sigo los pasos de **[esta guia]("http://www.ubuntu-es.org/index.php?q=node/45097")**.

La cosa es que la guia me pide que haga **$ sudo apt-get install build-essential**... y no puedo porque precisamente necesito instalar el modem para poder conectar a Internet para poder ejecutar apt-get...
Asi que el Build-Essential lo bajé de [http://packages.ubuntu.com/](http://packages.ubuntu.com/) y tambien bajé todas sus dependencias, y las dependencias de sus dependencias.

Luego en linux instalé casi todo sin problemas... excepto una que se llama **g++-4.1**
Me dice que no puedo instalarla pk falta la dependencia **libstdc++6-4.1-dev**, pero cuando kiero instalar esta, me dice que no puede pk falta la dependencia **g++-4.1**...

Osea es un circulo, una me pide a la otra, y viceversa...

Que hago?

Se agradece cualquier ayuda!!

---

### Post by sebas.rhcp on 2007-05-22
los build essentials estan los cds

---

### Post by jayflower on 2007-05-22
En otro post habia pasado a alguien algo similar, los paquetes se pueden bajar de aca:[http://packages.ubuntu.com/]("http://packages.ubuntu.com/"). Se instalan como si fueran ejecutables de Windows y si te pide otro paquete por las dependencias, te fijas cualesson, los bajas y dejas todo listo para compilar tu modem. Espero sirva de ayuda. Eso es algo un poco molesto, pero también tiene sus ventajas. te vas a cansar de hacer apt-get install es practiquisimo!

---

### Post by natanzuelo on 2007-05-23
Gracias por responder.
Si, el build-essential esta en el cd, y tambien sus dependencias... pero sigo con el mismo problema...

El **g++-4.1** me pide que tenga instalado el **libstdc++6-4.1-dev**... cuando lo voy a instalar me dice que tengo que tener instalado el **g++-4.1**... es un circulo...

Esto es igual tanto con los packages que descargo de packages.ubuntu.com como con los que trae el CD.

Es re loco... no entiendo...

---

### Post by godzeus on 2007-05-23
Yo tuve un problemita similar, cuando recien instale Edgy( que viejos estamos), lo que tenes que hacer es primero entrar en Terminal, y poner " sudo apt-add cdrom " con el cd de Feisty puesto, lo que va a hacer es agregarlo al repositorio, despues, pones " uname -r " que te dice que version exacta de kernal tenes instalado y luego "sudo apt-get build-essential linux-headers-2.6.20.15-generic " en el caso de que al ejecutar uname -r te de este kernel, sino cambialo por lo que te figure en pantalla.
Cualquier cosa avisa que te doy otra manito, me costo un peludo hacer andar el alfajorcito del diablo de Arnet, pero no es imposible.

Saludos

---

### Post by natanzuelo on 2007-05-23
Voy a la consola, hago **sudo apt-cdrom add** y me dice que inserte un CD, que no hay ninguno puesto... lo mismo en el gestor de paquetes de Kubuntu...
Sin embargo, el CD me lo reconoce en el escritorio y lo puedo abrir y todo... incluso cuando reinicio con el CD puesto tambien me lo toma.
Y tambien lo puedo navegar desde windows.

O sea, el CD esta bien, y tambien es reconocido por linux. Pero cuando le hago **sudo apt-cdrom add** el cd no existe...

Tengo ke hacerle algo para ke reconoza el CD?
Es muy raro lo que me esta pasando?

Gracias por la aiuda

---

### Post by jpmorelli on 2007-05-24
> **natanzuelo said:**
> Voy a la consola, hago **sudo apt-cdrom add** y me dice que inserte un CD, que no hay ninguno puesto... lo mismo en el gestor de paquetes de Kubuntu...
Sin embargo, el CD me lo reconoce en el escritorio y lo puedo abrir y todo... incluso cuando reinicio con el CD puesto tambien me lo toma.
Y tambien lo puedo navegar desde windows.

O sea, el CD esta bien, y tambien es reconocido por linux. Pero cuando le hago **sudo apt-cdrom add** el cd no existe...

Tengo ke hacerle algo para ke reconoza el CD?
Es muy raro lo que me esta pasando?

Gracias por la aiuda

La verdad que si es raro, porque que en entorno gráfico lo monte y no lo veas en consola es muy raro.
Vos estas en la parte gráfica, abrís una consola y cuando corres el comando apt-cdrom -add te dice que no hay CD ? o inicias la PC en modo consola pura ?

---

### Post by natanzuelo on 2007-05-24
No, corro consola en la parte grafica... no entro en terminal pura...
No se ke puede ser che...

---

### Post by natanzuelo on 2007-05-30
Bueno al final no agregue el CD a los repositorios, pero para eliminar el bucle de dependencias infinito use** sudo dpkg -i --force-all paquete.deb **con esos dos que me traian problemas.
Asi logre instalarlos sin problemas.


Saludos y gracias igual!

Mods ya pueden cerrar el tema si quieren

---

### Post by UAhmad on 2007-05-30
Hi i having the same problem error message 

E: Couldn't find package linux-headers-2.6.20.15-generic

I don't understand your language can anyone help me in english.

Thanks Guys ,Please.

---

### Post by jpmorelli on 2007-05-30
> **UAhmad said:**
> Hi i having the same problem error message 

E: Couldn't find package linux-headers-2.6.20.15-generic

I don't understand your language can anyone help me in english.

Thanks Guys ,Please.

You can run this command and force it to work:

sudo dpkg -i --force-all *.deb

Good Luck !

---

