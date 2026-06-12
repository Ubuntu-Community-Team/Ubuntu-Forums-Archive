---
title: "Help installing Java"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by cudayne on 2006-09-28
I have looked an read what I could about this but I am still stuck.

I have both self extraction files on my descktop from sun I enable them to extract I double click on them to extract. Read the EULAG type yes an it extracts to where i dont know I found it once but then I couldn figure out how to install it an now I can't even find it again.

1. went to suns web sight got the java self extraction files(both)

2. right clicked an went to properties an enabled it to execute

3. went through the EULA typed yes

4. No idea where it extracted it too

5. cant make heads or tails out of how to make it work when i find where it did extract it too.

Would app. any idiot prrof instructions an or direction I can be pointed too as I just cant figure this out at all even after reading the wiki an suns own instructions.

---

### Post by Perfect Storm on 2006-09-28
If you want the latest version + plus a .deb (manual way):

NB: (important) requires that you have universe/multiverse enable in your sourcelist.

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

### Post by Sef on 2006-09-28
First enable the repositories.

To enable them, [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu#what")

Then Applications > Add/Remove > in the search box, type in 'SunJava' (without the quotes) > click Sun Java 5.0 Runtime

---

### Post by scottym on 2006-10-09
Thank you for all the replies. I have it installed but now am getting the following:

Error: Could not find libjava.so
Error: could not find Java 2 Runtime Enviromment.

The first seems to be a bug but I don't know how to fix it.

---

### Post by Perfect Storm on 2006-10-09
Which one of the howto did you follow?

---

### Post by n0dl on 2006-10-09
Well the best way to install java is to move the binary into /usr/lib then execute the binary in that directory. Once that is done simply cd into /usr/lib/firefox/plugins and ln -s /location/of/java/plugin.so . as root (the . is mandatory fore it stands for "make this symbolic link in this directory). For some reason sudo does not install and unpack jre in the correct directory.

---

### Post by [D-Tail] on 2006-11-21
Artificial Intelligence, I tried to get the latest sun java working on my Edgy system (that is, the one supplied in the repositories, 1.5.0_08). The point is that I can install it well, and use update-alternatives --config java too, to set the default java to the newly installed 1.5.0_08, but when I do a java -version I still get a ```
d-tail@malhavoc:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
```The output of update-alternatives --display java is:```
d-tail@malhavoc:~$ update-alternatives --display java
java - status is manual.
 link currently points to /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
/usr/lib/jvm/java-gcj/jre/bin/java - priority 1041
 slave java.1.gz: /usr/lib/jvm/java-gcj/man/man1/java.1.gz
/usr/bin/gij-wrapper-4.0 - priority 40
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.0.1.gz
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java - priority 53
 slave java.1.gz: /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/man/man1/java.1.gz
/usr/bin/gij-wrapper-4.1 - priority 41
 slave java.1.gz: /usr/share/man/man1/gij-wrapper-4.1.1.gz
Current `best' version is /usr/lib/jvm/java-gcj/jre/bin/java.

```Can you possibly shed any light on this?

---

### Post by Perfect Storm on 2006-11-21
Uninstall the previous version first.

---

### Post by hod139 on 2006-11-21
Also, you should be using
```

sudo update-java-alternatives -s java-1.5.0-sun

```
to update the java alternatives.

---

### Post by [D-Tail] on 2006-11-23
The trick was to manually remove the java 1.5.0_06 (which I had installed manually, but forgot that I did that... :(). It struck me that there wasn't a single Java package selected anymore in Synaptic, well, this was the proper reason :P
Next, after a long search ('which java' yielded a good result) I had to remove a $PATH extension in my .bashrc. I also forgot that I did that manually, to have Java 1.5.x on Breezy, all those months ago. Having done that, I logged out and in, and it all seems to be working just fine now! Running 1.5.0_08 as we speak. Thanks everyone for the help & continuing support!

---

