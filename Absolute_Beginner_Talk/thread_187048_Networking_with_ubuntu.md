---
title: "Networking with ubuntu"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by MoiraA on 2006-06-02
Hi

This is my first post here. :)  I've got a copy of ubuntu which came on a dvd with a PC magazine and I would like to try it on my laptop (which is quite old and not high spec but it currently dual boots between XP and Suse, so I think it should run ubuntu without problems).

What concerns me is that I have it nicely set up with samba so that I can brownse the Windows files from Suse and vice versa.  At the time it took quite a while for me to get my head around samba and I'm wondering how hard this is going to be if I install ubuntu.  Would it be useful to keep my samba config file before formatting the linux partition of the laptop?

---

### Post by adam.tropics on 2006-06-02
It couldn't hurt to keep a copy if only for referencem but you shouldnt have too much trouble. [Just in case!]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=samba&titlesearch=Titles")

---

### Post by Iowan on 2006-06-02
[QUOTE=MoiraA]  Would it be useful to keep my samba config file before formatting the linux partition of the laptop?[/QUOTE] I would... If you're REALLY lucky (I NEVER am...), you might install Samba on Ubuntu, rename the smb.conf file (just-in-case), copy your old smb.conf file in place of the now-renamed one, reboot (or just restart Samba), and have it work flawlessly.

---

### Post by MoiraA on 2006-06-02
Many thanks for the suggestions .... this is now going to sound a really dumb question :(  I went into Suse and looked around for /etc/smb without any success.  I tried over the network from this XP computer, I looked in \\Suselaptop\root and \\Suselaptop\users\<username>, and I'm sure I have hidden files showing but the only smb.conf file I appear to have anywhere is 0 kb.  Yet samba must be there or I wouldn't be browsing the linux network from windows (?) and anyway I remember spending a whole sodding afternoon installing and configuring it ages ago.

I simply can't find it on the laptop and clearly haven't got a shortcut to it here - am I missing something obvious?  Other than perhaps I should forget about installing ubuntu if I can't do a simple thing like this!

---

### Post by Kilz on 2006-06-02
[QUOTE=MoiraA]Many thanks for the suggestions .... this is now going to sound a really dumb question :(  I went into Suse and looked around for /etc/smb without any success.  I tried over the network from this XP computer, I looked in \\Suselaptop\root and \\Suselaptop\users\<username>, and I'm sure I have hidden files showing but the only smb.conf file I appear to have anywhere is 0 kb.  Yet samba must be there or I wouldn't be browsing the linux network from windows (?) and anyway I remember spending a whole sodding afternoon installing and configuring it ages ago.

I simply can't find it on the laptop and clearly haven't got a shortcut to it here - am I missing something obvious?  Other than perhaps I should forget about installing ubuntu if I can't do a simple thing like this![/QUOTE]

There should be a samba folder in etc that holds the .conf file. At least I seem to remember there being one there when I ran suse.

---

### Post by adam.tropics on 2006-06-02
Personaly, and this is just me (! ) I'd just go ahead and install Ubuntu. But like I said tht's just me.

Try looking /usr/share/samba, or yes /etc/samba

---

### Post by MoiraA on 2006-06-03
Many thanks, in fact I discovered the Find Files option in Suse and it located the Samba file, which I've kept a copy of - just in case.  I'm now going to start the install.

Wish me luck!

**Edit 4 am Sunday 4th June**  Well after several starts, it's proceeding at snail's pace.  It's 2% into scanning /cdrom/pool/main something.  I'll probably have to leave it overnight to see if it either resolves or just doesn't like the laptop.  The version is 5.10 which came free with a PC magazine - is it normally so slow?  This is about my third try to get it to progress at all.  If it isn't successful should I try downloading the latest version?

---

### Post by MoiraA on 2006-06-04
This doesn't seem to be very successful.  I've now had the CD in the drive for 16 hours and it's still not progressed beyond 22% of scanning "/cdrom/pool/main/l ...".  In fact, overnight it went from 2% to 22% but now it's been stuck for hours.

Does anyone know why this is happening?  I'm just going to have to abort the whole idea shortly, in fact I really should have done it by now but I kept hoping it might progress.

---

