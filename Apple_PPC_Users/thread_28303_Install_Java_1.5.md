---
title: "Install Java 1.5"
date: 2005-04-19
forum: Apple PPC Users
---

### Post by n!x on 2005-04-19
Hi,

I'm totally new to Linux, but have installed Ubuntu (which is so great) on my Powerbook G4. The meaning with this installation (Dualboot, OS X) was that I could develop Java and use the Java version 1.5.

So my question is how do I install Java 1.5 (if I can)? If not, how do I install Java 1.4?

Is someone in here familiar with developing Java apps to mobile devices (J2ME)? Is there any guide to this?

Thanks!

n!x

---

### Post by Laurent Cazalet on 2005-04-19
- Get the JDK from sun.com
[http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)
(dunno what you have to get for J2ME)

- you get a jdk-1_5_0_02-linux-i586.bin

- change to the directory you want to install it (the install will use the current directory)
if you want it in in your home dir, just

# cd
# sh <DOWNLOAD DIR>/jdk-1_5_0_02-linux-i586.bin

if you want to install it system-wide, like /usr/local

# cd /usr/local
# sudo sh <DOWNLOAD DIR>/jdk-1_5_0_02-linux-i586.bin

---

### Post by n!x on 2005-04-19
Thanks for the quick answer.

I have used your guide and have said "yes" to the license and it is starting to extract, but stops with this message:

```

/home/seest/Desktop/jdk-1_5_0_02-linux-i586.bin: line 336: ./install.sfx.27658: cannot execute binary file
/home/seest/Desktop/jdk-1_5_0_02-linux-i586.bin: line 603: cd: jdk1.5.0_02: No s uch file or directory
```

What am I doing wrong?

---

### Post by xet7 on 2005-04-19
Hi,
Sun's Java is only for i386 etc, not powerpc. And Blackdown's newest PowerPC Java is for 1.3.

