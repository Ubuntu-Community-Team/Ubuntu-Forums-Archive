---
title: "how to run installed apps?"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by vvnoob on 2005-11-30
i have installed some apps like hamachi,bittornado etc..but i have no idea how to run them.They do not apear in applications meni, and there is no such thing like windows program files folder in ubuntu 5.04.Tiping in command line "bittornado","hamachi" does not help>command not found :confused: . What now?
2nd question is how to install Jawa?I need it for azureus.
3rd how to add installed apps in application meni?

---

### Post by matthewv on 2005-11-30
did you install the apps through synaptic/add applications/apt-get??
If you did they should appear in the menus

---

### Post by oskude on 2005-11-30
[QUOTE=vvnoob]and there is no such thing like windows program files folder in ubuntu 5.04.[/QUOTE]well, there are more places than one in linux, but on ubuntu its mostly```
/usr/bin
```
and a tip: the program name you can run, is not allways the same as the name of the package. try "man bittornado" and "man hamachi"...
(i would also like to know how to determine what program name was installed...)

---

### Post by manicka on 2005-11-30
[QUOTE=vvnoob]
2nd question is how to install Jawa?I need it for azureus.[/QUOTE]

[http://doc.gwos.org/index.php/PLF](http://doc.gwos.org/index.php/PLF)


[QUOTE=vvnoob]3rd how to add installed apps in application meni?[/QUOTE]

Applications --> System Tools --> Applications Menu Editor

---

### Post by vvnoob on 2005-11-30
@ oskude i found bittornado files in /usr/bin before with file browser but i do not know wich one to run and how.
@manichka   i have not option in application> system tools >Applications Menu Editor:confused: .only add remove programs.how to bring back this option in ubuntu 5.04?

@mathewi have installed bittornado thru synaptic, hamachi thru command line

@oskude when i tipe man bittornado i get answer bittornado can not be run manually:confused:

---

### Post by oskude on 2005-11-30
[QUOTE=vvnoob]@oskude when i tipe man bittornado i get answer bittornado can not be run manually:confused:[/QUOTE]i never used bittornado, and "man bittornado" doesnt give me nothing (yeah, i apt-got it)... but "apt-cache show bittornado" shows```
This package only contains the curses interfaces, install the package bittornado-gui to get the GUI components
```
and reading the manual on their site that says```
f you're using a web browser which doesn't respect /etc/mailcap you can go into the mime-type configuration for your web browser and manually associate application/x-bittorrent with btdownloadgui.py (with the appropriate path, of course.)
```so i tried "locate btdownloadgui.py" but it was not there... so you may have to install that "bittornado-gui"... i wonder why theres no commandline client...

ps. yes, i tested these on ubuntu hoary...

---

### Post by vvnoob on 2005-11-30
@oskude
 tnx i did all this and now i can run bittornado with command line and with "run application" and still have not bittorent in applications meni.

Can you pls help me about this  "Applications Menu Editor" in system tools?
is it standard ubuntu 5.04 realese? i did not find something similar in synaptic package manager.How to install this feature? It will help me in the future and to 4 example get bittorent in application meni.

TNX

---

### Post by oskude on 2005-11-30
dunno what gnome uses in breezy, thats not in hoary...
you could try "smeg" (but i never used it)

or add a "custom application launcher" to your gnome-panel...

but there should be an "easy" way to manually add those gnome menu entries, im just too lazy to google...

---

### Post by manicka on 2005-12-01
[QUOTE=vvnoob]@oskude
Can you pls help me about this  "Applications Menu Editor" in system tools?
is it standard ubuntu 5.04 realese? i did not find something similar in synaptic package manager.How to install this feature? It will help me in the future and to 4 example get bittorent in application meni.
TNX[/QUOTE]

Ah, didn't realise you were using hoary :)

You can download a version of smeg (Applications Menu Editor) that will run in hoary at the link below. 

[http://dev.realistanew.com/smeg/0.7.5/smeg_0.7.5-0ubuntu1_all.deb](http://dev.realistanew.com/smeg/0.7.5/smeg_0.7.5-0ubuntu1_all.deb)

Download it to your desktop, then in a terminal change to your desktop

```
cd Desktop
```

and run the command

```
sudo dpkg -i smeg_0.7.5-0ubuntu1_all.deb
```

Restart gnome and smeg will be in the menus somewhere. Under System Tools from memory.

---

### Post by vvnoob on 2005-12-01
[QUOTE=manicka]
and run the command

```
sudo dpkg -i smeg_0.7.5-0ubuntu1_all.deb
```[/QUOTE]

after this i become this:

(Reading database ... 66970 files and directories currently installed.)
Unpacking smeg (from .../smeg_0-1.7.5-0ubuntu1_all.deb) ...
dpkg: dependency problems prevent configuration of smeg:
 smeg depends on python-xdg (>= 0.14); however:
  Version of python-xdg on system is 0.9-1.
dpkg: error processing smeg (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 smeg

i have python-xdg but it is new version should i deinstall it and install olderer version?

And thank you for your help

---

### Post by manicka on 2005-12-01
hmmm, that version of smeg must have relied on a python backport. You could try some of the older 0.7 releases until you find one that works.

Find them here    [http://dev.realistanew.com/smeg/](http://dev.realistanew.com/smeg/)

Edit: I just noticed that you can get the python 0.14 package at the link above. You could try downloading that and installing it with dpkg, then have a go at the smeg 0.75 package again

---

### Post by gruepig on 2005-12-01
[QUOTE=oskude]
(i would also like to know how to determine what program name was installed...)[/QUOTE]

If you know the name of an installed package, you can run 'dpkg -L <packagename>' in the terminal to list all files installed by the package.  Most likely the binary (program name) is one of the ones in /usr/bin/ (or /usr/sbin/).  Conversely, if you know the name of a file, but not the name of the package it came from, you can run 'dpkg -S <file>'.

---

### Post by vvnoob on 2005-12-01
Big TNX for all. Smeg is in takt and work fine. I find tnx to manicka and some similiar software "alacarta" so i will tru bouth.

But i have some more questions:)  :

How to insatall "jre-1_5_0_05-linux-i586.bin" ? i  downloaded it but it is "bin" so with      
  "sudo alien jre-1_5_0_05-linux-i586.bin"  i can not convert it in .deb package.
So the question is how to install .bin package in unbutu 5.04?

---

### Post by manicka on 2005-12-01
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

