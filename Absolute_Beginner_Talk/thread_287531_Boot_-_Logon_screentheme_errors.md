---
title: "Boot - Logon screen/theme errors"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by BackInTimeMan on 2006-10-28
Just upgraded to Edgy and am having problems with my boot splash and logon screen.

With an unmodified /boot/grub/menu.lst:

```
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=98174f4c-3996-4866-91c7-676e1e088d75 ro  quite splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

and my usplash conf:

# Usplash configuration file
xres=1024
yres=768
```

this is what happens:

Start up, grub is detected and after the countdown starts to boot the system. I see a quick screen full of text flashing by and then the boot splash is there. I can just make it out because it is very dark and is almost invisible against the dark screen background. Boot continues to where my logon screen should appear but then I see the same text on my monitor that appears when it is going into blank screen mode (don't run screensavers). At this point I hear the little drum roll that usually accompanies the appearance of the logon screen, but the logon screen/theme does not appear. I act as if it has, enter my username and password, hit Enter and continue to the desktop.

On shut down the boot splash is the same, almost too dark to be seen.

I've seen this thread:

[http://www.ubuntuforums.org/showthread.php?p=1541970](http://www.ubuntuforums.org/showthread.php?p=1541970)

so I added: vga=0x317 to a couple of parts of menu.lst, like so:

```
# defoptions=quite splash vga=0x317

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=98174f4c-3996-4866-91c7-676e1e088d75 ro  quite splash vga=0x317
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot
```

Now when I boot up I get a message saying something like: "You have passed an undefined vidio mode" and I get some options to choose a number from a list, scan, or continue. Which ever I choose makes no difference, I still cannot see the boot splash nor the logon splash.

If I look in Admin --> Logon Window, my themes are still there and one is selected.

I wonder why it says: UUID etc. in my menu.lst instead of: /dev/hda1. Does that have anything to with the problem?

Any ideas please?

---

### Post by BackInTimeMan on 2006-10-29
Can anyone help me with this?

---

### Post by human on 2006-12-05
I'm in the same boat, can someone help us?

---

### Post by BackInTimeMan on 2006-12-08
Hi human,

I went back to Dapper but can't quite remember if I fixed this or not. although I think I did. I reckon I tried using /dev/hda1 instead of the UUID string though and maybe used  vga=5 instead of vga=0x317. Can't be sure though and it would probably be different for different hardware. I did install Edgy on another machine and didn't have this particular problem. Sorry not to be of any specific help... did you get anywhere with it yet?

---

### Post by human on 2006-12-11
Thanks for the reply, I'll try that and tell you guys if it worked

---