But, at least IBM has Java 1.4.2 for Linux PowerPC at:
[http://www-106.ibm.com/developerworks/java/jdk/](http://www-106.ibm.com/developerworks/java/jdk/)

I found the link from google article with seach "java linux powerpc 1.4" which pointed to article [here](http://www.ppcnux-projekt.de/modules.php?name=News&file=article&sid=3856) 

So that's for linux, but if you are interested about Java 1.5 for Mac OSX, there is apple faq [here](http://developer.apple.com/java/faq/#anchor2)

---

### Post by x2l2 on 2005-04-20
you can install a java 1.4 for ppc that is on IBM web 
you need download java for   "32 bits  iSeries/pSeries" that is a powerpc server  from ibm 
here : [http://www-106.ibm.com/developerworks/java/jdk/linux140/](http://www-106.ibm.com/developerworks/java/jdk/linux140/)
(registration needed)

uncompress all on /usr/local/ibm-java 

an then copy this two lines on ~/.bashrc

export JAVA_HOME=/usr/local/ibm-java
export PATH=$JAVA_HOME/bin:$PATH

Now you have hava instaled, but you dont have java plugins for firefox instaled , can any one help me to configure this? 

source: [http://www.asturlinux.org/comunidad/node/view/374](http://www.asturlinux.org/comunidad/node/view/374) (in spanish)
(sorry for my bad english !! )

---

### Post by xet7 on 2005-04-21
Java plugin for firefox:
on my i386 pc after installing Sun Java JDK it's for firefox something like: 
```
 ln -s /usr/lib/sun-j2sdk1.5.0/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/
```

So just change IBM JDK path there, and same for Mozilla:
```
ln -s /usr/lib/sun-j2sdk1.5.0/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
```

Then restart Firefox/Mozilla.

Taken from bottom of the page of:
[http://www.ubuntulinux.org/wiki/Java15](http://www.ubuntulinux.org/wiki/Java15) 
Link to there found from:
[http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

---

### Post by agravain on 2005-04-21
[QUOTE=n!x]I'm totally new to Linux, but have installed Ubuntu (which is so great) on my Powerbook G4. The meaning with this installation (Dualboot, OS X) was that I could develop Java and use the Java version 1.5.[/QUOTE]
Won't work. There is no Java 1.5 release for neither OS X nor Linux at the moment.

---

### Post by trash on 2005-05-23
I dunno, java is a real headache on mac... i've got all of em from IBM installed and the ones in the repository and not one has worked... worked out fine in Warty but i do remember dreading having to do it all over again in Hoary.
I'm just about to remove em all and start over, with the simple instructions x2l2 posted. 

I hope sometime soon java will be in the Ubuntu repository or at least a repository somewhere so we don't have to go through this every 6 months.

---

### Post by flim on 2005-05-24
For development, the latest jvm is 142 SR1a ( checked 22.05.05) from IBM. For G4 macs, you'll have to take the 32-bit iSeries/pSeries version - I'm not sure what would be needed for a G5 (but I assume it's the same). You can download the jdk here:
[https://www6.software.ibm.com/dl/lxdk/lxdk-p](https://www6.software.ibm.com/dl/lxdk/lxdk-p)
or, for some more infos: [http://www-106.ibm.com/developerworks/java/jdk/linux140/](http://www-106.ibm.com/developerworks/java/jdk/linux140/)

The important part about the installation is to set the following variable
JITC_PROCESSOR_TYPE=5
which will tell the jdk that it is running on a mac. Of course, you'll normally want to set
JAVA_HOME=/whereever/you/installed/it/to
as well.
As far as I know, the ibm version does not support plugins. You'll have to go for the Blackdown 1.3 jdk. I haven't tested that myself though.

---

### Post by calum on 2005-05-24
[QUOTE=agravain]Won't work. There is no Java 1.5 release for neither OS X nor Linux at the moment.[/QUOTE]

Java 1.5 *is* available for OSX, but only for 10.4:
[http://www.apple.com/support/downloads/java2se50release1.html](http://www.apple.com/support/downloads/java2se50release1.html)

---

### Post by ktindle on 2005-05-25
I have installed (well, unpacked) the Blackdown JRE 1.3.1.  Neither Firefox 1.02 nor Mozilla 1.76 will recognize the plug-in.

I cannot set the system-wide PATH environ var.  Editing /etc/profile has no effect in Ubuntu 5.04.  This could be a problem.

Yes, I made soft links to the plug-in, I didn't copy it.  I have no idea what kind of funky Java-specific environ vars, like JAVA_HOME, might be needed.  Doesn't matter- as they can't be added system-wide to Ubuntu anyway.

---

### Post by clb137 on 2005-05-25
hello guys



follow the guide   [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)

clinton@ubuntu:~$ java -version
java version "1.5.0_03"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_03-b07)
Java HotSpot(TM) Client VM (build 1.5.0_03-b07, mixed mode, sharing)


clinton

---

### Post by flim on 2005-05-25
[QUOTE=clb137]hello guys
follow the guide   [http://www.ubuntuguide.org/#jre](http://www.ubuntuguide.org/#jre)
clinton[/QUOTE]

guess the correct url would be [http://powerpc.ubuntuguide.org/#jre](http://powerpc.ubuntuguide.org/#jre)
but that guide doesn't help with the problem.

Just in case you didn't notice yet, we working on POWER  ;)

---

### Post by clb137 on 2005-05-25
[QUOTE=flim]guess the correct url would be [http://powerpc.ubuntuguide.org/#jre](http://powerpc.ubuntuguide.org/#jre)
but that guide doesn't help with the problem.

Just in case you didn't notice yet, we working on POWER  ;)[/QUOTE]


SORRY,

My mistake should pay a little more attention


thanks

clinton

---

### Post by flim on 2005-05-25
Hi,

after this many questions I decided to actually try to get it working myself. As it looks, you cannot use any java version currently available for powerpc with mozilla/firefox. But what you can do is using opera or konqueror.
I tested opera8 (used the static deb version from [http://opera.com](http://opera.com), not the debian one), but it complained about the jvm (IBMJava2-SDK-142) not being valid. So I went on to Konqueror (which I think is the best browser anyway;-)) and: it works:-)

After installing Konqueror via synaptic all I had to do is open configuration, click on java/javascript in the left section of the window and then enter the path to the java executable in the very bottom. After I had done that I visisted 
[http://java.sun.com/applets/other/TumblingDuke/index.html](http://java.sun.com/applets/other/TumblingDuke/index.html)
to verify it was working and found Konqueror loading, loading, loading. So, I restarted Konqueror, visited the page again and the applet worked.

At that time I thought it might have been a restart issue with opera as well and I now can confirm that: after restart opera could display applets as well.

If anyone needs more details, let me know.

Cheers
flim

---

### Post by flim on 2005-05-25
[QUOTE=ktindle]
I cannot set the system-wide PATH environ var.  Editing /etc/profile has no effect in Ubuntu 5.04.  This could be a problem.
[/QUOTE]

I'm not a debian/ubuntu expert myself and was missing the profile.d stuff as well. Anyhow, you don't need those variables system-wide if you are just running java from your user account: it's enough to place them in .bashrc in your home directory.
I've added the following:
#IBM JVM stuff:
JITC_PROCESSOR_TYPE=6
export JITC_PROCESSOR_TYPE

JAVA_HOME="/usr/java/current/"
export JAVA_HOME;

#path of course depends on where you put the jdk
PATH="$PATH:/home/flim/bin:/usr/java/current/bin"

---

### Post by trash on 2005-05-26
YAY!!!... Thanks people and ppc starter guide(which may need more exposure!)
java -version
java version "1.4.2"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2)
Classic VM (build 1.4.2, J2RE 1.4.2 IBM build cxppc32142sr1a-20050209 (JIT enabled: jitc))

Opera is pretty peppy too!
this link works great
[http://java.sun.com/applets/other/TumblingDuke/index.html](http://java.sun.com/applets/other/TumblingDuke/index.html)
but java.com doesn't do anything at all... it's supposed to play a java preview if java is installed.

I also tried to install Mercury but the installer keeps quiting anybody know if its a java issue or an installer issue?
sudo ./1708_Linux_VM
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

./1708_Linux_VM: line 2313: /tmp/install.dir.7795/Linux/resource/jre/bin/java: cannot execute binary file
./1708_Linux_VM: line 2313: /tmp/install.dir.7795/Linux/resource/jre/bin/java: Success

Also to test java in Opera I wen't to yahoo and icq's web messenger, neither worked but icq did launch and connected me but the connection drops after my logging is complete. My path is set in Opera... /usr/java/IBMJava2-ppc-142/jre/bin

---

### Post by flim on 2005-05-26
[QUOTE=trash]
I also tried to install Mercury but the installer keeps quiting anybody know if its a java issue or an installer issue?
sudo ./1708_Linux_VM
./1708_Linux_VM: line 2313: /tmp/install.dir.7795/Linux/resource/jre/bin/java: Success[/QUOTE]

It's a both, a java and an installer issue. Try to get a mercury version without included jre because the jre they deliver is for x86 and won't run on ppc (that's the error you get).

May I suggest using amsn instead (following the open source idea...) which is available using synaptic ;)

flim

---

### Post by trash on 2005-05-26
[QUOTE=flim]It's a both, a java and an installer issue. Try to get a mercury version without included jre because the jre they deliver is for x86 and won't run on ppc (that's the error you get).

May I suggest using amsn instead (following the open source idea...) which is available using synaptic ;)

flim[/QUOTE]

Thanks flim
actually I have amsn 0.94, it's great... I am just trying to keep up with the Jones's and Mercury seems to be the messenger closest to offering functional webcam(vid conference).
no installer available without jre for linux.:(
I will be waiting

---

### Post by agravain on 2005-05-29
[QUOTE=calum]Java 1.5 *is* available for OSX, but only for 10.4:
[http://www.apple.com/support/downloads/java2se50release1.html](http://www.apple.com/support/downloads/java2se50release1.html)[/QUOTE]
One month later after my message :)
IBM plans to release JDK 1.5 for Linux powerpc this spring too.

---

### Post by Larry Miller on 2005-07-04
[QUOTE=flim]For development, the latest jvm is 142 SR1a ( checked 22.05.05) from IBM. For G4 macs, you'll have to take the 32-bit iSeries/pSeries version - I'm not sure what would be needed for a G5 (but I assume it's the same). You can download the jdk here:
[https://www6.software.ibm.com/dl/lxdk/lxdk-p](https://www6.software.ibm.com/dl/lxdk/lxdk-p)
or, for some more infos: [http://www-106.ibm.com/developerworks/java/jdk/linux140/](http://www-106.ibm.com/developerworks/java/jdk/linux140/)

The important part about the installation is to set the following variable
JITC_PROCESSOR_TYPE=5
which will tell the jdk that it is running on a mac. Of course, you'll normally want to set
JAVA_HOME=/whereever/you/installed/it/to
as well.
As far as I know, the ibm version does not support plugins. You'll have to go for the Blackdown 1.3 jdk. I haven't tested that myself though.[/QUOTE]

1. You instructions seem to work fine but I have the same problem with both the IBM and Blackdown jdk's. I keep getting the error message
Error: can't find libjava.so

I have copied this library and installed links everywhere I can think of and BOTH packages give the same error messages and won't do anything else.

What am I missing? How do I show java and javac where this libjava.so is? It is actually IN the home/jre/bin directory, along with all of the other libxxxx.so's.

2. WHAT sets the $PATH variable in Ubuntu bash? I have tried editing every profile and bashrc file in /etc and in my home directory. I still get paths that are in NONE of these files; obviously, Ubuntu got "creative" on where it gets its initialization.

Thanks,

Larry Miller

---

### Post by Larry Miller on 2005-07-06
[QUOTE=trash]YAY!!!... Thanks people and ppc starter guide(which may need more exposure!)
java -version
java version "1.4.2"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2)
Classic VM (build 1.4.2, J2RE 1.4.2 IBM build cxppc32142sr1a-20050209 (JIT enabled: jitc))

 /usr/java/IBMJava2-ppc-142/jre/bin[/QUOTE]
What do you have in the way of a Java environment-- i.e., what else did you have to do to get the compiler to work?

I always get the message
Error: can't find libjava.so

When I do a ldd (lib dependencies) on jre/bin/libjava.so I find the following libraries missing:
libjvm.so <--this looks like the Java Virtual Machine!
libhpi.so
libjsig.so

There is a libjvm.so in jre/bin/classic and if I copy it to /lib then ldd finds it. Sorta makes sense. But no luck on the other two, and they are not in the Ubuntu distro. 

So I apparently don't have the basic underpinnings for a Java environment. I couldn't find anything with the Synaptics Package Manager that looks helpful...

Any advice hugely appreciated!

Remember, this is for a powerpc version.

Thanks,

Larry Miller

---

