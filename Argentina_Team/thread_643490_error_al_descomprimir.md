---
title: "error al descomprimir"
date: 2007-12-17
forum: Argentina Team
---

### Post by sharkg on 2007-12-17
Hola a todos. quiero instalar el vmware server y me da error al descomprimir el archivo .tar.gz
me dice error el comandos y cuando veo, son errores del q no puede acceder, no tiene permisos y demas! hice lo q dice en todos los foros, manuales y demas para poder instalar el programa y no hay forma, no me deja descomprimir el archivo asi instalo el vmware. hace desde el viernes q estoy con lo mismo y no puedo hacer nada.... alguno tiene idea q puede ser, me falta alguna libreria, uso otro programa..
baje 5 veces el archivo y pasa lo mismo siempre!:confused:
saludos

---

### Post by marianom on 2007-12-17
Danos un ejemplo constante y sonante por favor.

---

### Post by sharkg on 2007-12-18
bueno si quiero usar el archivo .rpm me pasa esto...

sharkg@Pinky-Movil:/media/sda7/descargas$ sudo alien --scripts VMware-server-1.0.4-*.rpm
[sudo] password for sharkg:
chown: cambiando el propietario de `VMware-server-1.0.4//etc/vmware': Operación no permitida
failed chowning /etc/vmware to 0:0: Búsqueda ilegal at /usr/share/perl5/Alien/Package/Rpm.pm line 246, <GETPERMS> line 1.

me esta faltando alguna libreria o q?

---

### Post by Hei Ku on 2007-12-18
tenes instalado el alien?

sudo apt-get install alien

El alien permite abrir archivos RPM, que es el sistema de instalacion para Red Hat y otros, similar al apt-get.

---

### Post by sharkg on 2007-12-18
si, lo tengo, lo baje tmb, pero no me deja, me da error mal!!! eso es lo q me dice si lo hago por consola! si lo descomprimo me tira error en todos los archivos

---

### Post by sharkg on 2007-12-18
bueno, me fije como todos los dias y hoy aparecieron los repositores de vmware-server, ya los instale y por lo poco q vi parece q anda!! sino ya estare preguntando algo... :S jeje, saludos y gracias

---

### Post by kowal on 2007-12-19
> **sharkg said:**
> bueno, me fije como todos los dias y hoy aparecieron los repositores de vmware-server, ya los instale y por lo poco q vi parece q anda!! sino ya estare preguntando algo... :S jeje, saludos y gracias

Justamente eso te iba a decir.. vmware-server está en los repositorios "comerciales" de Canonical:

```
deb http://archive.canonical.com/ubuntu gutsy partner
```

Saludos

---

### Post by sharkg on 2007-12-19
la verdad q me anda muy lento!!! tarda como 5 minutos en abrir una maquina para poder instalar algo :S la verdad es q estoy probando un Win Xp en la maquina y anda un caño, me parece q se instalo algo mal en ubuntu y me trajo problemas... medio raro! o suele pasar... porq en Win me anda todo muy bien! o es otro el problema :S

---

### Post by kowal on 2007-12-19
[quote=sharkg]la verdad q me anda muy lento!!! tarda como 5 minutos en abrir una maquina para poder instalar algo :S la verdad es q estoy probando un Win Xp en la maquina y anda un caño, me parece q se instalo algo mal en ubuntu y me trajo problemas... medio raro! o suele pasar... porq en Win me anda todo muy bien! o es otro el problema :S[/quote]

No termino de entender.. Lo que te anda lento es Ubuntu virtualizado en VMware? o el VMware en si?.

A mi me andan sin problemas la mayoría de los SO que probé. Por las dudas te dejo una guía de la alternativa a VMware: VirtualBox.. [aquí. ](podrhttp://tuxpepino.wordpress.com/2007/05/29/virtualbox-windows-en-ubuntu-linux/)

Saludos

---

### Post by User21 on 2007-12-20
Yo uso VirtualBox tambien, y no he tenido NI UN PROBLEMA. Mas que recomendable.

---

### Post by sharkg on 2007-12-20
lo q me anda lento en si es la maquina!!! jejejeje, creo q ya solucione ese tema, pero lo que yo quiero hacer es virtualizar varias maquinas asi hago pruebas para controladores de dominio y demas en W2003 con terminales en  Xp y tmb servidores con W2008 y Ubuntu server 7.10, y demas... trabajos del laboratorio de la facu, pero en casa :-)

---

### Post by faktorqm on 2007-12-21
capaz eso lo tengas ke hacer para la facu, pero si queres instalar un SO para servidores de verdad, openbsd, netbsd o freebsd son lo mejor. salu2!

---

### Post by sharkg on 2007-12-21
uhh voy a ver q onda eso!
te comento estoy en un laboratorio y tenemos servidores con W03, pero tenemos libertad de hacer un controlador de dominio secundario y lo quiero implementar con linux! el unico inconveniente q tengo es con los perfiles.. hay unas 200 maquinas con Xp a las cuales no les puedo quitar el perfil, me matan si pasa eso jeje.. asi q estoy buscano info para ver q puedo hacer!! si sabes de algo te agradesco el dato.. saludos y gracias

---

### Post by faktorqm on 2007-12-23
compilas samba para open/net/free-bsd y listo.... el perfil lo mantenes con el .cmd que tenes ahora en w03 :D lo unico, te aviso desde ya que vas a tener problemas si haces el primario en w y el secundario en openbsd, si usas ldap. hay 2 problemas basicos, que w03 te acepta nombres que NO SON ESTANDAR en netbios, y el otro problema es que es el fingerprinting del ldap no es 100% compatible con openldap, solo Dios sabe por que. Si tenes dudas pregunta, **bsd es lo mas feo y mas horrible y mas rapido y mas seguro que vas a encontrar, digno de un buen servidor no? jajaj salu2!

---

### Post by sharkg on 2007-12-25
bueno gracias por la info, voy a ver q puedo hacer!!

---

