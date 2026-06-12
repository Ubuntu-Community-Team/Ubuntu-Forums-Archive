---
title: "i installed jdk1.5 but can't compile java programs"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-25
hello to every one

  i have recently installed ubuntu on my pc.i was much pleased to see its graphics and its office tools.i have two operating systems on my pc

1-windows
2-ubuntu

i want to use ubuntu only bcoz it is nice

i have installed jdk1.5 update 6
i installed using the instruction given in sun microsystem site but when i compile using javac command, it says javac command not found
i also gave it  direction to the directory where i installed it but still it  did'nt work.it says javac command not found.

all directories which should be in jdk are present.
i am not new to linux at all but new to ubuntu
plz reply as soon as possible

---

### Post by meng on 2006-05-25
If you're getting "command not found", then javac cannot be in the PATH. Precisely what do you mean when you say you gave it direction to the directory?

---

### Post by colo on 2006-05-25
Please post the output of the following commands:
```
echo $PATH
```
```
find / -type f -a -name javac 2>/dev/null
```

---

### Post by mlind on 2006-05-25
You should install Sun's java directly from repositories or
the preferred [debian way]("https://wiki.ubuntu.com/RestrictedFormats#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e")

---

### Post by u04f061 on 2006-05-25
[QUOTE=colo]Please post the output of the following commands:
```
echo $PATH
```
```
find / -type f -a -name javac 2>/dev/null
```[/QUOTE]

here is the output

ejaz@ejaz:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
ejaz@ejaz:~$ find / -type f -a -name javac 2>/dev/null

/home/ejaz/jdk/jdk1.5.0_06/bin/javac
ejaz@ejaz:~$
ejaz@ejaz:~$

plz can u explain these commands

i've been using redhat in my lab of data structures in java .i only worked on pannel and only know how to use pannel commands for running and compiling programming languages

thnk u 4 u'r nice help

---

### Post by u04f061 on 2006-05-25
[QUOTE=meng]If you're getting "command not found", then javac cannot be in the PATH. Precisely what do you mean when you say you gave it direction to the directory?[/QUOTE]

this is the result of commands given by one of nice guy

ejaz@ejaz:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
ejaz@ejaz:~$ find / -type f -a -name javac 2>/dev/null

/home/ejaz/jdk/jdk1.5.0_06/bin/javac
ejaz@ejaz:~$
ejaz@ejaz:~$

now i give u the result of what i did

ejaz@ejaz:~$ ls
Desktop  download-manager  hello.java  jdk  sofwrs
ejaz@ejaz:~$ javac hello.java
bash: javac: command not found
ejaz@ejaz:~$

this i did bcoz on sun's site it was advised to do so

here is another simulation

ejaz@ejaz:~$ ls
Desktop  download-manager  hello.java  jdk  sofwrs
ejaz@ejaz:~$ cd jdk
ejaz@ejaz:~/jdk$ ls
hello.java   jdk-1_5_0_06-linux-i586.bin  jdk-1_5_0_06-linux-i586-rpm.bin
jdk1.5.0_06  jdk-1_5_0_06-linux-i586.rpm
ejaz@ejaz:~/jdk$ javac hello.java
bash: javac: command not found
ejaz@ejaz:~/jdk$

this is the  complete simulation which i used to do in ms-dos,and tried to ubuntu.
this was also recommended in sun's site.in laba i used to work on redhat but there was not such a problem


