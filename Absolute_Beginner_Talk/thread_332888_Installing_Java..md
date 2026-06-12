---
title: "Installing Java."
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Axis on 2007-01-06
I am trying to install java on the computer but it requires a manual install and I have no clue how to do it. Which file do I download from here 

[http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)

and then how do I install it after I download the file?

Thanks alot,
Axis

---

### Post by vijayanand_sodadasi on 2007-01-06
Hi, I assume you are trying to install jdk on your machine.  Check this link
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0")

---

### Post by taurus on 2007-01-06
Linux (self-extracting file).

---

### Post by oyvindaa on 2007-01-06
First you'll need to enable your universe and multiverse repositories.

Then do this in the terminal:

```
sudo apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts
```

During the installation you'll have to agree with the DLJ license terms.

At this point, Java is installed.

Check your installation:

```
java -version
```

Should say something like:

```
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition etc etc
```

If it doesn't, do this:

```
sudo update-alternatives --config java
```

From there, pick the Sun version by entering the correct number and press Enter.

To check whether the plugin is installed, type this in your browser (address bar):

```
about:config
```

And you'll hopefully see some information about the plugin and whether it's enabled or not.

---

### Post by jporter91 on 2007-01-06
Just install it with automatix2 ([www.getautomatix.com)](www.getautomatix.com)).

---

### Post by Sasa_Ivanovic on 2007-01-06
yeah java rules!!!
but what are you trying to install ?
jre, jdk, or firefox plugin ?

---

### Post by oyvindaa on 2007-01-06
Well his link is to a JRE download, isn't it? ;)

---

### Post by Severa on 2007-01-06
Thank you kindly, oyvindaa, your instructions worked perfectly for me. :-D

---

### Post by newagelink on 2007-01-07
Grr. I installed the wrong package. Stupid me.
```
daniel@daniel-laptop:~$ sudo apt-get install sun-java5-jdk
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libltdl3 odbcinst1debian1 sun-java5-bin sun-java5-demo sun-java5-jre
  unixodbc
Suggested packages:
  sun-java5-doc sun-java5-source sun-java5-plugin ia32-sun-java5-plugin
  sun-java5-fonts libmyodbc odbc-postgresql libct1
The following NEW packages will be installed:
  libltdl3 odbcinst1debian1 sun-java5-bin sun-java5-demo sun-java5-jdk
  sun-java5-jre unixodbc
0 upgraded, 7 newly installed, 0 to remove and 4 not upgraded.
Need to get 44.8MB of archives.
After unpacking 117MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com dapper/main libltdl3 1.5.22-2 [168kB]
Get:2 http://archive.ubuntu.com dapper/main odbcinst1debian1 2.2.11-11build1 [63.8kB]
Get:3 http://archive.ubuntu.com dapper/main unixodbc 2.2.11-11build1 [269kB]
Get:4 http://archive.ubuntu.com dapper/multiverse sun-java5-bin 1.5.0-06-1 [22.1MB]
Get:5 http://archive.ubuntu.com dapper/multiverse sun-java5-jre 1.5.0-06-1 [7341kB]
Get:6 http://archive.ubuntu.com dapper/multiverse sun-java5-demo 1.5.0-06-1 [9869kB]
Get:7 http://archive.ubuntu.com dapper/multiverse sun-java5-jdk 1.5.0-06-1 [4986kB]
Fetched 44.8MB in 54s (830kB/s)
Preconfiguring packages ...
Selecting previously deselected package libltdl3.
(Reading database ... 94978 files and directories currently installed.)
Unpacking libltdl3 (from .../libltdl3_1.5.22-2_i386.deb) ...
Selecting previously deselected package odbcinst1debian1.
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-11build1_i386.deb) ...
Selecting previously deselected package unixodbc.
Unpacking unixodbc (from .../unixodbc_2.2.11-11build1_i386.deb) ...
Selecting previously deselected package sun-java5-bin.
Unpacking sun-java5-bin (from .../sun-java5-bin_1.5.0-06-1_i386.deb) ...
Selecting previously deselected package sun-java5-jre.
Unpacking sun-java5-jre (from .../sun-java5-jre_1.5.0-06-1_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java5-demo.
Unpacking sun-java5-demo (from .../sun-java5-demo_1.5.0-06-1_i386.deb) ...
Selecting previously deselected package sun-java5-jdk.
Unpacking sun-java5-jdk (from .../sun-java5-jdk_1.5.0-06-1_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Setting up libltdl3 (1.5.22-2) ...

Setting up odbcinst1debian1 (2.2.11-11build1) ...

Setting up unixodbc (2.2.11-11build1) ...

Setting up sun-java5-jre (1.5.0-06-1) ...
Setting up sun-java5-bin (1.5.0-06-1) ...

Setting up sun-java5-demo (1.5.0-06-1) ...

Setting up sun-java5-jdk (1.5.0-06-1) ...

daniel@daniel-laptop:~$
```So, now that I've installed that, I'm going to try ```
sudo apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts
``` ...
I think I got an error when I tried it: ```
daniel@daniel-laptop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin sun- java5-fonts
Password:
Reading package lists... Done
Building dependency tree... Done
sun-java5-jre is already the newest version.
The following NEW packages will be installed:
  sun-java5-fonts sun-java5-plugin
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 3158B of archives.
After unpacking 180kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/multiverse sun-java5-fonts 1.5.0-06-1 [18 24B]
Get:2 http://archive.ubuntu.com dapper/multiverse sun-java5-plugin 1.5.0-06-1 [1 334B]
Fetched 3158B in 0s (6447B/s)
Selecting previously deselected package sun-java5-fonts.
(Reading database ... 97780 files and directories currently installed.)
Unpacking sun-java5-fonts (from .../sun-java5-fonts_1.5.0-06-1_all.deb) ...
Selecting previously deselected package sun-java5-plugin.
Unpacking sun-java5-plugin (from .../sun-java5-plugin_1.5.0-06-1_i386.deb) ...
Setting up sun-java5-fonts (1.5.0-06-1) ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.

Setting up sun-java5-plugin (1.5.0-06-1) ...

daniel@daniel-laptop:~$
```What does that mean ...?

