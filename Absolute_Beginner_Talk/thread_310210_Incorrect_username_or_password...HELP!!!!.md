---
title: "Incorrect username or password...HELP!!!!"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by gentay on 2006-11-30
Fellow Ubuntu users I need your help.I am not a very computer savy guy so plaese bear with me.
I am useing Unbuntu 5.10.I logged out of my computer last weekend,got up the next day to log in and got the "Incorrect username or password" I tried a few times to log in thinking I may have miss typed something wrong,but still got the same promt.
So I have come here to find out what to do. I found many threads that I think could help me but its all techno talk to me. I see things like Grub menus and Recovery/Rescue menus,and Root passwords and sudo stuff.....Its all seems so over whelming to me.
If some could take the time to help me and explain it to me in avery simple point by point way to get back into my computer I would repay you some way some how.
I have been told if i can get a copy(newier the better)of Ubuntu and that I should be able to boot off it and get back in and put in a new password? that is on its way,but I need to get into my computer ASAP.
So help plaese!!!

---

### Post by taurus on 2006-11-30
From the GRUB menu, use the down arrow to highlight the recovery mode then hit return.  Until it finishes booting, you will get a prompt and from there, you can change your password with

```
passwd gentay
(assuming gentay is your login name...)
```
Reboot and see if you can log in with your usrname, gentay, and the new password.

```
shutdown -r now
```

---

### Post by gentay on 2006-11-30
=) Kool,but how do I get into the Grub menu? at which point when I turn the comptuer on can I get into it?

---

### Post by taurus on 2006-11-30
When you turn on the computer, do you see a menu with options?  If not, try to press the Esc key then...

---

### Post by gentay on 2006-12-01
Mmmmmm? if there is it goes by pretty fast. When I do start my computer it does the normal boot up,there are a few moments where it pauses long enough that I might be able to type someting in. I did try hitting ESC but did not effect the boot up as far as i could tell.
Would Ctrl/Alt/F1 work for this at all? I know when I do that it asks for my login name then passwd.
let me know,and thank you for your help thus far =)

---

### Post by CatKiller on 2006-12-01
I understand that the default setup is for GRUB to pause the boot process for three seconds in case you want to enter the GRUB menu. At the point you can do this it says "Press Esc to enter GRUB menu" or something similar.

You may find that pressing Esc every second or so after you turn on the computer might get you to the menu.

Doing it from the virtual console (Ctrl-Alt-F1) would be possible if you could log in, but since that's what you're trying to fix, you can't. The recovery mode automatically logs you in so that you can fix stuff.

Have you checked Caps Lock/Num Lock to see if you've inadvertently turned one of those on?

---

### Post by gentay on 2006-12-09
Ok I have tried many times to find or go in to the grub menu...with no success. I've tried a few things...I've hit esc to no avail and aswell as crtl/alt/a...nothing...it does pause for about a minute...is there something I can type at that point to get into the grub menu?
What am i doing wrong?  I'm sorry to seem like a pain in the butt.I am not in anyway a computer smart guy...but I do take direction very well. so please point me in the right direction.
Thank you for help up to this point =)

---

### Post by taurus on 2006-12-09
When you first turn on your machine, it will go through your RAM and video stuff.  Then you would see the GRUB with timing counting down on the right.  That's where you press Esc.  You need to do it quick since you only have 3 seconds to press that key to see GRUB menu...

---

### Post by CatKiller on 2006-12-09
If you didn't install Ubuntu yourself, it's possible that the person who did has changed the timeout for the GRUB menu. Does that seem likely? That is defined in /boot/grub/menu.lst, and you can change it from the live cd if that does turn out to be the case.

---

### Post by gentay on 2006-12-10
Ok...I do see the grub menu thingy, when the computer starts up. I do hit esc in that 3 secs that I have...but it just continues the start up. The only real pause is when the start up gets to * configuring network interface. That is the only long pause the whole time durring start up. I have attempted to type /boot/grub/menu.list at the pause.but nothing happends.
But I now have a copy of the newest ubuntu...
So here are my question...
1.when it reads the disk it says...
Start or install ubuntu
Start ubuntu in safe graphics mode
Check cd for defects
Memory test
Boot from frist hard disk
So this is the list they give me.the first one is already high lighted,I cant seem to choose any other one, and it gives me about 30 secs to make a choose.
So should I just allow it to do the frist one? Will it whipe out all my stuff it i alllow it to install?
So does anyone knbow how i can select any of the others?
Wouldnt the last one boot from frist hard disk be the one to go with?
I feel so close to having this fixed...what do i do?

