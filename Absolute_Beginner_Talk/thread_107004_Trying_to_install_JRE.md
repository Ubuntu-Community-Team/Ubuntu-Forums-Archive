---
title: "Trying to install JRE"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by linux_is_2_hard_4_me on 2005-12-22
okay everyone. i have been using linux for about 8 hours straight now and STILL cant even install one little thing. what i'm trying to do is install the java runtime environment. i looked at the wiki page for 'Getting Java' ...but there is an error that comes up and that's where i'm stuck. i think that if i didn't get this error it would work fine and i would be well on my way by now. the error im recieving is at the step where i am supposed to make a jpkg out of jre-1_5_0_06-linux-i586.bin. heres the error i get from the command line:

```
dpkg-architecture: warning: Couldn't determine gcc system type, falling back todefault (native compilation)
sh: gcc: command not found
```

does anyone know how i can fix this, or how i can make it recognize the "gcc system type"? any help is appriciated...and i need it fast. thanks in advance!

---

### Post by arpunk on 2005-12-22
You need to install the *build-essential* metapackage which contains gcc. To do it:
```
sudo apt-get install build-essential
```

---

### Post by tmahmood on 2005-12-22
you are not supposed to build the package.. its a self extracting file.. all you have to do is
```

sh jre-1_5_0_06-linux-i586.bin

```
this will extract the files from the package...

---

### Post by audax321 on 2005-12-22
Another way is to add the penguin liberation front repositories to your /etc/apt/sources.list file.

You can edit the file by opening up a Terminal (Applications > Accessories > Terminal) and then typing: sudo gedit /etc/apt/sources.list

The servers that need to be added are available here: [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

Save the file, open up Synaptic (System > Administration > Synaptic Package Manager), Reload the servers, and search for "sun-j2re1.5". The package for java version 1.5 should pop up and you can just select it and install.

After you're done and you don't need the PLF servers anymore, make sure to edit the sources.list file again and put a # in front of the lines for the servers and Reload the list in Syaptic again. This will make Synaptic ignore those servers since you want most of your software from the official Ubuntu repositories.

---

### Post by linux_is_2_hard_4_me on 2005-12-22
okay thank you arpunk...i installed the build-essential package and now i dont get the gcc error, but im stuck on another one. it seems pretty easy to fix. whenever im running this command to convert the .bin file into a .deb as the installation instructions tell me to, i run into this problem. here is a copy of my command line:

> Extracting...
./install.sfx.21082: error while loading shared libraries: libfakeroot.so.0: can not open shared object file: No such file or directory
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 529: cd: jre1.5.0_06: No s uch file or directory
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 285: /home/tyler/.mailcap:  Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 285: /etc/mailcap: Permiss ion denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 433: /usr/share/mime-info/ java-archive.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 434: /usr/share/mime-info/ java-archive.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 435: /usr/share/mime-info/ java-archive.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 436: /usr/share/mime-info/ java-archive.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 437: /usr/share/mime-info/ java-archive.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 438: /usr/share/mime-info/ java-archive.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 441: /usr/share/mime-info/ java-archive.mime: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 442: /usr/share/mime-info/ java-archive.mime: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 445: /usr/share/applicatio n-registry/java-archive.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 446: /usr/share/applicatio n-registry/java-archive.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 447: /usr/share/applicatio n-registry/java-archive.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 448: /usr/share/applicatio n-registry/java-archive.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 449: /usr/share/applicatio n-registry/java-archive.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 450: /usr/share/applicatio n-registry/java-archive.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 433: /usr/share/mime-info/ java-web-start.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 434: /usr/share/mime-info/ java-web-start.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 435: /usr/share/mime-info/ java-web-start.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 436: /usr/share/mime-info/ java-web-start.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 437: /usr/share/mime-info/ java-web-start.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 438: /usr/share/mime-info/ java-web-start.keys: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 441: /usr/share/mime-info/ java-web-start.mime: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 442: /usr/share/mime-info/ java-web-start.mime: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 445: /usr/share/applicatio n-registry/java-web-start.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 446: /usr/share/applicatio n-registry/java-web-start.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 447: /usr/share/applicatio n-registry/java-web-start.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 448: /usr/share/applicatio n-registry/java-web-start.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 449: /usr/share/applicatio n-registry/java-web-start.applications: Permission denied
/home/tyler/Desktop/jre-1_5_0_06-linux-i586.bin: line 450: /usr/share/applicatio n-registry/java-web-start.applications: Permission denied

Done.

Testing extracted archive...
Invalid size (1 MB) of extracted archive. Probably you have not
enough free disc space in the temporary directory. Note: You can
specify an alternate directory by setting the environment variable
TMPDIR.


Aborted.

Removing temporary directory: done


-its some kind of permission denied error. i tried logging on as the root and making the .deb but it said for security reasons being under root it would not allow me to.  any suggestions? thanks everyone for all of the help.

---

### Post by linux_is_2_hard_4_me on 2005-12-22
to tmahmood:

ive also done that...executed the .bin, but it only extracts into a folder in the same directory that the .bin file is located. it doesnt actually install the files into the linux filesystem. if i knew where to put the file so it would extract itself in all the right directories, then i would do that.

to audax331:
thanks dude that seems like it would work. i will try doing that, thanks for your in-detail instructions too...haha. most people only post some command that i dont know how to run that or whatever, so i appriciate it.

---

### Post by bscbrit on 2005-12-22
You could always install j2re1.4 (otherwise known as 'blackdown') direct from synaptic.  It provides a Java runtime environment.

EDIT:  I think that you might need to invoke 'sudo' if you want a bin running in your user area to write to a system directory elsewhere.

EDIT2:  I see that audax321 has already suggested a similar solution.  Methinks that you might find the suggested alternatives easier than your current path!

---

### Post by Perfect Storm on 2005-12-22
Any reason why not using the Java packages from PLF?

---

### Post by bscbrit on 2005-12-22
None whatsoever.  Its just that j2re is already in my repos and I haven't setup PLF.

---

### Post by Perfect Storm on 2005-12-22
Ah ok :)


