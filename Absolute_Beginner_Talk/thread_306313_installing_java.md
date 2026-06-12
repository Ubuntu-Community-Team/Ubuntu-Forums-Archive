---
title: "installing java"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by inkimar on 2006-11-24
Hello,

installed a ubuntu-LAMP-server.
the installation did fine.

wanting to install java and later tomcat or jboss.
did burn down a image of the latest server, it is in the cd-slot.

trying the following:

sudo apt-get install sun-j2sdk1.5

not working.
I get the following message:
'Reading package lists... Done
Bulding dependency tree ... sibw
E: Couldn't find package sun-j2sdk1.5'

the computer has an internet connection, I 
was successful installing subversion with 'sudo ap-get'

what am I doing wrong ?

now that java is GPL, will java be distributed on your next
iso ?

regards, i

---

### Post by taurus on 2006-11-24
First, make sure you have enable both universe & multiverse in /etc/apt/sources.list.

Then, update it and install it...

```
sudo aptitude update
sudo aptitude install sun-j2sdk
```
Otherwise, download it from Sun's site and install it by hand.

---

### Post by dlehman on 2006-11-24
it is not working because 1.5 is not in the repository (at least not in mine) try using 1.4 or manually install it you could also skip the command line and use synaptic package manager 


hope this helps:)

---

### Post by inkimar on 2006-11-25
Hello!

Thank you for the advices.
- is there any proper HOW-TO that you can point me to ?
-- still having probs.

did edit that file using 'sudo vi /etc/apt/sources.list'
and removing the remark from all the lines that made sense.

did then run the:
[INDENT]sudo aptitude update
sudo aptitude install sun-j2sdk[/INDENT]

Got the message back:
'Couldn't find any package whose name or description
matched "sun-j2sdk" '.

Where am I going wrong, do have internet connection
that is working.

best regards, Ingimar

---

### Post by ron999 on 2006-11-25
Hi inkimar

Automatix2 will install Java Sun 1.5 JRE

