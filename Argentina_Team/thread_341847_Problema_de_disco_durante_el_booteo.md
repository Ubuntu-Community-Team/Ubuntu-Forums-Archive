---
title: "Problema de disco durante el booteo"
date: 2007-01-19
forum: Argentina Team
---

### Post by Hex_Mandos on 2007-01-19
Hoy mientras trataba de bootear vi que el proceso iba lentísimo. Pensé que se había colgado, resetee y probé en el modo de recuperación, viendo los procesos de booteo. Entonces vi que lo que pasaba es que me tiraba mil errores de disco como este:
> 
ide: faled opcode was: unknown sector
end_request: I/O error, dev hdb, sector 20964825
Buffer I/O error on device hdb2, logical block 0

Después de un tiempo larguiiiiisimo probando, logré entrar como root. Alguien sabe como solucionar un problema así desde la línea de comandos o desde un LiveCD? En lo posible, me gustaría salvar a esa partición, está montada como /home.

---

### Post by scrooge_74 on 2007-01-19
yo diria que bootes desde un live cd y hagas backup de los datos

Tal vez si luego la formateas se corrijan los errores, pero suena como que vas a perder el disco

---

### Post by Hex_Mandos on 2007-01-19
Te parece? Por lo que probé desde modo texto, los programas andan (x ej, usé w3m y links para ver un par de sitios en internet). No hay una manera de hacerle ignorar ese sector?

---

### Post by scrooge_74 on 2007-01-19
No estoy seguro como hacerlo en linux, yo lo hacia en windows, pero siempre era algo temporal a la larga el disco se va a dañar.  Por eso te sugirio que hagas backup de tus datos, si tienes /home en esa partición podrías intentar formatearla de nuevo luego de sacar los datos.

En el pasado (cuando usaba windows) yo podía usar la Pc bien, de vez en cuando tenía unos freeze de medio segundo que eran intermitentes, pero con el tiempo el problema creció y el disco se terminó de dañar, llevandose datos importantes.

---

### Post by Hex_Mandos on 2007-01-19
Entiendo... este disco tuvo algunos problemas en el pasado. Por lo menos tengo la suerte de tener dos discos físicos, así que puedo seguir con este que estoy ahora (con Win, pero pasan cosas peores en la vida).

Alguien tiene alguna experiencia con adaptadores SATA por PCI (mi mother no tiene soporte nativo de SATA) o me dejo de joder y compro un disco IDE?

---

### Post by scrooge_74 on 2007-01-19
No tengo experiencia con los SATA, sólo sé que en algunos casos hay que instalar un driver para controlarlo, pero eso es en windows, creo que el linux eso ya viene en el kernel. 

Deberías probar bootear un live cd y tratar de montar el disco SATA

---

### Post by Hex_Mandos on 2007-01-19
Si, pero hay un tema: hoy por hoy no tengo un disco SATA para probar, y no me voy a comprar uno para después ver si me anda.

---

### Post by scrooge_74 on 2007-01-19
Compra uno IDE cada día están más baratos

---

### Post by lavaramano on 2007-01-19
se.
se ve como un disco pidiendo el cambio :/

igual de ultima, siempre podes guardarlo y meterlo al freezer un rato, que se recupera (?)

---

### Post by beuno on 2007-01-19
> **Hex_Mandos said:**
> Hoy mientras trataba de bootear vi que el proceso iba lentísimo. Pensé que se había colgado, resetee y probé en el modo de recuperación, viendo los procesos de booteo. Entonces vi que lo que pasaba es que me tiraba mil errores de disco como este:


Después de un tiempo larguiiiiisimo probando, logré entrar como root. Alguien sabe como solucionar un problema así desde la línea de comandos o desde un LiveCD? En lo posible, me gustaría salvar a esa partición, está montada como /home.

¿Tenes S.M.A.R.T. activado en el bios?

Siempre es bueno tenerlo para avisos tempranos de fallos.

Si no lo tenes, activalo y fijate si se queja.

---

### Post by Hex_Mandos on 2007-01-20
Bueno, tengo decidido comprarme un disco nuevo, pero mientras decido que/cuando/donde formatee el disco defectuoso e instalé Kubuntu (para variar un poco, estaba con ganas de probar KDE por un tiempo mas o menos largo, pero sin llegar al extremo de probar otra distro y joderle la vida a la flia que usa la maq y mas o menos ya tenían la vida solucionada con Ubuntu/Gnome... instalo ubuntu-desktop y fue). Por lo pronto, veo que el disco mal que mal anda, así que va a ir a otra máquina para usos no críticos.

Sobre el tema disco: alguien puede recomendar marca/negocio para comprarlo en capital o zona norte? Por lo que estuve viendo en Mercadolibre, el precio por giga mas o menos se mantiene en todos los discos grandes... estaba acostumbrado a que cuanto mas grande mas barato.

(moderadores: si les parece que ese pedido es desubicado, los invito a censurarlo)

---

### Post by felipelerena on 2007-01-21
Galeria Jardin????

---

### Post by Hex_Mandos on 2007-01-21
En general, es mi lugar de referencia, pero estaría bueno tener el nombre de un local confiable (en galerías jardín o cualquier otro lugar). Digo porque esta máquina la compré allá, después de varias semanas comparando precios y lugares... y me salió como el culo. No se si hay algo mas allá de mother y micro que no haya tenido que tocar por causas no provocadas (por ejemplo, el disco... dio un error así hace un par de años, y lo compré con la máquina en 2003).

---

### Post by felipelerena on 2007-01-21
ja, dijiste confiable y galeria jardin...

datasoft a mi siempre me trato bien y nunca tuve problemas.

igual no hay mucho que comparar en la jardin, los precios son todos mas o menos iguales entodos lados

---

