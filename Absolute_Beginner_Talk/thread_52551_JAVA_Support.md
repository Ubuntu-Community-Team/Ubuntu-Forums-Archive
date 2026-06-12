---
title: "JAVA Support"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by hamiltonZN on 2005-07-28
I need to run some Java dependant software. I've installed the Synaptics Java (base of all Java packages). When I try to run the software from com.prompt I get 'java - command not found'

What are my options???

---

### Post by kevcart3 on 2005-07-28
[QUOTE=hamiltonZN]I need to run some Java dependant software. I've installed the Synaptics Java (base of all Java packages). When I try to run the software from com.prompt I get 'java - command not found'

What are my options???[/QUOTE]

First, make 100% sure java is installed, open terminal, then type "java -version"

If you get the same "java - command not found" issue, make sure you have "sun-j2re1.5" installed by using [this](http://ubuntuguide.org/#extrarepositories) guide to add sources, and then:

"apt-get update"

and, finally:

"apt-get install sunj2re1.5"

Then, you should be able to run "java -version" and it should tell you some info about what version of java you are running. 

Hope this helps!

---

### Post by garnertr on 2005-07-28
Greetings,

OK, now I'm stumped, b/c I have SUN-JRE installed but yet in firefox it states that it cannot run the java environment and then points back to SUN's homepage...

Any idea on getting JAVA to work inside of OPERA and/or FIREFOX?

---

### Post by hamiltonZN on 2005-07-28
Hi there,

I tried what you told me and changed that source.list file. This is a sample of the errors I get on running update :
"
Err [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) hoary-updates Release.gpg
  Could not connect to za.archive.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused) [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused) [IP: 82.211.81.138 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused) [IP: 82.211.81.138 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
...
...
"

What next?

---

### Post by kevcart3 on 2005-07-28
hmmm, that's strange, here is what my sources.list looks like:


```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

deb http://acm.cs.umn.edu/ubp/ hoary-backports main universe multiverse restricted

```

Maybe you can compare them and see if there is some kind of difference.

---

### Post by jeffe on 2005-07-28
i have the same issue,...

java -version -> 
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)

but can't seem to use it in firefox.   ](*,) 

[QUOTE=garnertr]Greetings,

OK, now I'm stumped, b/c I have SUN-JRE installed but yet in firefox it states that it cannot run the java environment and then points back to SUN's homepage...

Any idea on getting JAVA to work inside of OPERA and/or FIREFOX?[/QUOTE]

---

### Post by jeffe on 2005-07-28
i found what to do on another thread

we basically have to install the plug in ourselves 

sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins


[QUOTE=garnertr]Greetings,

OK, now I'm stumped, b/c I have SUN-JRE installed but yet in firefox it states that it cannot run the java environment and then points back to SUN's homepage...

Any idea on getting JAVA to work inside of OPERA and/or FIREFOX?[/QUOTE]

---

### Post by Copter on 2005-08-20
[QUOTE=kevcart3]
...
"apt-get install sunj2re1.5"
...
[/QUOTE]it worked here, using Opera 8.01 :). previously i installed .rpm from sun site and aliened it. it did not work and it used to crash any app that was using java. i removed it (jre) and now everything works fine.

thanks!

copter :]

---