---

### Post by oyvindaa on 2007-01-07
> **Severa said:**
> Thank you kindly, oyvindaa, your instructions worked perfectly for me. :-D

That's great! Glad to help :)

---

### Post by oyvindaa on 2007-01-07
> **newagelink said:**
> So, now that I've installed that, I'm going to try ```
sudo apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts
``` ...

I think I got an error when I tried it: ```
daniel@daniel-laptop:~$ sudo apt-get install sun-java5-jre sun-java5-plugin sun- java5-fonts
Password:
Reading package lists... Done
Building dependency tree... Done
sun-java5-jre is already the newest version.
The following NEW packages will be installed:
  sun-java5-fonts sun-java5-plugin
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 3158B of archives.
After unpacking 180kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com dapper/multiverse sun-java5-fonts 1.5.0-06-1 [18 24B]
Get:2 http://archive.ubuntu.com dapper/multiverse sun-java5-plugin 1.5.0-06-1 [1 334B]
Fetched 3158B in 0s (6447B/s)
Selecting previously deselected package sun-java5-fonts.
(Reading database ... 97780 files and directories currently installed.)
Unpacking sun-java5-fonts (from .../sun-java5-fonts_1.5.0-06-1_all.deb) ...
Selecting previously deselected package sun-java5-plugin.
Unpacking sun-java5-plugin (from .../sun-java5-plugin_1.5.0-06-1_i386.deb) ...
Setting up sun-java5-fonts (1.5.0-06-1) ...
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.
Use of uninitialized value in print at /var/lib/defoma/scripts/gs.defoma line 10 8.

Setting up sun-java5-plugin (1.5.0-06-1) ...

daniel@daniel-laptop:~$
```What does that mean ...?

I think your install might be ok. Have you tested the plugin?

about:config in your browser address bar should tell the tale.

---

