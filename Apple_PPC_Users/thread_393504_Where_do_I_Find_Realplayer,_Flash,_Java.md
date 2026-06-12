---
title: "Where do I Find Realplayer, Flash, Java"
date: 2007-03-25
forum: Apple PPC Users
---

### Post by Who on 2007-03-25
Hi all,

I've just moved over from x86 to an iMac G4 - I'm using Feisty beta (I'm used to it, on x86). I'm very happy with how smoothly the install went, but I'm struggling to find the software tools I and my family normally use:

Here's what I'm looking to do and what I've tried already:
[LIST]

[*]1. **Realplayer** OR something that reliably plays streams from the bbc website 
*already tried helix player and mplayer - neither seem to work. I have found realplayer 8 but would like something newer if possible. curiously neither totem, mplayer, or vlc can open the streams from the bbc website*
[*]2. **Flashplayer** OR something to allow me to use youtube
*I have libflash-mozplugin, libflashswfplayer and swf-player installed, but no Youtube and Pandora crashes*
[*]3. **Java **RE and browser plugin
*all the official SUN packages seem to be available except the *-bin one, which is essential!*

[/LIST]

I hope people can point me in the right directions

---

### Post by Kevkill on 2007-03-25
Hi, 
Im not sure if it works on Feisty, but Automatix does all of the above under Edgy.
 
[www.getautomatix.com](www.getautomatix.com)

-Kev

---

### Post by Who on 2007-03-25
> **Kevkill said:**
> Hi, 
Im not sure if it works on Feisty, but Automatix does all of the above under Edgy.
 
[www.getautomatix.com](www.getautomatix.com)

-Kev

It does ALL? for Power PC?

That sounds pretty useful. What are my chances of successfully using Edgy's Automatix on Feisty? They've dropped ppc support from now on

---

### Post by qamelian on 2007-03-25
> **Who said:**
> It does ALL? for Power PC?

That sounds pretty useful. What are my chances of successfully using Edgy's Automatix on Feisty? They've dropped ppc support from now on

According to their site, Automatix does not support PowerPC at all, just i386 and AMD64.

---

### Post by Auria on 2007-03-25
Hmm you should have read a bit before installing Ubuntu on PPC - very unfortunately there is NO reliable way to use java and flash on PPC.

For flash, you can try Gnash - but it won't play much stuff - on my computer the only thing it plays correctly is ads

FOr Java, you can install IBM's VM or GJC (or is it GCJ?) but once again won't run much stuff, and almost no graphical stuff.

---

### Post by dpny on 2007-03-25
> **Auria said:**
> Hmm you should have read a bit before installing Ubuntu on PPC - very unfortunately there is NO reliable way to use java and flash on PPC.

For flash, you can try Gnash - but it won't play much stuff - on my computer the only thing it plays correctly is ads

FOr Java, you can install IBM's VM or GJC (or is it GCJ?) but once again won't run much stuff, and almost no graphical stuff.

I have IBM's latest JAVA on my Pismo and it works fine. No Flash, tho.

---

### Post by Who on 2007-03-25
> **Auria said:**
> Hmm you should have read a bit before installing Ubuntu on PPC - very unfortunately there is NO reliable way to use java and flash on PPC.

For flash, you can try Gnash - but it won't play much stuff - on my computer the only thing it plays correctly is ads

FOr Java, you can install IBM's VM or GJC (or is it GCJ?) but once again won't run much stuff, and almost no graphical stuff.


Well, I had repaired a broken mac and had no other OS - so no flash is better than nothing at all :)

Do you have a different distro you'd recomend for ppc/linux? It looks like Fedora is nicely sorted...

Can I get the IBM VM through the repos?

Thanks for the response :)

Who

---

