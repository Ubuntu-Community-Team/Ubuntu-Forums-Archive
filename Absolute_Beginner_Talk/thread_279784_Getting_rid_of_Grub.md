---
title: "Getting rid of Grub"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by gmabry1 on 2006-10-18
Hi, I have recently decided to quit dual booting with ubuntu and windows XP.    How can i get rid of Grub in linux.  Thanks

---

### Post by doobit on 2006-10-18
You need some kind of bootloader, and GRUB is not a bad one to have. How you get rid of Windows will depend on the current structure of your partitions. How do you have your hard drive set up right now?

---

### Post by tonyr1988 on 2006-10-18
Are you keeping WinXP or Ubuntu? 

If you're keeping WinXP, you'll want to restore the MBR. This should do it:

[http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html](http://www.tippscout.de/repair-and-restore-master-boot-record-mbr_tipp_3114.html)

If you're keeping Ubuntu, you shouldn't need to get rid of GRUB. You'll only have to edit the menu.lst to make it not show up. (If that's what you want to do, I can give specific details and what to do)

As far as I know, you have to have *something* in your MBR (Master Boot Record - the first thing your computer boots into) so that it knows what to do. So you can't "get rid of grub", but you can make it:

1) Not show up, or
2) Replace it with another bootloader.

Hope that helps, and I hope it's WinXP you're getting rid of! :P

---

### Post by gmabry1 on 2006-10-18
Yea I am getting rid of XP actually i already have, i just don't want Grub showing up when I load the computer
Thanks

---

### Post by bulldog on 2006-10-18
You can fix your MBR with the windows cd by going to recovery console and type fixmbr.

I presume you don't want to use Ubuntu anymore.

Not to see Grub by booting up is easy to do.

Alter this section in your menu.lst.

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

And uncomment hiddenmenu

---

### Post by tonyr1988 on 2006-10-18
> sudo gedit /boot/grub/menu.lst

I *think* you can comment out (put a # before each line) all of the OSes until you have just one left and it'll automatically load that one. But I'm not sure.

An easy work-around is, at the top of the file, edit this line:

> timeout		10

to

> timeout		1

This is how long (in seconds) it waits before booting the default. You can try using 0 instead of 1. I haven't tried, but using 0 will either:

1) automatically boot into your default, or
2) never timeout

And YAY for keeping Ubuntu! :)

PS You may not want to comment out all of the other ones - sometimes Ubuntu recovery mode or memtest86 can be useful. Having it wait one second is slightly annoying, but it gives you a chance to use those other boot methods if you need to.

---

### Post by Rui Pais on 2006-10-18
> **gmabry1 said:**
> Yea I am getting rid of XP actually i already have, i just don't want Grub showing up when I load the computer
Thanks

Would be better to leave the grub in case you need to start in recovery mode or try different versions or distros.

just change in /boot/grub/menu.lst:
```

timeout=0
```

and you won't see grub anymore.

---

### Post by bulldog on 2006-10-18
> **Rui Pais said:**
> Would be better to leave the grub in case you need to start in recovery mode or try different versions or distros.

just change in /boot/grub/menu.lst:
```

timeout=0
```

and you won't see grub anymore.

It's not wise to do so,you can't acces your GRUB without changing that.

Just uncomment hiddenmenu as adviced and you'll be okay.

If you want to see GRUB just hit ESC and it's there.

See my previous post.

---

### Post by Rui Pais on 2006-10-18
> **bulldog said:**
> It's not wise to do so,you can't acces your GRUB without changing that.

Just uncomment hiddenmenu as adviced and you'll be okay.

If you want to see GRUB just hit ESC and it's there.

See my previous post.

i know it was not wise, i said that, too. 
Just reply to the question of **completely** remove grub post by gmabry1.

Not seeing grub at all it's not dangerous. You can always access menu.lst from the running OS or from a liveCD. Is deleting grub (or any boot manager) the really dangerous/not-wise action.

Anyway the hidenmenu will only... hide the menu. If your timeout is, say 10 sec, you will need to wait and look for grub for that time... not exactly what is pretended by gmabry1.

