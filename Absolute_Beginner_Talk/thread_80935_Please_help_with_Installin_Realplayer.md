---
title: "Please help with Installin Realplayer"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by Darrin on 2005-10-23
Ive tried posting this before, but couldnt get it right.  Messed it up bad. Ended up having to reinstall ubunut. I really need a step by step guide on this. I am totally new and dont uderstand command line stuff. 
Someone here want to take the time to help me get this up and running?  Pretty please ;)

---

### Post by paddyg on 2005-10-23
This more or less sums up what was said at
[http://www.ubuntuforums.org/showthread.php?t=80024](http://www.ubuntuforums.org/showthread.php?t=80024)
with almost no command line:

Before doing everything you should get libstdc++5 (Breezy uses version 6 and realplayer doesn't seem to work with that). You can either copy it from Hoary ---if you have Hoary---- and paste it to /usr/lib or do as Artificial Intellingence said:

sudo apt-get install libstdc++5

Then go on:

1. download realplayer bin from their site into your home folder
2. log out as normal user and log in as root
3. copy and paste the bin file from your home folder (/home/you) to where you'd like realplayer to be installed--say, /usr/share
4. rightclick on the file and check for properties-->permissions (execute must be ticked off, and root should be owner & group) 
5. open the Terminal
6. type cd .. (=cd space dot dot) until you have the root folder /
7. type cd /usr/share (where you pasted the realplayer bin file)
8. type ./RealPlayer10GOLD.bin
The file should start a script, you must answer some questions about paths. For example, RealPlayer directory (/usr/share/Realplayer), suffix (/usr), plugins...
9. Once finished, exit from Terminal, and log out.

I think the trickiest part is whether you manage to get the libstdc++5 file.
Hope all that works now.

---

### Post by Darrin on 2005-10-23
Thanks for taking the time to write the steps down. This should be a lot easier. 
 How do I get libstdc++5 from Hoary? Im not sure where to go.
I did the sudo apt-get install libstdc++5 thing and it stated "libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

 tried to place the bin file into my user/share foder but said I didnt have permissions.

2. Not sure how to log out and sign in as root. I only have one log in.

Thats where am at right now.

---

### Post by paddyg on 2005-10-24
[QUOTE=Darrin]Thanks for taking the time to write the steps down. This should be a lot easier. 
 How do I get libstdc++5 from Hoary? Im not sure where to go.
I did the sudo apt-get install libstdc++5 thing and it stated "libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

 tried to place the bin file into my user/share foder but said I didnt have permissions.

2. Not sure how to log out and sign in as root. I only have one log in.

Thats where am at right now.[/QUOTE]

*) To log in as root:

1. give root a password:
system-->administration-->users and groups (show all users and groups)--> root -->properties
then select a password

2. select:
system-->login screen setup -->security-->tick off "allow root to login with GDM"

**) In Hoary go to /usr/lib the file should be called libstdc++.so.5.0.7. Copy it and paste it somewhere (floppy, usb shuttle) to use it in Breezy. Be careful, don't copy the link to it (usually named libstdc++.so.5)

In Breezy, go to /usr/lib as root. There should be two files: libstdc++.so.6something anda link to it. Don't delete them (!), just paste there the libstdc++.so.5.0.7 you have on your floppy. Then make a link to it (rightclick---> Make Link, rename the link: libstdc++.so.5). Then check permissions of both files (owner and group = root; chmod = 644 (that is--owner read write; group read; others read))

---

### Post by Darrin on 2005-10-26
Thanks again for posting. Ive been away for a couple days out of frustration. I messed it up again and uninstalled Ubuntu. I put it back on tonight. Im going to read your post carefully and hope I dont mess it up. I really want ubuntu to work for me. Ill be at it again in the morning. One thing I do know how to do very well now, is reinstall ubuntu :)

---

### Post by verlossen on 2005-10-27
I have had no end of trouble installing RealPlayer,I have managed to do it (finally), it was crash my GUI (right now i cant be sure whether the next time I log in I will have to reinstall) but that is what I have done this time:

I downloaded from [www.real.com/linux](www.real.com/linux) their file

