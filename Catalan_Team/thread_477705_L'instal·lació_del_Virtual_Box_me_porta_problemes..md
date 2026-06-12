---
title: "L'instal·lació del Virtual Box me porta problemes..."
date: 2007-06-18
forum: Catalan Team
---

### Post by lo gambusí on 2007-06-18
Salut 

He anat a instal·lar el Virtual Box, perquè és un programeta que sempre m'ha fet gràcia provar, i a mitja instal·lació se m'ha quedat penjat (l'he descarregat de la web en arxiu .deb i l'he executat).

Des que he fet això no puc actualitzar res. L'he intentat esborrar però no me dixa fer-ho del tot perquè diu que està danyat, i tampoc puc tornar-lo a instal·lar.

Alguna idea?

El missatge d'error que em dóna al anar a actualitzar mitjançant l'update manager és:

[I]Could not initialize the package information



A unresolvable problem occurred while initializing the package information.



Please report this bug against the 'update-manager' package and include the following error message:



'E:El paquet virtualbox necessita ser reinstal·lat, però no se li pot trobar un arxiu.'
__________________[/I]

---

### Post by papapep on 2007-06-18
Estaria bé que descriguessis fil per randa (el que has teclejat) el que has fet per a instal·lar-lo, quin paquet has utilitzat i si t'han sortit missatges quan s'ha quedat clavada la instal·lació.

Abans però, seria interessant que executis a un terminal:

```
sudo aptitude update
```

I a veure què diu.

---

### Post by lo gambusí on 2007-06-18
Molt bé, anirem per pams.

He descarregat [este]("http://www.virtualbox.org/download/1.4.0/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb") paquet a l'escriptori. L'he obert i li he donat a instal·lar. S'ha completat l'intercanvi d'arxius i quan ja es disposava a instal·lar-lo definitivament s'ha quedat com penjat. He hagut de forçar-ne la sortida. Llavors he anat a intentar actualitzar lo sistema, fent  sudo "update-manager" i m'ha donat lo següent missatge d'error:

[I]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:El paquet virtualbox necessita ser reinstal·lat, però no se li pot trobar un arxiu.'
[/I]

Dir també que a la consola me diu: *warning: could not initiate dbus*

---

### Post by lo gambusí on 2007-06-18
Afegeixo, al sudo aptitude update me diu:

