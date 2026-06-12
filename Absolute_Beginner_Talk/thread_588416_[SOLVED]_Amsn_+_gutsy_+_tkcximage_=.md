---
title: "[SOLVED] Amsn + gutsy + tkcximage = ????"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by benevolent on 2007-10-23
I've just upgraded my system to 7.10 version!!! I try to open Amsn (fully working @ 7.04 before) and I get this error:


[img]http://img152.imageshack.us/img152/3691/amsnwe0.jpg[/img]


Anyone??:confused::confused:


I try to reinstall from synaptic, but, nothing!!!!

---

### Post by Arkian on 2007-10-23
Strange - my aMSN worked fine after upgrade apart from the icon being changed with no help of me.

---

### Post by lordpuppet on 2007-10-23
try this: 
```
sudo mv /usr/bin/wish /usr/bin/wish-backup
sudo ln -s /usr/bin/wish8.4 /usr/bin/wish
```

Also, install tlc-dev with this:

```
sudo apt-get install tcl8.4-dev
```

---

### Post by Ashrael on 2007-10-23
I just uninstalled tcl 8.5 and all worked fine, when you do this package TILE will also be uninstalled, this package is needed for widgets... just as you know...


greetz erthlingz.

---

### Post by benevolent on 2007-10-24
> **lordpuppet said:**
> try this: 
```
sudo mv /usr/bin/wish /usr/bin/wish-backup
sudo ln -s /usr/bin/wish8.4 /usr/bin/wish
```

Also, install tlc-dev with this:

```
sudo apt-get install tcl8.4-dev
```


this worked!! thx!!!  :)



edit: It can't recognize the greek font!!!!!

---

### Post by aedwards on 2007-11-04
awesome, this worked for me as well.

I had the same problem!

---

### Post by Centx on 2007-11-10
Thanks, worked for me too after I uninstalled tcl 8.5

---

### Post by joemacnz on 2007-11-21
Sweet, worked for me too. Thank you.

---

### Post by Brian031168 on 2007-12-10
No, still not working for me. I still get the same dialog.

It's strange, it's been running fine for 2 weeks.

Any ideas?

---

### Post by israel1601 on 2008-04-11
Instalação automática Pra todos LINUXERS: aMSN v0.98SVN + TCL 8.6 + TK 8.6 com Anti-Aliase

Por qualquer problema relacionado com o que compilei, meu email e msn é: [email]israel2k9@gmail.com[/email],
testei com sucesso no Mandriva Spring 2008.1, no Ubuntu Hardy Beta, e no Gentoo 2008.
Criei em pacotes de forma que funcione em todas distribuições linux, hoje é sua hora de sorte.

Se seu sistema de pacote for estilo Debian (Funciona em *Ubuntu, *Debian, etc): 

[http://www.mediafire.com/?6l2dxbrbkmn](http://www.mediafire.com/?6l2dxbrbkmn)

Use o comando: 

para instalar: dpkg -i --force- arquivo.deb
para desinstalar:  dpkg -r --force- amsn-0.98svn-10-03-2008-tcl

Se seu sistema de pacote for estilo Redhat (Funciona em *RedHat, *Mandrake, *OpenSuse, etc): 

[http://www.mediafire.com/?ogsjkwgyuuz](http://www.mediafire.com/?ogsjkwgyuuz)

Use o comando: 

para instalar: rpm -i --nodeps arquivo.rpm
para desinstalar:  rpm -e --nodeps aMSN-0.98SVN-10-03-2008-tcl

Se você não sabe qual é seu sistema linux, nem o seu tipo de pacote, baixe este tipo de pacote (para todos sistemas linux, *universal*):

[http://www.mediafire.com/?xd3nbr6myxj](http://www.mediafire.com/?xd3nbr6myxj)

use o comando:
tar -xvzf aMSN-10-03-2008-tcl-tk8.6-installer.tar.gz
para instalar: sh instalar.sh
para desinstalar: sh uninstall.sh


Terminando...

Isso é opcional, no caso da instalação rpm e deb e não tiveres o link: /usr/bin/wish e /usr/bin/tclsh, crie um link com o comando abaixo:
ln -sf /usr/local/amsn/bin/wish8.6 /usr/bin/wish
ln -sf /usr/local/amsn/bin/tclsh8.6 /usr/bin/tclsh


Agora, basta somente duas coisas:

No terminal digite: amsn ou se preferes Vá no Menu do Seu Sistema,
Aplicações -> Internet -> Clique no atalho, ao abrir o aMSN, mude o idioma para PT-BR estará no de Portugal, feche o aMSN
e abra-o novamente e vá em > conta > preferências > Avançado.

Procure por TLS lá embaixo e defina o caminho como /usr/local/amsn/share/amsn/tls1.50

PRONTO! clique Salvar, Aproveite sua webcam, no seu novo aMSN com tcl 8.6 e tk 8.6 Anti-Aliase!

---

### Post by benevolent on 2008-04-11
Hmm... I cannot undestand you, but i've come to 2 solutions for Amsn!!


1) [Emesene]("http://emesene.org/")

2) Install Amsn, from a script located [here]("http://ubuntuforums.org/showthread.php?t=595744")

:roll:

---

### Post by scraghty604 on 2008-04-11
i did the steps but no it just dosent do anythign it will show :starting amsn: in the task bar but the goes away if i restart then the tcx error come back as posted by the frist guy...whats the code to un install 8.5?

---

### Post by benevolent on 2008-04-12
go at this thread [http://ubuntuforums.org/showthread.php?t=595744](http://ubuntuforums.org/showthread.php?t=595744) and download the aMSN_Installer.sh and then follow the instructions:

> You just need to download it to your user folder, give it executing privileges(right click on the icon>properties>permisions/privileges>allow execution) and then in the terminal go the folder where you downloaded the script and do:```
./aMSN_Installer.sh
```

---