elena@ubuntu:~$ sudo -s
root@ubuntu:~# cd /home/elena/ (HOME/ELENA is my home directory where the downloaded file was
root@ubuntu:~# ls -la
total 124
drwxr-xr-x  18 elena elena 4096 2005-10-27 06:11 .
drwxr-xr-x   3 root  root  4096 2005-10-26 20:57 ..
drwx------   6 elena elena 4096 2005-10-26 20:52 .amsn
drwx------   2 elena elena 4096 2005-10-26 21:06 amsn_received
-rw-------   1 elena elena   88 2005-10-26 21:33 .bash_history
-rw-r--r--   1 elena elena  414 2005-10-26 20:57 .bash_profile
-rw-r--r--   1 elena elena 2227 2005-10-26 20:57 .bashrc
drwxr-xr-x   2 elena elena 4096 2005-10-27 06:16 Desktop
-rw-------   1 elena elena   24 2005-10-27 06:10 .dmrc
-rw-------   1 elena elena   16 2005-10-26 19:47 .esd_auth
drwx------   3 elena elena 4096 2005-10-27 06:15 .gaim
drwx------   4 elena elena 4096 2005-10-27 06:11 .gconf
drwx------   2 elena elena 4096 2005-10-27 06:13 .gconfd
-rw-r-----   1 elena elena    0 2005-10-27 05:56 .gksu.lock
drwx------   6 elena elena 4096 2005-10-27 06:10 .gnome2
drwx------   2 elena elena 4096 2005-10-26 19:47 .gnome2_private
drwxr-xr-x   2 elena elena 4096 2005-10-26 19:47 .gstreamer-0.8
-rw-r--r--   1 elena elena   87 2005-10-26 19:48 .gtkrc-1.2-gnome2
-rw-------   1 elena elena  157 2005-10-27 06:11 .ICEauthority
drwx------   3 elena elena 4096 2005-10-26 19:48 .metacity
drwx------   3 elena elena 4096 2005-10-26 19:57 .mozilla
drwxr-xr-x   3 elena elena 4096 2005-10-26 19:48 .nautilus
drwx------   3 elena elena 4096 2005-10-26 21:32 .openoffice.org2
-rw-------   1 elena elena  942 2005-10-26 21:32 .recently-used
-rw-r--r--   1 elena elena 1156 2005-10-26 20:25 sources.list
drwx------   4 elena elena 4096 2005-10-26 21:07 .thumbnails
drwx------   2 elena elena 4096 2005-10-26 19:48 .Trash
drwx------   2 elena elena 4096 2005-10-26 19:48 .update-notifier
-rw-------   1 elena elena  117 2005-10-27 06:10 .Xauthority
-rw-r--r--   1 elena elena 8925 2005-10-27 06:17 .xsession-errors

Then I installed the libstdc++5 

root@ubuntu:~# apt-get install libstdc++5
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Se instalarán los siguientes paquetes extras:
  gcc-3.3-base
Se instalarán los siguientes paquetes NUEVOS:
  gcc-3.3-base libstdc++5
0 actualizados, 2 se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0B/446kB de archivos.
Se utilizarán 1077kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s

Sorry about the lines in Spanish, I basically chose yes to carry on with the installation

Preconfigurando paquetes ...
Seleccionando el paquete gcc-3.3-base previamente no seleccionado.
(Leyendo la base de datos ...
58574 ficheros y directorios instalados actualmente.)
Desempaquetando gcc-3.3-base (de .../gcc-3.3-base_1%3a3.3.6-8ubuntu1_i386.deb) ...
Seleccionando el paquete libstdc++5 previamente no seleccionado.
Desempaquetando libstdc++5 (de .../libstdc++5_1%3a3.3.6-8ubuntu1_i386.deb) ...
Configurando gcc-3.3-base (3.3.6-8ubuntu1) ...
Configurando libstdc++5 (3.3.6-8ubuntu1) ...

Then I copied the Realplayer file in the /usr/bin and changed its permissions to 777

root@ubuntu:~# cp /home/elena/Desktop/RealPlayer10GOLD.bin /usr/bin
root@ubuntu:~# chmod 777 /usr/bin/RealPlayer10GOLD.bin

Then I went to that directory and 
root@ubuntu:~# cd /usr/bin/

and typed : ./RealPlayer10GOLD.bin
root@ubuntu:/usr/bin# ./RealPlayer10GOLD.bin
Extracting files for RealPlayer installation........................

Welcome to the RealPlayer (10.0.6.776) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...


Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.

I chose that directory so that all users on the system might use RealPlayer
Directory:  [/usr/bin/RealPlayer]:

You have selected the following RealPlayer configuration:

Destination:            /usr/bin/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F


Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: .y.
enter the prefix for symbolic links [/usr]: ..
Setting up realplay symlinks in /usr...
configuring icons...
configuring document icons...
.configuring pixmaps...
configuring locale...
configuring desktop...
configuring applications...
configuring GNOME mime types...
Configuring realplay script...

RealPlayer installation is complete.
Cleaning up installation files...
Done.

root@ubuntu:/usr/bin#



Touch wood, my GUI remains safe and sound, but I have the feeling it will, since it is the first time that I manage to install it on this ubuntu....

Verlossen

---

### Post by Darrin on 2005-10-27
Thank you **paddyg** Realplayer works. :D. I appreciate the clear instructions. Thanks again.

---

### Post by paddyg on 2005-10-27
[QUOTE=Darrin]Thank you **paddyg** Realplayer works. :D. I appreciate the clear instructions. Thanks again.[/QUOTE]
:D :D :D


