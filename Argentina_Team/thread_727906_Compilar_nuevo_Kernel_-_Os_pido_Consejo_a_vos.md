---
title: "Compilar nuevo Kernel - Os pido Consejo a vos"
date: 2008-03-18
forum: Argentina Team
---

### Post by krixiwin on 2008-03-18
Hola Comunidad

Mi objetivo es compilar el **kernel**, para aprovechar el máximo rendimiento del hardware.

He leido muchos Manuales de diferentes web, publicadas hace bastante años.

Como el software avanza, me gustaría que me recomendara su mejor manual actualizado a la versión **7.10 de ubuntu**, y consejo para compilar el kernel.

Quiero un kernel pequeño pero potente. Eliminar todo aquello que no uso. Que sea Facil / Complicado de hacer.

Las características del equipo (PC) son las siguiente:

[B][PLACA BASE GIGABYTE M61SME-S2 AM2 DDR2, 256+PCI-EXPRESS]("http://latam.giga-byte.com/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2459&ProductName=GA-M61SME-S2")

Micro AMD  Athlon AM2 X2 4200 (2,2Ghz)
HDD PATA 300GB x2
HDD SATA 250GB x1[/B]

Quiero Exprimir todo el rendimiento gráfico, los dos núcleos y los 64 bits. Se que esto es sencillo de hacer, pero quiero ver todas las maneras nuevas desde mi ausencia a compilar kernel.

Gracias, Saludos:)

---

### Post by marianom on 2008-03-18
¿Viste [este documento]("https://help.ubuntu.com/community/Kernel/Compile")?
No tiene nada del otro mundo pero basa sus comentarios sobre el kernel de Ubuntu y además trae algunos links a otros recursos que por ahí son de más ayuda.

---

### Post by felipelerena on 2008-03-19
hay un thrad en ubuntu forums que se llama "master kernel thread" busca ahi

---

### Post by krixiwin on 2008-03-19
Gracias **marianom** por el enlace aportado, seguire a hora todos los pasos indicados.

Gracias  **felipelerena** buscare el master kernel thread, y ya os comentare que tal va todo.

Es este no ¿? [http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+thread]("http://ubuntuforums.org/showthread.php?t=311158&highlight=master+kernel+thread")

Tiene muy buena pinta, se ve muy completo.

Sigo Admitiendo más sugerencia.

Saludos

---

### Post by felipelerena on 2008-03-19
ese es EL thread, es constantemente actualizado a la ultima version del kernel y es usado como referencia por muchisima ente

---

### Post by krixiwin on 2008-03-19
Tengo unas dudas sobre EL thread.

Antes del paso 6 hay una nota:
# NOTE: IF YOU WILL BE PATCHING THE KERNEL FOR A PROGRAM (ex. fbsplash, bootsplash) APPLY THE PATCH AND SKIP TO STEP 8. IF NOT, GO AHEAD TO THE NEXT STEP.

Y en el paso 6:
 (Do NOT do this or the step below if you are using a different patch like beyond, emission, etc.)

¿Que es lo que se refiere? Si voy a parchear el kernel para unos determinados programas,... 

Estos pasos son opcionales, pero, son recomendables, correigen bug importantes ¿?

---

### Post by marianom on 2008-03-19
Generalmente parcheas el kernel para agregarle funcionalidad que por su caracter experimental no está incorporado al código fuente. Recuerdo que hace un tiempo para poder crear un live cd basado en slackware era necesario parchear el kernel y agregarle un filesystem comprimido que no venía en el código original (no recuerdo si era unionfs o splashfs). Ahora todo eso está mucho más simplificado.

No creo que por el momento necesites preocuparte por eso, seguí los pasos que hablan de compilar un kernel normal sin aditivos: si el thread aún está activo no dudes en agregar tus dudas ahí, seguro que hay mucha gente con la gimnasia necesaria en esos asuntos como para que obtengas ayuda.

---

