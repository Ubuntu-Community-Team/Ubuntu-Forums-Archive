---
title: "Consulta sobre directorio TMP y pendrive (7.10)"
date: 2008-01-05
forum: Argentina Team
---

### Post by matlnx on 2008-01-05
Buenas tardes, queria consultarles por algo extraño que me paso para ver que les parece:

1ro) el otro dia me dieron un pendrive que puse en mi Ubuntu, tenia unas fotos, asi que las borre y me dispuse a grabar en el. Cuando lo conecto en un windows me aparecieron unos archivos medios raros con unas extensiones que el ubuntu no habia visto.

Consulta: Puede ser que sean archivos guardados por el ubuntu para determinada cosa??? no recuerdo los nombres, pero eran nombres raros como ser .nombre_del_archivo

2do) a Raiz de ver los archivos esos me entro la duda asi que fui a mi casa que tengo Ubuntu (7.10 tambien) y vi que en el TMP habian unos archivos como mi username.
Puntualmente me llamo la atención uno que decia Tracker-username.5426 (en donde dice username estaba el mio).

Puede ser que mi pc este infectada?? al igual me aparecion un paquete init.d que nunca habia visto, y un par de archivos mas con mi usuario. Es esto normal en Ubuntu???

Vale aclarar que los borre, reinicio y aparecen de nuevo salvo el tracker famoso.

Desde ya muchas gracias.
MatLnx

---

### Post by srmantis on 2008-01-05
No te asustes, esos archivos son parte de ubuntu.

Para el pendrive ubuntu crea un archivo oculto que sirve de papelera, su nombre es:
.trash-username (donde username corresponde a tu nombre de usuario)
Todos los archivos que empiezan con un punto estan ocultos en ubuntu.

Si buscas encontraras muchos archivos que llevan tu nombre de usuario y si creas mas usuarios apareceran archivos con esos nuevos nombres.

Relajate :)

---

### Post by newtonfn on 2008-01-05
Hasta donde se el directorio /tmp contiene archivos temporales que crean las aplciaciones cuando lo necesitan. Seria el equivalente LInux a TEMP de Windows.

Por ejemplo, yo en mi directorio Temp tengo, entre otros, los siguientes directorios
virtual-fernando.3aycE7, Tracker-fernando.6188, gconfd-fernando y alugnos archivos como y9BscA

Como verás, además que mi nombre de usuario es Fernando, también tengo el archivo Tracker (realmente es un directorio). Si no me equivoco este es creado, precisamente por un programa de indexación de archivos (Tracker Search Tool segun figura en el menú)

Sobre los archivos raros en el Pen, ahi si no se que decirte, el único archivo raro que he visto que se crea cuando borro algo en un pen, es el directorio .Trash que es donde estan los archivos de la "papelera de reciclaje"

Primero me aseguraría que el problema del Pen no haya sido que lo sacaste sin desmontarlo, o algo por el estilo que genero esos archivos.

Por ahora, no me preocuparía por virus, hace más de un año que estoy usando ubuntu sin antivirus y lo ultimos tiempos sin firewall siquiera, y no he tenido el más mínimo problema. (Aún hay muy pocos virus aputnados a Linux, y los virus de Windows no pueden afectar a este sistema operativo)

Igualmente, es una buena práctica y te lo recomiendo, que tengas siempre un Firewall y un antivirus.

Como firewall lo mejor, para mi, es tener un lindo router. El router mismo, por su naturaleza es un buen firewall y además todos (al menos que yo conozco) traen funciones de firewall para bloquear puertos y demás.

Si no tienes, puedes usar un firewall por software, linux trae en su kernel algo llamado IPTABLES, que hace las veces de firewall entre otras cosas, si se lo configura a tal efecto, para configurarlo te aconsejo usar un programa lllamado firestarter. (se encuentra en los repositorios)

Con respecto a antivirus, nunca usé ninguno en linux asi que no sabría cual aconsejarte. Lo unico que usé es el clam-av como antivirus para un servidor de emails, supongo que puede hacer también las veces como antivirus de escritorio, pero no lo se.

---

