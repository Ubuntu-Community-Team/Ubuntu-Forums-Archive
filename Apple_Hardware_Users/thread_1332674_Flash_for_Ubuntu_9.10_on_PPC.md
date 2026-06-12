---
title: "Flash for Ubuntu 9.10 on PPC"
date: 2009-11-20
forum: Apple Hardware Users
---

### Post by 8oluf7 on 2009-11-20
I acquired via Freecycle an Apple Power Macintosh G4/933 (QS 2002) expanded with a 100MB Ethernet card, Pioneer DVD-RW, to which I have added the full complement (1.5GB) of RAM. The display is a LaCie electron22blue with phenomenal resolution capability. 

Disappointed by the lack of support for PPC in Snow Leopard, I decided to try Ubuntu 9.10 on a second (120GB) hard drive. I have several years experience with this distro on i386 PCs, both Intel and AMD. I won't go into the problems I had getting the beast installed - including having to run a script in order to get the correct key assignment for the tilde on the Mac keyboard.

My problem is - I do like to listen to/view BBC broadcasts, both live and catch-up. For this, the BBC insists that I have 'genuine' Macromedia Flash. The FOSS alternatives are not recognised. I have learned, by poking around, that:[LIST]
[*]Ubuntu on PPC is, effectively, the 'free' version. 
[*]Medibuntu won't install. 
[*]There isn't a Linux/PPC version of Flash
[*]nspluginwrapper isn't available for 9.10[/LIST]
OK - plan B is to install Mac on Linux and use the OS X facilities for BBC iPlayer. 'mol' is in the 9.10 repositories but, guess what, it won't install. There appears to be a dependency inconsistency that synaptic can't resolve. "xxx depends on mol but this isn't going to be installed".

Move to Plan B2 - make Mac on Linux from source. Get source, follow instructions as far as running ./configure, when it throws an error - can't find zlib. Neither can I - for 9.10 it has been replaced with something else. A bug was raised on this problem and sorted shortly before 9.10 was released. But this fix hasn't reached the PPC version yet.

Any news on when any of these alternative ways of getting 'genuine' flash working will be fixed - or any suggestions for another way in which I can get access to BBC iPlayer content?

---

### Post by linuxopjemac on 2009-11-20
you can try this:
[http://ubuntuforums.org/showthread.php?t=951546&page=2](http://ubuntuforums.org/showthread.php?t=951546&page=2)

---

### Post by 8oluf7 on 2009-11-20
> **linuxopjemac said:**
> you can try this:
[http://ubuntuforums.org/showthread.php?t=951546&page=2](http://ubuntuforums.org/showthread.php?t=951546&page=2)
The latest reviews are not encouraging - doesn't work with Firefox 3.5.3, don't use with Linux ...

---

### Post by rjcalifornia on 2009-11-21
you can use Xine to watch Youtube video without downloading them instead....

---

### Post by linuxopjemac on 2009-12-14
I compiled the latest version of Gnash and Gnash plugin. It works a little bit for simple flash. Not Youtube and why I intended it for, Google analytics flash content.

---

### Post by nizuri on 2010-02-13
Did anyone find a solution?

---

### Post by linuxopjemac on 2010-02-13
[http://mac.linux.be/content/watching-youtube-and-lack-flash](http://mac.linux.be/content/watching-youtube-and-lack-flash)

---

### Post by oswaldkelso on 2010-02-13
MOL works on Debian lenny. And older versions of Ubuntu (apparently) 

genuine flash - NO. Youtube yes, lots of methods 

iplayer yes for most with get_iplayer  (I do like to watch MOTD)

apt-get install get_iplayer

[http://linuxcentre.net/getiplayer](http://linuxcentre.net/getiplayer)

---

### Post by nizuri on 2010-02-13
Thank you two so much! Using clive to fetch the youtube-videos and mplayer to open them worked just fine.

---

### Post by oswaldkelso on 2010-02-13
> **nizuri said:**
> Thank you two so much! Using clive to fetch the youtube-videos and mplayer to open them worked just fine.

I use 

```
cclive -s youtube-URL  
```

You need to edit the hidden  .ccliverc file as per man page

[http://code.google.com/p/cclive/](http://code.google.com/p/cclive/)
[http://code.google.com/p/cclive/wiki/FAQ#How_is_cclive_different_from_clive](http://code.google.com/p/cclive/wiki/FAQ#How_is_cclive_different_from_clive)

use the abby gui for multiple URL's 

The advantage is it's work's with out a browser so is light and fast. You just need the url. It works on other sites (see the list) You get to keep the clips if you choose. If your on old hardware you can use a light fast browser like dillo2 or net-surf. It just works :)

---

