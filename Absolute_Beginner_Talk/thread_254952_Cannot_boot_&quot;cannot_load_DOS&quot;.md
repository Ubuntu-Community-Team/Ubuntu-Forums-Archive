---
title: "Cannot boot: &quot;cannot load DOS&quot;"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by skelter15 on 2006-09-10
My pc is running on XP pro right now, but I want a dual boot and install Linux on a different partition.
But I have a problem that I can't solve myself.

I burned an cd-rw with the iso-image and set the disc to bootable.
When I am booting my computer, there is a notification like:
[I]'boot device CD-rom  OK
 cannot load DOS - any key to retry'[/I]
When I strike a key it boots again, but with no result.

I can acces XP, so thats no problem. I only want Ubuntu to get running.

Thanks in advance

---

### Post by RobsterUK on 2006-09-10
When you said you set the disk to bootable it sounds like you might have inadvertantly added some windows/dos booting stuff to the disc, which is causing the problem.

If you just burn the ISO it should be bootable anyway.

What did you use to burn it?

---

### Post by skelter15 on 2006-09-10
I used CDburnerXPpro 3 on recommedation of the Dutch Ubuntu-site.
When you get to the burning-settings there is an option:
*'set the disc to bootable'.*

Is that causing problems you think?
I am going to test it.

---

### Post by NetworkGuy on 2006-09-10
Don't set the bootable option.  The ISO by default is bootable.

---

### Post by skelter15 on 2006-09-11
I tried to boot several times with the normal burned iso-file. So I did not took the option bootable/non-bootable.

But when I boot, the computer recognizes the cd, but continues to start xp.

I set my bios to start-up with the disc, but I still cannot start Ubuntu!

---

### Post by 3rdalbum on 2006-09-11
You say that the computer recognises the CD. What does it do that tells you that it recognises the CD?

Try burning at a slower speed, like 8x. Make sure that the disc has a whole bunch of files and folders on it, not just one.

---

### Post by skelter15 on 2006-09-11
It says:* 'boot device CD-rom OK'*

The program that I use gives me the option to burn the ISO file. That means to me that I only have to drag the downloaded ISO file to the disc and burn it.

Or do I have to unpack the ISO and then burn it?

---

### Post by monktbd on 2006-09-11
you need to burn the iso as a disc image or iso image and not as a normal data cd (and also not making this normal data cd bootable).

look in your burning program for an option like i mentioned above:

burn iso image
burn cd image

sometimes this choice is not in the wizard that shows up at the beginning and you need to search through the menus for it.

---

### Post by skelter15 on 2006-09-11
It is solved, thanks.

When I used Nero I found the option to burn the ISO image like it should. So now it is working.
:-D

---

