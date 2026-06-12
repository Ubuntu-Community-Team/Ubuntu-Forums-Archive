---
title: "Scanner HP 3500 error"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Benzorro on 2006-05-05
I  have a HP scanjet 3570c scanner that works great in XP.  Whenever I try to use it I get an error which says Backend sends more image data than defined in parameters.  I can close this and do a scan but the scan comes out horrible.  Why do I keep getting this error and how can I get rid of it?

---

### Post by Wormsie on 2006-10-01
Hmm, I'm suprised it works at all. I have the same scanner as you and it doesn't work... This might help, I'm hoping ti will help me in getting the scanner to work at all. :p

[http://www.ubuntuforums.org/showpost.php?p=1030523&postcount=16](http://www.ubuntuforums.org/showpost.php?p=1030523&postcount=16)

---

### Post by Sef on 2006-10-01
So when you get that message after Applications > Graphics > Xsane Image Scanner?

If so, what version are you using? (Etchy, Dapper, Breezy, etc.)

Also check out the [the sane project.]("http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD")

---

### Post by Benzorro on 2006-10-02
When I originally had this problem I was using Breezy.  Now that I upgraded to 6.06, my scanner is not recognized at all.  I did give up but now that the weather is getting colder I will give it a try again.  I will load the back end again and see what happens.

---

### Post by HanZo on 2007-02-18
I have an HP 3500c and this one, despite being now officially supported by the sane backend (rating "good"), does not seem to be doing anything apart from producing some horrible noise and crashing Xsane (but also other frontends don't work). tried several things, wasted precius hours of my life trying to find some informations on it... still nothing.
Looks like scanning is still not something that works on linux, my other scanner, an Epson perfection 2580, worked out of the box the first time I booted the newly installed ubuntu (that was dapper) but after that it would refuse to work again, same thing with edgy. Nobody knows anything about it, nothing to do.

---

### Post by old_geekster on 2007-02-18
I have the 3570, also.  It is recognized by Ubuntu 6.10, but does make more noise when it runs than with XP.

My problem is I get some print that has three colors when I scan a text document.  It evidently is not recognizing plain black text.  I will work on it when I have time.

I still have XP on the other drive, so if I require a scanner, I will use XP.

---

### Post by mhenriday on 2007-02-20
I can't seem to find the button for starting a new thread, so since my **HP ScanJet 3300C** is pretty close to the **3500** with which this thread is concerned and my problem - non-recognition is much the same, I thought I'd post here. I'm running Edgy with Gnome and Xsane installed, but the latter does not recognise my scanner - when I perform **Applications &#8594; Graphics &#8594; Xsane scanner**, I get an error message stating «No units available». I've tried to check in the terminal, using  «grep -e scanner /etc/group», which gives me the response 
«scanner: x:110:cupsys,mhenriday,hplip,[other user name], which would seem to me to indicate that I should have access to the scanner, but when I try commands like «chown root.scanner /dev/usb/scanner» I get the following response : 
«chown: cannot reach "/dev/usb/scanner": The file or catalogue does not exist». As I am dependent upon the scanner for many tasks, I should greatly appreciate help in getting it running. Any ideas and/or suggestions ?...

Henri

---

### Post by hotani on 2007-03-02
I'm trying to get a 3300c working as well, and not having any luck.

I tried downloading [the SANE backend](http://sourceforge.net/projects/hp3300backend), but when I try to do anything with it, it fails. :(

If anyone has this scanner running, please let us know how you did it.

---

### Post by mhenriday on 2007-03-15
No one yet seems to have come forward with a solution to our difficulties in making **Edgy** recognise **HP** scanners in the 3300 - 3500 range. Is this a known **Edgy** problem ? Is there any likelihood of its being corrected in **Feisty** ?...

Henri

---

### Post by hotani on 2007-03-15
Oops, I did not post back after fixing this. Mine was eventually recognized, and although I was all over the place with attempts to make it happy, I believe the above link is what actually did it.

---

### Post by mhenriday on 2007-03-16
**Hotani**, I'm certainly glad you posted back with your encouraging info ! I've now downloaded the **HP3300c SANE backend** to my desktop. Do you have any suggestions with regard to _installation_ ? I've had some difficulty installing other programmes on **Edgy**, so I'd be grateful for any advice you have to give in this regard....

Henri

---

### Post by hotani on 2007-03-17
once you download, unpack it:
```

tar -zxf backend-20060304.tar.gz

```

then go into the 'backend' directory and view the INSTALL doc:
```

> cd backend
> gedit INSTALL

```

In there are some not-so-clear instructions, including a 'testtool' which I never got to work. But the important part is later in the document:

```

To make your scanner system wide available,
you will need to "patch" SANE (http:/sane-project.org)

to patch the sane backends
get the latest sane-backend-sources from http:/sane-project.org,
unpack them and call:

$ ./patch-sane.sh /path/to/the/sane/sources/sane-backends-1.0.XX
$ cd /path/to/the/sane/sources/sane-backends-1.0.XX
$ ./configure --prefix=/usr # can be different on various systems
$ make
$ sudo make install
followed by the root-password

```

First off, the address needs to be this:
[http://www.sane-project.org/](http://www.sane-project.org/)

[Here is the direct download](http://alioth.debian.org/frs/download.php/1669/sane-backends-1.0.18.tar.gz). Once you have that, unpack it:
```

tar -zxf sane-backends-1.0.18.tar.gz

```

Once it is unpacked, that is the directory necessary for line 1 above, so go back to the /backend directory and run the shell script. I needed to make it executable first. This is what it looked like on mine:
```

> cd /home/hotani/downloads/backend/
> chmod a+x patch-sane.sh
> patch-sane.sh /home/hotani/downloads/sane-backends-1.0.18

```
The scanner *should* be recognized now, but I make no promises! :)

The next step would be to go back into the sane-backends directory and run configure, make then make install. If memory serves, that never worked. But the patch itself seemed to get the scanner going. It was one of those times when it just starts working and you back away, being careful not to touch anything else lest it stop...

---

### Post by mhenriday on 2007-03-17
Thanks for the reply, **Hotani** ! I followed your instructions and unpacked the backend and then tried to follow the INSTALL instructions, but like you, failed to get the «test tool» to work. *Tant pis ! * I then proceeded to download the patch, using the link you provided, and unpack it. Following your instructions, *mutatis mutandi* (I have never created a «download» sub-catalogue), I then made the download executable, as follows :
[INDENT]mhenriday@mhenriday-desktop:~$ cd /home/mhenriday/backend/
mhenriday@mhenriday-desktop:~/backend$ chmod a+x patch-sane.sh[/INDENT]
So far so good ! But when I attempted the next operation above, I got :
[INDENT]chmod: ändrar rättigheter på [changes permissions for] "patch-sane.sh": Operationen inte tillåten [Operation not allowed][/INDENT]
Thinking this then to be a simple question of permissions, I repeated the command after typing in «sudo», with the following result :
[INDENT]mhenriday@mhenriday-desktop:~/backend$ sudo chmod a+x patch-sane.sh
mhenriday@mhenriday-desktop:~/backend$ patch-sane.sh /sane-backends-1.0.1bash: patch-sane.sh: kommando hittades inte [Command not found]
mhenriday@mhenriday-desktop:~/backend$[/INDENT]
Obviously, I'm missing something, but what and why ? I'd be very grateful if you could bear with me and help me to figure out where I've gone wrong....

Henri

---

### Post by hotani on 2007-03-17
Maybe try it with a './' in front, and a full path to the backends dir like so:
```

> ./patch-sane.sh /home/username/sane-backends..../

```

---

### Post by mhenriday on 2007-03-18
> **hotani said:**
> Maybe try it with a './' in front, and a full path to the backends dir like so:
```

> ./patch-sane.sh /home/username/sane-backends..../

```
Who said that life was supposed to be easy ! Following your instructions, I commanded the following operation :
[INDENT]mhenriday@mhenriday-desktop:~/backend$ sudo chmod a+x ./patch-sane.sh[/INDENT]
And after supplying my password got :
[INDENT]mhenriday@mhenriday-desktop:~/backend$ ./patch-sane.sh /home/mhenriday/sane-backends-1.0.18
Adding new files to the SANE source tree...-e    DONE
Modifying doc/Makefile.in...-e                   DONE
Modifying backend/Makefile.in...-e               DONE
Relocating files...-e                            DONE
«Modifying backend/dll.conf...grep: /home/mhenriday/sane-backends-1.0.18/backend/dll.conf: Filen eller katalogen finns inte [File or catalogue does not exist]
-e                                               DONE-

SANE patched with success![/INDENT]
While I had some suspicions about that line saying that /home/mhenriday/sane-backends-1.0.18/backend/ did not exist, the last line to the effect that **SANE** had been patched successfully sounded hopeful, so I tried **Applications &#8594; Graphics &#8594; XSane scanner**, but alas, received for my pains only a message stating that no units were available. Upon clicking on «Help», I was told that the possible causes were :
[LIST=1]
[*]There is no unit which is supported by SANE
Compatible units are already in use
The unit file do not allow you to use it - try doing so as root
SANE does not load the drive routine (man sane-dll)
The drive routine has not been correctly configured (man sane-"backendname")
Possibly more than one version of SANE has been installed
[/LIST]

My suspicion is that the problem does in fact lie with that non-existent «/home/mhenriday/sane-backends-1.0.18/backend/». In that case, nice to know - but where do I go from there ?...

Henri

---

### Post by hotani on 2007-03-18
not sure what is going on there. I will try to get it going with a different machine on monday and post the full process (provided it works...).

From what I can tell, these backend sane drivers were not included because they were either buggy or incomplete. Hopefully we'll see them in the default install someday.

---

### Post by mhenriday on 2007-04-08
> **hotani said:**
> ...

From what I can tell, these backend sane drivers were not included because they were either buggy or incomplete. Hopefully we'll see them in the default install someday.

Anyone know if they've been included in the default install for **Feisty** ?...

Henri

---

### Post by hotani on 2007-04-09
Good news everyone!

I just plugged the scanner into my Feisty test mule(tm) and it worked! If memory serves, I did not do any tweaking last time I was trying to get it going, so it looks like they included the drivers.

---