( verlossen, never had problems installing realplayer in /usr/share. GUI always as solid.
hope things will be ok )

---

### Post by Mustard on 2005-10-27
A pretty good guide. :)

/me puts on his pedantic hat ;)

I would question the way you acheived the root login though.  The root account is disabled for security reasons and to discourage people just logging in as root and doing everything from there (and *potentially* doing some damage at the same time).

Safer practice for logging in as root in terminal would be to do a 

```
sudo -s
or
sudo -i

or I have even seen

sudo su
```

See the link below to the wiki explanation of Root and sudo.

[Sudo and root]("https://wiki.ubuntu.com/RootSudo?highlight=%28rootsudo%29")

---

### Post by paddyg on 2005-10-27
> **Mustard]A pretty good guide. :)

/me puts on his pedantic hat  said:**
> Sudo and root[/URL]

Yes, you're right, but i come from fedora, and i've learned to use root logging in very very carefully. You must know what you're doing.

So, yes, root logging in (if ever used) should never be lightheartedly, and generally discouraged.

---

### Post by moe458 on 2005-10-30
[QUOTE=paddyg]This more or less sums up what was said at
[http://www.ubuntuforums.org/showthread.php?t=80024](http://www.ubuntuforums.org/showthread.php?t=80024)
with almost no command line:

Before doing everything you should get libstdc++5 (Breezy uses version 6 and realplayer doesn't seem to work with that). You can either copy it from Hoary ---if you have Hoary---- and paste it to /usr/lib or do as Artificial Intellingence said:

sudo apt-get install libstdc++5

Then go on:

1. download realplayer bin from their site into your home folder
2. log out as normal user and log in as root
3. copy and paste the bin file from your home folder (/home/you) to where you'd like realplayer to be installed--say, /usr/share
4. rightclick on the file and check for properties-->permissions (execute must be ticked off, and root should be owner & group) 
5. open the Terminal
6. type cd .. (=cd space dot dot) until you have the root folder /
7. type cd /usr/share (where you pasted the realplayer bin file)
8. type ./RealPlayer10GOLD.bin
The file should start a script, you must answer some questions about paths. For example, RealPlayer directory (/usr/share/Realplayer), suffix (/usr), plugins...
9. Once finished, exit from Terminal, and log out.

I think the trickiest part is whether you manage to get the libstdc++5 file.
Hope all that works now.[/QUOTE]


Your documenation was excellent I must say.   Thanks for all the help :)

---

### Post by moe458 on 2005-10-30
[QUOTE=paddyg]This more or less sums up what was said at
[http://www.ubuntuforums.org/showthread.php?t=80024](http://www.ubuntuforums.org/showthread.php?t=80024)
with almost no command line:

Before doing everything you should get libstdc++5 (Breezy uses version 6 and realplayer doesn't seem to work with that). You can either copy it from Hoary ---if you have Hoary---- and paste it to /usr/lib or do as Artificial Intellingence said:

sudo apt-get install libstdc++5

Then go on:

1. download realplayer bin from their site into your home folder
2. log out as normal user and log in as root
3. copy and paste the bin file from your home folder (/home/you) to where you'd like realplayer to be installed--say, /usr/share
4. rightclick on the file and check for properties-->permissions (execute must be ticked off, and root should be owner & group) 
5. open the Terminal
6. type cd .. (=cd space dot dot) until you have the root folder /
7. type cd /usr/share (where you pasted the realplayer bin file)
8. type ./RealPlayer10GOLD.bin
The file should start a script, you must answer some questions about paths. For example, RealPlayer directory (/usr/share/Realplayer), suffix (/usr), plugins...
9. Once finished, exit from Terminal, and log out.

I think the trickiest part is whether you manage to get the libstdc++5 file.
Hope all that works now.[/QUOTE]

Just finished installing the RealPlayer it went thru just fine but only 2 files had some issues..here is the terminal window showing that.
--------------------------------------
Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: ..y
enter the prefix for symbolic links [/usr]: ....
Setting up realplay symlinks in /usr...
configuring icons...
configuring document icons...
.configuring pixmaps...
configuring locale...
install: cannot create regular file `/usr/share/locale/hi/LC_MESSAGES/realplay.m o': [COLOR="Red"]No such file or directory[/COLOR]
install: cannot create regular file `/usr/share/locale/hi/LC_MESSAGES/libgtkhx.m o': [COLOR="Red"]No such file or directory[/COLOR]
configuring desktop...
configuring applications...
configuring GNOME mime types...
Configuring realplay script...

RealPlayer installation is complete.
Cleaning up installation files...
Done.

moe@boomer:/usr/share/RealPlayer$
--------------------------------------------

---

### Post by paddyg on 2005-10-30
Moe458, does it work in spite of those two files?

---

