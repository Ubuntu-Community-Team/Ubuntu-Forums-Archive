---
title: "Two minor problems"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by JamesDS on 2008-04-11
Hey, I've got two small queries, one of which I know a solution exists for (and is really simple, but I can't find it), the other I can fix but I was hoping there would be another solution.

1. How can I make the Ubuntu boot/startup screen visible?  I think this is due to my laptop's widescreen resolution not being detected or something, I saw the fix somewhere once, now I can't find it.

2. VIdeos, screensavers and 3d games will flicker when desktop effects are on.  Is this able to be fixed, say in my xorg.conf, or is it a problem with my graphics driver?  I know my graphics card isn't officially supported, it's an ATI Mobility Radeon HD2600, but I managed to get it working really well with Envy.  I do like my desktop effects....

---

### Post by wannadumpwindows on 2008-04-11
#1. You might wanna have a look at this thread.

[http://ubuntuforums.org/showthread.php?t=580903&highlight=gutsy+slow+boot]("http://ubuntuforums.org/showthread.php?t=580903&highlight=gutsy+slow+boot")

#2. I don't know exactly, but it does sound like a config issue somewhere.

---

### Post by tobydeemer on 2008-04-11
As for the boot up issues, these are the two common fixes, that I've saved from threads gone by. I think I have the links to them somewhere, but I forgot where. I have the fixes saved in a doc though: 

Try rebooting, during the GRUB timeout, press ESC. Select your kernel (usually the one with the highest number that is not safe mode), press "e" (for edit). On the screen this opens, press "e" again, and remove the "splash" part of the line. Press Enter, then b (for boot).

Once booted, in the terminal you can type "sudo gedit /boot/grub/menu.lst"
This should open the GRUB config file, from there, what you will want to edit is usually near the end. You'll have a bunch of entries with "Title Ubuntu, kernel" and kernel numbers, you need to find the one you're booting from, then under it in the "kernel" part of the entry, you'll find the "splash" option. You can just delete "splash" and save. On next reboot, it should be permanent.
One drawback of editing options in the GRUB config files though is that you'll need to do it each time a new kernel is installed through update-manager (as it will create a new entry in GRUB with the default options). 
****OR*****

Does the black Ubuntu loading splash screen work when you do that?

If not, here is another (slightly longer) fix that was posted elsewhere to fix it for real. The problem with the slow boot is that the settings in Usplash can sometimes get messed up on install and hang up the boot. Removing some of the lines in menu.lst disables Usplash and fixes the problem. If you like the verbose boot up, then leave it. If you'd like the pretty Ubuntu boot up sequence, try this.

1) Put everything back in /boot/grub/menu.lst that you took out ( "ro quiet splash" in the kernel line and "quiet" at the end)

2) At the very end of the kernel line after "splash" , add "vga=791" Make sure this goes on the same line.

3) Save that file, close it, and open up /etc/usplash.conf

4) Change the screen resolution to the resolution you are actually using. Save it and close it.

5) Grub won't know anything about this until you rebuild the boot, so do the following commands.

uname -r
This lists your current kernel version.

sudo update-initramfs -u -k <insert results from uname -r here>

This rebuilds the image that Grub uses to start the system.

Also, you can always hit CTRL-F1 when the splash is running to get back to verbose mode.


The flickering issues- this is likely a combo issue of effects and ATI. Are you using the restricted drivers manager to get the ATI card working? You mentioned Envy, which several more experienced users than I recommended to me to not use (Automatix as well) since they can leave some unsightly edits in system code. But for general multi-media and video trouble shooting, this is a really good thread:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
It's really long, but if you take the time to read all of it, most video issues are likely mentioned at one point or another somewhere in the thread.

Hope this helps.

-toby

---

### Post by plucky on 2008-04-11
> One drawback of editing options in the GRUB config files though is that you'll need to do it each time a new kernel is installed through update-manager (as it will create a new entry in GRUB with the default options).


You can fix this by adding what default options you want to this line in **menu.lst**

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions= quiet splash vga=791

```

Then on a kernel update the default options are reinstated.[highlight]Do not remove the #[/highlight]

Good Luck

---

### Post by tobydeemer on 2008-04-11
Ah, good tip. Is the install in 8.04 better at keeping the boot settings correct? I've installed 7.10 on several machines, and had to rework the boot process on all of them.

---

