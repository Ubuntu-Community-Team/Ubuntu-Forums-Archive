---
title: "Error de gDesklets"
date: 2008-04-26
forum: Argentina Team
---

### Post by madelaki on 2008-04-26
Descargue e instale gdesklets y gdesklets data desde el gestor de paquetes synaptic sin ningun problema, pero cuando lo abro en la terminal pasa esto.

> Iniciando el servidor gdesklets…
Conectando al servidor [      ###    ]
==========================================================[04/27/08-00:24:42]===
Registering new control "/usr/lib/gdesklets/../../share/gdesklets/Controls/IMPC".


Conectando al servidor [        ###  ]
==========================================================[04/27/08-00:24:42]===
Registering new control "/usr/lib/gdesklets/../../share/gdesklets/Controls/SideCandySytadin".


Conectando al servidor [         ### ]
==========================================================[04/27/08-00:24:42]===
Registering new control "/usr/lib/gdesklets/../../share/gdesklets/Controls/Popmail".


Conectando al servidor [     ###     ]
==========================================================[04/27/08-00:24:43]===
Registering new control "/usr/lib/gdesklets/../../share/gdesklets/Controls/Boxmail".


Conectando al servidor [   ###       ]
==========================================================[04/27/08-00:24:43]===
Registering new control "/usr/lib/gdesklets/../../share/gdesklets/Controls/Countdown2".


Conectando al servidor [ ###         ]
==========================================================[04/27/08-00:24:43]===
Registering new control "/usr/lib/gdesklets/../../share/gdesklets/Controls/IExec".


Conectando al servidor [   ###       ]
==========================================================[04/27/08-00:24:44]===
Registering new control "/usr/lib/gdesklets/../../share/gdesklets/Controls/RBox".


Conectando al servidor [     ###     ]
==========================================================[04/27/08-00:24:44]===
Registering new control "/usr/lib/gdesklets/../../share/gdesklets/Controls/NewsGrab".


Conectando al servidor [       ###   ]
==========================================================[04/27/08-00:24:44]===
Registering new control "/usr/lib/gdesklets/../../share/gdesklets/Controls/YahooWeather".


Se conectó con el servidor en 3029 milisegundos.

==========================================================[04/27/08-00:24:44]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/bin/gdesklets: line 393 <module>
in /usr/bin/gdesklets: line 268 parse_command
in /usr/bin/gdesklets: line 177 __open_profile
in /usr/bin/gdesklets: line 167 __client_daemon
in /usr/lib/gdesklets/main/client.py: line 208 set_remove_command
in /usr/lib/gdesklets/main/client.py: line 38 __send
in /usr/lib/gdesklets/utils/xdr.py: line 75 recv
[EXC]/usr/lib/gdesklets/utils/xdr.py

[---]   70     chunk = ""
[---]   71     while (True):
[---]   72         try:
[---]   73             length = ord(s.recv(1))
[---]   74         except:
[ERR]>  75             raise XDRError
[---]   76 
[---]   77         if (length): chunk += s.recv(length)
[---]   78 
[---]   79         flag = s.recv(1)
[---]   80         if (flag == _CONT): continue
[---]   81 




---

### Post by Apokalyptica79 on 2008-04-27
Hola madelaki, aca encontré un enlace a ver si te sirve:
[http://www.ubuntu-es.org/index.php?q=node/35673]("http://www.ubuntu-es.org/index.php?q=node/35673")
Saludos

---

### Post by madelaki on 2008-04-27
Gracias pero son dos errores diferentes.

---