Here:-
[http://www.getautomatix.com/]("http://www.getautomatix.com/")

---

### Post by inkimar on 2006-11-25
Hi,

Using a LAMP-server, not any graphics here.
automatics is all about the graphics I believe !? or !?
Still new here, but learning.

regards, i

---

### Post by ron999 on 2006-11-25
Hi,

Using a LAMP-server, not any graphics here.
automatics is all about the graphics I believe !? or !?
Still new here, but learning.

regards, i
 

**I don't understand any of that**
:-k

---

### Post by meng on 2006-11-25
Isn't the package called:
sun-java5-jdk
??
(It may have changed but that's what I recall)

---

### Post by inkimar on 2006-11-26
Hello Ron,

Well, there is no graphic interface.
All I have is the prompt, that is the way LAMP-server is installed.
I do not need any graphics here, my intention was to just run a tomcat-server or a jboss-server and some other servers.

So I use the command 'apt-get'.

Any suggestions on how I should install this ?

regards, i

---

### Post by junglepeanut on 2006-11-26
Ok, I am guessing on what you need hopefully apt will catch the dependancies...

```
sudo aptitude install sun-java5-jre sun-java5-bin libservlet2.3-java libjine-jave libjaxp1.2-java libhsqldb-java java-common
```

some of those are for editing.

I am just guessing this is all you will need. Also I worte them by hand so I hope there are no typos.

---

### Post by inkimar on 2006-11-26
Hi,

I do need the j2sdk, I really do not need the jre.

regards, i

---

### Post by JurB on 2006-11-26
[This ]("http://ubuntuforums.org/showthread.php?t=201378") thread mentions a bug when trying to install sun-java5-jdk using the terminal.
Something to do with the license not displaying correctly...
They advise to use synaptic, but since you have no gui...

---

### Post by junglepeanut on 2006-11-26
Ok, then I dont know which of these you prefer but the names are 

for blackdowns version
j2sdk1.4 j2sdk1.4-demo j2sdk1.4src

and suns
j2sdk1.4-doc

I think I might be missing some of suns stuff since I only have that one but I got a lot of blackdown...

---

### Post by Circus-Killer on 2006-11-26
here's a great page for installation of different java environments: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

### Post by junglepeanut on 2006-11-26
If this still is not good enough I can probably come up with a "wget" way to get the binary from Sun's site, and then you can just run the install script.

I might be falling asleep soon so, "man wget" if that seems like a good idea to you and maybe you will get it all done before I wake up. Otherwise just keep asking.

---

### Post by junglepeanut on 2006-11-26
reading the page listed above it appears you may want all of the ones I listed if yo want docs etc, but the first blackdown is all you really need.

---

### Post by inkimar on 2006-11-26
Hi,

How do I install that from the sun site ?

rregards, i

---

### Post by junglepeanut on 2006-11-26
OK, but before I research all this can you tell me is this because you just want it from there site or you still can not get it from apt? Only because if it is not from apt I would prefer to fix it so that yo would then also automatically get updates. But if you just want it from their site I will look into it, you will need to update manually.

---

### Post by junglepeanut on 2006-11-26
Ok, I am not a cool coder so I have hit a wall the site requires you to get some cookies and junk before handing you the file so wget wont work so well unless somebody knows a work around. Lets try to fix your apt problem if not I can download it and send it to you, but I think that risks corruption as it is a large file, i.e. I download it,then I can scp it to you, but its big so it wont be fast.
 
So what are the errors with the apt approach?

---

### Post by junglepeanut on 2006-11-26
Oh I just thought of something you could go there yourself.(this is if you still dont want to do apt and you will have to manually update)

```
sudo aptitude install links
```

then
```

links
```


goto

[https://sdlc6e.sun.com/ECom/EComActionServlet;jsessionid=A4D83CEC7113825C04175B92DD02FADC](https://sdlc6e.sun.com/ECom/EComActionServlet;jsessionid=A4D83CEC7113825C04175B92DD02FADC)

I dont know how good that link will be as it wont let me do stuff with out java enabled, but it says it will work with out it.

---

### Post by JurB on 2006-11-26
Did anyony see my post?...
Since the license doesn't seem to be displaying correctly in the terminal, it doesn't matter what file you use to install it via the terminal... the license will not display and you won't be able to agree with it...
It seems the gui way is needed. You can always try to contact the op of the link i gave to see if there is another solution or get more info on the matter.

---

### Post by junglepeanut on 2006-11-26
I did, if you read my post it says "if" he can not get it working through apt, as he has a server install, he does not have synaptic. So I am trying to give him options for installing something other than what is also talked about on that page to install as it might work as it is "a different file."

That is why I tried the links option as well as it is a installation script which we might be able to play with the commands to make it work.

---

### Post by inkimar on 2006-11-26
Hello,

Did download two java-packages from the ftp.ubuntu.com .
sun-java5-bin_1.5.0-06-1_i386.deb
sun-java5-jre_1.5.0-06-1_all.deb

That worked. following this [guide]("https://help.ubuntu.com/community/Java") .

The guide is missing us users sitting on a prompt without graphics though. after downloading I use the following commands.

sudo dpkg -i sun-java5-jre_1.5.0-06-1_all.deb 
- which complains 
-- sun-java5-bin is not installed
-- ia32-sun-java5-bin is not installed

sudo dpkg -i sun-java5-bin_1.5.0-06-1_i386.deb 

and there is compain about that the java-common is not installed.

Anyone awake that can help me !?
Wanting to learn this, thought the above guide would give me a kickstart ..... 

regards, i

---

### Post by junglepeanut on 2006-11-26
I thought you said you need j2sdk

did you try installing them like I said?

```
sudo aptitude install j2sdk1.4 j2sdk1.4-demo j2sdk1.4-doc j2sdk1.4-src
```

---

### Post by junglepeanut on 2006-11-26
In my first code way back I gave you a command to install java-common, what was the error from that, or did you not try because jre was also in there. Lastly, I am going to bed. Try running the commands, post what your errors are and exactly what happened, not just it did not work. As many poeple here know what to do.

I am getting no errors installing them from the terminal.

JurB, I am sorry if I got cranky, I really thought this was more of a true error not just teaching someone how to use apt, and I am tired. But I am getting no errors from the terminal. (might be feisty in action though).

---

### Post by inkimar on 2006-11-26
Hello Junglepeanut,

thanks for trying your best, still - sleeping is a good thing.

Did 'sudo aptitude install sun-java5-jre sun-java5-bin libservlet2.3-java libjine-jave libjaxp1.2-java libhsqldb-java java-common'

And I get a number of errors.
No candidate version found for sun-java5-jre
No candidate version found for sun-java5-bin
couldnt find a package matche 'libservlet2.3-java'
couldnt find a package matche 'libjine-java'
No candidate version found for libjaxp1.2-java
No candidate version found for libhsqldb-java
No candidate version found for java-common

Would prefer java from SUN, I am using that here
at home on my XP and I am using it at work .....

Now that java has been freed ( under GPL ) nothing can
stop the Ubuntu team to put it on their latest ISO.

So, what am a doing wrong - is it my Repositories ( the source.list ) that must be changed ?

quite stuck here, thought that if I pulled this of, then 
installing tomcat or jboss would be a peace of cake.

regards, i

---

### Post by junglepeanut on 2006-11-26
If you try installing tomcat it should find all your dependencies.

go to 

sudo vim /etc/apt/sources.list
and take from mine what you need. But to be quick I am just cut and pasting mines as you probably have to write it down anyways and instead of writing feisty you just write dapper or edgy whichever yo are using.


```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe multiverse

## Proposed
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed universe main multiverse restricted

##Debug Packages
deb http://people.ubuntu.com/~pitti/ddebs feisty main universe

## PLF
## Please report any bug on https://launchpad.net/products/plf/+bugs
deb http://packages.freecontrib.org/ubuntu/plf/ feisty-plf free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf/ feisty-plf free non-free

##EasyCAM
deb http://blognux.free.fr/debian unstable main

##Canonical Commercial
deb http://archive.canonical.com/ubuntu dapper-commercial main

##Beryl
# Treviño's Ubuntu edgy Beryl-SVN Repository (GPG key: 81836EBF - DD800CD9)
# Daily Updated Beryl (and related projects) Packages...
deb http://download.tuxfamily.org/3v1deb edgy beryl-svn
deb-src http://download.tuxfamily.org/3v1deb edgy beryl-svn

```


Also just so you know blackdowns is a version of sun I am pasting from the info about j2sdk from apt 
> Blackdown Java(TM) 2 SDK, Standard Edition
The Blackdown Java-Linux Java 2 SDK is a development environment for
building applications, applets, and components that can be deployed
on the Java platform.

The Java 2 SDK software includes tools useful for developing and
testing programs written in the Java programming language and running
on the Java platform (this includes the Java 2 Plug-In for Netscape
and Mozilla browsers).

NOTE: You must accept Sun's EULA prior to successfully installing
this package

---

### Post by inkimar on 2006-11-26
Will do that now, and get back to you.

solong, i

---

### Post by inkimar on 2006-11-26
So according to JurB?
[I][INDENT]"Did anyony see my post?...
Since the license doesn't seem to be displaying correctly in the terminal, it doesn't matter what file you use to install it via the terminal... the license will not display and you won't be able to agree with it...
It seems the gui way is needed. You can always try to contact the op of the link i gave to see if there is another solution or get more info on the matter."[/INDENT][/I]

Well, i said yes and it seem to have taken that yes in account.
so, noone is able to install the java sdk via the terminal ?

regards, i

---

### Post by inkimar on 2006-11-26
Hello Peanut,

Did change my source.list exactly to be a replica of yours - did not add the lines after ##proposed.

Then i did the following:

'sudo aptitude-get update' ( did the mistake of not doing this at first )
'sudo aptitude install j2sdk1.4 j2sdk1.4-demo j2sdk1.4-doc j2sdk1.4-src'

Now things work!!!!
Thank you!!!

( problem with the j2sdk1.4-doc, think I can live with that ? )

My next step will be to install tomcat / jboss.
And test my subversion installation.

Did find this installation guide for [LAMP with a gui]("http://www.howtoforge.com/lamp_installation_ubuntu6.06") , we should find a way to include a non-gui tutorial into that one ? be a how-to

regards, i

---

### Post by inkimar on 2006-11-26
Hello,

not getting forward on this path.Still no java.
I will try using this [LAMP-guide-with-gui]("http://www.howtoforge.com/lamp_installation_ubuntu6.06")
 - would like to do everything from the prompt though.

regards, i

---

