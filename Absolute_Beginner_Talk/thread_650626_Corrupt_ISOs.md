---
title: "Corrupt ISOs???"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Tipo on 2007-12-26
Hey everyone,

I've been having some serious problems getting Ubuntu 7.10 onto a few of my computers.  I've downloaded the ISO and burned it to a CD, I pop it in, install seems to be going well, and then about 60% of the way through the install, it fails and tells me there is an issue copying files from the disc.

I've burned the ISO from three different computers, two macs, and another (HP) Ubuntu box. I've burned at least 100 ISOs in my experience, so I am positive that I am doing this process correctly.

I've also downloaded the ISO from three different mirrors... not that that makes a huge difference, but it helps to try.

I downloaded the x86 version, and I am attempting to install it on a Pentium 4 HP desktop and a Centrino mobile laptop (which has Ubuntu 7.04 on it already).

Any ideas as to what the issue could be?

Thanks in advance!

---

### Post by dannyboy79 on 2007-12-26
as long as you check the md5sum for the iso and it matches, than it's not the iso's. what about bad media? the cd's you're using, try another brand maybe. Also, are you trying to put the files on a partition that isn't large enough, just throwing out my thoughts no matter how trivial they seem I don't know if you haven't thought about these things yet.

---

### Post by Tipo on 2007-12-26
Thanks for the reply,

I have 'Verified' all the discs I've burned through the verification step that Ubuntu's installer offers, and all of them check out as good.  How would I check the md5sum?

I have tried using a different brand of CDs... 

On both machines I am doing a clean install, and in doing so reformatting the partitions completely. 

Any more suggestions? Keep 'em coming! :P :)

---

### Post by psusi on 2007-12-26
When booting from the cd, choose the option to check the disk.

---

### Post by dannyboy79 on 2007-12-26
i believe he stated that he's doing that already.

Well, the md5sum's of the iso's are normally located at the same webpage you downloaded the iso from. then you would use a tool called, md5sum. See here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

here's the md5sum of the newest Hardy iso x86 version: 8cc8b23eab7a1c3969ae37dcc7f86016

you would just make sure that the md5sum that you get when you follow the directions at the link I provided matches the number I got from here: [http://cdimage.ubuntu.com/releases/hardy/alpha-2/](http://cdimage.ubuntu.com/releases/hardy/alpha-2/)
then under the MD5SUM thingy at the top.

---

### Post by L Campbell on 2007-12-26
> **Tipo said:**
> Hey everyone,

I've been having some serious problems getting Ubuntu 7.10 onto a few of my computers.  I've downloaded the ISO and burned it to a CD, I pop it in, install seems to be going well, and then about 60% of the way through the install, it fails and tells me there is an issue copying files from the disc.

I've burned the ISO from three different computers, two macs, and another (HP) Ubuntu box. I've burned at least 100 ISOs in my experience, so I am positive that I am doing this process correctly.

I've also downloaded the ISO from three different mirrors... not that that makes a huge difference, but it helps to try.

I downloaded the x86 version, and I am attempting to install it on a Pentium 4 HP desktop and a Centrino mobile laptop (which has Ubuntu 7.04 on it already).

Any ideas as to what the issue could be?

Thanks in advance!

I have a PC with which I had similar sounding problems, some while ago and someone suggested the 'alternate' CD.  It worked like a charm for me.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by LowSky on 2007-12-26
maybe you have bad memory, or a bad sector on a hard drive?

use the CDs check memory function as well

---

### Post by Tipo on 2007-12-26
md5sum checks out...

Looks like the install succeeded on my desktop computer, but it still seems to be failing on my laptop. It reports this error:

```
[    196.912000]Buffer I/O error on device fdo, logical block 0
```

---

### Post by Tipo on 2007-12-26
> **L Campbell said:**
> I have a PC with which I had similar sounding problems, some while ago and someone suggested the 'alternate' CD.  It worked like a charm for me.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


Thanks for the tip, I'll give it a shot.

> **LowSky said:**
> maybe you have bad memory, or a bad sector on a hard drive?

use the CDs check memory function as well

What might be the probability of this happening on multiple machines? Heh, with my luck, I'd better check as well :)

---

### Post by e_james on 2007-12-26
In my limited experience (6.06 and 7.04 alternate CDs), you get different behaviour depending on whether or not you have a live internet connection during the install. I have never used a live CD for installation (repairs and testing only), but I believe it makes greater demands on the hardware just to run. From other comments on these forums, I think 7.10 goes further down this path.

---

### Post by dannyboy79 on 2007-12-27
> **Tipo said:**
> md5sum checks out...

Looks like the install succeeded on my desktop computer, but it still seems to be failing on my laptop. It reports this error:

```
[    196.912000]Buffer I/O error on device fdo, logical block 0
```

fd0 is the floppy drive. Not sure why it's trying to access it but is there a disk in it or maybe try putting a disc in it so it doesn't give you the disc I/O error. Also, I have had much success using the Alt CD on laptops always. It's textual based and normally always solves any graphics issues the normal installer has. You could always try that.

---

### Post by Tipo on 2007-12-27
> **dannyboy79 said:**
> fd0 is the floppy drive. Not sure why it's trying to access it but is there a disk in it or maybe try putting a disc in it so it doesn't give you the disc I/O error. Also, I have had much success using the Alt CD on laptops always. It's textual based and normally always solves any graphics issues the normal installer has. You could always try that.

I've tried the alternate install CD with no success.... I get that error on boot, the screen shuts off when I get to the login screen and I can't get any sort of network connection. My laptop has no floppy drive, so I do not know why it would try to access that...

I guess I'll try to put edgy or dapper back on the machine (edgy was on the machine before).

---

### Post by dannyboy79 on 2007-12-27
man I wish I could help you more. Not sure what to suggest. I hope you figure it out as Gutsy, Hardy or Feisy are all better than Dapper in my opinion (i skipped edgy). I normally only upgrade every other release. Once a year. I do have a new machine that was donated to me running Gutsy Mythbuntu which is really nice but I am just sticking with Feisty on my main server/desktop.

---

### Post by gn2 on 2007-12-27
Did you ever open the .iso file to browse the contents in Windows prior to burning the Live CD?
This can cause file corruption and result in a non-working CD.
If you have done this, the only option is to re-download the .iso

---

### Post by Tipo on 2007-12-27
Well, I haven't opened the iso to browse, and I've downloaded it multiple times.

I just spent 2 hours downloading dapper, only to find that the md5sum didn't check out.

I'll be giving up with Ubuntu on this laptop - rather strange that it used to install flawlessly. I've put Slackware on the laptop and it runs smoothly, thanks for the help!

---

