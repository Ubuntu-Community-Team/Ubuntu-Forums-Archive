---
title: "java runtime"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by ckonrad on 2006-10-13
I am trying to install the jre using add/remove programs under applications and when i click it to install it, i get the message "'sun-java5-bin' is not available in any software channel, the application doesnt support your system architecture"

I have the most recent ubuntu and have done all the updates needed. I also looked for the JRE in synaptic and it wasnt there, there is alot of stuff for java just nothing listed as a JRE. I also searched the ubuntu forums and found a command lind way to install it using apt-get and that didnt find anything either. Can it be installed at all?

Thanks

---

### Post by farmerbee on 2006-10-13
why not try jdk1.4?

---

### Post by ckonrad on 2006-10-13
> **farmerbee said:**
> why not try jdk1.4?

tried via synaptic, doesnt exist

tried via aptitude install in the terminal and its says
"Couldn't find any package whose name or description matched "jdk1.4""
tried in add and remove programs and it doesnt exist unless i choose the "unsupported package" check box which is obviosly why i was getting that other error about my architecture not being supported.

I am just looking for the quickest and simplest way to get the JRE working with my browser. 

thanks

---

### Post by DOD1951 on 2006-10-13
Try here [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) and select the Linux version right for you. I chose Linux RPM and after dsome fiddling got it to install and as far as Java site is concerned when I verified installation it said it was ok. Be that as it may it doesn't work totally accurately on some sites.

---

### Post by ckonrad on 2006-10-13
> **DOD1951 said:**
> Try here [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp) and select the Linux version right for you. I chose Linux RPM and after dsome fiddling got it to install and as far as Java site is concerned when I verified installation it said it was ok. Be that as it may it doesn't work totally accurately on some sites.


yeah i tried that too but i couldnt get the plugin to work with firefox. I have java enabled in my browser and i actually have a gnu java runtime that looks like its installed by default but for some reason that one cant recognize web content. I dont know, i thought java was a cross platform programming language and environment you think gettng it working on linux would be a snap.

---

### Post by ckonrad on 2006-10-13
> **farmerbee said:**
> why not try jdk1.4?
good good study ,day day up!!

what does that mean? It doesn make any sense in english, hehe. Its like this japanese guy i met once that had an electronic translator and said he wanted to know where his blue potato was.

---

### Post by atomic drizzle on 2006-10-13
hey i just got linix and have never used it before so im completely unfamiliar with command line. im trying to install runtime, and i went to java page, read how to installand readme , but dont really understand it.  is there any where i can get an in depth how to? any help would be appreciated.

---

### Post by farmerbee on 2006-10-13
i am sorry..  you can try" sudo apt-get install j2sdk-1.4" in termial cmd line

i am a chinese ,you see my english is very very very very poor ..  i hope you can understand what i say.. ^_^


good good study ,day day up is a popular chinese english   means 
work hard everyday and make progress everyday  ...

---

### Post by ckonrad on 2006-10-13
> **atomic drizzle said:**
> hey i just got linix and have never used it before so im completely unfamiliar with command line. im trying to install runtime, and i went to java page, read how to installand readme , but dont really understand it.  is there any where i can get an in depth how to? any help would be appreciated.

yeah sure, you can go through a full free course on the linux website
[http://www.linux.org/lessons/](http://www.linux.org/lessons/)

---

### Post by ckonrad on 2006-10-13
> **farmerbee said:**
> i am sorry..  you can try" sudo apt-get install j2sdk-1.4" in termial cmd line

i am a chinese ,you see my english is very very very very poor ..  i hope you can understand what i say.. ^_^


good good study ,day day up is a popular chinese english   means 
work hard everyday and make progress everyday  ...

yeah that doesnt work either, there is no such package.

ok that proverb makes more sense, :)

---

### Post by atomic drizzle on 2006-10-13
thankyou, ill check it out. nother question, i saw ur link to java's instructions. im following it, but when i try to change the permission to executable it tells me no file or dir exists. im in usr@usr-desktop, where would it be if not there?

---

### Post by farmerbee on 2006-10-13
can your apt-get find any other packages?if not you need to upgrade apt-get sources.list file.the location is "/etc/apt/sources.list"
but why dont you download jdk package form java home page manually and configure the environment var?

---

### Post by atomic drizzle on 2006-10-13
what is var?

---

### Post by r4ik on 2006-10-13
Try,

sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list

    * Replace everything with the following lines 

    To use your local mirror you can add "cc." before archive.ubuntu.com (cc = your country code) 
    e.g. deb [http://lv.archive.ubuntu.com/ubuntu](http://lv.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse 

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

    * Save the edited file 

wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
sudo apt-get update

and,

sudo apt-get install sun-java5-jre sun-java5-plugin

    * When asked, agree with DLJ license terms. 

    * To configure J2SE as the default JVM (necessary for programs such as Frostwire, Freenet, RSSOwl and as a plugin for Mozilla Firefox): 

sudo update-alternatives --config java

Then choose the option that corresponds to J2SE. 

From,

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Good luck !

Edit,

    * Download the "Linux (self-extracting file)" from [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp) 

    * Copy it to /usr/java/ 

sudo chmod a+x jre-1_5_0_08-linux-i586.bin
sudo ./jre-1_5_0_08-linux-i586.bin
cd /usr/lib/firefox/plugins
sudo ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so
cd /usr/lib/mozilla/plugins
sudo ln -s /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so

    * Restart Mozilla Firefox
    * If you get an error, try changing the 08's in the filenames to the appropriate version number. 

Might be more what you want.

---

### Post by David Corrales on 2006-10-13
Did you enable all the repositories?

---

### Post by atomic drizzle on 2006-10-13
thanks!

---

### Post by atomic drizzle on 2006-10-13
> **David Corrales said:**
> Did you enable all the repositories?

what r those?

---

### Post by TiredBird on 2006-10-13
I just loaded the JRE and plugin for Firefox. It's installed and working. I did it all since the last post so it was working a few minutes ago.

If you're still trying to solve the problem, I'll copy the directions I followed. (Command line stuff but I used cut and paste and it worked perfectly.)

---

### Post by TiredBird on 2006-10-13
r4ik has it right. I just used the same procedure and it worked for me. There is a lot of helpful information in the site he took that from. I use it all the time. [Check it out here.]("http://ubuntuguide.org/wiki/Dapper")

---

### Post by atomic drizzle on 2006-10-13
> **TiredBird said:**
> I just loaded the JRE and plugin for Firefox. It's installed and working. I did it all since the last post so it was working a few minutes ago.

If you're still trying to solve the problem, I'll copy the directions I followed. (Command line stuff but I used cut and paste and it worked perfectly.)

that would be cool. i think the problem is im not relly sure what im doing yet. iv had this os for a week and this is the first time i tried to install an app:)

---

### Post by TiredBird on 2006-10-13
Atomic Drizzle:

Did you get your problem solved? I was going to give you exactly the same thing that 'r4ik' did. I think the advice was very good. All I did in my last post was to repeat the link to the site. They have a lot of very specific directions for a lot of things. You can just cut and paste from their website. I've used a lot of it and I've never found an error. It always works as they say it will. I would recommend it heartily. [http://ubuntuguide.org/wiki/Dapper]("http://ubuntuguide.org/wiki/Dapper")

I started with Ubuntu a few months ago. I have two machines that are still running Windows XP but I don't use them anymore and I'm about to install Ubuntu on both. You're on the right track. It'll be frustrating at first but after a while you'll truly wonder why you ever used Windows.

Good luck!

---