Anyway here it is (works only for arch i386):

First open the terminal and write:

```
sudo gedit /etc/apt/sources.list
```

add these line:

> ## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

then:

```
sudo apt-get update
sudo apt-get install sun-j2re1.5

```

If you want a shortcut to Java control center:

```
smeg
```

select **System Tool** in the left viewer and click **New Entry**.

name: **Java Control Center**
Command: **sh /usr/lib/j2re1.5-sun/bin/ControlPanel**

and here's a nice icon for it attached on this post.

---

### Post by Danielle on 2005-12-22
[QUOTE=Artificial Intelligence]

If you want a shortcut to Java control center:

```
smeg
```

select **System Tool** in the left viewer and click **New Entry**.

name: **Java Control Center**
Command: **sh /usr/lib/j2re1.5-sun/bin/ControlPanel**

and here's a nice icon for it attached on this post.[/QUOTE]
hi, i want to do this, but the path might change when i update to the latest java version. will smeg let me edit the path without any problems when i update to version jre-1_5_0_06 if the path changes? thanks

---

### Post by Perfect Storm on 2005-12-22
Aye, just open smeg and right click on the java and choose properties

---

### Post by Danielle on 2005-12-22
[QUOTE=Artificial Intelligence]Aye, just open smeg and right click on the java and choose properties[/QUOTE]
thanks, AI. i already put the .png in pixmaps :D it's about the first time i managed to do something without looking it up first.

---

### Post by Perfect Storm on 2005-12-22
Good to hear ^^

best of luck :)

---

### Post by Danielle on 2005-12-22
[QUOTE=Artificial Intelligence]Good to hear ^^

best of luck :)[/QUOTE]
thank you.

---

