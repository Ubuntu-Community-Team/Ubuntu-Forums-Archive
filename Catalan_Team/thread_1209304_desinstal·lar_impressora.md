---
title: "desinstal·lar impressora"
date: 2009-07-10
forum: Catalan Team
---

### Post by muleta on 2009-07-10
Si us plau, quina és l'ordre exacta per a desinstal·lar una impressora?.

---

### Post by SiscoGarcia on 2009-07-10
No sé quin sabor d'ubuntu fas servir, en el cas de gnome només has d'anar a Sistema>Administració<Impressió i allà triar la impressora que vols desintal·lar i prémer la tecla "suprimir".

---

### Post by akyra on 2009-07-10
Podries anar a:
[http://localhost:631]("http://localhost:631")

Entraràs a una aplicació en entorn web que podràs administrar de forma gràfica les impresores.

Has de tenir instalar el cups i al cupssys (em sembla que no et fa falta res més).

Si et demanés alguna contrasenya, seria la de root.

Salutacions

---

### Post by muleta on 2009-07-10
> **SiscoGarcia said:**
> No sé quin sabor d'ubuntu fas servir, en el cas de gnome només has d'anar a Sistema>Administració<Impressió i allà triar la impressora que vols desintal·lar i prémer la tecla "suprimir".

No, tinc kde i és força més complicat perquè no m'ho deixa fer de forma gràfica. Em diu que no tinc privilegis.

Ho he probat per terminal amb l'ordre que em dona el menú K i em diu:

> ~$ sudo sh /opt/Samsung/mfp/uninstall/uninstall.sh
Cannot mix incompatible Qt libraries
Aborted

És una Samsung CLX-3170FN. Algú sap què he fet malament?. 

Això que m'indica l'akyra tampoc no em va, però gràcies a tots dos.

---

### Post by akyra on 2009-07-10
El que dic, sembla una mica tonto, però si no tens privilegis vol dir que no estàs actuant com root.

Tens els teus permisus d'usuari amb l'opció de administrar impressores? 

També podries habilitar entrar com a root en la finestra d'entrada i després tindràs tots el privilegis.

Ja diràs com va.

Salutacions

---

### Post by muleta on 2009-07-10
> **akyra said:**
> 

Tens els teus permisus d'usuari amb l'opció de administrar impressores? 



No ho sé. Com ho puc esbrinar?. Sembla que no perquè, si els tingués, no em diria això. Com els puc adquirir a Kubuntu?.

---

### Post by akyra on 2009-07-10
Ves a Sistema->Administració->Usuaris i Grups

Després desbloqueja'l amb la contrasenya de root, selecciona l'usuari que utilitzes per fer aquestes tasques i ves a la finestra de "Privilegis d'usuari".

Aquí has de tenir habilitada l'opció de administrar impresores.

Et paso una pantalla

A veure si hi ha sort.

Salutacions

---

### Post by muleta on 2009-07-10
Gràcies, però Kubuntu no va així, no hi ha res de tot això, em sap greu. T'ho agraeixo igual, al menys ho has intentat. Ja buscaré informació en algun altre lloc.

---

### Post by Miquel Ubuntero on 2009-07-10
Hola muleta.
Indiferentment si tens Kubuntu o Ubuntu, una eina fàcil i gràfica per desinsta&#320;lar una impressora a qualsevol tipus de Linux és [Http://localhost:631](Http://localhost:631) com altres companys ja han comentat.

Si no saps quin és el password del usuari root que te tots els privilegis, jo "googlejaria" una mica de com canviar aquest password que el necessitaràs sovint. Aquí en parlen: [http://www.debuntu.org/recover-root-password-single-user-mode-and-grub](http://www.debuntu.org/recover-root-password-single-user-mode-and-grub)

Salut!

---

### Post by akyra on 2009-07-10
Crec que hauries de afegir-te al grup "lpadmin"

Estàs segur que kubuntu no va igual??

Bé, ho pots fer des de consola:
  >  sudo gpasswd -a nom-usuari lpadmin

Torna a provar després a esborrar la impresora.

Ja diràs el què.

Adeu.

---

