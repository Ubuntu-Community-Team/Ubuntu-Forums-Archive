---
title: "[SOLVED] Totally Lost With a e-GeForce 6200 DDR2 256mb PCI"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Starbuck13 on 2007-10-10
I'm pretty much a total newbie, and I just installed Ubuntu 7.04, and am now trying to get it to work with my video card, and I have no luck. I tried using the ".run" file from Nvidia, and the xconfig thing from nvidia, but on bootup, my system just freezes. 

Sorry, I'm so new, I don't even know what relevant information I should post here to get help. 

Can anyone guide me by the hand???

---

### Post by skipb on 2007-10-10
First and foremost, welcome to the community!

As for your problem.
Can you describe when and what happens when your computer freezes? do you have anything on your screen at all after the freeze?

---

### Post by Starbuck13 on 2007-10-10
Thanks for the welcome!

I'm at the bootup graphics screen where the "orange progress bar" is progressing towards the right, and then it suddenly stops, my hard drive activity LED stops, and the computer just sort of freezes there.

---

### Post by kvonb on 2007-10-10
Boot your system and wait till the hard disk stops thrashing.

Press <ctrl><alt><f1> to get to the login screen.  If you get there then it's only the X-server that has stalled.

Login with the username and password you created on install.

Now copy this lot down and type them at the prompt:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

(some people have to omit the -phigh part)

Now it will present you with questions, for the video adapter choose "vesa", all the other questions you can safely just accept the defaults, or ignore them :).

When it finishes and you are back at the prompt, simply press <crtl><alt><del> to reboot.

You should then get back to a useable desktop.

If you do, then open firefox and go here:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Download Envy, then simply open the file you downloaded and select "Install Nvidia Driver", follow any instructions.

That should fix you up :).

But remember, if you do any updates you might have to run envy again, login as above and simply run:

```
sudo envy
```

It will re-make the driver module for you.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Starbuck13 on 2007-10-10
ok, at the point that everything freezes, I tried pushing ctrl+alt+F1, and nothing happened. 

So, I've got onboard intel gma950 graphics coming to my monitor via vga, so i connected that up, and switched the bios (at the boot screen) to use the onboard graphics,nd then did everything that you said. then I rebooted, and switched the bios to the pci graphics card,and then rebooted again, and it still froze.

my pci card is connected to my monitor via a DVI-D cable, and both are connected right now.

Help.

---

### Post by Starbuck13 on 2007-10-10
bumping it up

---

### Post by Teddy_P on 2007-10-10
I think I have the same problem.
Check out
[ [COLOR="Red"]My thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=565883")

How big is you power supply?
The specs say 300W and 18A on the +12V

I got a lot of help in that thread and I think I should try a new power supply next.


Teddy

---

### Post by Teddy_P on 2007-10-10
I also tried this card in two computers one I got to the command line, the other nothing.



Teddy

---

### Post by overdrank on 2007-10-10
> **Starbuck13 said:**
> ok, at the point that everything freezes, I tried pushing ctrl+alt+F1, and nothing happened. 

So, I've got onboard intel gma950 graphics coming to my monitor via vga, so i connected that up, and switched the bios (at the boot screen) to use the onboard graphics,nd then did everything that you said. then I rebooted, and switched the bios to the pci graphics card,and then rebooted again, and it still froze.

my pci card is connected to my monitor via a DVI-D cable, and both are connected right now.

Help.

Hi maybe this link will help, it mentions then nvidia graphics with intel onboard
[http://forum.compiz-fusion.org/showthread.php?t=1762](http://forum.compiz-fusion.org/showthread.php?t=1762)
Good luck !

---

### Post by Starbuck13 on 2007-10-11
Kvonb, your solution helped a bit!

Since I have onboard Intel graphics, they were fighting against my video card, even though I disabled them in the bios. So, once I put a "#" in front of the busID for my intel graphics, then ran Envy, all was well!!

---

