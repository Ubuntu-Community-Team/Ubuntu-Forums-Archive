---
title: "Installing jre-1_5_0_06-linux-i586.bin"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-09-24
Hi 

I tried to install the [COLOR="Lime"]jre-1_5_0_06-linux-i586.bin[/COLOR] so i downloaded it from the website [COLOR="Navy"]www.java.co[/COLOR]m and i used the [COLOR="Red"]chmod a+x jre-1_5_0_06-linux-i586.bin[/COLOR] to extract the package ... after that i tried to install [COLOR="SeaGreen"]limewire[/COLOR]...but it couldn't locate my java package... i think i need to copy my extracted files to[COLOR="DarkOrange"] opt folder [/COLOR]in order to do that...but i dun have the premission..what should i do ? :confused:

---

### Post by David Corrales on 2006-09-24
Get it from the repos, much easier.
**sudo apt-get install sun-java5-bin**

---

### Post by whizbaby on 2006-09-24
> **David Corrales said:**
> Get it from the repos
have *universe* and *multiverse* repositories enabled...

---

### Post by james_san on 2006-09-24
A much better idea is to install Java using synaptic (always look in synaptic before you download any programs for Ubuntu yourself... chances are that they are already there). The package is called 'sun-java5-jre', and you will probably also want 'sun-java5-plugin'. If you can't find it make sure you have all the repositories ticked under Settings -> Repositories.

After that you need to tell Ubuntu to use the sun-java5 instead of the one it comes with (which doesn't seem to work very well).
Open a terminal and type:
```
sudo update-alternatives --config java
```
Then follow the instructions and enable the Sun Java version

Then limewire should work :)

---

### Post by lifemaximum on 2006-09-24
dude i tried what u said and i got this 

[COLOR="Red"]faz@faz-laptop:~$ sudo apt-get install sun-java5-bin
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR]


what should i do next.?

---

### Post by Buffalo Soldier on 2006-09-24
[list=1]
[*] [Understandin Sudo](https://help.ubuntu.com/community/RootSudo) (Super User DO)
[*] [Methods of installing software in Ubuntu](https://help.ubuntu.com/community/InstallingSoftware)
[*] [What is a repository?](https://help.ubuntu.com/community/Repositories/Ubuntu)
[*] [Installing Java](https://help.ubuntu.com/community/Java)
[/list]

---

### Post by whizbaby on 2006-09-24
> **lifemaximum said:**
> [COLOR="Red"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.[/COLOR]

First do what deh comp suggests (with a *sudo* in front of the command of course) and post the errors of that (or retry if no errors).

---

### Post by Perfect Storm on 2006-09-24
If you want the latest version + plus a .deb (manual way):

NB: requires that you have universe/multiverse enable in your sourcelist.

Download Java Runtime Environment (JRE) 5.0 Update 8: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick **Linux self-extracting file**. Download it to your **Desktop**.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_08-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update08_i386.deb
sudo update-alternatives --config java

```
When asking for which version you want to choose pick;
```
  3        /usr/lib/j2sdk1.5-sun/bin/java
```

Testing;
```
java -version
```


Making a Launcher for Java Control Center;
```
sudo nano /usr/share/applications/java.desktop
```

fill in;

[b]
[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;
[/b]

Save and exit. <ctrl> + <o> | <ctrl> + <x>
You can find it now under Applications tab ---> System Tools.

---

### Post by mrphantastic on 2006-09-24
hey, i tried downloading the "other" and the "linux" types of limewire from limewire.com, and neither one can seem to be read by my ubuntu 6.06 LTS...i already have the java runtime/plugin, cuz i did the terminal command and enabled the java....what should i do????/

---

### Post by Perfect Storm on 2006-09-24
Download the .rpm version and convert it.

```
sudo aptitude install alien
cd /to/the/limewire.rpm
sudo alien -i Limewire.rpm
```

---

### Post by lifemaximum on 2006-09-24
or you could try installing automatix and install the forstwire...from there which is pretty much the same as limewire..

---