If timeout=0 sounds too radical, one can always choose timeout=1 and the hidenmenu uncommented, for the best approach to the no-grub boot...

---

### Post by bulldog on 2006-10-18
> **Rui Pais said:**
> i know it was not wise, i said that, too. 
Just reply to the question of **completely** remove grub post by gmabry1.

Not seeing grub at all it's not dangerous. You can always access menu.lst from the running OS or from a liveCD. Is deleting grub (or any boot manager) the really dangerous/not-wise action.

Anyway the hidenmenu will only... hide the menu. If your timeout is, say 10 sec, you will need to wait and look for grub for that time... not exactly what is pretended by gmabry1.

If timeout=0 sounds too radical, one can always choose timeout=1 and the hidenmenu uncommented, for the best approach to the no-grub boot...

Well if he want to use Ubuntu he can't delete GRUB :D 

I know you can edit the menu.lst,but why set it to 0 if there is an option to hide the menu.

The time out was not the question,only not seeing GRUB :D 

It goes a little too far to explain all the options in your GRUB,he get's the answer he asked for.

---

### Post by Rui Pais on 2006-10-18
> **bulldog said:**
> Well if he want to use Ubuntu he can't delete GRUB :D 

I know you can edit the menu.lst,but why set it to 0 if there is an option to hide the menu.

The time out was not the question,only not seeing GRUB :D 

It goes a little too far to explain all the options in your GRUB,he get's the answer he asked for.

I completely agree with you but (i probably get it wrong :() what i understood from the 5th post is that gmabry1 don't have a question with grub menu but simply want to start computer and go directly (no pauses) to OS. And  that would be the cause for he/she ask for something so radical as deleting grub... 

If i understood it wrong, my apologies :(

---

### Post by gmabry1 on 2006-10-18
Really all i want is for the Grub message to not show up when i start the computer.  If I set the time to zero then i would need to change it later if i ever decide to go back to dual booting correct?  But for right now i would like to know how to hide the grub message when i restart the computer.  Thanks

---

### Post by bulldog on 2006-10-18
> **Rui Pais said:**
> I completely agree with you but (i probably get it wrong :() what i understood from the 5th post is that gmabry1 don't have a question with grub menu but simply want to start computer and go directly (no pauses) to OS. And  that would be the cause for he/she ask for something so radical as deleting grub... 

If i understood it wrong, my apologies :(

No apologies needed,we're all here to help.

He wanted to delete grub so I presumed he wanted to go back to windows :D 

Later I saw he didn't want to see GRUB but just starting the OS.

Well then you hide GRUB menu.

You can't delete GRUB because it's necessary to boot Ubuntu.

But no harm done,we all try to contribute with different kind of solutions.

So we all learn from eachother cause we see solutions we didn't thought about.

---

### Post by doobit on 2006-10-18
I think the other question that's implied here, is how to get rid of Windows. You need to format the Windows partition in a Linux format, like ext.3 without wiping out your MBR, so you can make use of all that extra space.

---

### Post by bulldog on 2006-10-18
> **gmabry1 said:**
> Really all i want is for the Grub message to not show up when i start the computer.  If I set the time to zero then i would need to change it later if i ever decide to go back to dual booting correct?  But for right now i would like to know how to hide the grub message when i restart the computer.  Thanks

Well that's all explained to you in my first post.
```
gksudo gedit /boot/grub/menu.lst
```

Opens your menu.lst,alter the hiddenmenu option by uncommenting like,```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```
You can also set the timeout on 3 or so it's 10 by default,so you boot faster.

By hitting ESC you see your GRUB again to choose a different kernel or what ever.

---

### Post by Rui Pais on 2006-10-18
> **bulldog said:**
> No apologies needed,we're all here to help.

He wanted to delete grub so I presumed he wanted to go back to windows :D 
me too :D 

> But no harm done,we all try to contribute with different kind of solutions.

So we all learn from eachother cause we see solutions we didn't thought about.

Thats absolutely right bulldog.



**@gmabry1:**
for your 1st question of you last post, yes.
for the 2nd, read bulldog suggestion :)

*edit: well bulldog typed faster... *

---

