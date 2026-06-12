---
title: "How to switch between Partitions"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Flump5000 on 2007-10-18
I have Windows and I set up a partition for ubuntu, but now how do I switch between the two? Whenever I start my computer Windows runs. I want my computer to let me choose between the two when it starts up. can someone post a link to a guide or tell me how to do this? thanks.

---

### Post by tkharris on 2007-10-18
You're going to want to install a bootloader over your MBR, otherwise Windows will just keep booting.  I recommend installing Windows _before_ installing Linux on duel boot systems because of this ( windows will always make it the only system to boot ).

You can install grub, instructions are here: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)

You can get to the Ubuntu install by using a bootdisk: [http://ubuntuforums.org/archive/index.php/t-19428.html](http://ubuntuforums.org/archive/index.php/t-19428.html)

---

### Post by toddward on 2007-10-18
That's odd that you're not presented with a grub menu (to choose between the two OS'es).

<ASSUMPTION>
I realize that you said you set up a partition, but it sounds like you have installed on two different hard drives.  Your BIOS would then be the culprit because it would be pointing to the drive that doesn't have grub installed on the MBR.  If this is the case, tell your BIOS to boot the other drive first which should bring up your grub menu. 
</ASSUMPTION>

---

### Post by Flump5000 on 2007-10-18
nope i only have one harddrive. i partitioned it using ubuntu. (installed after installing windows)

i just know what to do next...

---

### Post by logos34 on 2007-10-18
try reinstalling grub to mbr like tkharris suggested above, but you'll need to do it from the livecd...use [this method]("http://ubuntuforums.org/showthread.php?t=224351") (most popular)

---

### Post by toddward on 2007-10-19
> **logos34 said:**
> try reinstalling grub to mbr like tkharris suggested above, but you'll need to do it from the livecd...use [this method]("http://ubuntuforums.org/showthread.php?t=224351") (most popular)
If you haven't done the above method yet, a simple check might be to head over to your /boot/grub/menu.lst.

Look at around the 17th line down where it says "timeout sec".  Make sure that your timeout is set to something higher than 0 (so you can quickly hit a key and choose something else...like your Windows XP Partition).

---

### Post by Flump5000 on 2007-10-19
it was the grub thing. i got my friend to guide me through it. it works now. thanks though.

---

### Post by toddward on 2007-10-19
> **Flump5000 said:**
> it was the grub thing. i got my friend to guide me through it. it works now. thanks though.
May I ask what that 'grub thing' was?

---

### Post by Flump5000 on 2007-10-19
> **toddward said:**
> May I ask what that 'grub thing' was?

this:  > **logos34 said:**
> try reinstalling grub to mbr like tkharris suggested above, but you'll need to do it from the livecd...use [this method]("http://ubuntuforums.org/showthread.php?t=224351") (most popular)

---

### Post by toddward on 2007-10-22
Oh, haha, oops.

---

