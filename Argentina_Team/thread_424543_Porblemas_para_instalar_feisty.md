---
title: "Porblemas para instalar feisty"
date: 2007-04-26
forum: Argentina Team
---

### Post by atari130xe on 2007-04-26
Le envi a un amigo en la plata un cd de ubuntu feisty final, compro una pc nueva con rxart y quiere instalar ubuntu tmb, pero sigue el procedimiento de instalacion y al llegar al 15 % de la instalacion se le cuelga la pc y nada. alguien tiene idea del motivo?

---

### Post by beuno on 2007-04-26
¿Tiene 256 de ram o mas?
En ese caso necesita la version "alternate" para instalarlo (aunque recomiento xubuntu si tiene menos de 256).
Ojo que quizas tiene 256mb de ram pero video onboard que le saca ram tambien.

---

### Post by valucha on 2007-04-26
[COLOR="DarkOrchid"]A mi me pasaba eso... yo tengo 256 de ram y cuando instalaba edgy andaba todo perfecto.
Pero con feisty (kubuntu y ubuntu) no pasaba del 15% inicial, que encima, es un 15% "mentiroso" proque todos sabemos que va hasta el 15% cuando dice "analizando particiones" (o algo asi) y después vuelve al 7% por ahi y empieza a cargar.
Lo resolví instalandolo desde el alternate.
Anda todo perfecto, es igual que instalarlo con el Live CD, solo que no tenés el Live.
[/COLOR]

---

### Post by lugonesjoaquin on 2007-04-26
Que lastima que tan buena distro se llene de errores...

Yo siempre culpo esto a que Ubuntu lanza tantas versiones en tan poco tiempo. 6 meses es muyyyyyy poco tiempo para arreglar errores. MINIMO un año.. Y esto se ve claramente, desde Edgy que las instalaciones viven fallando, cosas que pasan remotamente con otras distribuciones...

---

### Post by atari130xe on 2007-04-27
Muchas gracias por sus respuestas. Yo creo que es un garrón que pase esto, simplemente porque mi amigo es totalmente nuevo en esto y la impresión que puede llevarse no es la mejor, me refiero a que yo que vengo usando Ubuntu desde hace 1 año y me gusta la informática me puede ***** que pase algo así, pero a su vez es un desafio porque intento buscar la solucion, pero a alguien que solo quiere saber lo básico y partir de cero es un poco atemorizante. Yo me pregunto porque pasan esas cosas cuando por todas partes dicen que lo mínimo recomendable son 256MB y no 512 o cosas así. particularmente me pasó con algunas distros Live que funcionaban perfectamente en mi pc, de 10, pero al instalarlas era todo un desastre por alguna razón había cosas que no funcionaban (montar particiones, sonido etc). Yo vivo en bariloche y el en La Plata, se imaginan que yo no tengo forma de ir a su casa a ver que pasa, se me hace muy complejo, solo me llamaba al celu a cada rato diciendo "se me colgó al llegar al 15 %, que hagooooo!", como le instala el grub obviamente le inutiliza su pc porque no puede ingresar a Rxart, o sea no entiende mucho de compus por ende aunque haya formas alternativas es un garrón. Esa PC se la compró con Linux pero le hablé de Ubuntu y le mandé un cd chequeado por mi en perfectas conidciones, ahora imagino que le voy a enviar el alternate a ver que pasa, porque necesita su PC. Yo tengo una maquina bastante vieja K7 Athlon 600Mhz con 256MB de ram, alguien me puede explicar porque en mi pc funciona bien y en la suya (pentium IV 3.2MHz 256MB Ram no?, en fin misterios de la informática.
graciassss!

---

### Post by beuno on 2007-04-27
> **lugonesjoaquin said:**
> Que lastima que tan buena distro se llene de errores...

Yo siempre culpo esto a que Ubuntu lanza tantas versiones en tan poco tiempo. 6 meses es muyyyyyy poco tiempo para arreglar errores. MINIMO un año.. Y esto se ve claramente, desde Edgy que las instalaciones viven fallando, cosas que pasan remotamente con otras distribuciones...

Esto no es un *error*, esto es una falta de recursos, nada mas.
Se hacen releases estables cada 2 años aproximadamente, los otros en medio se podria decir que son "betas".

---

### Post by atari130xe on 2007-04-27
amigo beuno, una pregunta: falta de recursos???? perdon leiste lo último que postee? MI pc tiene 256Mb de ram tiene mas 7 años de antiguedad y corre, bien, no un avion, pero funciona, mi amigo tiene un procesador superior y la misma cantidad de memoria ram y NO le funciona, si hablamos de recursos no deberian ser los mismos para que algo funcione bien? hoy me decia que quedo decepcionado con Ubuntu y yo que me la pasé diciendole que es bárbaro, en fin no pretendo polemizar, me encanta Ubuntu, pero creo que alguien deberia saber que hacer en estos casos, compus de última generacion con los mismos recursos, en las cuales Ubuntu no funciona y compus viejas con recursos similares donde  si funciona. para pensarlo.
gracias por la onda!

---

### Post by sebas.rhcp on 2007-04-27
Un Pentium 4 3.2ghz es poco comun que tenga 256MB de ram, igual es cualquiera que no le ande. Creo que van a tener que parar la moto porque 6 meses no son suficientes.

PD: Parece que esa PC tiene video on-board no? en ese caso NO tiene 256MB de ram

---

### Post by Tinchio on 2007-04-27
Como dijo Beuno estas versiones cada seis meses se podrian decir que son algo "experimentales" si bien funcionan muy bien en la mayoria de los casos pueden tener muchos bugs, si quieren algo mas estable para eso estan las versiones LTS como por ejemplo Dapper, nadie nos olbiga a actualizarnos a feisty. Igual creo que es cuestion de  tiempo, creo que son los releases futuros muchas de estas cuestiones se van  a ir solucionando, cuestion de tiempo y experiencia.

---

### Post by godzeus on 2007-04-29
> **sebas.rhcp said:**
> Un Pentium 4 3.2ghz es poco comun que tenga 256MB de ram, igual es cualquiera que no le ande. Creo que van a tener que parar la moto porque 6 meses no son suficientes.

PD: Parece que esa PC tiene video on-board no? en ese caso NO tiene 256MB de ram
Creo que sebas.rhcp tiene razon, con un P4 y con solo 256MB de ram, me parece muy raro, par aesa maquina minimo 512. OJO no sea cosa que tenga los 512MB pero tenga una placa de video on-board que le esta sacando la mitad. O solo tiene 256MB y la placa onboard le saca minimo 64MB y te quedas cortisimo, porque no le decis que te especifique bien cuanta memoria tiene cuando arranca la maquina( EN EL BOOTEO) y si tiene placa de video aparte o es onboard.
Para hacerlo mas facil, que te diga donde la compro, si fue en Garbarino, Fravega, Compumundo o alguna casa de electrodomesticos, no tiene placa grafica.
Cualquier cosa postea de nuevo.

PD: yo le recomendaria Xubuntu.

Saludos.:)

---

### Post by atari130xe on 2007-04-29
Es simple la compró en Compumundo o sea no tiene placa grafica, a buscar una entonces. gracias!

---

### Post by sebas.rhcp on 2007-04-29
Uh entonces le salio bastante por lo que realmente vale :(

---

