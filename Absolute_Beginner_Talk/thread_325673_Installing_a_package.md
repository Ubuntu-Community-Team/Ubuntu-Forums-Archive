---
title: "Installing a package"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by agatha on 2006-12-26
Total newbie to Linux.
Installed Ubuntu Dapper OK.

Downloaded archive and extracted to desktop as the folder: "glipper-0.95.1"

What do I do to install it ?

Can someone walk me thru this, once ?

---

### Post by Titus A Duxass on 2006-12-26
Why don't you try installing it through synaptic or adept, glipper is in the repositories or from a command line do this:

sudo aptitude install glipper

---

### Post by pay on 2006-12-26
An archive is usually source code. I recommend trying synaptic or using apt to install packages. Open the terminal and type```
sudo aptitude install <package>
```
EDIT: Dang, Titus A Duxass and myself said the same thing. Anyway heres a guide thats useful when starting [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by agatha on 2006-12-26
HI, Thanks. I tried but got the following in Terminal:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
"Couldn't find any package whose name or description matched "glipper"
The following packages have been kept back:
  hal hal-device-manager libhal-storage1 libhal1 pmount
0 packages upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used."

Should I move or extract to a specific location from "glipper-0.95.1.tar.gz" , now on my desktop, first ?

---

### Post by tokj on 2006-12-26
If the file that you downloaded is a deb file, you can simply install by clicking twice on it.

Otherwise you can install it through terminal with dpkg. The commands are:
```
cd /Desktop
```

to switch on the Desktop

and
```
sudo dpkg --install filename.deb
```

to install it.

If you downloaded a source code (in other words if you downloaded an archive with extension *.tar.gz or *.tar.bz2) the installation is a little more complicate.

Excuse me for my terrible english :(

Cheers ;)

---

### Post by Sef on 2006-12-26
Read [How to Install Anything]("http://monkeyblog.org/ubuntu/installing/") in Ubuntu.

---

### Post by J-me on 2006-12-26
Thanks guys this also helped me out saved me posting at a later date. Well I hope so I'm gonna read that web pages first lol =)

---

### Post by J-me on 2006-12-26
Sorry me again 
I've tried what it says on that webpage, This is what i used
[http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif](http://monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif)

```

james@james-desktop:~$ cd /home/james/Desktop/firefox
james@james-desktop:~/Desktop/firefox$
james@james-desktop:~/Desktop/firefox$ ./configure
bash: ./configure: No such file or directory
james@james-desktop:~/Desktop/firefox$ make
bash: make: command not found
james@james-desktop:~/Desktop/firefox$


```

I also tried it for another tar.gzi had called akamaru.
Anyone know where im going wrong?

---

### Post by tokj on 2006-12-26
You have to install the "build-essential" package.

```
sudo apt-get install build-essential
```

---

### Post by tokj on 2006-12-26
For installing from source I raccomend you tu use checkinstall instead the normal procedure.

For informations about checkinstall read this [guide](https://help.ubuntu.com/community/CheckInstall).

---

### Post by J-me on 2006-12-26
Thank you for that I needed that to build them. The packages is still not installing this is what i get. 

```

james@james-desktop:~/Desktop/firefox$ make
make: *** No targets specified and no makefile found. Stop.

```

Thanks for all the help so far, Ubuntu forums are amazing! Ive been bugging you lot for 2days and no one is shy to help me. Best forum for help ever!:mrgreen:

---

### Post by Jukey on 2006-12-26
What is it that you're trying to install? the folder you're in is firefox. are you sure you unzipped/untarred it to the firefox folder or is it in a folder inside the firefox folder?

---

### Post by J-me on 2006-12-26
Yeah im sure im in the right folder I followed this [http://monkeyblog.org/ubuntu/videos/...escrobbler.gif](http://monkeyblog.org/ubuntu/videos/...escrobbler.gif)

when I first tried it, it didnt work as i didnt have the right build programs but then "tokj" set me right there. Now this is the new issue im having

```
james@james-desktop:~/Desktop/firefox$ make
make: *** No targets specified and no makefile found. Stop.
```

---

### Post by Jukey on 2006-12-26
What program are you trying to install?

---

