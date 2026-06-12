---
title: "Convertir correo de Outlook (Exchange) a KMail"
date: 2007-12-15
forum: Argentina Team
---

### Post by Hei Ku on 2007-12-15
Buenas, les cuento que tengo un problema cuando quiero convertir del correo de Outlook a KMail. Lo principal es que es el correo de mi novia, asi que en esta me va la vida. :D

Estoy siguiendo el procedimiento recomendado en estos casos, que es convertir primero con Thunderbird en Windows. Luego en Linux, desde KMail importar el correo desde Thunderbird.

Hasta ahi, todo lindo y bonito. Pero no convierte bien los mensajes cuando fueron enviados por smtp. O sea, todos los mensajes que ella envio solo por Exchange, estan barbaros. Pero los mensajes en formato HTML que intercambio con gente fuera de su empresa, no los convierte bien.

El KMail los reconoce como mensajes NO HTML, y entonces se ve el mensaje lleno de tags, y casi incomprensible, y como tampoco reconoce los headers, no aparece ni la fecha de envío ni el destinatario, nada.

Alguno tiene experiencia convirtiendo estos mensajes?

---

### Post by Hei Ku on 2007-12-17
Alguna idea?

---

### Post by marianom on 2007-12-17
Ninguna pero me da cosa que te quedes colgado.
Pregunta: en TB cuando los pasas a Ubuntu, se ven bien? Solo para confirmar que no es ruido generado por los firmes standares abiertos del Outlook.

---

### Post by faktorqm on 2007-12-18
Evidentemente ahi hay un problema de M$ que anda dando vueltas. Capaz el tipo te deja embeber un html dentro del texto, despues total lo interpreta y lo muestra. Capaz Kmail no te esta dando esa opcion y terminas en un problema de compatibilidad cuando migras.
Lo unico que se me ocurre es, si esta pasando esto, que conviertas desde outlook con alguna opcion rara o bien, para outlook express 95 :P bien basico y despues lo pases, o todo a texto plano, o me parece que habia una opcion por ahi que todas las fotos y las cosas que no sean texto te las tome como adjunto. Revisa esto ultimo, me parece que habia algo de eso. Y sino es mucho lio hacer un select all-> enviar a una cuenta vacia con kmail? :P o a la misma para el caso... salu2!

EDITO: viste esto? [http://kontact.kde.org/kmail/tools.php](http://kontact.kde.org/kmail/tools.php)
y esto? [http://www.softwareinreview.com/cms/content/view/29/](http://www.softwareinreview.com/cms/content/view/29/)
y esto: [http://www.linuxquestions.org/questions/linux-software-2/outlook.pst-in-kmail-336786/](http://www.linuxquestions.org/questions/linux-software-2/outlook.pst-in-kmail-336786/)

Fijate en el ultimo, que tira una re buena idea, te dice de irte a windows, instalar thunderbird, migrar de outlook a thunderbird, despues agarrar esa base, irte a un un linux, y migrarla desde ahi. 
Igual el chabon dijo que se tira por evolution, por que kmail te muestra mal el html. (te aviso por las dudas, que esto es mentira, como algunos codigos html comprometen la seguridad de tu sistema, algunos tags estan bloqueados en kmail, leer al respecto antes de decir alguna barbaridad... por favor! :D)
Espero que te haya servido. salu2!!

---

### Post by Hei Ku on 2007-12-18
Lo que hice fue justamente el consejo que dan en Kmail, que es migrar primero todo a thunderbird, y de ahi usar la herramienta de importacion de kmail (kmailcvt) para migrarlos desde thunderbird.

En cuanto a lo de los tags de html, es cierto. Kmail los maneja bien, salvo cuando son mensajes de Exchange externos. Supongo que serian MIME con HTML. Obviamente otro tema de los standards abiertos de M$, porque no tengo problemas con ningun otro.

Les cuento bien como es la cosa:
- En la maquina de windows instale thunderbird.
- Migre desde Outlook a Thunderbird usando la opcion de importacion
- Copie la carpeta Mail de Thunderbird a Linux por ssh
- En Kubuntu, use la opcion de importacion de KMail (kmailcvt) para importar las carpetas de Thunderbird

Resultado:
- todos los mensajes de Exchange internos se ven bien
- los mensajes de internet en formato html, KMail los reconoce como NO HTML y me los tira como texto plano (sin remitente, sin fecha de envio, y con los tags de html en el texto, ilegibles, bah)

La frustracion es que la información esta ahi, pero hay algo en los mensajes que kmail no digiere y entonces no los reconoce como html.

Desde ya, gracias por cualquier ayuda que me puedan dar.

Se me habia ocurrido usar el html2text, y tratar de importar los mensajes en texto plano a kmail, pero no se como hacerlo.

---

### Post by marianom on 2007-12-19
¿Tenés alguna pista de cual es el código basura que impide que se lean correctamente?
Por ahí podemos escribir un mínimo script que arregle el error.
Si da, busca un mensaje lo menos comprometedor posible (o inventá uno solo reemplazando las palabras) y pegalo aca así lo vemos e intentamos descubrir que lo hace ilegible.

Una cosa porque no estoy seguro que haya quedado respondido: en TB en linux, esos mensajes se ven bien?

---

### Post by Hei Ku on 2007-12-19
En TB en linux no pude probar, porque aparentemente algun archivo me falta y no me toma bien la carpeta. En cuanto tenga de vuelta la maquina con linux vuelvo a hacer la importacion de archivos para que me lo tome bien. A la tarde busco un mensaje y lo pego aca, a ver q puede ser el problema.

---

### Post by Hei Ku on 2007-12-22
Finalmente pude hacer la prueba en TB, y es ahi donde esta el problema. O sea, Thunderbird no maneja bien la conversion de los mensajes HTML de Outlook. Para el momento que los paso a KMail ya no hay nada que hacer.

Lo que estoy haciendo ahora es pasarlos a traves del IMAP de Gmail, que los toma bien. Si bien el proceso fue mas lento, hasta ahora viene saliendo joya.

---

