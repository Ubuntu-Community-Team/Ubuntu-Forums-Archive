---
title: "Noob in Distress."
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by GenghisJohn on 2008-03-17
Hello Everyone, I'm John.  I'm using Ubuntu for the first time, installed yesterday.  I've spent the past 26 hrs trying to teach myself before I remembered "oh yeah! Ubuntu has a forums!" so, here I am.

I can't seem to get java working, I've asked a friend of mine to help me install Java, which he did but I still get this error most times I'm trying to install things, and most java pages won't load the app.

```

JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 


```

When I type in:  $java -version I get:

```

john@john-desktop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
john@john-desktop:~$ 

```

I've of course tried going to the above advertised link to download what needs downloading but...to be honest, I'm not entirely sure what I'm doing so....here I sit, waiting patiently for someone to say "here's how you fix it".

Thank you in advance.

John

---

### Post by StOoZ on 2008-03-17
your java version is not the newest possible..
you should ho to 'sun' site,and there you'll find the latest java you need with explanations of how to install it.
[http://www.java.com/en/download/linux_manual.jsp]("http://www.java.com/en/download/linux_manual.jsp")

---

### Post by Xarok on 2008-03-17
How did you install Java?

The best way to install anything is through the repositories (they will work best with your system),
and only after completely updating your system.

Downloading and installing software randomly from sites tend not to work so well in my experience.

If you don't know how to update and install packages I will tell you:

- Go to the system preferances and go to the update manager and then update everything there.

- Then in the synaptic package manager, open all your repos (to see 3rd party software, non-free software, etc.) and search for "Java" and mark the packages for installation that you need.

If you need more detail just let me know.

---

### Post by bapoumba on 2008-03-17
Not an expert on java..
I get the exact same result (using Gutsy). How did you install it, and what is not working?

---

### Post by FreewheelinFrank on 2008-03-17
Ubuntu-Restricted-Extras in Synaptic.

Make sure you have all the repositories ticked in Settings>Repositories.

---

### Post by Zill on 2008-03-17
John:  There's lots of answers *already* on the forums ;-)
For example, take a look at [this link]("http://ubuntuforums.org/showthread.php?t=648160").

---

### Post by Nythain on 2008-03-17
EDIT <im a retard>:sudo apt-get install sun-java6-jre sun-java-plugin

that usually does teh trick on most 32bit systems... it gets trickier if ya be runnin x86_64

oh and you have to make sure all your repos are enabled, because those packages are probably hidden away somewhere in one of the not so free repos :)

---

### Post by jan quark on 2008-03-17
> oh and you have to make sure all your repos are enabled, because those packages are probably hidden away somewhere in one of the not so free repos

thats true

to enable the software sources go to

system > administration > software sources and enable everything except cd and source
then run in terminal
```

sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by GenghisJohn on 2008-03-17
wow...so many responses and so fast...firstly, thank you everyone for being so prompt and friendly.  I know that we DID do the respost.  let me first try the code that Jan put first, and if that doesn't work, I'll try the manual link that StOoz put.

Let me do that and let everyone know how it went.

---

### Post by jan quark on 2008-03-17
sry forget the 6 in sun-java6-plugin

---

### Post by GenghisJohn on 2008-03-17
When I did Jan's first code 
```
sudo apt-get update
```
everything worked fine, however, when I entered the second code:
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java-plugin
```

I get the following:

```
john@john-desktop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manual installed.
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
E: Couldn't find package sun-java-plugin

```

---

### Post by billgoldberg on 2008-03-17
After enabling the other repo's it might be wise to install it using 

sudo apt-get install ubuntu-restricted-extras

because most likely you'll need the things it installs anyway.

---

### Post by billgoldberg on 2008-03-17
> **GenghisJohn said:**
> When I did Jan's first code 
```
sudo apt-get update
```
everything worked fine, however, when I entered the second code:
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java-plugin
```

I get the following:

```
john@john-desktop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manual installed.
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
E: Couldn't find package sun-java-plugin

```

Go to synaptic package manager (system -> administration).

Look for "sun" and right click those packages, and choose "completely remove". Then press "apply". The press the reload button. And then install sun-java6-jre from synaptic.

or use the restricted extras

A little extra advice.

Since you're new, you'll have some other problems with media, like dvd and divx playback.

Add the medibuntu repository by using the instructions [here]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/"), and then install vlc. Or if you prefer totem (standard movie player) then isntall "non-free-codecs" and "libdvdcss2" using sudo apt-get install or synaptic.

---

### Post by GenghisJohn on 2008-03-17
Same error when I run that script bill, I get:

```
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

---

### Post by GenghisJohn on 2008-03-17
Ok Bill, will do, doing that now.  Give me just a moment sir.

---

### Post by GenghisJohn on 2008-03-17
when I open synaptic manager, I get:
```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

```

then, I open a terminal and put in:
```
$sudo dpkg --configure -a
```

and I get right back to the same error of:
```

john@john-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

---

### Post by jan quark on 2008-03-17
perhaps just try to do what the message says

go to
[https://sdlc2d.sun.com/ECom/EComActionServlet;jsessionid=68904169FA5BAF1CCFF3EEAD08AE012E](https://sdlc2d.sun.com/ECom/EComActionServlet;jsessionid=68904169FA5BAF1CCFF3EEAD08AE012E)
and download the file

Java(TM) SE Development Kit Documentation 6, English

then copy it to the location /tmp

```
sudo cp path/to/docfile /tmp
```

and change the ownership to root

```
sudo chown -R root:root /tmp/name of docfile
```

---

### Post by GenghisJohn on 2008-03-17
ok, gonna try that now.  give me just a few though.

---

### Post by billgoldberg on 2008-03-17
Did you completely remove the packages using syntapic, and then reinstalled them using synaptic?

You don't need to download the sun-java6-doc package.

The only package you need to download from synaptic is "sun-java6-jre". I think it will automatically install "sun-java6-plugin" and "sun-java6-bin".

Those are the only three java related files you need.

[IMG]http://img37.picoodle.com/img/img37/4/3/17/f_javam_c170082.png[/IMG]

Please install them using synaptic. Using the terminal makes things complicated and some people reported that installing using synaptic fixed something apt-get couldn't install, I never had that, but still.

---

### Post by GenghisJohn on 2008-03-17
> Did you completely remove the packages using syntapic, and then reinstalled them using synaptic?

yes, I tried but get the same error when I tried to use Synaptic so...I'm downloading the thing and see if that works.

---

### Post by bapoumba on 2008-03-17
Did you accept the license when it got installed?

---

### Post by blakboy on 2008-03-17
Another way to install Java and other stuff is buy installing automatix.

This will simplify a lot of other installations for you also.

---

### Post by billgoldberg on 2008-03-17
> **blakboy said:**
> Another way to install Java and other stuff is buy installing automatix.

This will simplify a lot of other installations for you also.
[URL="http://pimpyourlinux.com/linux-feature-review/automatix-can-break-your-linux-ubuntu-install/"]
Steer away from automatix![/URL]

---

### Post by jan quark on 2008-03-17
automatix is not recommend to install (by me and by others as well)

it can cause severe compatibility issues
lets stick to the normal way of installing applications

---

### Post by billgoldberg on 2008-03-17
There is a program by a ubuntuforum user that will install java6 for you.

It's basically a back-up solution but it install allot of other programs as well.

You could maybe try that.
[URL="http://ubuntu-utah.ubuntuforums.org/showthread.php?t=613462"]
LINK[/URL]

---

### Post by brownknight on 2008-03-22
Hi John. Is your problem solved already?

---

