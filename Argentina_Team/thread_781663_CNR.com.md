---
title: "CNR.com"
date: 2008-05-04
forum: Argentina Team
---

### Post by Applelnx on 2008-05-04
Hola abria este thread para hablar de **CNR.com**

Vi un thread similar pero es de hace 1 año. Queria saber que pensaban acerca de este programa. A mi, me soluciono varios problemas porque soy medio roca instalando programas manualmente :D

Saludos

---

### Post by Hei Ku on 2008-05-04
y que programas querias instalar manualmente que no estuvieran en los repositorios?

en todo caso, sajnox tiene un script para convertir cualquier source a un paquete .deb que se instala con un click.

Fuera de lo practico, CNR pertenece a Linspire, que firmo un acuerdo de patentes con Microsoft, asi que para mi eso es un NO rotundo. Al menos en mi caso, como desarrollador de software libre, representa un posible problema legal.

---

### Post by Applelnx on 2008-05-05
> **Hei Ku said:**
> y que programas querias instalar manualmente que no estuvieran en los repositorios?

en todo caso, sajnox tiene un script para convertir cualquier source a un paquete .deb que se instala con un click.

Fuera de lo practico, CNR pertenece a Linspire, que firmo un acuerdo de patentes con Microsoft, asi que para mi eso es un NO rotundo. Al menos en mi caso, como desarrollador de software libre, representa un posible problema legal.

Es no lo sabia :s :(:(:( #-o

El tema es que no manejo muy bien el tema de repositorios. Solo se 

sudo apt-get install paquete

pero despues no se donde se guarda o como desinstalarlo. Me resulta mas comodo hacerlo de forma grafica, por eso lo usaba.

Me podrian pasar ese script? :D
Serviria para los paquetes .tar.gz?

Saludos

pd: yo tambien estoy en contra de Microsoft en lo que se ha convertido.

---

### Post by sajnox on 2008-05-05
El script pedido.

En primer lugar instalar alien (es el programa que transforma las fuentes en .deb, tambien sirve para .rpm)

1) Instalar alien
```

sudo apt-get install alien
```

2) Convertir el archivo a .deb (tenes que estar en la carpeta donde esta el archivo o darle la direccion de a donde ir a buscarlo)

```
sudo alien "nombre del archivo tar.gz"
```

3) En la carpeta donde estaba el tar.gz esta un nuevo archivo con el mismo nombre, pero con extension .deb Podes hacer doble click en el archivo o instalarlo desde la consola (ambos metodos quedan registrados en synaptic y los podes reinstalar / desinstalar en forma grafica o por linea de comandos)

Para instalar en forma grafica, alcanza con un simple doble click sobre el archivo, para hacerlo por linea de comandos

```
sudo dpkg -i "nombre del archivo.deb"
```

Espero te sirva

Saludos

---

### Post by Hei Ku on 2008-05-05
Por que no usas Adept o Synaptic para instalar y desinstalar paquetes? Y desde ahi tambien podes manejar los repositorios. Es solo cuestion de buscar y hacer doble click en el paquete que queres instalar/desinstalar.

---

### Post by Applelnx on 2008-05-06
Gracias ambos :D, voy a probar las dos cosas

Gracias por tomarse el tiempo y responder ;)

---

