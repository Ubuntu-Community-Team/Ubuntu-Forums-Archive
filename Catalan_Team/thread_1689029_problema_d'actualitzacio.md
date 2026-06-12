---
title: "problema d'actualitzacio"
date: 2011-02-16
forum: Catalan Team
---

### Post by gunyoles on 2011-02-16
hola a tothom, de cop hem surt la notificació de la imatge que aporto. Algú hem pot donar un cop de ma?

[ATTACH]183600[/ATTACH]

---

### Post by wgarcia on 2011-02-16
Sembla un problema del directori cau de les actualitzacions. Prova de fer el següent:

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-RENAMED
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update && sudo apt-get upgrade

---

### Post by gunyoles on 2011-02-16
he seguit el teu suggeriment i hem diu

*********************************************
Bai:1 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-ca   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Bai:2 [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick Release.gpg [198B]                 
Obj [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick/main Translation-ca          
Obj [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-ca       
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-ca              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-ca
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-ca
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-ca
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Obj [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-ca    
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Obj [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-ca    
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Obj [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick/universe Translation-ca      
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates Release.gpg                  
Obj [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-ca  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Obj [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release  
  
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-ca
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-ca
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-ca
Ign [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick Release                        
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick Release                              
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates Release                      
Obj [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Obj [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/main Sources/DiffIndex         
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/universe Sources/DiffIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/main i386 Packages/DiffIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/multiverse i386 Packages/DiffIndex
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates/main i386 Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates/universe i386 Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/main i386 Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/restricted i386 Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/universe i386 Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) maverick/multiverse i386 Packages
396B baixats en 1s (279B/s)           
S'està llegint la llista de paquets... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages
E: No s'han pogut analitzar o obrir les llistes de paquets o el fitxer d'estat.
**************************************************

això pot aclarir alguna cosa?

---

### Post by gunyoles on 2011-02-18
algú te alguna altre idea? això segueix sensa funcionar.  ](*,)

---

### Post by kimet on 2011-02-18
> **gunyoles said:**
> algú te alguna altre idea? això segueix sensa funcionar.  ](*,)

Usar el cercador? 

[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

### Post by gunyoles on 2011-02-20
Gracies per la pista Kimet. Jo nomes havia buscat resultats en català, encara no havia mirat en angles, donat que el meu nivell es baix.

Per si algú li pot servir he anat fent servir el traductor i provant solucions que en el post referit es donen fins que he donat amb la que ha funcionat

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

a partir d'aquí s'actualitzat ell tot sol i ha tornat ha funcionar amb normalitat. =D>

---

