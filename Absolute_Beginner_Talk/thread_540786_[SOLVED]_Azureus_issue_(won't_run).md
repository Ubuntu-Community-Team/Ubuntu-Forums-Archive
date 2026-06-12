---
title: "[SOLVED] Azureus issue (won't run)"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Nathan Otis on 2007-09-02
After upgrading from Dapper to Edgy to Feisty today, Azureus won't run (the windows closes itself after about 3 seconds)

I'm a fairly recent Windows convert, so I'm trying "The Microsoft Solution" (uninstall, reinstall) with my fingers crossed... If you don't hear from me again (on this topic) assume it worked... Else, **I'll Be Back.**

---

### Post by Nathan Otis on 2007-09-02
That worked... NOT!

So what's going on? I'm not even sure what info to give. Worked fine last night, doesn't this morning after the upgrade to Feisty,

---

### Post by SOULRiDER on 2007-09-02
Try running it from a console by typing azureus and see if you get any errors. Somethign like that used to happen to me and it was caused by some torrents i had loaded, removing them fromt he azureus cache directory fixed it.

---

### Post by Nathan Otis on 2007-09-02
Terminal output:

[B]# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb04cf172, pid=6559, tid=3084629696
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_11-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x9172]
#
# An error report file with more information is saved as hs_err_pid6559.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
[/B]

I can't find the logfile the message refers to. Help me find it and I'll attach it.

---

### Post by SOULRiDER on 2007-09-02
uhm... try updating your java to java 6

```
sudo aptitude remove sun-java5-jre
sudo aptitude install sun-java6-jre
```[/code]

---

### Post by Nathan Otis on 2007-09-02
That actually made things worse... Now it won't even start. But I see the problem...

[B]desktop:~$ sudo aptitude install sun-java6-jre
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
[/B]

---

### Post by SOULRiDER on 2007-09-02
Any errors?

---

### Post by Nathan Otis on 2007-09-02
See edit above.

---

### Post by wormser on 2007-09-02
This [post]("http://ubuntuforums.org/showpost.php?p=1680674&postcount=13") resolved my issues.  The repository has an older version and updating to the new one fixes a lot of bugs.

> Go to [http://azureus.sourceforge.net](http://azureus.sourceforge.net) and download the newest jar.

Copy the downloaded jar file over your current Azureus2.jar (mine was located at /usr/share/java/Azureus2.jar

Open Azureus again and it should open without problems.

---

### Post by Nathan Otis on 2007-09-02
I have the new file AND have located the old file, but I get an error saying I don't have permission to write over that folder... I'm such a noob.

---

### Post by Perfect Storm on 2007-09-02
ok. Alot of stuff can happen when upgrading twice (nothing is  risk free).

```
cat /etc/apt/sources.list
java -version

```

post the output.

---

### Post by wormser on 2007-09-02
> **Nathan Otis said:**
> I have the new file AND have located the old file, but I get an error saying I don't have permission to write over that folder... I'm such a noob.

You need to use **sudo** before the command.  You could do it graphically also.

```
gksudo nautilus
```

---

### Post by Nathan Otis on 2007-09-02
> **Artificial Intelligence said:**
> ok. Alot of stuff can happen when upgrading twice (nothing is  risk free).

```
cat /etc/apt/sources.list
java -version

```

post the output.

[B]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted universe multiverse
#AUTOMATIX REPOS END
[/B]

and...

[B]otis@otis-desktop:~$ java -version
The program 'java' can be found in the following packages:
 * j2re1.4
 * gij-4.1
 * kaffe
 * jamvm
 * java-gcj-compat
 * cacao
 * sablevm
Try: sudo apt-get install <selected package>
Make sure you have the 'universe' component enabled
bash: java: command not found
otis@otis-desktop:~$ 
[/B]

---

### Post by Nathan Otis on 2007-09-02
> **wormser said:**
> You need to use **sudo** before the command.  You could do it graphically also.

```
gksudo nautilus
```

Thanks for that bit of code. I replaced the file, but Azureus still won't start.

---

### Post by Perfect Storm on 2007-09-02
ok.

```
sudo nano /etc/apt/sources.list
```

add:

[b]#### Multiverse ####
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) feisty multiverse
[/b]

(ctrl)+(o) (ctrl)+(x)

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
sudo update-alternatives --config java
```

pick: 
```
  /usr/lib/j2jre1.6-sun/bin/java

```

---

### Post by Nathan Otis on 2007-09-02
> **Artificial Intelligence said:**
> ok.

...

pick: 
```
  /usr/lib/j2jre1.6-sun/bin/java

```

Everything was going very well till this. It's not an option. Here's what I have to choose from:

[B]There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
[/B]

---

### Post by Perfect Storm on 2007-09-02
This one:

 3 /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by Nathan Otis on 2007-09-02
Hey look at that. It's working!

Thanks so much for your help.

---

### Post by Perfect Storm on 2007-09-02
My pleasure.

---

### Post by badguyanil on 2007-09-05
Well did all that mentioned above but it still does not work ;(. Having the same problem as mentioned by Mr. Nathan Otis!

---

### Post by Nathan Otis on 2007-09-07
Badguy,

Are you perhaps using a non-sony branded memory stick? I honestly believe that was my problem. Upgrading to Feisty was just icing. Before I picked up an "official" sony stick, I couldn't mount my PSP, I couldn't run backups or isos or any homebrew.

I'm no Ubuntu Guru. This is the only idea I have. I hope it helps you.
n.

---

