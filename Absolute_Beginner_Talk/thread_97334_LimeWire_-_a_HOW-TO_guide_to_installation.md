---
title: "LimeWire - a HOW-TO guide to installation"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-11-30
Everyone has helped me a great deal on the Ubuntu forums and now it is my turn to do my part.


------------------------------
I will try to make this as easy and painless as possible but be prepaired to do some major BASHing.

Please note that all of the steps below are exactly how I installed LimeWire (ver. 4.9).



NOTE:
Please note that you will have to have the latest version of java installed on your computer first.
----------------------------




Pre-Installation:

1- Go to [http://www.Limewire.com](http://www.Limewire.com) and download the latest version (should be an RPM file).
(You should get an error message if you try to run this package as an RPM. In BASH or by Clicking)

2- Open 'Synaptic Packange Manager' and search for RPM.

3- Install RPM and all the dependancies from the Synaptic Packange Manager(If there are none, install librpm4 aswell).

---Now that we have the correct files installed to view an RPM file we can start Dismantleing the package.---


Extraction:

1- Make a NEW Folder in the /home/<yourname> directory called limewire and place the LimeWirelinux.rpm pack into it.

2- Exctract all files from the Limewirelinux.rpm pack into the new folder.(Rite Click>Extract Here).

We should now have a folder named USR.

Inside the 'usr' folder there should be 3 seperate folders. bin,lib, and share.
----



This is where you are going to put some of your BASH\Terminal skills to work.
(But, seeing how I am such a nice guy I will simply type out all the bash commands for you so you can copy and past them.)



Installation:

1- Open a Terminal window (Applications>Accessories>Terminal. GNOME users)

I will use my /home/nitricacid/limewire directory as an example for the rest of this tutorial.
You will have to substitute my name (nitricacid) with whatever you have chosen as your directory name.


In the Terminal window Type... (One at a Time)

1- ```
sudo mv /home/nitricacid/limewire/usr/bin /usr/bin
```

2- ```
sudo mv /home/nitricacid/limewire/usr/lib/LimeWire /usr/lib
```

3- ```
sudo mv  /home/nitricacid/limewire/usr/share/applications/LimeWire.desktop /usr/share/applications
```

4- ```
sudo mv /home/nitricacid/limewire/usr/share/icons/hicolor/16x16/apps/limewire.png /usr/share/icons/hicolor/16x16/apps
```

5- ```
sudo mv /home/nitricacid/limewire/usr/share/icons/hicolor/32x32/apps/limewire.png /usr/share/icons/hicolor/32x32/apps
```

6- ```
sudo mv /home/nitricacid/limewire/usr/share/icons/hicolor/48x48/apps/limewire.png /usr/share/icons/hicolor/48x48/apps
```

7- ```
sudo mv /home/nitricacid/limewire/usr/share/pixmaps/limewire.png /usr/share/pixmaps
```


-------------------

If all has gone well then you should now be able to start LIMEWIRE from your Applicastions>Internet Directory in the MenuBar.

-----------------------------------


Explanation:
How all this works is very quite simple.
You are manually installing all the files needed to run Limewire in the directories where they would be installed by the RPM program. But since Ubuntu doesn't support RPM I just installed it manually.

If you open the the three files (bin,lib, and shared) that are in the USR folder that you extracted from the limewirelinux.rpm file you can simply back track each one to where they would go onto your system in the /usr folder itself.
-------------------

---

### Post by straw on 2006-01-02
I am very new to Linux and did all of your instructions.  Everything appeared as you said it would, but it still doesn't open.  Ths is what I got as a message.  Can you advise?       Details: Failed to execute child process "limewire" (No such file or directory)    I thought I followed everything correctly.

---

### Post by Jammy_Stuff on 2006-01-02
Can't you just use alien?

---

### Post by diggs on 2006-01-02
[QUOTE=straw]I am very new to Linux and did all of your instructions.  Everything appeared as you said it would, but it still doesn't open.  Ths is what I got as a message.  Can you advise?       Details: Failed to execute child process "limewire" (No such file or directory)    I thought I followed everything correctly.[/QUOTE]Sam here, yo!

---

### Post by mcmillan on 2006-01-02
Actually it looks like if you download the "Other" file instead of the linux it gives the compressed file that you just need to extract. I don't have java working yet, since I run the 64 bit which java is a bit more complicated, so I don't know if it's more complicated, but it seems that simple.

---

### Post by nitricacid on 2006-06-17
It seems i left out that you will need java installed in order to run Limewire, Since Limewire uses java.

you can find how to install Java just by searching for it on this forum.

---

### Post by dvarsam on 2006-06-19
Dear "nitricacid",

Thanks for your Tutorial!

> It seems i left out that you will need java installed in order to run Limewire, Since Limewire uses java.
You can find how to install Java just by searching for it on this forum.

If you want, you could go & edit your beginning (original) post on this Thread, by clicking on the "scissors" icon.

Then, hopefully you can correct & fully complete your Tutorial!

Anyway, thanks for your effort & hope you will fully complete it, so that newcomers can install with no problems!

---

### Post by Skia_42 on 2006-06-21
Okay, I followed all of your instructions without problems and I checked my version of Java in the Terminal. I recieved the following output:
> 
skye@ubuntu:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
skye@ubuntu:~$

But I still recieve the following error:
> 
Details: Failed to execute child process "limewire" (No such file or directory)
Does anyone know what I need to get Limewire up and running?

---

### Post by %hMa@?b&lt;C on 2006-06-21
why not use alien. it is a heck of a lot easier.  Or if you want, you could just install the frostwire ubuntu package
[www.frostwire.com](www.frostwire.com)

---

### Post by Skia_42 on 2006-06-21
Hey thanks, I am still new to linux and was wondering. How do you install frostwire? 
(I downloaded the .deb file)

---

### Post by %hMa@?b&lt;C on 2006-06-21
sudo dpkg -i /path/to/frostwire*.deb

---

### Post by Skia_42 on 2006-06-21
I was able to install FrostWire but I still need to install Java. I downloaded j2sdk-1_4_2_12-linux-i586.bin at [http://java.sun.com/j2se/1.4.2/install-linux.html](http://java.sun.com/j2se/1.4.2/install-linux.html) and I followed all the neccesary instructions. Thisis what I did:
> 
skye@ubuntu:~$ cd Desktop
skye@ubuntu:~/Desktop$ cd Java
skye@ubuntu:~/Desktop/Java$ chmod +x j2sdk-1_4_2_12-linux-i586.bin
skye@ubuntu:~/Desktop/Java$ ./j2sdk-1_4_2_12-linux-i586.bin
                Sun Microsystems, Inc.
             Binary Code License Agreement
                     for the
JAVATM 2 SOFTWARE DEVELOPMENT KIT (J2SDK), STANDARD EDITION,
                 VERSION 1.4.2_X
#The Lisense Agreement then goes on for a while...
Do you agree to the above license terms? [yes or no]
y
Unpacking...
Checksumming...
0
0
Extracting...
./j2sdk-1_4_2_12-linux-i586.bin: line 399: ./install.sfx.12126: cannot execute binary file
Done.

I know that something went wrong with the binary file but i don't know how to solve this dilema... Any input?

---

### Post by %hMa@?b&lt;C on 2006-06-21
you need to run the .bin file as root (sudo)

---

### Post by Skia_42 on 2006-06-21
I tried that, I still get the same error message. > 
Extracting...
./j2sdk-1_4_2_12-linux-i586.bin: line 399: ./install.sfx.13064: cannot execute binary file
Done.


---

### Post by Skia_42 on 2006-06-22
Any thoughts?

---

### Post by acht on 2006-06-23
whats wrong with frostwire?

---

### Post by Perfect Storm on 2006-06-23
**The way I do it -** 
(This require universe and multiverse in your sourcelist, check - to set it up [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Download the newest Java j2re (JRE 5.0 Update 7) from here:  [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) pick **Linux self-extracting file** and save it to your **Desktop**.
Open the terminal (Applications tab ---> Accessories --- terminal) and write: 

```
cd Desktop
sudo apt-get install fakeroot java-package java-common build-essential
fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
sudo update-alternatives --config java
java -version
```

Under **sudo update-alternatives --config java** you choose **/usr/lib/j2sdk1.5-sun/bin/java**

Now java is installed
Next Limewire:

Download Limewire **Linux .rpm file** and save it to you **Desktop**.
Open the terminal:
```
cd && cd Desktop
sudo apt-get install alien
sudo alien -i LimeWireLinux.rpm
```

Done.

You can start limewire under applications tab ---> Internet.

---

### Post by Skia_42 on 2006-06-23
okay I tryed that, the first step went without trouble but I got the following 2 errors for the next two steps:> 
skye@ubuntu:~/Desktop$ sudo apt-get install fakeroot java-package java-common build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
java-package is already the newest version.
java-common is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://www.beerorkid.com](http://www.beerorkid.com) breezy/main Packages (/var/lib/apt/lists/www.beerorkid.com_automatix_apt_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://www.beerorkid.com](http://www.beerorkid.com) breezy/main Packages (/var/lib/apt/lists/www.beerorkid.com_automatix_apt_dists_breezy_main_binary-powerpc_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
skye@ubuntu:~/Desktop$ fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXhx7xca
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
skye@ubuntu:~/Desktop$ sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
dpkg: error processing sun-j2re1.5_1.5.0+update07_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-j2re1.5_1.5.0+update07_i386.deb
skye@ubuntu:~/Desktop$


---

### Post by Perfect Storm on 2006-06-24
It may be because it's done diffrently on PPC structure, I don't know. I'm using i386

---

### Post by aeto on 2006-06-24
[*Deleted*]

*[size=1]Such talk are not permitted on the ubuntuforums.org, read the guidelines. Thanks. - Artificial Intelligence*[/size]

---

### Post by Geek Sanity on 2006-06-24
I'm getting the > Cannot launch entry

Details: Failed to execute child process "limewire" (No such file or directory) 
error myself.  I had to change /home/sanity (my home folder) to mnt/vanyel because my home folder is too small to install anything to except my OS.  mnt/vanyel is my bigger hd, which is setup as a seperate mnt point.

Is it like *shudder* windows, where you have to restart for new things to take effect?

---

### Post by user1397 on 2006-06-24
People Please!  To install java, just follow this wiki guide: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java") and to install limewire, follow this wiki guide: [https://help.ubuntu.com/community/P2PHowTo]("https://help.ubuntu.com/community/P2PHowTo")
(This is limewire version 4.10 anyway, so it's newer)

---

### Post by karloz on 2006-06-24
[QUOTE=Artificial Intelligence]**The way I do it -** 
(This require universe and multiverse in your sourcelist, check - to set it up [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Download the newest Java j2re (JRE 5.0 Update 7) from here:  [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) pick **Linux self-extracting file** and save it to your **Desktop**.
Open the terminal (Applications tab ---> Accessories --- terminal) and write: 

```
cd Desktop
sudo apt-get install fakeroot java-package java-common build-essential
fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
sudo update-alternatives --config java
java -version
```

Under **sudo update-alternatives --config java** you choose **/usr/lib/j2sdk1.5-sun/bin/java**

Now java is installed
Next Limewire:

Download Limewire **Linux .rpm file** and save it to you **Desktop**.
Open the terminal:
```
cd && cd Desktop
sudo apt-get install alien
sudo alien -i LimeWireLinux.rpm
```

Done.

You can start limewire under applications tab ---> Internet.[/QUOTE]


Thank you!!!   I've been working on my stupid Java all morning, and I finally did it this way and it worked!!!   Thanks again!

---

### Post by Just-trevor on 2007-08-21
for some reason I downloaded the package and its a deb file, does that matter?

---

### Post by mcmillan on 2007-08-22
> **Just-trevor said:**
> for some reason I downloaded the package and its a deb file, does that matter?

Notice the last post on this thread was over a year ago. Before files weren't available as .deb, only rpms. Looks like limewire has started distributing packages for debian based systems now. 

Just install the deb like you usually do:
sudo dpkg -i [file name]

I'm pretty sure you still need to install java seperatly. That should be more or less the same as in this thread

---

### Post by proxxer on 2007-09-14
Just go to [www.limewire.com](www.limewire.com) and it wil be a limewire for ubuntu there;)

---

