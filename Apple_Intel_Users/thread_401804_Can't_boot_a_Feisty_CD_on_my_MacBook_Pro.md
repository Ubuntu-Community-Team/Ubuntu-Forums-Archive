---
title: "Can't boot a Feisty CD on my MacBook Pro"
date: 2007-04-05
forum: Apple Intel Users
---

### Post by forkbeard on 2007-04-05
Alright, this is driving me nuts. I've downloaded, burned Kubuntu and Ubuntu (both feisty) isos but neither boot properly. 

The first two that I tried were Kubuntu and Ubuntu isos burned onto separate DVDs.. Both made it past the initial bootscreen and get into the "looping bar" boot screen but then the screen goes black afterwards.

The third one I tried was an Ubuntu iso on a CD-RW.. this time it locks up at 91% of the way through booting the kernel.

Makes no sense I tells ya. Previous versions and other distros burned to the same media of the brand/age/condition on the very same MacBook Pro work fine. Any ideas?

---

### Post by cantormath on 2007-04-05
> **forkbeard said:**
> Alright, this is driving me nuts. I've downloaded, burned Kubuntu and Ubuntu (both feisty) isos but neither boot properly. 

The first two that I tried were Kubuntu and Ubuntu isos burned onto separate DVDs.. Both made it past the initial bootscreen and get into the "looping bar" boot screen but then the screen goes black afterwards.

The third one I tried was an Ubuntu iso on a CD-RW.. this time it locks up at 91% of the way through booting the kernel.

Makes no sense I tells ya. Previous versions and other distros burned to the same media of the brand/age/condition on the very same MacBook Pro work fine. Any ideas?

a stupid question, do you have a ppc(older mac) cpu and if so did you download the ppc version of ubuntu.

if you have that straight, there is usually a key combination you have to hold down to boot to a disk on a mac, the one I know of is
```
Press Option-Command-Shift-Delete
during startup Bypass primary startup volume and seek a different 
startup volume (such as a CD or external disk) 
```

here is a page of other features.
[http://www.fif3.com/howto/archives/001983.html](http://www.fif3.com/howto/archives/001983.html)

goodluck.

---

### Post by forkbeard on 2007-04-05
If I had downloaded the PPC version or not hit the right key on boot, I wouldn't have gotten to the (k)ubuntu bootloader. And the key to hold to boot from a CD on a MacBook Pro is 'd' or 'Option' to manually select a boot disk.

Did you even read my post?

---

### Post by cyberdork33 on 2007-04-05
> **forkbeard said:**
> If I had downloaded the PPC version or not hit the right key on boot, I wouldn't have gotten to the (k)ubuntu bootloader. And the key to hold to boot from a CD on a MacBook Pro is 'd' or 'Option' to manually select a boot disk.

Did you even read my post?

Well reacting like that is not bound to get you more help...

---

### Post by forkbeard on 2007-04-05
I wasn't trying to be a dick, just trying to point out the fact that he didn't even bother to read anything beyond the title of my post before responding. If cantormath had actually read my entire post, s/he would see that I did, in fact, make it past the initial Apple boot screen and s/he wouldn't have posted such a blatantly ignorant response.

Sorry if I'm tired of getting the typical corporate-tech-support-style "Did you remember to plug it in?" flowchart-guided responses that the Ubuntu forums are becoming oh-so famous for.

[Edit] Looking at cantormath's post again, I noticed that s/he didn't even bother to read the title of my post. I posted in the **Intel** forums asking about by **MacBook Pro** and s/he responded by asking if I'm trying to boot a PPC mac. Seriously, is this the blanket response s/he gives to all posters asking about boot problems?

---

### Post by cyberdork33 on 2007-04-05
I understand the frustration, as I noticed it too, but realize that not everyone that comes to these forums with a great deal of knowledge about their system and the Linux/Ubuntu OS especially on Apple Hardware. Even those with a great deal of knowledge on the subjects at hand tend to overlook things every once in awhile.

Your request is very generic / vague. I don't think that anyone else has had an issue booting the CD. (I would maybe search and see if that is the case). If still no luck can you determine if you can get to a virtual console? (CTRL+ALT+F1)

---

### Post by CannedCorn on 2007-04-05
No way dudes, this is totally legit. Same thing happens on my Macbook Pro, X does not start on the feisty beta boot cd.

---

### Post by forkbeard on 2007-04-05
> **cyberdork33 said:**
> I understand the frustration, as I noticed it too, but realize that not everyone that comes to these forums with a great deal of knowledge about their system and the Linux/Ubuntu OS especially on Apple Hardware. Even those with a great deal of knowledge on the subjects at hand tend to overlook things every once in awhile.

That's no excuse for responding without reading the post.


Anyways, no I can't get to a virtual console.. It never gets far enough in the boot process to do it. With the iso burned to a CDRW it hangs while loading the kernel at exactly 91% every time (this is right after selecting Start installing.... from the bootloader).

---

### Post by phidia on 2007-04-05
I don't know if it will help but there's a link here: [http://ubuntuforums.org/showthread.php?p=2198954](http://ubuntuforums.org/showthread.php?p=2198954)

There appear to be some boot problems with intel macs-although ppc wasn't always a breeze either.

---

### Post by cyberdork33 on 2007-04-05
The parallels problem is a different issue.

You might be getting the kernel panic. Try adding the suggested line to startup the system:
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

---

### Post by forkbeard on 2007-04-05
No dice on the kernel panic solution. I just noticed a tiny little note stating that if you're using Feisty Herd 3 to use the Alternate CD. I'm going to give that a shot.

---

### Post by ubuntu-geek on 2007-04-05
> **CannedCorn said:**
> No way dudes, this is totally legit. Same thing happens on my Macbook Pro, X does not start on the feisty beta boot cd.
Same thing for me.. grumble..

---

### Post by cyberdork33 on 2007-04-06
Well I don't know about the X issue, I know on the 20" iMac, X starts but looks like it is all skewed. Installing fglrx fixes that though. This guys biggest issue is getting the kernel to even execute.

---

### Post by forkbeard on 2007-04-08
I posted this question on the LiveJournal Ubuntu community.. Someone recommended getting a Herd 4 disc to install then doing a dist-upgrade to the latest version. Apart from a couple partition-related hiccups, the Herd 4 disc worked fine.

---

### Post by ronocdh on 2007-04-08
I would just like to add that I too have been unable to run Feisty on my C2D MBP 15". I've tried both Ubuntu and Kubuntu, both i386 and 64-bit. That's four CDs! I verified the burns after disc creation, and also did a checksum from the boot menu when I ran the live CDs...

I have not tried the alternate CDs nor any DVDs. I'm not even sure whether those exist for betas. I'm waiting for final Feisty to give it another go.

---

### Post by xxzeenoxx on 2007-04-12
im having the same issues with the Kubuntu Feisty Beta CD.  i thought it might be my hardware, but the Ubuntu Edgy CD runs fine.

---

### Post by Chrisj303 on 2007-04-13
.

---

### Post by Chrisj303 on 2007-04-13
Has a bug report been filed?  - if not it might be an idea to get one in now before the final release.
The only real difference between the macbook and MBP is the graphics card, if i was a betting man thats were my money would be on where the bug lies.

chrisj303

---

