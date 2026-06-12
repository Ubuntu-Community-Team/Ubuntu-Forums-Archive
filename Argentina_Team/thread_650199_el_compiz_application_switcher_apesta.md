---
title: "el compiz application switcher apesta"
date: 2007-12-26
forum: Argentina Team
---

### Post by Skavenger on 2007-12-26
gente, no se uds pero a mi me rompe demasiado las pelotas el 'alt+tab' de compiz, es lento y molesto, si quisiera ver iconitos locos y previews usaria algun otro plugin, en fin... alguien sabe como desactivarlo y usar alguno al estilo windows? o el q tiene metacity, quiero algo bien simple

si desactivo ese plugin en el compiz settings manager, directamente deja de funcionar el alt+tab y tampoco quiero usarlo con velocidad 9999, sin opacidad ni nada de eso, QUIERO EL ALT+TAB CLASICO !! XD

gracias!

---

### Post by User21 on 2007-12-26
Desactivalo desde las opciones de compiz, y si no lo tenes instalado, pues :
```
 sudo apt-get install compizconfig-settings-manager
```
En el menu apariencia aparece un nuevo boton donde podras configurar TODO COMPIZ a tu conveniencia y desde alli, destilda la opcion de APPLICATION SWITCHER creo, para tener el original... o configuralo a gusto de modo que no sea lenta, ni transparente, etc...

Suerteee!

---

### Post by Skavenger on 2007-12-26
creo que no leiste todo mi post anteior... si desactivo esa opcion en el settings manager, me quedo sin alt+tab

---

### Post by Thalskarth on 2007-12-26
> **Skavenger said:**
> creo que no leiste todo mi post anteior... si desactivo esa opcion en el settings manager, me quedo sin alt+tab

Podes desactivarlo. Y luego, le asignas la convinacion de teclas "alt+tab" a otro que te paresca más comodo o te guste más. Por ejemplo, en una epoca yo lo usaba con el "ring swicher"

---

### Post by newtonfn on 2007-12-30
> **Skavenger said:**
> creo que no leíste todo mi post anterior... si desactivo esa opción en el settings manager, me quedo sin alt+tab

Tal vez me equivoque, pero creo que Compiz es un window manager al igual que lo es Metacity, por lo que cuando activas compiz estas desactivando metacity.
Así mismo, una de las funciones del window manager es precisamente el permitir el cambio de ventas con alt-tab o las teclas que tengas definidas a tal efecto

Por lo tanto, si tenes Compiz activado, y desactivas todos los plugins que pueden hacer una función similar a la del task-switcher te quedas sin esa funcionalidad ya que metacity no la puede hacer, por no ser el window manager activado.

En mi experiencia particular, algunos efectos de compiz pueden ser bastante lentos en mi pc que ya tiene sus añitos, pero afortunadamente no es el caso del task-switcher ni ningun otro importante (los lentos son el que simula gotas de agua, o la escritura con fuego sin los cuales puedo seguir viviendo)
Cuando probé Compiz en una pc aún más vieja que la mia, andaba realmente mal todo compiz, no solo el task-switcher, por lo que lo desactivé y listo.

O sea, si queres velocidad y no "fancy effects" desactiv Compiz y quédate con metacity. (o algun otro window manager que se ajuste mejor a tus necesidades)

---