ejaz@ejaz:~/jdk$ ls
hello.java   jdk-1_5_0_06-linux-i586.bin  jdk-1_5_0_06-linux-i586-rpm.bin
jdk1.5.0_06  jdk-1_5_0_06-linux-i586.rpm
ejaz@ejaz:~/jdk$ cd jdk1.5.0_06
ejaz@ejaz:~/jdk/jdk1.5.0_06$ ls
bin        hello.java  lib      README.html  THIRDPARTYLICENSEREADME.txt
COPYRIGHT  include     LICENSE  sample
demo       jre         man      src.zip
ejaz@ejaz:~/jdk/jdk1.5.0_06$ javac hello.java
bash: javac: command not found
ejaz@ejaz:~/jdk/jdk1.5.0_06$ cd bin
ejaz@ejaz:~/jdk/jdk1.5.0_06/bin$ ls
appletviewer   jar        java-rmi.cgi  jsadebugd  ktab          rmiregistry
apt            jarsigner  javaws        jstack     native2ascii  serialver
ControlPanel   java       jconsole      jstat      orbd          servertool
extcheck       javac      jdb           jstatd     pack200       tnameserv
hello.java     javadoc    jinfo         keytool    policytool    unpack200
HtmlConverter  javah      jmap          kinit      rmic
idlj           javap      jps           klist      rmid
ejaz@ejaz:~/jdk/jdk1.5.0_06/bin$ javac hello.java
bash: javac: command not found
ejaz@ejaz:~/jdk/jdk1.5.0_06/bin$ cd javac
bash: cd: javac: Not a directory
ejaz@ejaz:~/jdk/jdk1.5.0_06/bin$ ls
appletviewer   jar        java-rmi.cgi  jsadebugd  ktab          rmiregistry
apt            jarsigner  javaws        jstack     native2ascii  serialver
ControlPanel   java       jconsole      jstat      orbd          servertool
extcheck       javac      jdb           jstatd     pack200       tnameserv
hello.java     javadoc    jinfo         keytool    policytool    unpack200
HtmlConverter  javah      jmap          kinit      rmic
idlj           javap      jps           klist      rmid
ejaz@ejaz:~/jdk/jdk1.5.0_06/bin$ javac hello.java
bash: javac: command not found
ejaz@ejaz:~/jdk/jdk1.5.0_06/bin$

---

### Post by u04f061 on 2006-05-25
[QUOTE=mlind]You should install Sun's java directly from repositories or
the preferred [debian way]("https://wiki.ubuntu.com/RestrictedFormats#head-fabecb1554d75cd3116507e4da83335d4e4f8f3e")[/QUOTE]

can u tell me how to install from repositories

---

### Post by meng on 2006-05-25
Okay thanks for taking the time to be specific. Here's my advice:
1) Linux looks for commands in known folders/directories, those specified in the PATH (by the way Windows does this too!). javac is not in your PATH, but you can add /home/ejaz/jdk/... to your PATH if you wish.
2) If you want to run javac from the (non-PATH) directory you are presently in, as with your last example, you must preface with ./ as in "./javac hello.java". This is slightly different from Windows.

---

### Post by mlind on 2006-05-25
[QUOTE=u04f061]can u tell me how to install from repositories[/QUOTE]

1) add multiverse repository using [AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")
2) open terminal and type 

```

sudo apt-get update
sudo apt-get install fakeroot java-package java-common

```

---

### Post by mlind on 2006-05-25
Don't worry about those missing PATH entries.

After you've done installing java by the java-package way.

do
```

sudo update-alternatives --config java
sudo update-alternatives --config javac

```

as it's said on that wiki. Then correct java and javac will automatically be on your PATH.

---

### Post by meng on 2006-05-25
Yeah, what mlind said. Just use one method. This is probably the most appropriate for you.

---

### Post by u04f061 on 2006-05-25
[QUOTE=mlind]1) add multiverse repository using [AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")
2) open terminal and type 

```

sudo apt-get update
sudo apt-get install fakeroot java-package java-common

```[/QUOTE]

i used graphical demonstration on the link u gave.the following error message appeared

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Temporary failure resolving 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Temporary failure resolving 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Temporary failure resolving 'us.archive.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Temporary failure resolving 'security.ubuntu.com'

plz plz reply to this
thnx

---

### Post by mlind on 2006-05-25
[QUOTE=u04f061]i used graphical demonstration on the link u gave.the following error message appeared

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Temporary failure resolving 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg:) Temporary failure resolving 'us.archive.ubuntu.com'
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Temporary failure resolving 'us.archive.ubuntu.com'
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Temporary failure resolving 'security.ubuntu.com'

