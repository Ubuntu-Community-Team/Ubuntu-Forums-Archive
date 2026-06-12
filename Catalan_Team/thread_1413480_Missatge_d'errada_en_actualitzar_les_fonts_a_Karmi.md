---
title: "Missatge d'errada en actualitzar les fonts a Karmic"
date: 2010-02-22
forum: Catalan Team
---

### Post by ximoberna on 2010-02-22
Continue amb problemes distints després de solucionar els problemes de localització que es poden [vore aquí]("http://ubuntuforums.org/showthread.php?t=1412331"). 

Es tracta d'aquest missatge que surt quan intente actualitzar les fonts:

```
W: Error del GPG: http://debian.wgdd.de jaunty Release: Les signatures següents no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 0F719C35E394D996

```

Donat que aquest missatge fa referència a la Jaunty no em preocupa massa, donat que puc actualitzar amb l'Update Manager sense problemes, però després de for-ho, li done al botó de Comprovar i m'apareix aquest missatge sempre.

Salutacions i gràcies per davant!

---

### Post by papapep on 2010-02-22
Fes a un terminal:

```
sudo apt-get update && sudo apt-get install wgdd-archive-keyring
```

---

### Post by ximoberna on 2010-02-22
> **papapep said:**
> Fes a un terminal:

```
sudo apt-get update && sudo apt-get install wgdd-archive-keyring
```

Vet aquí com es queda la cosa al terminal:

```
joaquim@joaquim-desktop:~$ sudo apt-get update && sudo apt-get install wgdd-archive-keyring
[sudo] password for joaquim:                                                               
Obj http://archive.canonical.com karmic Release.gpg                                        
Ign http://archive.canonical.com karmic/partner Translation-ca                                                       
Obj http://archive.ubuntu.com karmic Release.gpg                                                                     
Bai:1 http://security.ubuntu.com karmic-security Release.gpg [189B]                                                  
Ign http://security.ubuntu.com karmic-security/main Translation-ca                                                   
Ign http://security.ubuntu.com karmic-security/restricted Translation-ca                                             
Ign http://security.ubuntu.com karmic-security/multiverse Translation-ca                                             
Ign http://security.ubuntu.com karmic-security/universe Translation-ca                                               
Obj http://archive.canonical.com karmic Release                                                                      
Obj http://archive.ubuntu.com karmic Release                                                                         
Bai:2 http://security.ubuntu.com karmic-security Release [44,1kB]                                                    
Obj http://es.archive.ubuntu.com karmic Release.gpg                                                                  
Obj http://archive.canonical.com karmic/partner Packages                                                             
Obj http://archive.ubuntu.com karmic/main Sources                                                                    
Bai:3 http://debian.wgdd.de jaunty Release.gpg [197B]                                                                
Ign http://debian.wgdd.de jaunty/main Translation-ca                                                                 
Obj http://es.archive.ubuntu.com karmic/main Translation-ca                                                          
Obj http://archive.ubuntu.com karmic/restricted Sources                                                              
Ign http://debian.wgdd.de jaunty/restricted Translation-ca                                                           
Ign http://debian.wgdd.de jaunty/universe Translation-ca                                                             
Ign http://debian.wgdd.de jaunty/multiverse Translation-ca                                                           
Bai:4 http://debian.wgdd.de jaunty Release [13,2kB]                                                                  
Ign http://debian.wgdd.de jaunty Release                                                                             
Obj http://es.archive.ubuntu.com karmic/restricted Translation-ca                                                    
Obj http://es.archive.ubuntu.com karmic/multiverse Translation-ca                                                    
Obj http://debian.wgdd.de jaunty/main Packages                                                                       
Bai:5 http://security.ubuntu.com karmic-security/main Packages [67,4kB]                                              
Obj http://es.archive.ubuntu.com karmic/universe Translation-ca                                                      
Bai:6 http://es.archive.ubuntu.com karmic-updates Release.gpg [189B]                                                 
Ign http://es.archive.ubuntu.com karmic-updates/main Translation-ca                                                  
Ign http://es.archive.ubuntu.com karmic-updates/restricted Translation-ca                                            
Ign http://es.archive.ubuntu.com karmic-updates/multiverse Translation-ca                                            
Ign http://es.archive.ubuntu.com karmic-updates/universe Translation-ca                                              
Obj http://es.archive.ubuntu.com karmic Release                                                                      
Obj http://debian.wgdd.de jaunty/restricted Packages                                                                 
Obj http://debian.wgdd.de jaunty/universe Packages                                                                   
Obj http://debian.wgdd.de jaunty/multiverse Packages                                                                 
Obj http://debian.wgdd.de jaunty/main Sources                                                                        
Obj http://debian.wgdd.de jaunty/restricted Sources                                                                  
Bai:7 http://es.archive.ubuntu.com karmic-updates Release [44,1kB]                                                   
Obj http://debian.wgdd.de jaunty/universe Sources                                                                    
Obj http://debian.wgdd.de jaunty/multiverse Sources
Bai:8 http://security.ubuntu.com karmic-security/restricted Packages [14B]
Bai:9 http://security.ubuntu.com karmic-security/multiverse Packages [1666B]
Bai:10 http://security.ubuntu.com karmic-security/restricted Sources [14B]
Bai:11 http://security.ubuntu.com karmic-security/main Sources [21,0kB]
Bai:12 http://security.ubuntu.com karmic-security/multiverse Sources [577B]
Bai:13 http://security.ubuntu.com karmic-security/universe Sources [6767B]
Bai:14 http://security.ubuntu.com karmic-security/universe Packages [32,4kB]
Obj http://es.archive.ubuntu.com karmic/main Packages
Obj http://es.archive.ubuntu.com karmic/restricted Packages
Obj http://es.archive.ubuntu.com karmic/multiverse Packages
Obj http://es.archive.ubuntu.com karmic/restricted Sources
Obj http://es.archive.ubuntu.com karmic/main Sources
Obj http://es.archive.ubuntu.com karmic/multiverse Sources
Obj http://es.archive.ubuntu.com karmic/universe Sources
Obj http://es.archive.ubuntu.com karmic/universe Packages
Bai:15 http://es.archive.ubuntu.com karmic-updates/main Packages [174kB]
Bai:16 http://es.archive.ubuntu.com karmic-updates/restricted Packages [14B]
Bai:17 http://es.archive.ubuntu.com karmic-updates/multiverse Packages [6930B]
Bai:18 http://es.archive.ubuntu.com karmic-updates/restricted Sources [14B]
Bai:19 http://es.archive.ubuntu.com karmic-updates/main Sources [52,8kB]
Bai:20 http://es.archive.ubuntu.com karmic-updates/multiverse Sources [3820B]
Bai:21 http://es.archive.ubuntu.com karmic-updates/universe Sources [25,8kB]
Bai:22 http://es.archive.ubuntu.com karmic-updates/universe Packages [103kB]
585kB baixats en 1s (311kB/s)
S'està llegint la llista de paquets... Fet
W: Error del GPG: http://debian.wgdd.de jaunty Release: Les signatures següents no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 0F719C35E394D996
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
S'està llegint la informació de l'estat... Fet
S'instal·laran els paquets NOUS següents:
  wgdd-archive-keyring
0 actualitzats, 1 nous a instal·lar, 0 a suprimir i 9 no actualitzats.
Es necessita obtenir 6056B d'arxius.
Després d'aquesta operació s'empraran 53,2kB d'espai en disc addicional.
AVÍS: No es poden autenticar els següents paquets!
  wgdd-archive-keyring


```

I aquí es queda...

Salutacions i gràcies!

---

### Post by mrc2407 on 2010-02-24
No sé si et seria útil, però pots provar d'aconseguir la clau pública seguint els passos que s'expliquen aquí (en castellà): [http://www.ubuntu-es.org/?q=node/78530#comment-324634](http://www.ubuntu-es.org/?q=node/78530#comment-324634)

Repeteixo que no sé si és ben bé el que necessites, sóc molt novato en això, però a mi em donava un error semblant no sé quina aplicació i ho vaig resoldre així.

---

### Post by wgarcia on 2010-02-25
ximoberna: i no et pregunta si ho vols instal·lar igual tot i que no es pugui autentificar el wgdd-archive-keyring?

---

