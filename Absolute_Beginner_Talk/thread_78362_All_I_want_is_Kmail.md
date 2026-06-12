---
title: "All I want is Kmail"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-10-18
Ubuntu 5.04. I installed kubuntu-desktop just so I could use Kmail, because Evolution is too much of a hog. Now I find Kmail is in Kontact, and that's a hog, too.

I've read Kmail (and Knode, while I'm at it) can be run as standalone apps. But how?

I'm getting to like the Gnome desktop, but I'll switch to KDE if I have to.

---

### Post by Manny C on 2005-10-18
Kmail can be run from the command line:
```
 kmail 
```

Or create a menu item and when asked for an executable, simply type "kmail".

Have you considered using Thunderbird as your email client?

---

### Post by editrix on 2005-10-18
[QUOTE=Manny C]Kmail can be run from the command line:
```
 kmail 
```[/QUOTE]

Thanks, I tried that, and got all kinds of error messages, something about no parent directory. So I quit before I really screwed things up. I even saved the error messages, but in Ubuntu, and right now I'm in Win :-( so I can get my mail & newsgroups.

[QUOTE=Manny C] Or create a menu item and when asked for an executable, simply type "kmail".[/QUOTE]

Um, how, please? Install the Gnome menu editor? 

[QUOTE=Manny C]Have you considered using Thunderbird as your email client?[/QUOTE]

Yes, and I prefer Kmail, which *used to be* a light program. Also, I'm on dialup, and as I recall, TB won't delete messages from server based on filters. I've got a lot of spam filters set up for OE, which work fairly well. Kmail, using regular expressions, is brilliant that way.

---

### Post by Manny C on 2005-10-18
[quote=editrix]Thanks, I tried that, and got all kinds of error messages, something about no parent directory. So I quit before I really screwed things up. I even saved the error messages, but in Ubuntu, and right now I'm in Win :-( so I can get my mail & newsgroups.[/quote] 
Will wait for your error messages.

[quote=editrix]
Um, how, please? Install the Gnome menu editor? 
[/quote]

Yes install SMEG. I use KDE and can't remember the workings of SMEG. From memory, very intuitive.

[quote=editrix]
Yes, and I prefer Kmail, which *used to be* a light program. Also, I'm on dialup, and as I recall, TB won't delete messages from server based on filters. I've got a lot of spam filters set up for OE, which work fairly well. Kmail, using regular expressions, is brilliant that way.[/quote] 
Cool. I don't use Thunderbird either. Use Kontact. ;)

---

### Post by editrix on 2005-10-18
Yuk! Still trying to figure out how to use replies. Meant to quote you, Manny C

> Will wait for your error messages.

I won't paste everything here, it's so repetitive.

Yuk, yuk! I *think* what's below if from apt. Damn, I'm confused. It *may* be from running kmail at the command line, but I'm almost postive not, but rather when it was installing.

Creating link /home/wolfgang/.kde/socket-ubuntu.
Created link from "/home/wolfgang/.kde/socket-ubuntu" to "/tmp/ksocket-wolfgang"Creating link /home/wolfgang/.kde/tmp-ubuntu.
Created link from "/home/wolfgang/.kde/tmp-ubuntu" to "/tmp/kde-wolfgang"
kbuildsycoca running...
Creating link /home/wolfgang/.kde/cache-ubuntu.
Created link from "/home/wolfgang/.kde/cache-ubuntu" to "/var/tmp/kdecache-wolfgang"
kbuildsycoca: WARNING: '/usr/share/applications/themus-theme-applier.desktop' specifies undefined mimetype/servicetype 'application/x-gnome-theme-installed'
kbuildsycoca: WARNING: '/usr/share/applications/nautilus-folder-handler.desktop' specifies undefined mimetype/servicetype 'x-directory/gnome-default-handler'

<snip>

kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'application/rss+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'application/rdf+xml'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav'
kbuildsycoca: WARNING: '/usr/share/applications/mozilla-firefox.desktop' specifies undefined mimetype/servicetype 'x-directory/webdav-prefer-directory'
kbuildsycoca: WARNING: '/usr/share/applications/rhythmbox.desktop' specifies undefined mimetype/servicetype 'audio/x-mpeg'
kbuildsycoca: WARNING: '/usr/share/applications/rhythmbox.desktop' specifies undefined mimetype/servicetype 'application/x-flac'
kbuildsycoca: WARNING: '/home/wolfgang/.local/share/applications/gedit-usercustom.desktop' specifies undefined mimetype/servicetype 'application/x-extension-WAB'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645impress.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.impress.template'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645impress.desktop' specifies undefined mimetype/servicetype 'application/vnd.ms-powerpoint'
kbuildsycoca: WARNING: '/usr/share/applications/kde/amarok.desktop' specifies undefined mimetype/servicetype 'audio/x-sid'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.global'
kbuildsycoca: WARNING: '/usr/share/applications/ooo645writer.desktop' specifies undefined mimetype/servicetype 'application/vnd.sun.xml.writer.template'

<snip>

kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/bmp'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/jpg'
kbuildsycoca: WARNING: '/usr/share/applications/eog.desktop' specifies undefined mimetype/servicetype 'image/x-gray'

<snip><snip><snip><snip><snip>

Invalid entry (missing '=') at /tmp/kde-wolfgang/kconf_updatef8yrva.tmp:1
Launched ok, pid = 30828
Launched ok, pid = 30853
Launched ok, pid = 30882
wolfgang@ubuntu:~$ There are already artsd objects registered, looking if they are active...

Error: Can't add object reference (probably artsd is already running).
       If you are sure it is not already running, remove the relevant files:

       /tmp/mcop-wolfgang/Arts_SoundServerV2
       /tmp/mcop-wolfgang/Arts_SoundServer
       /tmp/mcop-wolfgang/Arts_SimpleSoundServer
       /tmp/mcop-wolfgang/Arts_PlayObjectFactory
       /tmp/mcop-wolfgang/Arts_AudioManager

There are already artsd objects registered, looking if they are active...

Error: Can't add object reference (probably artsd is already running).
       If you are sure it is not already running, remove the relevant files:

       /tmp/mcop-wolfgang/Arts_SoundServerV2
       /tmp/mcop-wolfgang/Arts_SoundServer
       /tmp/mcop-wolfgang/Arts_SimpleSoundServer
       /tmp/mcop-wolfgang/Arts_PlayObjectFactory
       /tmp/mcop-wolfgang/Arts_AudioManager

What's below is *definitely* from when I typed kmail from the command line, then when it loaded I started to configure it. But when I noticed I had this whole new bunch of error messages, I stopped. So, I don't know at what point they showed up.

When I did run Kontact, Kmail seemed okay. At least, it had my imported OE messages--and ain't that a nice feature!

kmail: WARNING: Can not find parent folder
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3a010a0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3a010a0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  18
  Minor opcode:  0
  Resource id:  0x3a010a0
kmail: WARNING: Can not find parent folder
kmail: WARNING: Can not find parent folder
kmail: WARNING: Can not find parent folder
kmail: WARNING: Can not find parent folder
kmail: WARNING: Can not find parent folder
kmail: WARNING: Can not find parent folder
kmail: WARNING: Can not find parent folder

Oh, and I haven't installed smeg yet--need to update the sources for extra repositories--an odd program not to include by default, IMO

---

### Post by Manny C on 2005-10-18
Um, it looks pretty bad. Quick question. Do you have Gnome, KDE and XFCE installed?

Looking at your output, i am guessing (stress the guess), that your install is broken. Hopefully, you can easily backup your documents or at least have your /home directory on a separate partition. Because I think, and I stress, I think, you may need to clean install.

---

### Post by editrix on 2005-10-18
[QUOTE=Manny C]Um, it looks pretty bad. Quick question. Do you have Gnome, KDE and XFCE installed?[/QUOTE]

If XFCE is installed, I didn't put it there :-) Otherwise, yes to Gnome and KDE. In fact, I'm in KDE right now.

[QUOTE=Manny C]Looking at your output, i am guessing (stress the guess), that your install is broken.[/QUOTE]

Well, it may very well be that the Kubuntu install is broken, since I did it over many sessions on dialup. 

I switched to KDE hoping I'd find the answer to my original question there, but it isn't. Sigh!

---