plz plz reply to this
thnx[/QUOTE]

You can create new working /etc/apt/sources.list too
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Just remember to backup your existing one.

---

### Post by Sef on 2006-05-25
> You should install Sun's java directly from repositories or
the preferred debian way

The preferred Ubuntu way is now to download directly from Multiverse.

> Ubuntu 6.06

Thanks to a redistribution license change from Sun, official Sun java packages are now available in the multiverse repositories. Install it from the Applications -> Add/Remove... menu, or install the sun-java5-bin package.
Ubuntu 5.10

For Ubuntu 5.10 (Breezy Badger), the easiest method is to use the Blackdown Java 1.4 installer from Multiverse. To install Java with the installer, just install the j2re1.4 package. 

[RestrictedFormats]("http://wiki.ubuntu.com/RestrictedFormats")

---

### Post by u04f061 on 2006-05-25
[QUOTE=meng]Okay thanks for taking the time to be specific. Here's my advice:
1) Linux looks for commands in known folders/directories, those specified in the PATH (by the way Windows does this too!). javac is not in your PATH, but you can add /home/ejaz/jdk/... to your PATH if you wish.
2) If you want to run javac from the (non-PATH) directory you are presently in, as with your last example, you must preface with ./ as in "./javac hello.java". This is slightly different from Windows.[/QUOTE]

very very much thnx to u
now i can run and compile java programs by ./javac command.but it looks hideous to do so each time i open terminal.

can u tell me how to set up paths
plz..

---

### Post by u04f061 on 2006-05-25
below are the results of above

ejaz@ejaz:~$ sudo apt-get update
Password:
Sorry, try again.
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
ejaz@ejaz:~$





ejaz@ejaz:~$ sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package java-package
ejaz@ejaz:~$

---

### Post by Mustard on 2006-05-25
Are you online when you do this?

---

### Post by u04f061 on 2006-05-25
[QUOTE=Mustard]Are you online when you do this?[/QUOTE]
yes i am online now.
if u want me online to fix the problem then plz tell me the time when i should be?

---

### Post by Mustard on 2006-05-25
[QUOTE=u04f061]yes i am online now.
if u want me online to fix the problem then plz tell me the time when i should be?[/QUOTE]
We can talk about this issue in the other thread you started. :)

---

### Post by u04f061 on 2006-05-26
this is result
ejaz@ejaz:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number: 1
Using `/usr/bin/gij-wrapper-4.0' to provide `java'.
ejaz@ejaz:~$ sudo update-alternatives --config javac
No alternatives for javac.
ejaz@ejaz:~$ javac hello.java
bash: javac: command not found
ejaz@ejaz:~$

---

### Post by mlind on 2006-05-26
[QUOTE=u04f061]this is result
ejaz@ejaz:~$ sudo update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java

Press enter to keep the default[*], or type selection number: 1
Using `/usr/bin/gij-wrapper-4.0' to provide `java'.
ejaz@ejaz:~$ sudo update-alternatives --config javac
No alternatives for javac.
ejaz@ejaz:~$ javac hello.java
bash: javac: command not found
ejaz@ejaz:~$[/QUOTE]

You don't have Sun's java installed at all, that's why update-alternatives
can't configure it.

---

### Post by meng on 2006-05-26
Well I think he does have it installed, but it's in a funny place and the system doesn't recognize where it is. Based on the advice he's received so far, and his probable level of expertise (forgive me for presuming), I reckon he's best to delete the /home/ejaz java and use the repositories to re-install, thereby solving his PATH issue and allowing him to choose the default java.

---

### Post by u04f061 on 2006-05-27
[QUOTE=meng]Well I think he does have it installed, but it's in a funny place and the system doesn't recognize where it is. Based on the advice he's received so far, and his probable level of expertise (forgive me for presuming), I reckon he's best to delete the /home/ejaz java and use the repositories to re-install, thereby solving his PATH issue and allowing him to choose the default java.[/QUOTE]

