---
title: "ubuntu 9.1"
date: 2009-11-22
forum: Catalan Team
---

### Post by xevimarce on 2009-11-22
Hola gent ubuntaire,
Tinc uns quants dubtes per resoldre. He instal.lat el 8.04 al ord. fix i estic provant el 9.1 al portàtil (encara no està instal.lat ni formatejat). Com puc recuperar les dades del disc dur del meu portàtil si em diu que necessito els permisos de les carpetes i em diu que jo no en sóc el propietari? No sé quins permisos em demana ni on puc aconseguir-los ni on introduir-los. Tampoc em detecta la xarxa amb fil, sabeu com puc resoldre-ho?
A l'ordinador fix hi he instal.lat l'ubuntu 8.04. Hi ha dies que no m'hi deixa accedir, em quedo amb el logo d'ubuntu sense entrar a l'escriptori.

Fins aviat ;)

---

### Post by akyra on 2009-11-23
Hola.

Suposo que ho estàs provant des del live CD. Si és així hauries d'anar a la consola des dels accesoris i fer un "sudo su" i si no recordo malament, has de posar l'usuari "ubuntu", sense comentes i sense password.

A les hores si vols obrir el nautilus teclejant en la consola directament: "nautilus" (també sense cometes).

L'altre manera també podries fer des de la consola: "sudo nautilus", i quan et demani el usuari poses "ubuntu". Si en lloc de fer-ho amb el nautilus o vols fer amb comandes des de la consola també ho pots fer.

Recorda que essent usuari "root" pots fer malbé el sistema operatiu, així que porta molt de compte.

Per utilitzar la xarxa haurie de ser directament, i si no és així poder et falti instal·lar algun driver privatiu (normalment això només pasa amb les targes gràfiques o les de wifi). Per activar-ho ves a Sistema->Adminsitració->Activar drivers Propietaris (o alguna cosa així, no tinc l'ubuntu davant).

Salutacions.

---

### Post by xevimarce on 2009-11-23
H

---

### Post by xevimarce on 2009-11-23
Hola Akyra,

     Seguint les teves instruccions he aconseguit obrir els arxius (que fins ara no podia veurel's) però no em deixa copiar-los enlloc, insisteix amb que no tinc els permisos per llegir-los. He fet "sudo su" i llavors surt "root@ubuntu:/home/ubuntu" i jo escric; "nautilus" i llavors he accedit als arxius. Però ningú no m'ha demanat l'usuari. Sovint em diu; consulti l'administrador del sistema per permetre el canvi d'usuari. 
      Com punc tancar el terminal sense carregar-mel, en tancar la finestra em diu que "el puc matar". Sóc novell en tot això.

Merci pertot 
xevi

---

### Post by papapep on 2009-11-23
Xevi,

Uns quants comentaris sobre el teu fil:

- **Cal que el títol expliqui de què va el contingut de la consulta o comentari**, resumit evidentment, sinó ens veiem obligats a entrar a mirar què hi ha realment dins, i si anem justos de temps o amb feina acumulada podem no mirar-nos el fil, directament.

- Cada tema necessita d'**un fil diferent**, sinó es barregen els temes i després costa molt reaprofitar la possible solució a la que s'arriba, que és una de les parts més importants del fòrum: redistribuir el coneixement.

- La versió actual de l'Ubuntu és la 9.**10**, no la 9.1.
Pensa que la numeració és: la primera xifra l'any (9) i la segona, el mes de l'any en que s'ha publicat la versió (10). :)

Si no ho has fet ja, caldria que fessis una llegida al [fil pels nouvinguts]("http://ubuntuforums.org/showthread.php?t=599965"), que et donarà unes quantes pistes de com intentem funcionar.

---

### Post by akyra on 2009-11-24
Hola xevimarce,

Si et permet entrar fent des de la terminal fent "sudo su" i després executes nautilus, no has de tancar la consola sino que has de tancar el nautilus i després la consola. Si una vegada fet això et diu que pots matar el procés es refereix al procés al "sudo su", no pasa res si tancas la consola.

Una vegada estiguis al nautilus després d'haver entrat des de la consola amb el "sudo su" pots accedir a qualsevol carpeta. Si tens particions fetes, que suposo que seran de windows, hauries de clickar a sobre d'una d'elles per muntarla i poder extreure les dades o copiar-les a algun altre lloc.

Crec que seria bó que obrisis un altre fil, com diu en papapep, per la connexió de xarxa i expliquis quin simbol et surt de conexió. T'hauria de sortir un simbol com aquest quan estàs connectat "<-->".

Salutacions.

---

### Post by xevimarce on 2009-11-25
Hola Akyra,

Merci per tot, ja he recuperat els fitxers! 
Fins aviat

P.D: Disculpa papapep, procuraré fer-ho millor la propera vegada :)

---

