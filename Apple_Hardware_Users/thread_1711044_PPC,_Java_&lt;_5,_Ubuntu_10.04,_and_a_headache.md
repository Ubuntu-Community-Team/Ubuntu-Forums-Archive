---
title: "PPC, Java &lt; 5, Ubuntu 10.04, and a headache"
date: 2011-03-20
forum: Apple Hardware Users
---

### Post by Snipeye on 2011-03-20
First things first:  I'm very, very new to ubuntu.  In fact, I installed it yesterday on my old, old g4 tower (800mhz or something like that) in hopes of making it less useless.  I'm trying to get java up and running on it, but so far, I haven't really had any success - the openjdk java and that stuff seems to work, but in browser, it's being really, really painfully slow.  I've been trying to install sun java 6, but I've run into a couple of snags.  Here's directly from terminal:

```
joshua@joshua-desktop:~$ sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
joshua@joshua-desktop:~$ sudo apt-get update
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://archive.ubuntu.com lucid Release.gpg                      
Hit http://archive.ubuntu.com lucid-updates Release.gpg              
Hit http://ports.ubuntu.com lucid Release.gpg                        
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid/main Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                   
Ign http://archive.canonical.com/ lucid/partner Translation-en_US    
Hit http://archive.canonical.com lucid Release                       
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid/restricted Translation-en_US
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid/universe Translation-en_US
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid/multiverse Translation-en_US
Hit http://ports.ubuntu.com lucid-updates Release.gpg                
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid-updates/main Translation-en_US
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid-updates/restricted Translation-en_US
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid-updates/universe Translation-en_US
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid-updates/multiverse Translation-en_US
Hit http://ports.ubuntu.com lucid-security Release.gpg               
Hit http://archive.ubuntu.com lucid Release                          
Hit http://archive.canonical.com lucid Release                       
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid-security/main Translation-en_US
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid-security/restricted Translation-en_US
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid-security/universe Translation-en_US
Ign http://ports.ubuntu.com/ubuntu-ports/ lucid-security/multiverse Translation-en_US
Hit http://ports.ubuntu.com lucid Release                                      
Hit http://archive.ubuntu.com lucid-updates Release                            
Hit http://ports.ubuntu.com lucid-updates Release                              
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://ports.ubuntu.com lucid-security Release                             
Hit http://archive.ubuntu.com lucid/main Sources                     
Hit http://archive.ubuntu.com lucid/restricted Sources               
Hit http://archive.ubuntu.com lucid/universe Sources                 
Hit http://archive.ubuntu.com lucid/multiverse Sources               
Hit http://archive.canonical.com lucid/partner Packages              
Hit http://archive.ubuntu.com lucid-updates/main Sources             
Hit http://ports.ubuntu.com lucid/main Packages                      
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://ports.ubuntu.com lucid/restricted Packages
Hit http://ports.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://ports.ubuntu.com lucid/multiverse Packages
Hit http://ports.ubuntu.com lucid-updates/main Packages
Hit http://ports.ubuntu.com lucid-updates/restricted Packages
Hit http://ports.ubuntu.com lucid-updates/universe Packages
Hit http://ports.ubuntu.com lucid-updates/multiverse Packages
Hit http://ports.ubuntu.com lucid-security/main Packages
Hit http://ports.ubuntu.com lucid-security/restricted Packages
Hit http://ports.ubuntu.com lucid-security/main Sources
Hit http://ports.ubuntu.com lucid-security/restricted Sources
Hit http://ports.ubuntu.com lucid-security/universe Packages
Hit http://ports.ubuntu.com lucid-security/universe Sources
Hit http://ports.ubuntu.com lucid-security/multiverse Packages
Hit http://ports.ubuntu.com lucid-security/multiverse Sources
Reading package lists... Done
joshua@joshua-desktop:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (>= 6.24-1build0.10.04.1) but it is not installable or
                          ia32-sun-java6-bin (>= 6.24-1build0.10.04.1) but it is not installable
E: Broken packages

```Any suggestions?  Keep in mind, I'm on a PPC mac, not intel.
I don't necessarily NEED Java 6, all I know is the app I'm trying to make run (a game) requires a java that is at least 6.  I don't know a whole bunch about java, but if there's a version > 6 that would work on this computer, I'd be happy.

