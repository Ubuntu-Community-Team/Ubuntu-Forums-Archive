---
title: "Cantidad de entradas en &quot;Documentos Recientes&quot;"
date: 2008-04-10
forum: Argentina Team
---

### Post by margori on 2008-04-10
Estimados amigos:

He buscado por todos lados sin poder lograrlo. Estoy intentando aumentar la cantidad de entradas que figuran en la lista de Docuemtnos recientes de la barra de gnome (Lugares->Documentos recientes) pero no se como.

Si alguien sabe como hacerlo, le estaría muy agradecido.

---

### Post by MeduZa on 2008-04-10
> **margori said:**
> Estimados amigos:

He buscado por todos lados sin poder lograrlo. Estoy intentando aumentar la cantidad de entradas que figuran en la lista de Docuemtnos recientes de la barra de gnome (Lugares->Documentos recientes) pero no se como.

Si alguien sabe como hacerlo, le estaría muy agradecido.

eso debe estar seguro en el editor de gnome ( gconf-editor ) lo que no se es donde ni como se llama

---

### Post by spg76 on 2008-04-10
Yo estuve investigando un poco y, según varios posts, no se puede cambiar porque  al parecer ese parametro está "Hard-coded" (o como dice [Wikipedia]("http://es.wikipedia.org/wiki/Hard_code"), "incrustado directamente") en el código de GNOME y no se puede modificar desde ningún archivo de configuración.

---

### Post by margori on 2008-04-11
Realemente me he quedado sin palabras. Para mi era impensado que ese numero estuviera "hardcodeado".

Realmente para mi la lista es corta, asi que me pondre en campaña para ver si puedo modificar el codigo. Quien sabe capaz que le encuentro la vuelta.

Gracias igual.

---

### Post by MeduZa on 2008-04-12
mm realmente me parece que es algo que o bien esta asi temporalmente o bien metieron la pata, no es normal en los que programan en hardcodear variables 
muy raro, de todas maneras se puede editar el fuente y recompilar.

---

### Post by Hei Ku on 2008-04-12
> **MeduZa said:**
> mm realmente me parece que es algo que o bien esta asi temporalmente o bien metieron la pata, no es normal en los que programan en hardcodear variables 
muy raro, de todas maneras se puede editar el fuente y recompilar.

No sé qué programadores conoces vos, pero esa pesima práctica de hardcodear es una de las más extendidas. Basicamente, porque las configuraciones y parametros llevan mas tiempo (al principio), y cuando haces algo para salir del paso es mas rapido hardcodearlo, y ya sabemos como todo lo temporario se transforma en permanente, justamente por el... paso del tiempo :lolflag:

Me sorprende que no exista un lugar para cambiar la configuracion, pero por otro lado Gnome es famoso por su tendencia a quitar configuraciones por miedo de confundir al usuario. Espero realmente que este no sea el caso.

---

### Post by MeduZa on 2008-04-12
> **Hei Ku said:**
> No sé qué programadores conoces vos, pero esa pesima práctica de hardcodear es una de las más extendidas. Basicamente, porque las configuraciones y parametros llevan mas tiempo (al principio), y cuando haces algo para salir del paso es mas rapido hardcodearlo, y ya sabemos como todo lo temporario se transforma en permanente, justamente por el... paso del tiempo :lolflag:

Me sorprende que no exista un lugar para cambiar la configuracion, pero por otro lado Gnome es famoso por su tendencia a quitar configuraciones por miedo de confundir al usuario. Espero realmente que este no sea el caso.

solo me base en que todo aca tiene archivos conf realmente extendidoen variables, y en que yo trato (pero como dijiste vos a veces el tiempo gana) de hacerlo con variables asignadas desde un conf

---

