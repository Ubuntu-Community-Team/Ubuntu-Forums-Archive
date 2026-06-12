---
title: "Screenlet Temperature2"
date: 2007-10-23
forum: Argentina Team
---

### Post by santiagoward2000 on 2007-10-23
Hola gente!
Recién instalé Screenlets, y traté de agregar algunos. Casi todo bien!
Pero cuando agregué el screenlet Temperature2 y lo corrí, me tiró este error:
```
Launch Temperature2
Launching Screenlet from: /home/santi/.screenlets/Temperature2/Temperature2Screenlet.py
Logging output goes to: $HOME/.config/Screenlets/Temperature2Screenlet.log
REGISTER screenlet: Temperature2Screenlet
Traceback (most recent call last):
  File "/home/santi/.screenlets/Temperature2/Temperature2Screenlet.py", line 251, in <module>
    screenlets.session.create_session(Temperature2Screenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 392, in create_session
    session.start()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 186, in start
    sl = self.screenlet(session=self, id=self.__get_next_id())
  File "/home/santi/.screenlets/Temperature2/Temperature2Screenlet.py", line 68, in __init__
    self.__hddtemp = self.get_hddtemp_data()
  File "/home/santi/.screenlets/Temperature2/Temperature2Screenlet.py", line 126, in get_hddtemp_data
    s.connect(('localhost', 7634))
  File "<string>", line 1, in connect
socket.error: (111, 'Connection refused')
```

Alguien sabe cómo hacerlo andar?

---

### Post by santiagoward2000 on 2007-10-24
Hola gente!
Bueno, les cuento que para probar, instalé el Screenlet Temperature viejo (parte de Updated old 3rd party Screenlets). Y este anda sin problema. No puedo ver la temperatura de mi disco, pero bueno, lo que yo quería era ver la de mi CPU.
Igual, me gustaría si alguien me puede explicar el problema con Temperature2.
Saludos!

---

### Post by marianom on 2007-10-25
Solo leyendo el trace que posteás parece fallar porque algun proceso le niega la posibilidad al programa de conectarse para obtener la información.

Habría que ver que significa el segundo miembro de esa tupla que se pasa con s.connect. ¿Un puerto? ¿en ese caso es posible que el puerto esté protegido? Así nomás es imposible saberlo.

Fijate que tiene que haber un archivo: $HOME/.config/Screenlets/Temperature2Screenlet.log

Si existe (debería), comprimilo y así, my prolijito, subilo al foro así le podemos echar un ojo los pythonistas entusiastas. Si es muy grande, sería mejor por ahi pegarlo en un pastebin y pasar la dirección correspondiente para que lo analicemos.

---

### Post by santiagoward2000 on 2007-10-25
Hola marianom,
Acá va el archivo. Pesa unos 255B, supongo que no hay problema de postearlo acá.
Gracias

---

### Post by marianom on 2007-10-25
Seis líneas que supongo que solo son informativas para el desarrollador porque lo es este problema, no aporta nada.

Si hago tiempo en estos días me bajo la aplicación y le echo un ojo al código a ver que saco en limpio.

---

### Post by santiagoward2000 on 2007-10-25
Bueno gracias!
Igual no te preocupes si es mucho trabajo. La versión vieja me anda lo más bien y hace lo que quiero...

---