[I]oriol@oriol-laptop:~$ sudo aptitude update
Obté:1 [http://mirror.anl.gov](http://mirror.anl.gov) feisty Release.gpg [191B]                          
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty/main Translation-ca                           
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/restricted Translation-ca                      
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty/multiverse Translation-ca                     
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty/universe Translation-ca                        
Obté:2 [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates Release.gpg [191B]                  
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/main Translation-ca
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/restricted Translation-ca
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/multiverse Translation-ca
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/universe Translation-ca
Obté:3 [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security Release.gpg [191B]
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/main Translation-ca
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/restricted Translation-ca
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/multiverse Translation-ca             
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/universe Translation-ca               
Obté:4 [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports Release.gpg [191B]                
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports/main Translation-ca                  
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports/restricted Translation-ca            
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports/universe Translation-ca              
Ign [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports/multiverse Translation-ca            
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty Release                                       
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates Release                               
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security Release                              
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports Release                             
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty/main Packages                                 
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty/restricted Packages                    
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty/multiverse Packages                    
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty/main Sources                           
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty/restricted Sources                     
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty/universe Packages                      
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/main Packages                  
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/restricted Packages            
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/multiverse Packages            
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/main Sources                   
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/restricted Sources             
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-updates/universe Packages              
Obté:5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B] 
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/main Packages                        
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/restricted Packages           
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-ca   
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/multiverse Packages                  
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/main Sources                         
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/restricted Sources                   
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-security/universe Packages                    
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports/main Packages                       
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports/restricted Packages                 
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports/universe Packages                   
Prem [http://mirror.anl.gov](http://mirror.anl.gov) feisty-backports/multiverse Packages                 
Prem [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Prem [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
S'han recollit 5B en 13s (0B/s)                                                 
S'està llegint la llista de paquets... Fet 
oriol@oriol-laptop:~$ [/I]

---

### Post by papapep on 2007-06-18
Doncs podries començar posant a un terminal(i al directori on tens el paquet):

```
sudo dpkg-reinstall virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
``` 

a veure què diu tot plegat.

---

### Post by lo gambusí on 2007-06-18
*sudo: dpkg-reinstall: command not found*
:?

---

### Post by papapep on 2007-06-18
Perdó:

sudo dpkg-reconfigure virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb

---

### Post by lo gambusí on 2007-06-18
El paquet «virtualbox_1.4.0-21864_ubuntu_feisty_i386.deb» no està instal·lat i no hi ha informació disponible.
Useu dpkg --info (= dpkg-deb --info) per a examinar els fitxers d'arxiu,
i dpkg --contents (= dpkg-deb --contents) per a llistar-ne el contingut.
/usr/sbin/dpkg-reconfigure: virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb no està instal·lat
oriol@oriol-laptop:~$

---

### Post by papapep on 2007-06-18
Doncs com que sembla que el sistema no el dóna per instal·lat, fem en un terminal :

```
sudo dpkg -i virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
```

Així el diàleg de configuració que s'obrirà el podràs gestionar amb el teclat.

---

### Post by lo gambusí on 2007-06-19
dpkg: s'ha produït un error en processar virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb (--install):
 no es pot accedir a l'arxiu: No such file or directory
S'han trobat errors en processar:
 virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
oriol@oriol-laptop:~$ 
:?:?:?

---

### Post by papapep on 2007-06-19
Això significa que no estàs al directori on tens el paquet descarregat:

> **no es pot accedir a l'arxiu: No such file or directory**

Has de "anar" fins on estigui desat.
Per exemple, suposem que el tens a /home/elteuusuari/Desktop, doncs hauràs de fer:

```
cd /home/elteuusuari/Desktop
```

I, seguidament, torna a executar la comanda del dpkg. Una altra manera, és dir-li directament a la comanda on el tens:

```
sudo dpkg -i /home/elteuusuari/Desktop/virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
```

Qualsevol de les dues maneres et funcionarà.

---

### Post by lo gambusí on 2007-06-19
Me surt una pantalla a la consola, tipus setup d'ms-dos, però al intentar avançar en lo teclat no me dixa.

---

### Post by papapep on 2007-06-19
Si et refereixes a alguna cosa semblant a això:

[[IMG]http://imajr.com/th/dialog_126759.png[/IMG]](http://imajr.com/dialog_126759)

L´únic que has de fer és prèmer Intro, si no et funciona prem el tabulador fins que el "D'acord" estigui vermell i, aleshores, prems Intro.

---

### Post by lo gambusí on 2007-06-19
Cert, cert, quina tonteria.

He anat seguint los passos que m'ha donat, fins que se m'ha qudat aquí:

Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
Success!
 * Starting VirtualBox kernel module vboxdrv                             [ OK ] 

M'he deixat alguna cosa per fer? o ja està instal·lat? en cas de ser així, com l'enjago? 

gràcies!:p

---

### Post by papapep on 2007-06-19
> Messages emitted during module compilation will be logged to /var/log/vbox-install.log.
**Success!**
* Starting VirtualBox kernel module vboxdrv [ OK ] 

Success= Èxit :-)

Aleshores, si vas a Aplicacions > Eines del sistema, hauries de tenir una entrada que es diu "innotek VirtualBox".

---

### Post by lo gambusí on 2007-06-19
Efectivament, estava allí...:lolflag:

Estic seguint [esta]("http://www.kriptopolis.org/virtualbox-ii-windows-fundamentals-bajo-linux") guia per a instal·lar-lo, i quan ja vaig a executar l'emulador i em dóna la senyal d'error, me diu de posar a la consola *chown oriol:wheel /dev/vboxdrv*.

Ho poso, i me diu que el grup no és vàlid. *chown: «oriol:wheel»: el grup no és vàlid*

Pot ser que tingue alguna cosa mal feta? Lo nom d'usuari hauria de ser este, perquè quan entro a la sessió d'ubuntu poso això i la contrassenya. He provat de posar oriol-laptop i tampoc...:?

Gràcies!

---

### Post by maleses on 2007-06-19
Jo també vaig seguir aquesta guia.
Simplement tens que ficar *chown oriol /dev/vboxdrv* o *chown oriol: (grup al que pertany el usuari) /dev/vboxdrv*

---

### Post by papapep on 2007-06-19
Si fas:

```
cat /etc/group|grep oriol
```

veuràs els grups on és el teu usuari (això és a títol didàctic).

A efectes de tenir el dispositiu **/dev/vboxdrv** a la teva disposició, pots fer:

```
sudo chown oriol:oriol /dev/vboxdrv
```

---

### Post by lsrg on 2007-06-19
Amb aquesta solució tindreu problemes si feu servir més d'un usuari.. 
executa:
```
~# ls -l /dev/vboxdrv 
crw-rw---- 1 root vboxusers 10, 61 2007-06-18 14:24 /dev/vboxdrv
```

fixa't que el grup vboxusers ja te permisos per fer servir el dispositiu.. 
per tant és més senzill executar:

```
sudo adduser nom_usuari vboxusers
```

hauras de sortir i tornar a entrar per actualitzar els membres als que formes part.. 
per comprovar-ho, pots executar amb el teu usuari:

```
groups
```

Sort.

Sergi

---

### Post by papapep on 2007-06-19
No puc fer més que donar-te la raó Sergi :-)

---

### Post by lo gambusí on 2007-06-19
Moltes gràcies a tots!! He aconseguit posar l'usuari, però al anar a iniciar el programa se'm carrega, semblant que funciona bé, però després de passar lo logotip, me surt lo següent missatge d'error: *FATAL: No bootable medium found! System halted.*

---

### Post by papapep on 2007-06-19
Què significa "passar lo logotip"? Fes-nos-en una impressió de pantalla.

---

### Post by lo gambusí on 2007-06-19
[IMG]http://img224.imageshack.us/img224/2211/capturasg7.png[/IMG]

---

### Post by lsrg on 2007-06-19
Has creat un disc virtual???

per defecte estan a ~/.VirtualBox/VDI

Suposo que si, per tant et falta posar el CD arrencable per poder iniciar la instal·lació del sistema.. 
crec...

---

### Post by lo gambusí on 2007-06-19
Sí, l'he fet.

En això vols dir que he d'agafar lo meu cd de windows xp per a arrencar lo programa, diguessem?

---

### Post by lo gambusí on 2007-06-19
Sí, veig que és això.

Ho estic instal·lant, si tinc més dubtes preguntaré. :P

Gràcies a tots!

---

