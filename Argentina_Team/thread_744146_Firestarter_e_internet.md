---
title: "Firestarter e internet"
date: 2008-04-03
forum: Argentina Team
---

### Post by nandazo on 2008-04-03
Soy nuevo en lInux y nuevo en ubuntu, por ahoar todo va bien pero ahora que tengo internet aparecio un problema, bueno configure el internet sin problemas pude navegar tranquilamente.
pero como vengo de Windows y la paranoia de la seguridad esta en mi sangre informatica decide instalar firestarter para mayor tranqulidad, recuerdo que eso lo hice tarde en una noche asi que fue lo ultimo que hice en la pc lo apague y me fui. Al dia siguiente no pude acceder a internet pense que se habia desconfigurado la conexion asi que la volvia a hacer de hecho como no pude conectarme a internet habre hecho la configuracion varias veces, despues decide leer lo que dice firefox cuando no puede abrir una pagina, diec primeramente lo obvio de una coneccionmal hecha, pero me di cuenta que tambien dice que posiblemente el firewall no este permitiendo el acceso a internet atravez de firefox, asi que detuve firestarter y tod funciono mejor pude navegar sin problemas, pero el firewall esta ahi sin hacer nada pregunto ¿si el firewall tengo que tenerlo desactivado para que me funcione internet de que me sirve o algo no hice?
espero ayuda con este asunto ahh y lo olvide Ubuntu esta  lento en mi pc no se porque ni Windows lo tengo asi.

---

### Post by Mauro22 on 2008-04-03
Firestarter no es un firewall ni mucho menos. Es un FrontEnd, es la interfaz grafica de iptables.

Iptables es el firewall y viene incluido en el kernel y esta activo desde que encedes la PC hasta que la apagas.

Firestarter sirve unicamente para configurar iptables de una forma grafica pero bajo ningun punto de vista se debe confundir con un firewall tampoco hay que tenerlo corriendo todo el dia, solo en caso de querer configurar iptables.

---

### Post by jclevien on 2008-04-03
nandazo,

Te recomiendo usar una computadora vieja con Coyote Linux. El link es: [http://www.vortech.net/downloads/Default.aspx](http://www.vortech.net/downloads/Default.aspx), ahí elegís el creador de discos que necesites.

Lo que necesitás para la máquina vieja es: floppy 3 1/2, y dos placas de red soportadas por Coyote, 16 MB RAM, una 486 y no mucho más que eso.

Tiene una consola de administración web muy piola y soporta SSH.

Saludos.


Juan

---

### Post by Hei Ku on 2008-04-03
Probablemente hayas configurado el firestarter para que te bloquee tambien las conexiones salientes, o para que te haga bloqueo total, que es para cuando estas justo bajo ataque.

Arranca el firestarter y fijate que configuracion tiene. En principio deberias bloquear las conexiones entrantes, salvo puertos especificios (como algun port de bittorrent, por ejemplo) y permitir todas las conexiones salientes (despues podes ponerte mas exquisito con eso)

---

