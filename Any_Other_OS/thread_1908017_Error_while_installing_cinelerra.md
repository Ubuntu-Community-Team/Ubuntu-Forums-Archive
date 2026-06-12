---
title: "Error while installing cinelerra"
date: 2012-01-12
forum: Any Other OS
---

### Post by silveringking on 2012-01-12
Hi I'm having problems installing cinelerra:

The following errors appear to me:

```
carlos@carlos:~$ sudo apt-get build-dep cinelerra
[sudo] password for carlos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Serão instalados os seguintes NOVOS pacotes:
  docbook docbook-to-man liba52-0.7.4-dev libavc1394-dev libdv4-dev
  libfaac-dev libfftw3-dev libflac-dev libiec61883-dev libilmbase-dev
  libmjpegtools-dev libogg-dev libopenexr-dev libpopt-dev libquicktime-dev
  libraw1394-dev libsndfile1-dev libsp1c2 libtheora-dev libtiff4-dev
  libtiffxx0c2 libvorbis-dev libxv-dev libxxf86vm-dev nasm sp uuid-dev
  x11proto-video-dev x11proto-xf86vidmode-dev
0 pacotes actualizados, 29 pacotes novos instalados, 0 a remover e 0 não actualizados.
1 pacotes não totalmente instalados ou removidos.
É necessário obter 8129 kB de arquivos.
Após esta operação, serão utilizados 32,5 MB adicionais de espaço em disco.
Deseja continuar [Y/n]? y
Obter:1 http://archive.ubuntu.com/ubuntu/ oneiric/main libtiffxx0c2 i386 3.9.5-1ubuntu1 [6816 B]
Obter:2 http://archive.ubuntu.com/ubuntu/ oneiric/main docbook all 4.5-4 [450 kB]
Obter:3 http://archive.ubuntu.com/ubuntu/ oneiric/main libsp1c2 i386 1.3.4-1.2.1-47.1 [1422 kB]
Obter:4 http://archive.ubuntu.com/ubuntu/ oneiric/main sp i386 1.3.4-1.2.1-47.1 [159 kB]
Obter:5 http://archive.ubuntu.com/ubuntu/ oneiric/main docbook-to-man i386 1:2.0.0-28 [72,4 kB]
Obter:6 http://archive.ubuntu.com/ubuntu/ oneiric/universe liba52-0.7.4-dev i386 0.7.4-16 [44,0 kB]
Obter:7 http://archive.ubuntu.com/ubuntu/ oneiric/multiverse libfaac-dev i386 1.28-0ubuntu1 [41,7 kB]
Obter:8 http://archive.ubuntu.com/ubuntu/ oneiric/main libfftw3-dev i386 3.2.2-1ubuntu2 [1938 kB]
Obter:9 http://archive.ubuntu.com/ubuntu/ oneiric/main libogg-dev i386 1.2.2~dfsg-1ubuntu1 [63,3 kB]
Obter:10 http://archive.ubuntu.com/ubuntu/ oneiric/main libflac-dev i386 1.2.1-4ubuntu1 [209 kB]
Obter:11 http://archive.ubuntu.com/ubuntu/ oneiric/main libraw1394-dev i386 2.0.7-1 [59,5 kB]
Obter:12 http://archive.ubuntu.com/ubuntu/ oneiric/main libiec61883-dev i386 1.2.0-0.1build1 [33,6 kB]
Obter:13 http://archive.ubuntu.com/ubuntu/ oneiric/main libilmbase-dev i386 1.0.1-3build2 [195 kB]
Obter:14 http://archive.ubuntu.com/ubuntu/ oneiric/universe libquicktime-dev i386 2:1.2.3-4 [32,8 kB]
Obter:15 http://archive.ubuntu.com/ubuntu/ oneiric/multiverse libmjpegtools-dev i386 1:1.9.0-0.5ubuntu5 [302 kB]
Obter:16 http://archive.ubuntu.com/ubuntu/ oneiric/main libopenexr-dev i386 1.6.1-4.1 [383 kB]
Obter:17 http://archive.ubuntu.com/ubuntu/ oneiric/main libpopt-dev i386 1.16-1 [50,3 kB]
Obter:18 http://archive.ubuntu.com/ubuntu/ oneiric/main libvorbis-dev i386 1.3.2-1ubuntu2 [448 kB]
Obter:19 http://archive.ubuntu.com/ubuntu/ oneiric/main libsndfile1-dev i386 1.0.24-1ubuntu2 [309 kB]
Obter:20 http://archive.ubuntu.com/ubuntu/ oneiric/main libtheora-dev i386 1.1.1+dfsg.1-3 [401 kB]
Obter:21 http://archive.ubuntu.com/ubuntu/ oneiric/main libtiff4-dev i386 3.9.5-1ubuntu1 [278 kB]
Obter:22 http://archive.ubuntu.com/ubuntu/ oneiric/main x11proto-video-dev all 2.3.1-1 [15,4 kB]
Obter:23 http://archive.ubuntu.com/ubuntu/ oneiric/main libxv-dev i386 2:1.0.6-2 [34,9 kB]
Obter:24 http://archive.ubuntu.com/ubuntu/ oneiric/main x11proto-xf86vidmode-dev i386 2.3.1-2 [6116 B]
Obter:25 http://archive.ubuntu.com/ubuntu/ oneiric/main libxxf86vm-dev i386 1:1.1.1-2 [14,7 kB]
Obter:26 http://archive.ubuntu.com/ubuntu/ oneiric/main nasm i386 2.09.08-1 [1030 kB]
Obter:27 http://archive.ubuntu.com/ubuntu/ oneiric/main libavc1394-dev i386 0.5.3-1build4 [31,1 kB]
Obter:28 http://archive.ubuntu.com/ubuntu/ oneiric/main libdv4-dev i386 1.0.0-3 [72,7 kB]
Obter:29 http://archive.ubuntu.com/ubuntu/ oneiric/main uuid-dev i386 2.19.1-2ubuntu3 [25,5 kB]
Obtidos 8129 kB em 6s (1199 kB/s)                                              
A seleccionar pacote anteriormente não seleccionado libtiffxx0c2
(A ler a base de dados ... 230251 ficheiros e directórios actualmente instalados.)
A descompactar libtiffxx0c2 (desde .../libtiffxx0c2_3.9.5-1ubuntu1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado docbook
A descompactar docbook (desde .../archives/docbook_4.5-4_all.deb) ...
A seleccionar pacote anteriormente não seleccionado libsp1c2
A descompactar libsp1c2 (desde .../libsp1c2_1.3.4-1.2.1-47.1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado sp
A descompactar sp (desde .../sp_1.3.4-1.2.1-47.1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado docbook-to-man
A descompactar docbook-to-man (desde .../docbook-to-man_1%3a2.0.0-28_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado liba52-0.7.4-dev
A descompactar liba52-0.7.4-dev (desde .../liba52-0.7.4-dev_0.7.4-16_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libfaac-dev
A descompactar libfaac-dev (desde .../libfaac-dev_1.28-0ubuntu1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libfftw3-dev
A descompactar libfftw3-dev (desde .../libfftw3-dev_3.2.2-1ubuntu2_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libogg-dev
A descompactar libogg-dev (desde .../libogg-dev_1.2.2~dfsg-1ubuntu1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libflac-dev
A descompactar libflac-dev (desde .../libflac-dev_1.2.1-4ubuntu1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libraw1394-dev
A descompactar libraw1394-dev (desde .../libraw1394-dev_2.0.7-1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libiec61883-dev
A descompactar libiec61883-dev (desde .../libiec61883-dev_1.2.0-0.1build1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libilmbase-dev
A descompactar libilmbase-dev (desde .../libilmbase-dev_1.0.1-3build2_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libquicktime-dev
A descompactar libquicktime-dev (desde .../libquicktime-dev_2%3a1.2.3-4_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libmjpegtools-dev
A descompactar libmjpegtools-dev (desde .../libmjpegtools-dev_1%3a1.9.0-0.5ubuntu5_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libopenexr-dev
A descompactar libopenexr-dev (desde .../libopenexr-dev_1.6.1-4.1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libpopt-dev
A descompactar libpopt-dev (desde .../libpopt-dev_1.16-1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libvorbis-dev
A descompactar libvorbis-dev (desde .../libvorbis-dev_1.3.2-1ubuntu2_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libsndfile1-dev
A descompactar libsndfile1-dev (desde .../libsndfile1-dev_1.0.24-1ubuntu2_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libtheora-dev
A descompactar libtheora-dev (desde .../libtheora-dev_1.1.1+dfsg.1-3_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libtiff4-dev
A descompactar libtiff4-dev (desde .../libtiff4-dev_3.9.5-1ubuntu1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado x11proto-video-dev
A descompactar x11proto-video-dev (desde .../x11proto-video-dev_2.3.1-1_all.deb) ...
A seleccionar pacote anteriormente não seleccionado libxv-dev
A descompactar libxv-dev (desde .../libxv-dev_2%3a1.0.6-2_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado x11proto-xf86vidmode-dev
A descompactar x11proto-xf86vidmode-dev (desde .../x11proto-xf86vidmode-dev_2.3.1-2_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libxxf86vm-dev
A descompactar libxxf86vm-dev (desde .../libxxf86vm-dev_1%3a1.1.1-2_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado nasm
A descompactar nasm (desde .../nasm_2.09.08-1_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libavc1394-dev
A descompactar libavc1394-dev (desde .../libavc1394-dev_0.5.3-1build4_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado libdv4-dev
A descompactar libdv4-dev (desde .../libdv4-dev_1.0.0-3_i386.deb) ...
A seleccionar pacote anteriormente não seleccionado uuid-dev
A descompactar uuid-dev (desde .../uuid-dev_2.19.1-2ubuntu3_i386.deb) ...
A processar 'triggers' para doc-base ...
Processing 4 added doc-base files...
Registering documents with scrollkeeper...
A processar 'triggers' para man-db ...
A processar 'triggers' para install-info ...
A instalar cinelerra (1:2.2-0.3~ppa1~oneiric1) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: erro ao processar cinelerra (--configure):
 subprocesso script post-installation instalado retornou erro do status de saída 4
A instalar libtiffxx0c2 (3.9.5-1ubuntu1) ...
A instalar docbook (4.5-4) ...
A instalar libsp1c2 (1.3.4-1.2.1-47.1) ...
A instalar sp (1.3.4-1.2.1-47.1) ...
A instalar docbook-to-man (1:2.0.0-28) ...
A instalar liba52-0.7.4-dev (0.7.4-16) ...
A instalar libfaac-dev (1.28-0ubuntu1) ...
A instalar libfftw3-dev (3.2.2-1ubuntu2) ...
A instalar libogg-dev (1.2.2~dfsg-1ubuntu1) ...
A instalar libflac-dev (1.2.1-4ubuntu1) ...
A instalar libraw1394-dev (2.0.7-1) ...
A instalar libiec61883-dev (1.2.0-0.1build1) ...
A instalar libilmbase-dev (1.0.1-3build2) ...
A instalar libquicktime-dev (2:1.2.3-4) ...
A instalar libmjpegtools-dev (1:1.9.0-0.5ubuntu5) ...
A instalar libopenexr-dev (1.6.1-4.1) ...
A instalar libpopt-dev (1.16-1) ...
A instalar libvorbis-dev (1.3.2-1ubuntu2) ...
A instalar libsndfile1-dev (1.0.24-1ubuntu2) ...
A instalar libtheora-dev (1.1.1+dfsg.1-3) ...
A instalar libtiff4-dev (3.9.5-1ubuntu1) ...
A instalar x11proto-video-dev (2.3.1-1) ...
A instalar libxv-dev (2:1.0.6-2) ...
A instalar x11proto-xf86vidmode-dev (2.3.1-2) ...
A instalar libxxf86vm-dev (1:1.1.1-2) ...
A instalar nasm (2.09.08-1) ...
A instalar libavc1394-dev (0.5.3-1build4) ...
A instalar libdv4-dev (1.0.0-3) ...
A instalar uuid-dev (2.19.1-2ubuntu3) ...
A processar 'triggers' para libc-bin ...
ldconfig deferred processing now taking place
Foram encontrados erros enquanto processava:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Falhou processar as dependências de compilação
carlos@carlos:~$ sudo apt-get install cinelerra --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cinelerra já está na versão mais recente.
Os seguintes pacotes foram instalados automaticamente e já não são necessários:
  libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
  libmono-messaging2.0-cil libmono-i18n-west2.0-cil
  libmono-system-messaging2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-system-data-linq2.0-cil libmono-sqlite2.0-cil
  libmono-system-web2.0-cil libmono-sharpzip2.84-cil libmono-corlib2.0-cil
  libmono-wcf3.0-cil libmono-system2.0-cil
Utilize 'apt-get autoremove' para os remover.
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
1 pacotes não totalmente instalados ou removidos.
Após esta operação, serão utilizados 0 B adicionais de espaço em disco.
Deseja continuar [Y/n]? y
A instalar cinelerra (1:2.2-0.3~ppa1~oneiric1) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: erro ao processar cinelerra (--configure):
 subprocesso script post-installation instalado retornou erro do status de saída 4
No apport report written because MaxReports is reached already
                                                              Foram encontrados erros enquanto processava:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)
carlos@carlos:~$ sudo apt-get build-dep cinelerra --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
1 pacotes não totalmente instalados ou removidos.
Após esta operação, serão utilizados 0 B adicionais de espaço em disco.
Deseja continuar [Y/n]? y
A instalar cinelerra (1:2.2-0.3~ppa1~oneiric1) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: erro ao processar cinelerra (--configure):
 subprocesso script post-installation instalado retornou erro do status de saída 4
Foram encontrados erros enquanto processava:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Falhou processar as dependências de compilação
carlos@carlos:~$ sudo apt-get purge cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Os seguintes pacotes foram instalados automaticamente e já não são necessários:
  libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
  libmono-messaging2.0-cil libmono-i18n-west2.0-cil
  libmono-system-messaging2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-system-data-linq2.0-cil libmono-sqlite2.0-cil
  libmono-system-web2.0-cil libmono-sharpzip2.84-cil libmono-corlib2.0-cil
  libmono-wcf3.0-cil libmono-system2.0-cil
Utilize 'apt-get autoremove' para os remover.
Serão REMOVIDOS os seguintes pacotes:
  cinelerra*
0 pacotes actualizados, 0 pacotes novos instalados, 1 a remover e 0 não actualizados.
1 pacotes não totalmente instalados ou removidos.
Após esta operação, será libertado 23,5 MB de espaço em disco.
Deseja continuar [Y/n]? y
(A ler a base de dados ... 231522 ficheiros e directórios actualmente instalados.)
A remover cinelerra ...
A purgar os ficheiros de configuração para cinelerra ...
A processar 'triggers' para desktop-file-utils ...
A processar 'triggers' para gnome-menus ...
A processar 'triggers' para bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
A processar 'triggers' para menu ...
A processar 'triggers' para man-db ...
carlos@carlos:~$ sudo apt-get build-dep cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 pacotes actualizados, 0 pacotes novos instalados, 0 a remover e 0 não actualizados.
carlos@carlos:~$ sudo apt-get install cinelerra --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Os seguintes pacotes foram instalados automaticamente e já não são necessários:
  libmono2.0-cil libmono-data-tds2.0-cil libmono-system-data2.0-cil
  libmono-messaging2.0-cil libmono-i18n-west2.0-cil
  libmono-system-messaging2.0-cil libmono-posix2.0-cil libmono-security2.0-cil
  libmono-system-data-linq2.0-cil libmono-sqlite2.0-cil
  libmono-system-web2.0-cil libmono-sharpzip2.84-cil libmono-corlib2.0-cil
  libmono-wcf3.0-cil libmono-system2.0-cil
Utilize 'apt-get autoremove' para os remover.
Serão instalados os seguintes NOVOS pacotes:
  cinelerra
0 pacotes actualizados, 1 pacotes novos instalados, 0 a remover e 0 não actualizados.
É necessário obter 0 B/11,2 MB de arquivos.
Após esta operação, serão utilizados 23,5 MB adicionais de espaço em disco.
A seleccionar pacote anteriormente não seleccionado cinelerra
(A ler a base de dados ... 231246 ficheiros e directórios actualmente instalados.)
A descompactar cinelerra (desde .../cinelerra_1%3a2.2-0.3~ppa1~oneiric1_i386.deb) ...
A processar 'triggers' para man-db ...
A processar 'triggers' para menu ...
A processar 'triggers' para desktop-file-utils ...
A processar 'triggers' para gnome-menus ...
A processar 'triggers' para bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
A instalar cinelerra (1:2.2-0.3~ppa1~oneiric1) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: erro ao processar cinelerra (--configure):
 subprocesso script post-installation instalado retornou erro do status de saída 4
No apport report written because MaxReports is reached already
                                                              Foram encontrados erros enquanto processava:
 cinelerra
E: Sub-process /usr/bin/dpkg returned an error code (1)
carlos@carlos:~$ 

```

I have always this kind of error whatever I try.

---

### Post by silveringking on 2012-01-12
Now I noticed I didn't recover from a very nasty error. What can i do?

---

### Post by silveringking on 2012-01-12
Ok I was able to fix the cinelerra problem (I had to remove the ppa, the  key and purge it all) but still I am having problems with my visual, my  mint is not updating and the visual is broken.

---

### Post by silveringking on 2012-01-12
I thought the dpkg was fixed but it is not. So I did what is said [here with the etc/sudoers](forums.linuxmint.com/viewtopic.php?f=141&t=67502&start=1120) I used gksudo gedit etc/sudoers and it didn't open so I did sudo visudo after and it open the temp and I add the line there, then I cleaned my system with bleachbit, tried to install cinelerra again and I had the same problem. Also my workstation since the error looks like this: [http://imageshack.us/photo/my-images/46/screenshotat20120112232.png/](http://imageshack.us/photo/my-images/46/screenshotat20120112232.png/) suddently it doesn't have the default looking of gnome 3 that came with linux mint. Thank you for any help.

---

