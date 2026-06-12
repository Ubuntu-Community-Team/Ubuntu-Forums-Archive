---
title: "Problem al actualizar con apt en Ubuntu 16.04"
date: 2017-09-09
forum: Argentina Team
---

### Post by emirbet on 2017-09-09
Buena!

Cuando intento instalar o actualizar aplicaciones obtengo el siguiente error:

sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
E: El valor «stable» no es válido para APT::Default-Release ya que dicha distribución no está disponible en las fuentes


He intentado restaurar el fichero de repositorios  a su valor inicial: /user/apt/sources.list


Podría decirme alguién como solucionarlo.

Muchas gracias

---

### Post by papibe on 2017-09-09
Hola emirbet.

Puedes ejecitar este commando y pegar que te da de resultado? (puedes seleccionar el texto del terminal y usar el mouse para copiar y pegar)
```
find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Saludos.

---

### Post by emirbet on 2017-09-10
Esta es la salida que me da:

emirbet@emirbet-X541UAK:~$ find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/ubuntu-desktop-ubuntu-ubuntu-make-xenial.list

     1    deb [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) xenial main

/etc/apt/sources.list.d/rojtberg-ubuntu-hdjmod-xenial.list

     1    deb [http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu](http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu](http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu) xenial main

/etc/apt/sources.list.d/paolorotolo-ubuntu-android-studio-xenial.list

     1    deb [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main
     3    # deb-src [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main

/etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list

     1    deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main

/etc/apt/sources.list.d/maarten-fonville-ubuntu-android-studio-xenial.list

     1    deb [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial main

/etc/apt/sources.list

     1    
     2    
     3    ###### Ubuntu Main Repos
     4    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse 
     5    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse 
     6    
     7    ###### Ubuntu Update Repos
     8    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse 
     9    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse 
    10    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-proposed main restricted universe multiverse 
    11    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse 
    12    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse 
    13    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse 
    14    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-proposed main restricted universe multiverse 
    15    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse 
    16    
    17    ###### Ubuntu Partner Repo
    18    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    19    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    20    
    21    
emirbet@emirbet-X541UAK:~$

---

### Post by emirbet on 2017-09-10
Esta es la salida que me da:

emirbet@emirbet-X541UAK:~$ find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/ubuntu-desktop-ubuntu-ubuntu-make-xenial.list

     1    deb [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu](http://ppa.launchpad.net/ubuntu-desktop/ubuntu-make/ubuntu) xenial main

/etc/apt/sources.list.d/rojtberg-ubuntu-hdjmod-xenial.list

     1    deb [http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu](http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu](http://ppa.launchpad.net/rojtberg/hdjmod/ubuntu) xenial main

/etc/apt/sources.list.d/paolorotolo-ubuntu-android-studio-xenial.list

     1    deb [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main
     3    # deb-src [http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu](http://ppa.launchpad.net/paolorotolo/android-studio/ubuntu) xenial main

/etc/apt/sources.list.d/webupd8team-ubuntu-java-xenial.list

     1    deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial main

/etc/apt/sources.list.d/maarten-fonville-ubuntu-android-studio-xenial.list

     1    deb [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial main
     2    # deb-src [http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu](http://ppa.launchpad.net/maarten-fonville/android-studio/ubuntu) xenial main

/etc/apt/sources.list

     1    
     2    
     3    ###### Ubuntu Main Repos
     4    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse 
     5    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse 
     6    
     7    ###### Ubuntu Update Repos
     8    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse 
     9    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse 
    10    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-proposed main restricted universe multiverse 
    11    deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse 
    12    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse 
    13    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse 
    14    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-proposed main restricted universe multiverse 
    15    deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse 
    16    
    17    ###### Ubuntu Partner Repo
    18    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    19    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    20    
    21    
emirbet@emirbet-X541UAK:~$

---

### Post by emirbet on 2017-09-10
Ya lo he resuelto he cambiado el fichero apt.conf, ahora lo tengo así:

root@emirbet-X541UAK:/etc/apt# cat apt.conf
APT:default-Release *;
root@emirbet-X541UAK:/etc/apt# 

Muchas gracias a todos!!!!!!!

Soy nuevo en este foro, ¿cómo podría dar por resuelto este hilo?

---

