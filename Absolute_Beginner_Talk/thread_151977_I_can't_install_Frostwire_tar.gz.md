---
title: "I can't install Frostwire tar.gz"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-28
I got lucky with ies4 tar.gz by typing
ies4linux/ies4linux
after I unzipped it. I don't know how to read the readme file in terminal I tried
cd / FrostWire-4.10.9/usr/lib/fros twire/README.txt
 but that puts me in some other dir

lou@c-67-163-247-106:/$ ls
bin   cdrom        dev  home    lib         media  opt   root  srv  tmp  var
boot  debootstrap  etc  initrd  lost+found  mnt    proc  sbin  sys  usr
 

How do Iinstall frostwire tar.gz file or any for that matter??](*,)

---

### Post by Qrk on 2006-03-28
Frostwire comes in a .deb package. There is no need to bother with tar.gz

[http://prdownloads.sourceforge.net/frostwire/FrostWire-4.10.9-1.i586.deb?download](http://prdownloads.sourceforge.net/frostwire/FrostWire-4.10.9-1.i586.deb?download)

Be sure to install Java first. Blackdown isn't good enough (at least it wasn't for me)

---

### Post by wolfee on 2006-03-28
[QUOTE=Qrk]Frostwire comes in a .deb package. There is no need to bother with tar.gz

[http://prdownloads.sourceforge.net/frostwire/FrostWire-4.10.9-1.i586.deb?download](http://prdownloads.sourceforge.net/frostwire/FrostWire-4.10.9-1.i586.deb?download)

Be sure to install Java first. Blackdown isn't good enough (at least it wasn't for me)[/QUOTE]
 

I dont know how to install a deb package. Everything I've done is through synaptic

---

### Post by aysiu on 2006-03-28
Any reason in particular you have to read the README file in the terminal?

---

### Post by wolfee on 2006-03-28
t won't open I keep getting an error when I click on page icon "README"

---

### Post by aysiu on 2006-03-28
[QUOTE=wolfee]I dont know how to install a deb package. Everything I've done is through synaptic[/QUOTE] It's a lot less involved than installing a .tar.gz--trust me!

Go to the Frostwire homepage and select the Debian/Ubuntu package. Download it to your desktop.

