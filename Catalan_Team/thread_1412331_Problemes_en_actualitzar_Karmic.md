---
title: "Problemes en actualitzar Karmic"
date: 2010-02-21
forum: Catalan Team
---

### Post by ximoberna on 2010-02-21
Hola a tothom!

Tinc uns problemes desconeguts per actualitzar el Karmic en un dels tres equips que he instal·lat.

Les errades sembla que afecten els paquets de localització al català i ara que he instal·lat el paquet educatiu del Kubuntu tot el KDE em surt en anglés. 

Vos posaré el que em surt en Terminal:

```

joaquim@joaquim-desktop:~$ sudo aptitude update && sudo aptitude safe-upgrade
[sudo] password for joaquim:                                                 
S'està escrivint la informació d'estat estesa... Fet                         
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                            
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-ca              
Prem [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-ca                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-ca        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-ca        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-ca          
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Prem [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic Release.gpg                            
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/main Translation-ca                    
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/restricted Translation-ca              
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                              
Obté:1 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release.gpg [197B]                          
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Translation-ca                            
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Prem [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/multiverse Translation-ca              
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/universe Translation-ca                
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/main Translation-ca             
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/restricted Translation-ca       
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/multiverse Translation-ca       
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/universe Translation-ca         
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                        
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Translation-ca                      
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Translation-ca                        
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Translation-ca                      
Obté:2 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release [13,2kB]                            
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic Release                                
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release                                        
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Prem [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Prem [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Packages                                 
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates Release                        
Prem [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Packages                           
Prem [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Packages                             
Prem [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Packages                           
Prem [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Sources                                  
Prem [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Sources                            
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/main Packages                          
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/restricted Packages                    
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/multiverse Packages                    
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/restricted Sources                     
Prem [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Sources                              
Prem [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Sources                            
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/main Sources                           
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/multiverse Sources                     
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/universe Sources                       
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/universe Packages                      
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/main Packages                  
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/restricted Packages            
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/multiverse Packages            
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/restricted Sources             
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/main Sources                   
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/multiverse Sources             
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/universe Sources               
Prem [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/universe Packages              
S'han obtingut 198B en 0s (308B/s)                                              
S'està llegint la llista de paquets... Fet                                      
W: Error del GPG: [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release: Les signatures següents no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 0F719C35E394D996                                                                  

S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat... Fet  
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
No s'instal·larà, actualitzarà o suprimirà cap paquet.
0 paquets a actualitzar, 0 a instal·lar, 0 a suprimir i 0 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'utilitzaran 0B.
S'està llegint la llista de paquets... Fet                                   
S'està construint l'arbre de dependències                                    
S'està llegint la informació de l'estat... Fet                               
S'està llegint la informació d'estat estesa                                  
S'estan inicialitzant els estats dels paquets... Fet                         

joaquim@joaquim-desktop:~$ sudo apt-get update
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-ca                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-ca             
Bai:1 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release.gpg [197B]                          
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Translation-ca                           
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Translation-ca                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-ca       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-ca       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-ca         
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Translation-ca                       
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Translation-ca                     
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic Release.gpg                            
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/main Translation-ca                    
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/restricted Translation-ca              
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Bai:2 [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release [13,2kB]                            
Ign [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release                                       
Obj [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                              
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/multiverse Translation-ca              
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/universe Translation-ca                
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/main Translation-ca            
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/restricted Translation-ca      
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/multiverse Translation-ca      
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/universe Translation-ca        
Obj [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Packages                                 
Obj [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                        
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic Release
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Obj [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Packages
Obj [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Packages
Obj [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Packages
Obj [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/main Sources
Obj [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/restricted Sources
Obj [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates Release
Obj [http://debian.wgdd.de](http://debian.wgdd.de) jaunty/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/main Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/main Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) karmic-updates/universe Packages
198B baixats en 0s (289B/s)
S'està llegint la llista de paquets... Fet
W: Error del GPG: [http://debian.wgdd.de](http://debian.wgdd.de) jaunty Release: Les signatures següents no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 0F719C35E394D996

```



Vos posaré també /etc/apt/sources.list:

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
# newer versions of the distribution. 

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic main restricted multiverse 
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic main 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-updates main restricted multiverse 
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-updates main 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic universe 
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic universe 
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-updates universe 
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse 
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse 
 
## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner 
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted multiverse 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe


```

Perdoneu, però la meua inexperiència en Ubuntu/Debian ha de ser la causa de tot això. 

Vos done les gràcies en tot cas per la vostra atenció.

Salutacions!

---

### Post by SiscoGarcia on 2010-02-21
Has provat d'actualitzar els paquets d'idioma? A mi de vegades m'ha passat i al cap d'un temps m'ha funcionat. Amb KDE no sé, però amb Gnome es troben a "Sistema>Administració>Suport d'idioma". Suposo que no ha de ser gaire diferent.

---

### Post by ximoberna on 2010-02-21
> **SiscoGarcia said:**
> Has provat d'actualitzar els paquets d'idioma? A mi de vegades m'ha passat i al cap d'un temps m'ha funcionat. Amb KDE no sé, però amb Gnome es troben a "Sistema>Administració>Suport d'idioma". Suposo que no ha de ser gaire diferent.

Efectivament era això més o menys!

Concretament la ruta ha estat: Aplicacions > Preferències > Arranjament del Sistema > País/Regió i Idioma

De tota manera he intentat actualitzar les fonts i continua apareguent el missatge: 

```
W: Error del GPG: http://debian.wgdd.de jaunty Release: Les signatures següents no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 0F719C35E394D996
```

Moltissimes gràcies per la teua ajuda!

Salutacions!:D

---

### Post by SiscoGarcia on 2010-02-21
El que et passa és que la clau que tens d'aquest paquet és de la jaunty i no el troba per la karmic. Has d'actualitzar-te les claus. Seguint el que diu a [http://debian.wgdd.de/](http://debian.wgdd.de/) el que has de fer està descrit a [http://debian.wgdd.de/repository#gpgkey](http://debian.wgdd.de/repository#gpgkey)

Suposo que fent
```
$ su
# gpg --keyserver pgp.mit.edu --recv-keys 0xE394D996
# gpg --armor --export 0xE394D996 | apt-key add -
```
serà suficient.

EDITO: no tens el paquet als dipòsits de kubuntu?

---