In short:  How do I install Java that is >= 6 on a ppc mac running ubuntu 10.04?

---

### Post by mikewhatever on 2011-03-20
Sun-java probably conflicts with openjdk-java, so try removing the latter. Don't think it's going to be much faster tough.

---

### Post by Snipeye on 2011-03-20
I've tried adding a lot of different repositories, but when I update an do "sudo aptitude search sun-java6" it only ever comes up with these four files:

p   sun-java6-fonts                 - Lucida TrueType fonts (from the Sun JRE)  
p   sun-java6-javadb                - Java(TM) DB, Sun Microsystems' distributio
p   sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-java6-source                - Sun Java(TM) Development Kit (JDK) 6 sourc


Any way I can build from the source, or a repository that for sure has the jdk and the plugin?  Perhaps I can direct download .deb for them all?

---

### Post by mikewhatever on 2011-03-20
Not really sure why, but there is no 'sudo -java6-jdk' package for PPC architecture in the partner repository.:confused:
[http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-powerpc/Packages](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-powerpc/Packages)

---

### Post by Snipeye on 2011-03-20
I've been adding repositories like a mad man, and I still can't find it anywhere... know where I could get a sun-java6-bin?  If I can find that, that covers the requirements for sun-java6-jre, meaning I can have java, even if not in-browser...

EDIT:  Wait, I would also need sun-java6-ia32-bin or whatever it is.

---

