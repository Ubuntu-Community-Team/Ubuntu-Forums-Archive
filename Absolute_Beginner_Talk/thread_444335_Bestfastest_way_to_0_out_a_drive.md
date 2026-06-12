---
title: "Best/fastest way to 0 out a drive?"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-05-15
Basically, I've re-written the partition table and such so many times, any partition change in GParted or Vista seems to have issues, so i want to 0 out my HD and partition it ONCE.

What is the best way to go about this?

(And to anyone who's seen my posts in the past, I've found a way to install GRUB to (hd0) AND keep Dell's MediaDirect!)

---

### Post by EndPerform on 2007-05-15
When I want to zero out a drive, I use Darik's Boot and Nuke:

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

Burn a CD, drop it in the drive, select some options and off you go.  I use this if I get rid of a hard drive :)

---

### Post by HereInOz on 2007-05-15
I take it you mean to completely erase your hard drive and start again?  Is that correct?  If so, try Darik's Boot & Nuke.  Just run the quick erase in that utility and you will have a clean slate.

If I mis-understand you, then I apologise.

---

### Post by gohanssjn on 2007-05-15
That sounds perfect.

About how long does this usually take to run, for say, 100gb drive?  It's a 5400rpm I believe, if that matters.

---

### Post by insane_alien on 2007-05-15
boot a live CD go to a terminal and type 'cat /dev/zero > /dev/hda' if hda is your drive. it might show up as sda. that'll set evverything to 0 literally.

---

### Post by gohanssjn on 2007-05-15
Really?  Is that faster/slower than Nuke?

---

### Post by starcraft.man on 2007-05-15
> **gohanssjn said:**
> Really?  Is that faster/slower than Nuke?

I'm going to back up endperform, I've both used and seen DBAN in action and I like it, its the easiest way I know of zeroing a drive. I doubt that there is much noticeable difference between it and the live cd, I just think DBAN is the tried and true program I've used for a while. Its had lots of experience nuking drives :p.

---

### Post by gohanssjn on 2007-05-15
Ok, thanks.  I'll try DBAN tonight on quick then.  Just WAY to much writing of partitions in the last few nights.  Hopefully this will stop GParted saying the table is wrong every time :)

---

### Post by wtfbrb on 2007-08-12
I have 2 hard drives in a machine and both have ubuntu on them, I am trying to delete my old installation, but I don't have permission.

Any software or terminal commands I can use?

Thanks in advance,
wtfbrb

---

### Post by HermanAB on 2007-08-12
The utility to securely erase a drive is built into the drive firmware.   All you need to do, is activate it:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

---

### Post by wtfbrb on 2007-08-13
Bah there has to be something better than a windows prog.

---

### Post by wallydallas on 2007-09-22
Boot and nuke is an Awesome Tip.  
Thanks for the Tip and thanks to all the developers, Darik, I guess is her/his name..and 
Erik Andersen's, and H. Peter ,Gilles Vollant's and source forge
And everyone on the project.

I used my mac to download the ISO file and then burn with toast.
I've got to find a tool to burn an ISO image on Ubuntu.

I used boot and nuke in the automatic mode, 3 passes.
Thanks again for the tip written for us novices.

peace out, happy endings.

---

### Post by dr johnson on 2007-11-06
I tried the "cat /dev/zero > /dev/hda" suggestion (actually sda, not hda on my advent 7111 laptop) while I had the computer booted from an Ubuntu 7.10 cd. I got a
**bash: /dev/sda: Permission denied**
reply in the command line. So I entered the command with sudo; same response though. Tried it from a 6.06 cd too, same there.

Can anybody tell me what to do, cause this method--if I could just get it to work--would be a neat way of avoiding the dreaded dban disc...

---

### Post by DakotaBlue on 2007-11-06
I used the free download of [KillDisk]("http://www.killdisk.com/features.htm"). It is one pass, but I wasn't concerend with security; just with having a blank drive.

---

### Post by DakotaBlue on 2007-11-06
> **wallydallas said:**
> Boot and nuke is an Awesome Tip.  
Thanks for the Tip and thanks to all the developers, Darik, I guess is her/his name..and 
Erik Andersen's, and H. Peter ,Gilles Vollant's and source forge
And everyone on the project.

I used my mac to download the ISO file and then burn with toast.
I've got to find a tool to burn an ISO image on Ubuntu.

I used boot and nuke in the automatic mode, 3 passes.
Thanks again for the tip written for us novices.

peace out, happy endings.Can this program be used to clean a specified drive, but leave the others on the computer alone?  Their web site says it automatically nukes every drive it can detect.

---

### Post by dr johnson on 2007-11-06
: "cat /dev/zero > /dev/hda"

Well duh, from a live disc, I think I would actually need "cat /dev/zero > /media/disk/dev/hda" would I not? Anyway, tried that too it I still get the *permission denied* response.

Oh, and thanks for the very quick replies guys!

---

### Post by dr johnson on 2007-11-06
Thanks for the killdisk suggestion DakotaBlue. Its sure is fast; 75gb disc zeroing much faster than it was with dban on my 'puter. Still, dban is licenced under the gpl so that at least makes it cool.

Would be nice to be able to zero out like you can using "Disk Utility" on Mac OSX, or preferably from the command line.

---