how can i delete it.just moving it to trash graphically will remove all of contents of it?

is there any efficient command line method to uninstall the installed packages even  from apt-get install ?

---

### Post by meng on 2006-05-27
Hmm, good question. I'm not sure of the answer. I had thought there was an uninstaller, but I was confusing the JDK with Netbeans IDE (which does have an uninstaller). 

You won't be able to use apt-get or dpkg to uninstall it, because you didn't use them to install it originally. (Hence the advice to install from repositories whenever possible).

I'd wait for someone more knowledgeable to come up with the answer, but if you really can't wait, then I would install java from repositories and THEN delete the other directory.

---

### Post by u04f061 on 2006-05-27
i have deleted that and tried this but failed badly

ejaz@ejaz:~$ sudo apt-get install fakeroot java-package java-common Password:
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
java-package is already the newest version.
java-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 158 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--21:39:10--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--21:39:15--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Temporary failure in name resolution.
--21:39:20--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Temporary failure in name resolution.
--21:39:25--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--21:39:35--  [http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Temporary failure in name resolution.
--21:39:40--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Temporary failure in name resolution.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
ejaz@ejaz:~$ javac hello.java
bash: javac: command not found
ejaz@ejaz:~$

---

### Post by meng on 2006-05-27
It looks like apt-get tried to install msttcorefonts, but did not install java. So don't fret, I think you just need to solve the msttcorefonts issue first. Except I don't know the command to fix your truetype font installation so that apt-get can get onto the business of installing java.

---

### Post by u04f061 on 2006-05-27
where from can i search for this command????????????????????????

plz any bod can help me in fixing msttcorefonts problem

---

### Post by meng on 2006-05-27
Try uninstalling msttcorefonts by:
sudo apt-get remove msttcorefonts

then:
sudo apt-get update
sudo apt-get install fakeroot java-package java-common

---

### Post by u04f061 on 2006-05-27
after following above commands succesfully   the result of last is below

ejaz@ejaz:~$ sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
java-package is already the newest version.
java-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 158 not upgraded.
ejaz@ejaz:~$
ejaz@ejaz:~$ javac hello.java
bash: javac: command not found
ejaz@ejaz:~$

---

### Post by meng on 2006-05-27
Okay that's good, that output in fact explains a lot. The packages so far installed enable you to install java in a readily uninstallable fashion. But now you need to proceed with the next step. Go to the directory where the [java-installer].bin file is, and if not already executable, you should

chmod +x [java-installer].bin

but since you have already used it to install previously, it should already be executable.

Next:

fakeroot make-jpkg [java-installer].bin

and this should generate a sun-j2dk[something].deb file. Next step:

sudo dpkg -i sun-j2dk[something].deb

Let us know how it works out.

---

### Post by u04f061 on 2006-05-27
yessssssssss..................

it worked 100%

now should i remove  sun-j2dk[something].deb in my home directory because i think it is transferred somewhere else?
can u explain me how above huge cycle of such difficult commands worked.how u remember suck difficult things?

if u have time plz explain their working 

i think u can solve my this problem also
my gaim messenger is not working
it says 
         "connection error notification server
            messenger.hotmail.com
           unable  to connect"
                       
thnx.l

---

### Post by mlind on 2006-05-27
[QUOTE=u04f061]yessssssssss..................

it worked 100%

now should i remove  sun-j2dk[something].deb in my home directory because i think it is transferred somewhere else?
can u explain me how above huge cycle of such difficult commands worked.how u remember suck difficult things?l[/QUOTE]

If you successfully installed Sun's java using make-jpkg, then the procudes are
explained on wiki entry that was on post [#4]("http://www.ubuntuforums.org/showpost.php?p=1051758&postcount=4").

Good you got it finally sorted.

---

### Post by Koech on 2006-05-27
[QUOTE=u04f061]
can u explain me how above huge cycle of such difficult commands worked.how u remember suck difficult things?

if u have time plz explain their working 

i think u can solve my this problem also
my gaim messenger is not working
it says 
         "connection error notification server
            messenger.hotmail.com
           unable  to connect"
                       
thnx.l[/QUOTE]
 About the commands, it's easy, the fakeroot jpkg... thing converts .bin(binary) files to .deb(debian) files. The chmod +x means change mode of file to executable therfore can be installed. The dpkg... is an instruction to the installer to install the debian package.
About Gaim, you should ensure your ports are open or you can tunnel thro other open ports. Sometimes it's a temporary problem.

---

### Post by Mustard on 2006-05-27
[QUOTE=u04f061]
i think u can solve my this problem also
my gaim messenger is not working
it says 
         "connection error notification server
            messenger.hotmail.com
           unable  to connect"
                       
thnx.l[/QUOTE]

I would say this is related to your university proxy.  Check the preferences in GAIM  and look for an option to use a proxy server.

---

### Post by meng on 2006-05-27
Congratulations on getting java to work. It's a great feeling isn't it? If you continue to have gaim problems, my suggestion is to start a new thread, so that anyone who can help you will know to look there.

---

### Post by u04f061 on 2006-05-27
[QUOTE=Mustard]I would say this is related to your university proxy.  Check the preferences in GAIM  and look for an option to use a proxy server.[/QUOTE]

i specified the http proxy and port

my proxy server is  of format 
xx.xx.xx.x 
and port of format
xxxx
i specified it still having aproblem

---

### Post by Mustard on 2006-05-27
[QUOTE=u04f061]i specified the http proxy and port

my proxy server is  of format 
xx.xx.xx.x 
and port of format
xxxx
i specified it still having aproblem[/QUOTE]

Yeah, I've never had any luck running MSN (on GAIM) through a proxy myself. I'm not sure how you would get around this.  Is anyone else able to use instant messengers through your university proxy?

---

### Post by u04f061 on 2006-05-27
i myself use msn messenger on windows.i can say surely that there would'nt be anyone using linux in my hostle.i think i am the only person in my hostle to be using linux.so i can't get help from anyone here
the problem is real.i installed aria(internet download manager) it is not working.it says temporary error in the name resolution
i don't know what to do with it.should i start a new thread for this or not.

i am too much confused.

---

### Post by meng on 2006-05-27
There are alternatives to gaim, particularly if you only want to use MSN.
Examples: amsn, kopete, mercury messenger.

Unfortunately, amsn from ubuntu repositories is a little old, not sure if that old version supports webcam; kopete will require lots of kde packages to be installed; and mercury won't be in repositories.

---

### Post by Mustard on 2006-05-27
I notice on gaim, in the login section for your msn account, you can choose 'use http method'.  I wonder whether this, in combination with your proxy settings will fix the problem.

---

### Post by Mustard on 2006-05-27
[QUOTE=u04f061]i myself use msn messenger on windows.i can say surely that there would'nt be anyone using linux in my hostle.i think i am the only person in my hostle to be using linux.so i can't get help from anyone here
the problem is real.i installed aria(internet download manager) it is not working.it says temporary error in the name resolution
i don't know what to do with it.should i start a new thread for this or not.

i am too much confused.[/QUOTE]

All these connection errors are related to the same thing.  You need to configure applications to work with your proxy server.

---

### Post by JNowka on 2006-05-27
Ok, I just installed java myself and had the same problem. 

The java installer from sun.com installs the folder into the /opt/ as default.  The directory should look something like j2sdk1.5_6 or something close to that.  Go on and find that directory name.

goto your project folder and type ln -s /opt/(java directory here)/javac

now whenever you want to compile the program you will need to type
./javac filename.java

If you downloaded java with netbeans though it should be in Applications->Programming->NetBeans.  That is the GUI that java uses.

---

### Post by u04f061 on 2006-05-27
[QUOTE=Mustard]All these connection errors are related to the same thing.  You need to configure applications to work with your proxy server.[/QUOTE]

how to configure applictions??
yesterday there was problem with apt-get thnx god u helped me ,now can u help me once again?

---

