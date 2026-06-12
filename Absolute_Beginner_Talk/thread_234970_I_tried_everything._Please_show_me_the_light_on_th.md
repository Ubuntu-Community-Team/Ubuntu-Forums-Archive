---
title: "I tried everything. Please show me the light on this one."
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by fabittar on 2006-08-12
Hi everyone,

Third day using Ubuntu and already figured out lots of interesting things on my own and most road bumps went easy on me thanks to either these forums or patience itself. But it just so happens I ran out of patience waiting for a solution to this one:

apt-cache search sun-java5-plugin tells me there is no such file available to me.

Here is a snippet of my problem:

fabittar@fabittar-desktop:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
fabittar@fabittar-desktop:~$ su
Password:
root@fabittar-desktop:/home/fabittar# apt-get install sun-java5-plugin
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
E: Impossível achar pacote sun-java5-plugin
root@fabittar-desktop:/home/fabittar#


If I go to Youtube, for example, I am unable to see any videos. I can, however, see flash animations. But again, I couldn't find the file specified in these forums in my APT.

It's like my APT lacks almost everything I see in these and all other help forums including the Ubuntu help files and guides. Lots of packages are simply not there and I don't know why.

---

### Post by Lord Illidan on 2006-08-12
Are you using Ubuntu Warty by any chance?

---

### Post by fabittar on 2006-08-12
Dapper Drake 6.06

---

### Post by Tomosaur on 2006-08-12
Try running 'sudo apt-cache update'.

---

### Post by fabittar on 2006-08-12
fabittar@fabittar-desktop:~$ sudo apt-cache update
Password:
E: Operação update inválida
fabittar@fabittar-desktop:~$ su
Password:
root@fabittar-desktop:/home/fabittar# apt-cache update
E: Operação update inválida
root@fabittar-desktop:/home/fabittar#


I am guessing that option is not valid either. What do I do now?

---

### Post by Tomosaur on 2006-08-12
Try using the 'aptitude' command instead of 'apt-get'?

---

### Post by fabittar on 2006-08-12
Here is what I did next:

fabittar@fabittar-desktop:~$ su
Password:
root@fabittar-desktop:/home/fabittar# apt-get upgrade
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
root@fabittar-desktop:/home/fabittar# apt-get update
Obtendo:1 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper Release.gpg [189B]
Obtendo:2 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Obtendo:3 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports Release.gpg [189B]
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper Release
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-updates Release
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports Release
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper/main Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper/restricted Packages
Obtendo:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper/main Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper/restricted Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper/universe Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper/universe Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-updates/main Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-updates/restricted Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-updates/main Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-updates/restricted Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports/main Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports/restricted Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports/universe Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports/multiverse Packages
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports/main Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports/restricted Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports/universe Sources
Atingido [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) dapper-backports/multiverse Sources
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Atingido [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Baixados 4B em 1s (2B/s)
Lendo Lista de Pacotes... Pronto
root@fabittar-desktop:/home/fabittar# apt-get upgrade
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
root@fabittar-desktop:/home/fabittar#


Still, nothing. Nada. The packages in the guides, etc are not there. Help.

---

### Post by fabittar on 2006-08-12
> **Tomosaur said:**
> Try using the 'aptitude' command instead of 'apt-get'?

Aptitude?

---

### Post by Tomosaur on 2006-08-12
'sudo aptitude install sun-java5-plugin'

---

### Post by fabittar on 2006-08-12
fabittar@fabittar-desktop:~$ sudo aptitude install sun-java5-plugin
Password:
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Inicializando estados de pacotes... Pronto
Construindo banco de dados de etiquetas... Pronto
Não foi possível encontrar nenhum pacote cujo nome ou descrição casasse com "sun-java5-plugin"
Nenhum pacote será instalado, atualizado ou removido.
0 pacotes atualizados, 0 novos instalados, 0 a serem removidos e 0 não atualizados.
É preciso obter 0B de arquivos. Depois do desempacotamento, 0B serão usados.
fabittar@fabittar-desktop:~$


Nope. I told you, it's like the package isn't there at all. And it isn't according to apt-cache search.

---

### Post by jimrz on 2006-08-12
> **fabittar said:**
> fabittar@fabittar-desktop:~$ sudo aptitude install sun-java5-plugin
Password:
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
Inicializando estados de pacotes... Pronto
Construindo banco de dados de etiquetas... Pronto
Não foi possível encontrar nenhum pacote cujo nome ou descrição casasse com "sun-java5-plugin"
Nenhum pacote será instalado, atualizado ou removido.
0 pacotes atualizados, 0 novos instalados, 0 a serem removidos e 0 não atualizados.
É preciso obter 0B de arquivos. Depois do desempacotamento, 0B serão usados.
fabittar@fabittar-desktop:~$




Nope. I told you, it's like the package isn't there at all. And it isn't according to apt-cache search.

just checked synaptic...it is there...make sure you have multiverse repo enabled

---

