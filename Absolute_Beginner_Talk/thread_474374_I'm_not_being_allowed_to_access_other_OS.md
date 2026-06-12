---
title: "I'm not being allowed to access other OS"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Infosponge on 2007-06-15
Alright guys and gals, If this has been posted either here or  on another forum, I haven't found it. I've looked for 3 days for a solution.
  First off: I'm BRAND NEW to the world of Unix / Linux / Ubuntu. All I've ever experienced came from Billy. I had always wanted to try Linux, but was afraid I wouldn't understand how to. Anyway, I finally took the plunge. I downloaded Ubuntu and burned it to CD. Install was dual boot with windows and was very smooth. I used the first "Guided" option since this was a whole new thing for me. I played around in Ubuntu for a couple of days. Then I realized I had a problem.
  No matter what I do, I cannot get back into windows. During boot, when it gets to the screen where you select the OS you want to boot into, Ubuntu is highlighted. When i try to move the highlight to windows, it stays on Ubuntu. It times out in 10 seconds and boots straight into Ubuntu.
1. I've rebooted 20-30 times---same result.
2. I've inserted the "full install" version of windows that I bought retail--known to be good--same result.
3. With the CD in at boot, I get the option to boot from CD. Followed by a 2 second pause, then I'm prompted to "press any key to boot from CD". However, no matter what keys I press, or how many times I press them----same result.
  I am truly at my wits end. I've read a little about "nuking" a drive, thought about it, but shouldn't the windows CD come up before grub starts to do it's thing? If that's the case, then after nuke, I may still be stuck with his same issue.
  Can someone---anyone, shed some light on the issue here.     B.T.W. if you want me to post some certain file please explain in detail where and how to get it---remember I've had just a few days of experience in Ubuntu.
   Thank You all for reading my long post--just wanted to provide as much useful info as I could.

---

### Post by jimk0512 on 2007-06-15
Since the computer I'm using is dual-booting fine between Windows XP Home and Ubuntu Feisty Fawn, I'm not certain why yours is not working. I use the up and down arrows to select which OS to boot.

Anyway. from your description, it sounds like your computer is not seeing the keyboard during boot, but then it finds it once Ubuntu boots. Just guessing, do you have a USB keyboard? On one of my computers, I have to tell the BIOS if I am using a USB connected keyboard.

---

### Post by Infosponge on 2007-06-15
Thanks for the response! I am able to access BIOS during boot by hitting the delete key, so I'm not sure if what you suggested is the issue. But be sure I'm gonna try it. Thank You again.

---

### Post by Infosponge on 2007-06-15
Nope. Keyboard options in BIOS did nothing for the issue. Thanks though. Anyone else have an idea?

---

### Post by steve.horsley on 2007-06-15
Is there anythong unusual about your keyboard that could possibly be the reason that the bootloader can't see it? 

If you have a USB keyboard, is there any possibility of borrowing a non-usb keyboard (with a round connector) to prove the point? Baing USB sticks out as a possible reason, a;though I have seen USB keyboards working with the GRUB bootloaded (and never personally seen it not work).

---

### Post by jimk0512 on 2007-06-15
Just grasping at straws here, but are the arrow keys on your keyboard part of the number pad? I have seen a small keyboard which only had one set of keys for both the number pad and the arrow keys. You had to press the Num Lock to switch what the keys did.

---

### Post by Infosponge on 2007-06-16
Well Jim, I have both. I have separate arrow keys as well as those included with the number pad. Neither one change the highlighted bar's position from Ubuntu to windows.
  Steve, I access my BIOS before I ever get to the screen that gives me the OS "prompt". So, I'm not so sure that the bootloader "can't see" my keyboard.
  To all----Even though it may appear that I'm just shooting down suggestions, I'm NOT trying to do that. Thats the very reason that this issue has driven me so !nuts! over this last week. Everything that makes sense seems to leave the issue unresolved. I'll keep checking back, but in the mean time I'm gonna check out any possible "deals" that I might get on new drives.
  Thanks guys/gals!

---

### Post by confused57 on 2007-06-16
If you're using a USB keyboard...check if there is an option in your bios to enable something like "USB Legacy".
Don't know if it'll help or not.

---

### Post by Infosponge on 2007-06-16
Thanks Confused57! I'll go look now.

---

### Post by Nikron on 2007-06-16
If your really need to get back into Windows, you can always just boot into ubuntu and and edit the /boot/grub/menu.lst file so that everything between "title ... chainloader +1" is before the linux entries.  (don't put it too far up though)

---

### Post by DSHANNY on 2007-07-05
Infosponge, I just went thru the same thing. I got into bios (del during startup). Then selected "features set up" and then changed "usb function for dos" to enable. The keyboard then worked in the dual boot screen.;):

---