---

### Post by CatKiller on 2006-12-10
Ah. I think I see what's happening. Is it a USB keyboard?

You'll need to borrow a PS/2 keyboard from somewhere, and boot up with that instead. Then either use that for the duration of fixing your problem, or use that to go into the BIOS setup program for your motherboard to be able to use the USB keyboard.

Getting into the BIOS is a similar method to getting into the GRUB menu. There's a point in the boot process - before the GRUB message, just after the beep - that you can press a certain key. It's usually the Del key or one of the F keys, and it should say at the time or in your motherboard manual which it is. This will take you to a menu system. You'll be looking for an option called "Legacy USB Support," or something sililar, to turn on. Why it isn't on by default completely escapes me.

This will allow you to use the USB keyboard before the USB drivers are loaded.

---

### Post by gentay on 2006-12-10
ok update...heres where I'm at.
Keyboard is not usb,but I did plug into the other port for it and now am able to get into the grub menu(YA!!!!)
I have high lighted recovery mode as suggested,and let is load up also as suggested.
The promt I get is... Give root password for maintenance
(or type control-D to continue):
I've have tried entering my old passwd and root and sudo
all I get is login in correct...ARG!!!!
Guys I'm here almost at the finish line...
what am i doing wrong?

---

### Post by gentay on 2006-12-10
OH And I also have the cd now...how do I get in with that?
I know lots of questions....I should just have one of you call me...I'll pay for the call.

---

### Post by CatKiller on 2006-12-11
Out of interest, have you tried logging in normally since you switched the keyboard port?

> **gentay said:**
> The promt I get is... Give root password for maintenance
(or type control-D to continue):

I've not seen that. Recovery mode has always just automatically logged me in as root. I don't think I tried it with 5.10 though, so possibly that's one of the changes that happened with later releases.

You could try editing one of the entries in the GRUB menu, and putting **single** at the end of the kernel line.

If that doesn't help, apparently adding **init=/bin/bash** to the end of the kernel line might. That will terminate the boot process early, so (again, apparently) you'll have to use this command ```
mount -o remount,rw /
``` once you get to a prompt.

> **gentay said:**
> OH And I also have the cd now...how do I get in with that?

If it's one of the recent ones, you can just boot from it and get into a live environment. I don't really know what you'd do when you got there in this case though. You'd have to mount your hard drive and then presumably edit /etc/shadow relative to where you'd mounted it. But you'd possibly have to edit it with vi, which I find scary, and I don't really know what you'd edit it to. Maybe there's some dead clever method using chroot or something, but I don't know enough myself to know what that would be.

---

### Post by gentay on 2006-12-11
Ok good morning..I'm skipping work today...i have to get this thing to work today or aleast this week.
I did try to re enter my passwd when i re plugged in my keyboard..its the frist thing i did...but I didnt get in :(
I have tried to boot off the disk...it just goes to the passwd/username screen and guess what?  Yup I get Incorrect username or passwd.
This is really killing...I know I'm soo close to fixing this.
So back to the start.. Grub menu
When I hit ESC I get 3 choices
1 Ubuntu, kernel 2.6.12-9-386
2 Ubuntu, kernel 2.6.12-9-386 (recovery mode)
3 Ubuntu, memtest86+
then under all of them it says....
Use the up and down keys to select which entry is highlighted.
Press enter to boot the selected OS, 'e' to edit the commsnd before booting, or 'c' for a command-line.
If i go into the frist one these are my choices by pressing'e' I get these choices...
1 root  (hdO,O) but there are 2 dots in the o's not sure how to do that
2 kernel /vmlinuz-2.6.12-9386 root=/dev/hda2 ro quiet splash
3 initrd /initrd.image-2.6.12-9-386
4 savedefault 
5 boot
Are any of these a way into fixing my passwd or getting into my silly computer?
I'll be here waiting :)

---

### Post by max.diems on 2006-12-11
> Ubuntu, kernel 2.6.12-9-386 (recovery mode) lets you change any non-root password.

---

### Post by gentay on 2006-12-11
but should i hit 'e' and edit something?
because when i highlight in and press enter in goes through its thing...then promts me Give root passwd for maintence.
So then what?

---

### Post by CatKiller on 2006-12-12
> **gentay said:**
> but should i hit 'e' and edit something?

Yes, you could try editing the line, as I said above.

---

