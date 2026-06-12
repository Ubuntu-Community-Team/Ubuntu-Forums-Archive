---
title: "How do i install AvastAV .deb    ...??"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by jason.b.c on 2006-07-30
> 1. Download the deb release (avast4workstation_1.0.6b-2_i386.deb)
2. Right click it and choose the 'Installer' option.



I downloaded the avast4workstation_1.0.6b-2_i386.deb package and in that quote up there it say's to right click on the .deb and choose the **"install option"**.., Funny i don't see an install option when i click on it..!!

What am i doing wrong..???

How do i install it..??

Could someone please help me install this..?

---

### Post by trent dillman on 2006-07-30
...

---

### Post by jason.b.c on 2006-07-30
> **trent dillman said:**
> If it doesn't happen by 2x click, open a terminal and use:
```
sudo dpkg -i /path/to/your/installer.deb
```

It didn't work..??

```
jason@Hp-Vectra-VL:~$ sudo dpkg -i/home/jason/Desktop/avast4workstation_1.0.6b-2_i386.deb
Password:
dpkg: unknown option -/

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jason@Hp-Vectra-VL:~$




```

Have any idea's..????

---

### Post by Perfect Storm on 2006-07-30
You forgot space between -i /the/path/

---

### Post by jason.b.c on 2006-07-30
> **Artificial Intelligence said:**
> You forgot space between -i /the/path/

Does this mean it's installed..??

```
jason@Hp-Vectra-VL:~$ sudo dpkg -i /home/jason/Desktop/avast4workstation_1.0.6b-2_i386.deb
Selecting previously deselected package avast4workstation.
(Reading database ... 57192 files and directories currently installed.)
Unpacking avast4workstation (from .../avast4workstation_1.0.6b-2_i386.deb) ...
Setting up avast4workstation (1.0.6b-2) ...

jason@Hp-Vectra-VL:~$




```

:D

---

### Post by Perfect Storm on 2006-07-30
yup.

---

### Post by jason.b.c on 2006-07-30
> **Artificial Intelligence said:**
> yup.

Ok so how do i make a desktop shortcut to it..????

I think the command is:

```
avastgui
```



I think..!?

Or do i ```
**start avastgui**
```.???

---

### Post by Perfect Storm on 2006-07-30
try with
```
whereis avast
```

or

```
locate avast
```

the command should be located in a ~/bin folder

or open synaptic and find the avast package, select properties and go to the installed files tab and find the a file located in ~/bin.

---

### Post by jason.b.c on 2006-07-30
```
jason@Hp-Vectra-VL:~$ locate avast
jason@Hp-Vectra-VL:~$ whereis avast
avast: /usr/bin/avast /usr/bin/X11/avast /usr/share/man/man1/avast.1.gz
jason@Hp-Vectra-VL:~$

```


Does this tell me what the avast executable is...?????

---

### Post by Perfect Storm on 2006-07-30
Aye, you can see that in /usr/bin/avast

so try type avast in the terminal.

---

### Post by jason.b.c on 2006-07-30
> **Artificial Intelligence said:**
> Aye, you can see that in /usr/bin/avast

so try type avast in the terminal.

Is this it..???

```
/usr/lib/avast4workstation/bin/wrapper-script.sh
```


The executable that i would make the shortcut to.

---

### Post by Perfect Storm on 2006-07-30
Don't know. I don't run any anti-virus applications (though I wrote a few howto on the subjects). 
But did the avast command worked? If so then just make a launcher and insert the command **avast**
You can properly get more information by:
```
avast --help
man avast
```

---

### Post by jason.b.c on 2006-07-30
> **Artificial Intelligence said:**
> Don't know. I don't run any anti-virus applications (though I wrote a few howto on the subjects). 
But did the avast command worked? If so then just make a launcher and insert the command **avast**
You can properly get more information by:
```
avast --help
man avast
```

Seems to work when i type avast in the terminal , Although i don't get a gui that i can interact with...?

But i guess it's scanning.....But i need the gui.

I know it has one because i had avast in windows....

---

### Post by Perfect Storm on 2006-07-30
Well I don't think avast for linux has a gui, mainly because it's aiming for server purpose. 
If you want an anti-virus with gui check the howto section for F-prot and/or AVG. I personally recommend F-prot as it seems to be the best of the two.

F-prot: [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)
AVG: [http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)

---

### Post by jason.b.c on 2006-07-30
> **Artificial Intelligence said:**
> Well I don't think avast for linux has a gui, mainly because it's aiming for server purpose. 
If you want an anti-virus with gui check the howto section for F-prot and/or AVG. I personally recommend F-prot as it seems to be the best of the two.

Well as far as i can tell it has a partial gui., Because i had to use it to aquire the activation product key and enter it..

There are options in it for , What to scan (where) , Automatic or manual updating , Scan now button , etc etc.....

But the thing is , it has another one (or at least the windows version does) , So i'm wondering if this one does as well...?

Maybe i'll go the avast forum and ask how to do it ( if it has one )....

Oh and thanks for your help....:D

---

### Post by marcusg on 2006-07-30
i'm having the same sort of problem. i just installed a .deb containing gimpshop..but I can't figure out how to launch gimpshop. i've tried

marcusg@marcusg-laptop:~$ locate gimpshop
marcusg@marcusg-laptop:~$ whereis gimpshop
gimpshop:
marcusg@marcusg-laptop:~$ gimpshop
bash: gimpshop: command not found

thanks.

typing the first letters of the app, in this case gi
then press Tab key twice, shows a list of commands starting with those letters.

marcusg@marcusg-laptop:~$ gi
gij-4.1          gimp             gimp-remote      gimptool-2.0
gij-wrapper-4.1  gimp-2.2         gimp-remote-2.2
marcusg@marcusg-laptop:~$ gi

i guessed from that list that i needed to type gimp to launch gimpshop. 
sorry if this was off topic

marcus.

---

### Post by jason.b.c on 2006-07-30
He needed a *Bump up*...

I have avast installed and it runs perfectly..

---

### Post by Perfect Storm on 2006-07-30
> **marcusg said:**
> i'm having the same sort of problem. i just installed a .deb containing gimpshop..but I can't figure out how to launch gimpshop. i've tried

marcusg@marcusg-laptop:~$ locate gimpshop
marcusg@marcusg-laptop:~$ whereis gimpshop
gimpshop:
marcusg@marcusg-laptop:~$ gimpshop
bash: gimpshop: command not found

thanks.

typing the first letters of the app, in this case gi
then press Tab key twice, shows a list of commands starting with those letters.

marcusg@marcusg-laptop:~$ gi
gij-4.1          gimp             gimp-remote      gimptool-2.0
gij-wrapper-4.1  gimp-2.2         gimp-remote-2.2
marcusg@marcusg-laptop:~$ gi

i guessed from that list that i needed to type gimp to launch gimpshop. 
sorry if this was off topic

marcus.

Try check it through synaptic, as I explained it earlier and post the file list.

---

