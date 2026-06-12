---
title: "edgy v. dapper boot"
date: 2006-12-25
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-12-25
I've had dapper on my desktop for a year and recently put edgy on my laptop and noted that when dapper is booting, there is a text summary of the steps it is going through during the process but this isn't displayed for edgy.  Well, today this caused some problem as edgy was taking a long time to load as my son was trying to impress his grandfather with it!  The reason it was taking so long was this was the 30th boot and so it was going through the long system check.  We didn't know this because edgy doesn't display what is going on during the boot process.  So, thinking it was hung up, my son did a hard reboot.
I figured out the problem later but the hard reboot has caused my vmware server not to load.  Any ideas what the problem would be with vmware or how to solve it? I suppose I can reinstall it and reinstall my virtual windows but that's a pain!

---

### Post by Ecthelion on 2006-12-26
> I've had dapper on my desktop for a year and recently put edgy on my laptop and noted that when dapper is booting, there is a text summary of the steps it is going through during the process but this isn't displayed for edgy. 
You can make that text summary appaer in Edgy too if you want.
Just remove "quiet" from the menu input in grub/menu.lst you use to start up edgy.
```
gksudo gedit /boot/grub/menu.lst
```
So you just have to remove "quiet" twice in the first menu input.

---

### Post by flyingsolo on 2006-12-26
Thanks for the help.  That will help avoid problems in the future.  Now, for my second issue, does anyone know what might have been messed up that now makes vmware not start up?  It seems to be the only program that was affected by the hard reboot.
(Is ubuntu "sensitive" to hard reboots?  ie-pressing and holding the start button of the computer to force it to stop)

---

### Post by bulldog on 2006-12-26
> **flyingsolo said:**
> Thanks for the help.  That will help avoid problems in the future.  Now, for my second issue, does anyone know what might have been messed up that now makes vmware not start up?  It seems to be the only program that was affected by the hard reboot.
(Is ubuntu "sensitive" to hard reboots?  ie-pressing and holding the start button of the computer to force it to stop)

In normal cases it's not good to do,but you'll won't get any errors afterwards.
But a file check is somewhat different,and it's certainly not a good idea to interrupt.

You can damage your hard disks severe with this procedure,just use reboot instead of turning it off.

About vmware,I think there's something like reconfigure.pll in /usr/bin.
Just type vmware in your terminal and see what it spits out.

---

### Post by Ecthelion on 2006-12-26
> I suppose I can reinstall it and reinstall my virtual windows but that's a pain!
Normally you shouldn't reinstall your virtual windows if you reinstall vmware.
You just have to tell vmware where the "image" with windows on it is.
Vmware will then recognize it as a virtual machine and you can boot it up again.

---

### Post by flyingsolo on 2006-12-26
Thanks bulldog--simply running vmware in terminal provided the instructions to restore it and all is well again.
I never would have done the hard reboot but the fact edgy seemed to be taking such a long time to boot is what started the problem--I'll certainly change it so it displays the loading steps.  I'm not sure why the default would be to hide this since it was this lack of feedback that caused my son to doubt whether it was still loading properly.

---

### Post by bulldog on 2006-12-26
Well no harm done,and all your apps. are running again,that's the important thing.

I know you wouldn't turn it off in normal conditions,and,well if you're not going to make it a habit,it isn't that important.
Just reboot in any case it happens again,it's less harmful for your hardware.

About the screen,I read more users have this issue,but I can inform you that whenever my fsck is running,I get it displayed,with all the info about which partition it's checking and so on.
And my boot is set as quit as well,just a little bug I suppose.

---

