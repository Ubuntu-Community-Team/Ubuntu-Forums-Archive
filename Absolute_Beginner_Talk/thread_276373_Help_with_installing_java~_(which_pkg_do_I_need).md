---
title: "Help with installing java~ (which pkg do I need?)"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by UnknownVariable on 2006-10-12
I downloaded the ubuntu package of frostwire from [www.frostwire.com](www.frostwire.com). Upon clicking it's entry in my applications menu, nothing would happen. Being the bright guy I am, I tried to run it manually through the terminal and received this:

```
alexander@alex-laptop:/usr/lib/frostwire$ ./runFrost.sh
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
alexander@alex-laptop:/usr/lib/frostwire$
```

Synaptic says I currently have these following java related packages installed. Am I missing some, or do I need to install a different JRE from java.com?

```
bsh
epiphany-extensions
fastjar
gcj-4.1-base
gdb
gij-4.1
java-common
java-gcj-compat
konqueror
libapache2-mod-php5
libbcprov-java
libcairo-java
libcommons-cli-java
libgcj7
libgcj7-jar
libgcj-common
libglib-java
libgnome-speech3
libgnucrypto-java
libgtk-java
libgtk-jni
libgtksourceview-common
libhsqldb-java
libjaxp1.2-java
libjessie-java
libjiline-java
liblog4j1.2-java
libseda-java
libservlet2.3-java
libswt3.1-gtk-java
libswt3.1-gtk-jni
libxalan2-java
libxerces2-java
libxt-java
mozilla-browser
openoffice.org
openoffice.org-base
openoffice.org-java-common
php5
php5-cli
php5-common
php5-curl
php5-gd
php5-mhash
php5-mysql
php5-mysqli
php-pear
python2.4-epydoc
python-epydoc
screem
```

Yes, I realize a lot of those aren't directly related to java, but all I did was go into synaptic, search for "java" in titles and descriptions, and list all that came up in the list as installed. :D

Thanks. :)

---

### Post by bollix47 on 2006-10-12
Try searching for sun-java.

Make sure you have universe and multiverse repositories activated.

synaptic - settings - repositories

reload after adding

---

### Post by dmizer on 2006-10-12
there may be more helpful information for java implimentation here:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by UnknownVariable on 2006-10-12
I can confirm that the Java Runtime Environment 5.0 has been installed. This is shown in both Applications -> Add / Remove and in Synaptic. However, when I try to run frostwire I still receive this:

```
alexander@alex-laptop:/usr/lib/frostwire$ ./runFrost.sh
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
alexander@alex-laptop:/usr/lib/frostwire$
```

I did a search through my files and found that the folder named java is located in /usr/bin when frostwire is looking for it in /usr/java.

How do I fix this? D:

---

### Post by dmizer on 2006-10-14
i'm not positive (only because i don't use frostwire), but you should be able to either edit the runFrost.sh script with your favorite text editor and change the directory, or some other config file.

---

### Post by Perfect Storm on 2006-10-14
```
sudo update-alternatives --config java
```

pick:
```
3        /usr/lib/j2sdk1.5-sun/bin/java
```


If you want the latest java as a .deb package read on:




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

### Post by s0c0 on 2006-10-21
Here's what worked for me when trying to get limewire working.  First I installed the jre and othber java related stuff using easyubuntu.  I then went to java.com to verify java was working correctly.  Next I downloaded limewire (the non-rpm self-extracting linux version).

I then had to edit runLime.sh so it would find the java files:  Just make your runLime.sh look like this and it may work as with most stuff in Linux:

```

look_for_java()
{
 JAVADIR=/usr/
 if look_for_javaImpl ; then
    return 0
 fi
 JAVADIR=/usr/share/
 if look_for_javaImpl ; then
       return 0
 fi
 JAVADIR=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06
 if look_for_javaImpl ; then
       return 0
 fi
 return 1
}


```

Note, the important directory is /usr/lib/jvm/java-1.5.0-sun-1.5.0.06.  Thats where they hid the files.  The other directories were just trial & and error.  If your java files are not located in there maybe just run a search for the jvm or java-1.5.* .... Maybe oneday Linux will get some standards on where stuff goes, until then we are stuck with this.

And now I'm listening to some RATM - No Shelter.

---

### Post by infoseeker on 2006-10-21
These are the settings I had to use.....they seem to differ from user to user, depending.........
```
[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/java/jre1.5.0_06/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;

```
Just search for 'ControlPanel' and you should find it.
```
#cd /
#find -iname ControlPanel
#./usr/java/jre1.5.0_06/bin/ControlPanel

```
BTW. where is the icon?  In Kubuntu I get no icon in the menu, but I do get an icon if I copy the menu item to the desktop.
EDIT. Found them in '/usr/java/jre1.5.0_06/lib/images/icons/'

---

