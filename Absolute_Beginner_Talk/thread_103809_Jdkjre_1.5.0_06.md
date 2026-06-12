---
title: "Jdk/jre 1.5.0_06"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by linuxnewbeee on 2005-12-14
Hi All:

As my name suggests, I'm totally new to Linux.

I'm trying to set up JDK/JRE 1.5.0 on an IBM laptop, on which Ubuntu 5.04 Hoary has been installed. I've followed various instructions but for some reason the machine can't find the bin directory for java. Here's what I did:

1. I installed JDK and JRE onto the /home/MYUSER/ directory (where MYUSER is my login) using the root terminal.

2. I then opened etc/profile using the root terminal, by typing sudo gedit ../../etc/profile so that I can open the file without it being read-only.

3. I then added the following lines to the file (my additions are in red):

 if ["`id -u`" -eq 0; then
     PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11[COLOR="Red"]:./home/MYUSER/jdk1.5.06/bin:./home/MYUSER/jre1.5.06/bin[/COLOR]"
 else
     PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11/usr/games[COLOR="Red"]:./home/MYUSER/jdk1.5.06/bin:./home/MYUSER/jre1.5.06/bin[/COLOR]"
 fi

then, at the end of the profile, right above PATH, I wrote
 [COLOR="red"]export CLASSPATH=./home/MYUSER/jdk1.5.0_06/bin:./home/MYUSER/jre1.5.0_06/bin[/COLOR]

I'm trying to run eclipse, and apparently eclipse can't find the bin directories for java. I went into the terminal, and typed "echo $PATH" and it gives me the path string but without my entry above. I type in echo $CLASSPATH and I get a blank.

Obviously, I'm doing something wrong here and don't understand really what I'm doing. Can anyone help me out here?

Thanks!

Joe

---

### Post by pertti on 2005-12-14
[QUOTE=linuxnewbeee]PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11[COLOR="Red"]:./home/MYUSER/jdk1.5.06/bin:./home/MYUSER/jre1.5.06/bin[/COLOR]"
[/QUOTE]

I've never run eclipse from a "manually" installed java, so I can't help much here. Try removing that dot in the path entry that you've added (":/home/MYUSER/jre1.5.06/bin" instead of ":./home/MYUSER/jre1.5.06/bin").

It seems that you installed java using the .bin from Sun's website. Perhaps it would be easier if you install java as a package (programs and libraries in ubuntu are managed as packages). This way java will be available to all users and can be uninstalled using a package manager like apt-get or Synaptic.

You'll have to package java yourself (don't worry, it's easy). This wiki page explains how to do it: /usr/lib/j2sdk1.5-sun/bin/java[https://wiki.ubuntu.com/JavaPackageBuildNewVersions]("https://wiki.ubuntu.com/JavaPackageBuildNewVersions").

After that issue this command:

```
sudo update-alternatives --config java
```

and from the list select something like "/usr/lib/j2re1.5-sun/bin/java".

---

### Post by linuxnewbeee on 2005-12-14
Thanks for the response. The removal of the "." didn't work (i should have mentioned that I tried it without it first before adding it).

After some frustrating tries, I went with what you suggested (adding it as a package, following the instructions found on the linked page you kindly referenced). I'm working through it and hopefully I'll get it to work.

Any other comments or suggestions are very welcome.

Thanks again!

---

### Post by linuxnewbeee on 2005-12-14
Okay, I'm having some trouble as usual.

Here is where I got:

1. I type in the terminal the following: 
sudo fakeroot make-jpkg ./Desktop/Distribution/jdk-1_5_0_06-linux-i586.bin

RESULT:
Can't do it cuz Ubuntu says that i am a real root (from doing the sudo thing, I take it).

2. So, I remove the 'sudo' and just type instead: 
fakeroot make-jpkg ./Desktop/Distribution/jdk-1_5_0_06-linux-i586.bin

RESULT:
Inflation of a bunch of things, creating several things, then the last MANY lines I get PERMISSION DENIED in a bunch of things. I'd cut and paste it here but the ubuntu machine is not the same machine on which I'm accessing these forums. I'm writing on these forums using my windows machine, which is much faster and more stable.

What's happening here? I'm guessing that I'm getting the PERMISSION DENIED because I'm not a root user. But I can't install the package as a root--it won't let me.

joe

---

### Post by pertti on 2005-12-15
Woops! You're right, I also get some "permission denied" warnings :(. I installed the JDK some time ago and it's been working ok for me, but maybe I'm missing some "integrations" things (ie. some of those files are icons and mime-types). I'll look for a solution to this - I want my java mime-types back :).

As for the "sudo" problem, it's alright. The job of "fakeroot" is to make the java installer believe that it has permission to mess with system, . "jpkg" logs what the installer is doing, and uses that information to build the package.

---

### Post by My8os on 2005-12-15
There are programs that look for the env. variable JAVA_HOME and not look into PATH to find the java-executable.Maybe eclipse is one of them.
Try do what i do every time i install suns' .bin:
1. Open /etc/profile as you do.
2. Just write:
```

JAVA_HOME=/home/MYUSER/jdk1.5.06
PATH=$JAVA_HOME/bin:$PATH
export PATH

CLASSPATH=.:$CLASSPATH
export CLASSPATH

```

Works for me...hope it does for you too :) .

---

### Post by linuxnewbeee on 2005-12-15
Thanks for the suggestions fellas. So far, nothing seems to work. I added the suggested JAVA_HOME and CLASSPATH but only to no avail (tried logging out, rebooting, etc.). Doing an echo on PATH gives me a path string without the java_home. Doing an echo on CLASSPATH gives me nothing.

Again, suggestions are welcome.

I have to get this laptop to someone with eclipse and a java environment installed on it by 4 p.m. today. I might just have to install Windows 98 on it, since at this point Windows 98 seems to be the better of the two for the purposes at hand (even though I hate Win 98).

---

### Post by Leif on 2005-12-15
try installing java using these instructions instead :

[https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)

---

