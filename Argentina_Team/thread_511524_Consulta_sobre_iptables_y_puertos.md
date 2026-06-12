---
title: "Consulta sobre iptables y puertos"
date: 2007-07-27
forum: Argentina Team
---

### Post by tony_feisty on 2007-07-27
Buenas a todos, tengo dos preguntas:

1) Algun buen manual sobre como configurar iptables, porque lo que descargue es muy general y no consigo ninguno con buenos ejemplos.

2) Que puertos son usados para navegar (ej. Firefox) y para mensajeria tipo el Kopete.

Un abrazo y saludos a todos. Gracias.

---

### Post by jpmorelli on 2007-07-28
Nunca me puse a mirar mucho sobre iptables aunque buscando por google no creo que te falten opciones para encontrar alguno que te sirva a lo que buscas exactamente,
Si querés podés empezar instalando el programa firestarter que no es más que una interfaz gráfica para iptables ( aunque obviamente mucho más limitado que laburar directamente por consola en las reglas, aparte de que uno se "achancha" y aprende más, sobre todo para esos servers que no tienen interfaz gráfica ya que así consumen muchos menos recursos y son más rápidos )
Con respecto a los puertos, firefox es solo la ventana que abre diferentes servicios según lo que estés utilizando, por ej. generalmente la navegación http se hace por el puerto 80, la https se hace por el 443, el ftp se hace por el 21, y así podríamos seguir por los 65535 puertos de comunicación de una máquina.

---

### Post by tony_feisty on 2007-07-28
Listo, gracias por la info.

Saludos.

---