### Post by spikee on 2007-03-25
As for flash I would check this out. I haven't tried it myself, but looks really promising. 
[http://swfdec.freedesktop.org/wiki/](http://swfdec.freedesktop.org/wiki/)

---

### Post by Who on 2007-03-25
Hmmm....

I found:
[https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/)

But none of the PPC downloads work - I just get 0 byte files!?

Does anyone still have an installer binary kicking around I can have?

---

### Post by ZoiaGuyver on 2007-03-26
swfdec is a good choice tbh although ive had some problems getting it to build in the past due to a ALSA requirement problem.

gnash is good but as it has been said here doesnt do a lot

As for Realplayer i know the older RealPlayer 8 works for a fact (i run it on my G3's and G4's) im not so sure about the new Realplayer 10 though (tbh i havnt tried it) but i spose you could get the source and build it from that.

Tbh ive found Ubuntu to be the best Distro (for ease of use and maintence) out of all the distros ive tried, these have included Fedora, Debian, Gentoo, Slackware, Yellowdog and MKlinux on PPC arch. 

Remember if you can find the sources for linux these should be platform independant and with a few commands in term should be able to build the app for your Arch. Most the time its a case of going to term typing three commands (./configure, make and make install) and thats it job done.

Hope this helps you a little and please dont give up on ubuntu at the first hurdle. Linux is a learning curve but its worth the effort for the end product. Ubuntu may have made theyre PPC releases "Unofficial" and a "Community" project but in my eyes that not all bad as it means if we get more ppl involved, we get more say on what we want to see if future versions and what we really want to work.

---

### Post by BryannMelvin on 2007-03-26
I'm using gnash...it chokes on some of the earlier macs like my g3 ibook unless it's compiled against  cairo....I did this but the source put the plugin in my home directory....I'll be doing another compile soon...as root...or get it from sourceforge and do it.

there is a gplflash library in the dapper repositories that plays more stuff thatn gnash...but plays it somewhat raggedly.1

The helix player is going to be lacking for codecs in ppc. I don;t have a solution for that.

the IBM java is installed here....think you can get it in the medibuntu repository

the 1.4.2 choked a bit in some OOo functions...the 1.5 is now available.

---

### Post by calum on 2007-03-26
> **Who said:**
> Hmmm....

I found:
[https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/)

But none of the PPC downloads work - I just get 0 byte files!?


Try [https://helixcommunity.org/frs/?group_id=154](https://helixcommunity.org/frs/?group_id=154), that's where I got mine from.  Note: works fine with audio, but just hangs with video, for me.

---

### Post by Who on 2007-03-27
> **calum said:**
> Try [https://helixcommunity.org/frs/?group_id=154](https://helixcommunity.org/frs/?group_id=154), that's where I got mine from.  Note: works fine with audio, but just hangs with video, for me.


Perfect! Thanks a lot. It works on the bbc, which is really all I need :)

---

### Post by bogoliubov on 2007-04-02
If you install the Ibm Java package (ibm-j2re1.5), you might need to do this to get java support in Firefox (at least, I had to):

mkdir ~/.mozilla/plugins
sudo ln -s /usr/lib/j2sdk1.5-ibm/jre/bin/libjavaplugin_oji.so ~/.mozilla/plugins/libjavaplugin_oji.so

And restart Firefox....

---

### Post by ZoiaGuyver on 2007-04-03
The ibm java ln -s above should also work for Opera (i just copied the plugin over as i dont have mozilla/firefox installed).

The ibm java also works in Opera on certain things but tbh im waiting got the ibm 6.0 sdk to include the plugin before i really test it the 5.0 does manage to do ok with Eclipse though.

---

### Post by 3rdalbum on 2007-04-19
Is there any special trick for getting a compiled Gnash working at peak efficiency?

I've tried the version in the Edgy repository, and that worked very slowly on my iMac G3 without direct rendering. Then I tried compiling my own with the Cairo rendering engine and Gstreamer for sound, and that was actually much slower.

If anyone has compiled it on a G3 iMac, please tell me if there are any special parameters to pass to the configure script. I've done a search through this forum, and all I've heard is that people with DRI have had success with the OpenGL renderer.

---

### Post by Salpiche on 2007-04-19
> **3rdalbum said:**
> Is there any special trick for getting a compiled Gnash working at peak efficiency?

I've tried the version in the Edgy repository, and that worked very slowly on my iMac G3 without direct rendering. Then I tried compiling my own with the Cairo rendering engine and Gstreamer for sound, and that was actually much slower.

If anyone has compiled it on a G3 iMac, please tell me if there are any special parameters to pass to the configure script. I've done a search through this forum, and all I've heard is that people with DRI have had success with the OpenGL renderer.


what kind of G3 iMac? color? I am running ubuntu on a slot loaded "blue"

---

### Post by jon1984 on 2007-04-19
> **Who said:**
> 
Do you have a different distro you'd recomend for ppc/linux

Yellow Dog Linux. Best for PPC. The latest Yellow dog linux Yellow Linux 5, is what lots people install on their playstation 3's. Its as graphicay as all the other new linuxes, similar to ubuntu.. knoppix. YDL 5 is also suggest for an install on 233mhz G3 and up.... To latest hardware. I installed YDL 4 on one imac i had that was 350MHZ. 128mb of ram. It was alright, pretty speedy. I could listen to internet streamed radio, irc, and web browse at the same time. modzilla.. could install plugins... Could check my myspace on modzillas version in YDL4. I was using YDL4 because imac didn't have a dvd drive for the YDL5 dvd iso. And i didn't have enough CDR's. If YDL5 is anything like version 4, i suggest absolutely giving it a try. It's probably the best linux for PPC, so i've heard.

[http://en.wikipedia.org/wiki/Yellow_Dog_Linux](http://en.wikipedia.org/wiki/Yellow_Dog_Linux)

---

