---
title: "wow, lots of download errors"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by 09amw on 2006-08-11
I have determined that my computer (an old Compaq Presario 7970) does not have enough system resources to properly install ubuntu from the livecd that shipit sent me.  So, I have tried to download the alternate iso to install it.

This is harder than it appears, apparently.

I have downloaded the file four times, two from US mirrors, and two via bittorrent (I use the uTorrent client), and all four have failed the same md5 checksum verification.

The failed "things" (I don't know what they're called)are as follows:

.install\netboot\prelinux.cfg\default
.install\netboot\prelinux\0
.pool\main\x\xserver-xorg-input-mouse_1.0.3.l+cvs.20060109-0ubuntul.l_i386.deb
.pool\main\x\xserver-xorg-input-synaptics_0.14.3+seriouslythistime-0ubuntu3_i386.deb

Will ubuntu still install with these failed parts?  Why do I keep getting these fails?  Is there a "good" copy of the alternate download that I can get?  Is the problem with my download or the burn?

AH!  Please help me!

Haha, thanks a lot, hopefully I'll be able to get this straightened out with a bit of help.

Andy

---

### Post by GuitarHero on 2006-08-11
Ah no those files are important.  What speed are you burning the cds at?  Anything higher than 8x may have errors on it.  Burn it on a very low speed and try it again.

---

### Post by 09amw on 2006-08-11
Well, I was burning at 24x, which easily could have been the problem.

I reburned at 2x (better safe than sorry, right?), and got the same four failed checksums.

I have been burning with CDBurnerXP Pro 3, if that helps any.

Should I try to re-download the iso, or could there be something else that I'm doing wrong?

Also, is there a way to verify the checksums before burning the disc?

Furthermore, I have been using a program called md5summer to check the checksums, but I should note that none of my burns have installed thus far.

Thanks again for your help

Andy

---

### Post by 09amw on 2006-08-11
I just thought of something else:

I have been able to boot ubuntu from the livecd that shipit sent me, it just keeps crashing during the install.

Is there a command that I can use in the bash (I believe this is what comes up when I hit Ctrl + Alt + F1) that would install ubuntu without using the gui that taxes my system resources too far?

Thanks

Andy

---

### Post by GuitarHero on 2006-08-11
Not that I know of but I could be wrong.  If you can, try another burning program.  Did you do the check disk once you boot up the cd using the check disk utility that comes with the disk?

---

### Post by 09amw on 2006-08-12
This time, the internal check disk utility sait that the file

./pool/main/v/vim/vim-runtime_6.4-006+2ubuntu6_all.deb

failed the MD5 checksum check.  This was the only error reported.  I asuume that, since this is one of those .deb files, that this is a fatal error, and won't let me install.

What is puzzling is that this is a different file than the problems listed by the other utility that I used.

Gah I'm so confused.

Thanks for the help.

Andy

---

### Post by 09amw on 2006-08-12
I had another idea:

I have a 1 GB flash drive that I could burn the image to.  I think this would erase the issue with burn errors, right?

So I now have two questions.  How do I burn an iso to a flash drive, and how do I make the drive bootable?

I assume that the drive would be under the "removable devices" category in the BIOS, but again, I'm not really sure.

If someone could help me out with this problem, that would be great.

Thanks!

Andy

---

### Post by bobpur on 2006-08-12
I am using a Compaq 5WV252 dual booting Dapper Kubuntu and Ubuntu and my old Compaq runs better now than it ever did on Win ME.I googled for the specs on yours but couldn't come up with anything. You said you were running Win 98 SE so I'm assuming yours is older than mine. 
Maybe you could have someone else download and burn the ISO for you and see what happens after that.  Good Luck!

---

### Post by bobpur on 2006-08-12
I forgot to mention that while downloading the latest version of Dapper(v.6.06.1) the other night, I had loads of errors too. It seems that after a wreck that screwed up the phone system, my DSL was screwed up wreaking havoc with my connection speed.
After reading over this I have to clarify that I did not wreck while fooling with my computer:) I was home. the wreck was in my neighborhood.

---

### Post by Polygon on 2006-08-12
are you sure that the iso you are using to burn the cd is not corrupted?

check this site for a guide to make sure that the iso you downloaded is completly correct

[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

if you cant download it correctly through http, try using a bittorrent program (bitcomet works well) and download the iso through a torrent.

---

### Post by jimmygoon on 2006-08-21
Sounds like the ISO itself is bad. If thats the case then you need to DELETE and redownload the file.

---

### Post by Doppelbock on 2006-11-26
> **Polygon said:**
> are you sure that the iso you are using to burn the cd is not corrupted?

check this site for a guide to make sure that the iso you downloaded is completly correct

[http://psychocats.net/ubuntu/iso.html](http://psychocats.net/ubuntu/iso.html)

if you cant download it correctly through http, try using a bittorrent program (bitcomet works well) and download the iso through a torrent.


I figured I'd reply to this topic rather than starting a new one. I've downloaded the alternate install ISO three times from three different mirrors and every one of them fails the MD5 check for the following four files:

.\install\netboot\pxelinux.0\default - Does not exist
.\install\netboot\pxelinux.0 - Checksum failed
.\pool\main\x\xserver-xorg-input-mouse\xserver-xorg-input-mouse_1.0.3.1+cvs.20060109-Oubuntu1.1_i386.deb - Does not exist
.\pool\main\x\xserver-xorg-input-synaptics\xserver-xorg-input-synaptics_0.14.3+seriouslythistime-Oubuntu3_i386.deb  - Does not exist
 
I then downloaded the DVD image from a UK mirror and the same four files came up with the same errors. That last file name is a little fishy, no? This is after I just mounted the ISO to my desktop via DaemonTools so no burn errors are possible in my case.

I wouldn't think that the PXE files would matter to me since I'm not doing a net boot but the mouse and synaptics files are a little troubling.

---

### Post by kinematic on 2006-11-26
have you checked your ram?

---

### Post by Doppelbock on 2006-11-26
No, hadn't thought of that since a couple of the files from the MD5  list were flat-out missing. I ended up installing from the CD without issue though (server). Since this box is my backup workstation also I need the GUI so I'm installing that now, will have to see if the mouse fails or not.

---

### Post by Doppelbock on 2006-11-26
Install from the live DVD went fine and mouse is working so apparently those weren't fatal errors.

---