### Post by rsavage on 2011-03-21
Let us know if you get this to work [http://ubuntuforums.org/showthread.php?t=1116368](http://ubuntuforums.org/showthread.php?t=1116368)

---

### Post by Snipeye on 2011-03-21
At one point, he says this:

sudo apt-get java-package


I'm not sure which package he's referring to.

---

### Post by rsavage on 2011-03-21
That is the command you need to type in a terminal window.  It will install this package [http://packages.ubuntu.com/lucid/java-package](http://packages.ubuntu.com/lucid/java-package) which is just a step to getting IBM java to work.  There is no Sun Java for power pc btw.

I'm afraid I've never needed to look into Java so can't really help you any more.  You will have to do a search, but everything I've seen roughly follows the same steps.  Except Yellow Dog Linux [http://www.yellowdog-board.com/viewtopic.php?t=2935](http://www.yellowdog-board.com/viewtopic.php?t=2935) but I couldn't tell you if that is helpful with Ubuntu.

I would follow the first guide I gave you and report any problems.  Somebody has bound to have done it or can help you further.   Or there is a deb you can install in the last post if you trust that.

---

### Post by rsavage on 2011-03-21
Scrap that, these instructions on the IBM website look easy to follow [http://www-01.ibm.com/support/docview.wss?uid=swg21456902](http://www-01.ibm.com/support/docview.wss?uid=swg21456902)

---

### Post by Snipeye on 2011-03-21
I can't seem to find the rpm-build it mentions, and building via alien doesn't seem to be getting me anywhere.

---

### Post by Snipeye on 2011-03-21
Wait, scratch that.  It worked, just really slowly.  Now I just need to find out how to make it my default java.

EDIT:  I really can't seem to make it 'go' - it's in the same folder as the other 'java' i have installed (tried install 1.7.0 earlier, that failed) but when I try setting it as an alternative, gives me this:

sudo update-alternatives --set java '/usr/lib/jvm/java-ppc-60/jre/bin/java' 
update-alternatives: error: alternative /usr/lib/jvm/java-ppc-60/jre/bin/java for java not registered, not setting.

Help?

---

### Post by rsavage on 2011-03-22
Okay, I'm a bit confused!  Where did 1.7 come from?!!

What guide did you use in the end?  If it was the first one I gave then have you followed it to the end?  That tells you to create a link to the plugin.  Have you done this and does it work?

rpm-build is probably part of the rpm package or is named slightly different or something.  It will be there somewhere I would expect.  A google search will tell you.

As for the update-alternatives thing, well I had to look into that.  I think you need something like:

sudo update-alternatives --install "/usr/bin/java" "java"  "/usr/lib/jvm/java-ppc-60/jre/bin/java" 1

before the command you gave.

You are testing the limits of my knowledge of java and linux I'm afraid!  Sorry I can't be more help.

---

### Post by Snipeye on 2011-03-22
1.7 came from a while ago, before I posted, when I was trying to get java to work.  As for the guide I used - I got the link from the guide you posted, downloaded the ibm-java package appropriate for my computer, then downloaded alien (for installing .rpm packages on ubuntu), installed it with --scripts enabled, and I haven't yet tried to link the plugin.

I'm about to try the command you gave me to make that java a valid option to select, thanks for all your help, I hope this works!

---

### Post by Snipeye on 2011-03-22
Alright, I did what you told me and it looked like it worked, but then I tried to check my java version (I just typed in 'java' to terminal to see if it was installed correctly) and it gave me this:

java: error while loading shared libraries: libjsig.so: cannot open shared object file: No such file or directory[B]

:([/B]  Thanks for all the help, think you could help me resolve this, too?

---

### Post by rsavage on 2011-03-22
Well that is the kind of error you could spend a lot of time on I think.  It probably has an easy solution, but it is just finding it!

I don't suppose this command solves it?
sudo update-alternatives --config java

First thing to do I guess would be to check that libjsig.so exists.  Then it is just a question of working out why java can't find it.  Is a previous version of Java conflicting?  There must be some pointer somewhere that needs setting.  Has this alien thing not worked correctly? 

I think if I were you I would try and start again.  Try and uninstall everything Java-ish that you've installed and then follow the IBM 'install anywhere' instructions.  If that doesn't work then I'd ask a question on the IBM Java forum because I doubt you will find the answer on this (ubuntu) forum (please somebody prove me wrong).  

Alternatively, it is just google searching.  For example, there is this [http://www-01.ibm.com/support/docview.wss?uid=swg21257022](http://www-01.ibm.com/support/docview.wss?uid=swg21257022) but it is an old error and shouldn't be affecting you.

Good luck! (report back if you get it to work please!)

---

### Post by rsavage on 2011-03-23
Just to confuse you more I've been looking into over ways to speed up Java on PowerPc.  There are quite a number of Java Virtual Machines out there that to be honest I never knew existed.  Two of them, Cacao and JamVM, are actually in the Ubuntu Software Centre.  I've only really looked into JamVm so far, see [http://jamvm.sourceforge.net/](http://jamvm.sourceforge.net/).  The author says of PowerPc "for many years my main platform, so this is well tested. Built and tested on G3 and G4 systems".  You have to say building and maintaining a virtual machine is very impressive and I think the project deserves greater recognition and use.  I'm surprised to find that there are no references to it at all on the apple forum!

Details about the latest version can be found here [http://draenog.blogspot.com/2011/02/openjdkjamvm-git-repository.html](http://draenog.blogspot.com/2011/02/openjdkjamvm-git-repository.html) .  There is also a forum [http://sourceforge.net/projects/jamvm/forums/forum/256481](http://sourceforge.net/projects/jamvm/forums/forum/256481) .  

For Cacao see [https://launchpad.net/ubuntu/lucid/powerpc/icedtea-6-jre-cacao/6b18-1.8-0ubuntu1](https://launchpad.net/ubuntu/lucid/powerpc/icedtea-6-jre-cacao/6b18-1.8-0ubuntu1) .  "The package provides an alternative runtime using the Cacao VM and the Cacao Just In Time Compiler (JIT). This is a somewhat faster alternative than the Zero port on architectures like alpha, armel, m68k, mips, mipsel, powerpc and s390."   Perhaps this is even easier to install?

Why aren't these being more widely used?  Am I missing something?

---