Then go to the terminal and type ```
cd ~/Desktop
sudo dpkg -i FrostWire-4.10.9-1.i586.deb
``` You may get an error. If so, consult this page:
[https://wiki.ubuntu.com/FrostWireHowTo](https://wiki.ubuntu.com/FrostWireHowTo)

---

### Post by Mustard on 2006-03-28
A .deb package would be the way to go. You can install them using the dpkg command...

```

#an example command with generic packagename.deb
sudo dpkg -i packagename.deb
```

-edit-

Beaten to the punch. I'm redundant again. :)

---

### Post by wolfee on 2006-03-29
[QUOTE=aysiu]It's a lot less involved than installing a .tar.gz--trust me!

Go to the Frostwire homepage and select the Debian/Ubuntu package. Download it to your desktop.

Then go to the terminal and type ```
cd ~/Desktop
sudo dpkg -i FrostWire-4.10.9-1.i586.deb
``` You may get an error. If so, consult this page:
[https://wiki.ubuntu.com/FrostWireHowTo](https://wiki.ubuntu.com/FrostWireHowTo)[/QUOTE]
  WOW You guys CRUSH that was easy!!! when I opened up synaptics and did frostwire search it was 4.10.9 I guess it worked no error message Now I'll see if it still craps out my cpu. Should I have uninstalled old frostwire 1st?

---

### Post by aysiu on 2006-03-29
[QUOTE=wolfee]WOW You guys CRUSH that was easy!!! when I opened up synaptics and did frostwire search it was 4.10.9 I guess it worked no error message Now I'll see if it still craps out my cpu. Should I have uninstalled old frostwire 1st?[/QUOTE] There is no old Frostwire. Any application you install using the *sudo dpkg -i* command will appear in Synaptic, and you would uninstall it the same way you would any other application you installed the "normal" Synaptic way.

---

### Post by wolfee on 2006-03-29
[QUOTE=aysiu]There is no old Frostwire. Any application you install using the *sudo dpkg -i* command will appear in Synaptic, and you would uninstall it the same way you would any other application you installed the "normal" Synaptic way.[/QUOTE]
  
It put icon on application/internet but won't launch. And synaptic has a green box so I guess it's installed wrong? O should I do Java deb package as well? This is what i got

lou@c-67-163-247-106:~$ cd ~/Desktop
lou@c-67-163-247-106:~/Desktop$ sudo dpkg -i FrostWire-4.10.9-1.i586.deb
Selecting previously deselected package frostwire.
(Reading database ... 78289 files and directories currently installed.)
Unpacking frostwire (from FrostWire-4.10.9-1.i586.deb) ...
Setting up frostwire (4.10.9-1) ...
lou@c-67-163-247-106:~/Desktop$

---

### Post by Mustard on 2006-03-29
[QUOTE=wolfee]It put icon on application/internet but won't launch. And synaptic has a green box so I guess it's installed wrong? O should I do Java deb package as well? This is what i got

lou@c-67-163-247-106:~$ cd ~/Desktop
lou@c-67-163-247-106:~/Desktop$ sudo dpkg -i FrostWire-4.10.9-1.i586.deb
Selecting previously deselected package frostwire.
(Reading database ... 78289 files and directories currently installed.)
Unpacking frostwire (from FrostWire-4.10.9-1.i586.deb) ...
Setting up frostwire (4.10.9-1) ...
lou@c-67-163-247-106:~/Desktop$[/QUOTE]

What command are you using in the menu item properties to execute it?

---

### Post by aysiu on 2006-03-29
[QUOTE=wolfee]It put icon on application/internet but won't launch. And synaptic has a green box so I guess it's installed wrong? O should I do Java deb package as well? This is what i got

lou@c-67-163-247-106:~$ cd ~/Desktop
lou@c-67-163-247-106:~/Desktop$ sudo dpkg -i FrostWire-4.10.9-1.i586.deb
Selecting previously deselected package frostwire.
(Reading database ... 78289 files and directories currently installed.)
Unpacking frostwire (from FrostWire-4.10.9-1.i586.deb) ...
Setting up frostwire (4.10.9-1) ...
lou@c-67-163-247-106:~/Desktop$[/QUOTE] It is installed. My point was simply that there was no "old" Frostwire. The one you see in Synaptic is the "new" Frostwire--the one you just installed.

From the output you just posted, it looks as if it installed cleanly. Unfortunately, not being a Frostwire user myself, I have no idea how to start it.

---

### Post by wolfee on 2006-03-29
It wont run probably because it is i586 and I'm usin i386 update kernal right?

---

### Post by Mustard on 2006-03-29
[QUOTE=aysiu]It is installed. My point was simply that there was no "old" Frostwire. The one you see in Synaptic is the "new" Frostwire--the one you just installed.

From the output you just posted, it looks as if it installed cleanly. Unfortunately, not being a Frostwire user myself, I have no idea how to start it.[/QUOTE]

What would have happened to the last version of his Frostwire that he installed via a tarball installation? (just curious myself) :)

---

### Post by Mustard on 2006-03-29
[QUOTE=wolfee]It wont run probably because it is i586 and I'm usin i386 update kernal right?[/QUOTE]

I'm not convinced that the issue is a kernel version problem.

Try typing this in terminal and show me what you get...

```
which frostwire
```

---

### Post by wolfee on 2006-03-29
lou@c-67-163-247-106:~$ which frostwire
/usr/bin/frostwire

---

### Post by Qrk on 2006-03-29
I've heard there is a problem with the latest frostwire. I just tried to install it on my system and I also couldn't get it to work at first. A look back in the forum suggests that something wasn't configured right for Linux systems (one of the files is still for windows)

Anyway this is the fix:

```
sudo apt-get install sysutils
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```

It worked for me

---

### Post by wolfee on 2006-03-29
[QUOTE=Qrk]I've heard there is a problem with the latest frostwire. I just tried to install it on my system and I also couldn't get it to work at first. A look back in the forum suggests that something wasn't configured right for Linux systems (one of the files is still for windows)

Anyway this is the fix:

```
sudo apt-get install sysutils
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```

It worked for me[/QUOTE]

You guys never cease to amaze me what a great forum group!!! **_:eek: _**

---

