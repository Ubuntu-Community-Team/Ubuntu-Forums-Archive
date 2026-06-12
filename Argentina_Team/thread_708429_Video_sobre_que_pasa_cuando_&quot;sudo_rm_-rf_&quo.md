---
title: "Video sobre que pasa cuando &quot;sudo rm -rf /&quot; es ejecutado"
date: 2008-02-26
forum: Argentina Team
---

### Post by faktorqm on 2008-02-26
Hola, encontre este video en la web y queria compartirlo con ustedes.

[http://ubuntuarte.com/wordpress/?p=146#more-146](http://ubuntuarte.com/wordpress/?p=146#more-146)

es sobre que pasa cuando ejecutas "sudo rm -rf /" en un gnu/linux, aunke tambien sirve para mac. 

mataca: te diste cuenta que el error que se genera en todos lados es parecido al tuyo con el open office?
Espero que les haya gustado y opinen sobre esto. Salu2!!

---

### Post by Mafber on 2008-02-26
jajajaja fanatastico!!!! :)
lo unico que le faltó fue una cuenta regresiva y un cartel que diga "su sistema se destruirá en 3...2...1"

Aparte de romper el sistema ¿hace algun daño al hard? ¿se soluciona solo con reinstalar ubuntu? 
aclaro que no planteo hacérselo a alguien... algún día que tenga que reinstalar todo, me gustaría verlo en directo

---

### Post by santiagoward2000 on 2008-02-26
El gatito sobrevivió!!! :D
Buenísimo el video! Lo puse en mi firma!

> **Mafber said:**
> Aparte de romper el sistema ¿hace algun daño al hard? ¿se soluciona solo con reinstalar ubuntu?

Supongo que si se soluciona reinstalando (aunque no lo probe). Lo que hace ese comando es borrar todos los archivos en tu disco. Supongo que si tenés una partición de Windows o algún otro disco (como un pendrive) montados los borra también, ya que le dice que borre todo lo que esté en "/" y recursivo (o sea todas la carpetas y archivos adentro). Como los discos van a "/media/", me imagino que los borra también. Si lo hacés algún día para probar, fijate que no tengas nada importante montado.
La verdad que no estoy con muchas ganas de probarlo ahora :)

---

### Post by Mauro22 on 2008-02-26
Jjee, que grosos, 


Aun sin sistema, Linux sigue siendo estable, con errores, pero no se colgo ni reinició ni taró...


Re loco ese comando...

---

### Post by Mataca on 2008-02-28
> **faktorqm said:**
> mataca: te diste cuenta que el error que se genera en todos lados es parecido al tuyo con el open office?

:confused:Sipp es exactamente lo mismo que habia pasado con el OO. no se que habra pasado pero estoy seguro de no haber ejecutado ese comando. En fin, nada es perfecto no?

---

### Post by aregnando on 2008-02-28
Hola Faktorqm, fijate que al principio del foro hay un encabezado en celeste que habla sobre eso mismo.

[http://ubuntuforums.org/announcement.php?f=189](http://ubuntuforums.org/announcement.php?f=189)

Aparentemente ese comando es altamente perjudicial para el sistema y por lo que se ve puede venir disfrazado en diferentes formas por lo que aconsejan tener mucha precaución sobre los comandos que se introducen en consola.

Saludos.

---

### Post by faktorqm on 2008-02-28
Si ya lo lei, no estoy de acuerdo con la parte del "peligroso". para vos: un cuchillo es peligroso? y un destornillador? y un alicate? y un martillo? y un monitor? un monitor es peligroso si te lo tiro por la cabeza, o te punzo con un destornillador o un cuchillo, o te golpeo la nuca con un martillo. En manos de un cheff un cuchillo no es peligroso, en manos de un tecnico/ingeniero en electronica un monitor no es peligroso. Espero que hayas entendido la idea. Si tenes dudas sobre un script, o no lo instalas, o aprendes a programar en bash y listo! :D Salu2! (no t ofendas eh!)

---

### Post by leo_rockway on 2008-02-28
100% de acuerdo con faktorqm. Cuando salio la advertencia sobre rm -rf yo cree un thread que decia mas o menos lo mismo... rm -rf es un comando muy util!

---

### Post by aregnando on 2008-02-28
Disculpen si ofendí a alguien, en mi caso no soy programador solo soy un usuario común tratando de aprender lo más posible del mundo de linux, igualmente creo que en ningún caso puse peligroso sino perjudicial que no es lo mismo, explico el porque, como dije antes en mi caso que soy neofito total llegado el caso de que por error de interpretación pudiera ingresar ese comando sería perjudicial para mi máquina ya que la misma la comparto con mi familia y destruiría datos incluso creo yo en la partición en la que tengo Win.
No quiero polemizar, sobre todo con personas que me han ayudado con muy buena onda, pero supuse que las discusiones estaban abiertas a todo tipo de opinión.
Saludos.

---

### Post by faktorqm on 2008-02-28
no, no, tranquilo, no ofendes a nadie, siempre estamos abiertos a discutir cosas con coherencia y que valgan la pena.
Tenes razon pusiste perjudicial, lei cualquier cosa. (pasa en las mejores familias jajajaj)
De todas maneras no esta mal la aclaracion para aquellos lectores que donde dice "perjudicial" lean "peligroso". (jaja el chabon la quiere arreglar como sea para no decir que posteo al **** jaja)
Salu2!

---

### Post by pante on 2008-02-28
No va con mala onda:;)

Justamente el anuncio sobre el rm... está ahí porque no todos sabíamos lo perjudicial que puede ser, ni que puede tomar formas insospechadas. Nadie nace sabiendo, ni todos tenemos tiempo (o ganas) para dedicarnos a estudiar en profundidad nuestro sistema operativo preferido. 

Hace muy poco lo dijo Linus Torvalds: "el sistema operativo debe ser invisible al usuario".

Perdonen(nos) a los no-expertos.

Saludos :-)

---

