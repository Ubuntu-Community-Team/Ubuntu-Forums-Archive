---
title: "no rpm command?"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-11-28
I d/led jre-1_5_0_05-linux-i586.rpm.bin changed the permissions, and started unpacking then it asks, i pressed yes, and then it says rpm: comman not found...

Do you agree to the above license terms? [yes or no]
y
Unpacking...
Checksumming...
0
0
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-1_5_0_05-linux-i586.rpm
./jre-1_5_0_05-linux-i586-rpm.bin: line 593: rpm: command not found

Done.

What's rpm: command not found mean????

---

### Post by ecobuntu on 2005-11-28
[http://www.giannaros.org/public/breezydebs/sun-j2re1.5_1.5.0+update04_i386.deb](http://www.giannaros.org/public/breezydebs/sun-j2re1.5_1.5.0+update04_i386.deb)

Go there and d/l the java packages...also you need to use alien to convert a rpm to a deb package and then use dpkg to install it...thus it's a lot simpler to go that website...d/l java-1_5_0_05

To install this...run
sudo dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb

---

### Post by Turtle.net on 2005-11-28
Or you can also add the repositories ```
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

``` in your /etc/apt/sources.list (sudo gedit /etc/apt/sources.list)

and ```
sudo apt-get install sun-j2re1.5
```


simple ;)

---

### Post by ecobuntu on 2005-11-28
i think turtle's method would be easier for you.
BTW...debian based distros (i.e. Ubuntu) don't use RPMs but instead use deb files.  So if you ever have to install a rpm file because there is no alternative you must first d/l alien...
sudo apt-get install alien
then...
sudo alien *.rpm
then...
sudo dpkg -i *.deb
and everything should work

---

### Post by sjh on 2005-11-28
This guide will walk you thru the whole install:

[http://www.ubuntuforums.org/showthread.php?t=76754&highlight=install+jre+plugin+firefox](http://www.ubuntuforums.org/showthread.php?t=76754&highlight=install+jre+plugin+firefox)

---

### Post by adduds on 2005-11-28
ya i did that firefox thing, but i need the java 1.4.2 package on my computer for computer science, and eclipse comes up with an error.

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...

when i got to run my program..

It's uses a paint component to draw a tic-tac-toe board in a seperate window, other than console... so i figured my java package is messed

so i checked the version i have:

adduds@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

which seems right.... so i'm not sure what it could be

---

### Post by adduds on 2005-11-28
[QUOTE=Turtle.net] ```
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

```
simple ;)[/QUOTE]

when i type that in console it says ```
bash: deb: command not found
```

...

---

### Post by Adrian on 2005-11-28
[QUOTE=adduds]when i type that in console it says ```
bash: deb: command not found
```

...[/QUOTE]

Those two lines are not meant to be run in the terminal. They are repositories from which apt will download programs. You need to add them to your sources.list file, for instance by typing

```
sudo gedit /etc/apt/sources.list
```

and just appending them to the end of the file.

After saving the edited sources.list, type

```
sudo apt-get update
```

Now you should be able to install the program by typing
```

sudo apt-get install sun-j2re1.5
```

in the terminal, as Turtle.net said.

---

### Post by atoponce on 2005-11-28
[quote=adduds]I d/led jre-1_5_0_05-linux-i586.rpm.bin changed the permissions, and started unpacking then it asks, i pressed yes, and then it says rpm: comman not found...

Do you agree to the above license terms? [yes or no]
y
Unpacking...
Checksumming...
0
0
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-1_5_0_05-linux-i586.rpm
./jre-1_5_0_05-linux-i586-rpm.bin: line 593: rpm: command not found

Done.

What's rpm: command not found mean????[/quote]

Why did you download the rpm?  You can the the *.bin directly off of [java.sun.com]("http://java.sun.com").  Make the *.bin executable and run.  Worked flawlessly for me every time.

---

### Post by adduds on 2005-11-28
[QUOTE=Adrian]Those two lines are not meant to be run in the terminal. They are repositories from which apt will download programs. You need to add them to your sources.list file, for instance by typing
in the terminal, as Turtle.net said.[/QUOTE]

Thanks very much it's d/ling as we speak :) just needed to understand how to add those repositories.

Cheers/thanks,
ad

---

### Post by ndtoan13 on 2005-11-29
Why I get this error after follow your step? (edit source.list then sudo.. intall..)
Couldn't stat source package list [http://packages.freecontrib.org](http://packages.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/packages.freecontrib.org_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)

---

