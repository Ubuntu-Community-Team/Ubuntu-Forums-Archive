---
title: "Install, reboot, laptop = big problem!"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by prodigalson666 on 2007-12-16
Installed gutsy on my acer 5520, after reboot the bar freezes on the usplash and doesnt go any where. I rebooted and pressed alt-f2 to go into verbose mode, the reboot freezes at the reboot usplash screen resolution, it freezes on the 1280x1024, I did not choose this resolution during install, I used the alternative cd and choose 1280x800, the laptops native resolution. Booting into safe mode reproduces the same results.

At the grub menu, press "e" to edit the normal boot entry, scroll down to the line that begins with "kernel" and press "e" again. Remove the words "quiet splash" from the end, press enter to save, and "b" to boot. This will give you a no nonsense verbose mode. Is it hanging up in the same places, if at all? If it boots just fine, it is probably a known issue with your usplash resolution, check out the attached link.

I tried this suggestion but the same results.

ok after 3 min of being frozen I get this screen

busy box v1.1.3 (debian 1:1.1.3-5ubuntu7) built ion shell (ash)
enter help for a list of built in commands

(initramfs)

This is a re thread but I haver not received any more replies and this is very important, but beyond my experience, any ideas anyone?

---

### Post by shane2peru on 2007-12-16
> **prodigalson666 said:**
> Installed gutsy on my acer 5520, after reboot the bar freezes on the usplash and doesnt go any where. I rebooted and pressed alt-f2 to go into verbose mode, the reboot freezes at the reboot usplash screen resolution, it freezes on the 1280x1024, I did not choose this resolution during install, I used the alternative cd and choose 1280x800, the laptops native resolution. Booting into safe mode reproduces the same results.

At the grub menu, press "e" to edit the normal boot entry, scroll down to the line that begins with "kernel" and press "e" again. Remove the words "quiet splash" from the end, press enter to save, and "b" to boot. This will give you a no nonsense verbose mode. Is it hanging up in the same places, if at all? If it boots just fine, it is probably a known issue with your usplash resolution, check out the attached link.

I tried this suggestion but the same results.

ok after 3 min of being frozen I get this screen

busy box v1.1.3 (debian 1:1.1.3-5ubuntu7) built ion shell (ash)
enter help for a list of built in commands

(initramfs)

This is a re thread but I haver not received any more replies and this is very important, but beyond my experience, any ideas anyone?

This seems to be a common problem when you installed and then did a restore of a backup you had.  This may not have been what you did, however, it looks like your menu.lst is using the wrong UUID numbers and causing it to freeze.  I have seen this several times.  If you know what your hdd letter and partition number is you can try this.  When the boot screen comes up press 'e' to edit the line (this is not permanent it will only alter it for this boot time.)  Scroll down to the line that has your root hdd and replace the UUID=ak93981ks0sdafsd <- or whatever that super long string of alphanumeric characters is and put your booting partition.  ex.  sda3 or hda2  or whatever your setup is.  The letter would represent the hdd, 'a' would be the master hdd, 'b' would be the slave  etc.  the partition numbers a little more complex.  This is just a guess at your problem, if you can do this and it boots great, post back and we will fix your problem permanently.  If not, you will need to boot into a liveCD and we will have to troubleshoot it from there.

Shane

---

### Post by prodigalson666 on 2007-12-19
Sorry I've been away, do I delete the =uuid long alpha-numeric string with my sda3? do I keep quiet splash? Thanks

---

### Post by shane2peru on 2007-12-19
> **prodigalson666 said:**
> Sorry I've been away, do I delete the =uuid long alpha-numeric string with my sda3? do I keep quiet splash? Thanks


It should look like this:  
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=[COLOR="Red"]UUID=a23d5e6e-efe2-45eb-ad41-bdc5cc88c3b8[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

```

change it to this:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=[COLOR="Red"]/dev/sda1[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

```
Of course you will need to replace the sda1 with the proper setup you have.  
Actually I just had this problem and fixed it to boot up this morning and forgot to fix mine!  Thanks for the reminder :lol:

Back up your menu.lst before you go changing it, you may need what was there.  :)

Shane

---

### Post by prodigalson666 on 2007-12-19
WOW, nothing! its still stuck at the uspalsh, fails to load, 1280x1024, then fails to load 1152x864, using mode 1024x768 and it stops. What exactly is going on anyway, this is ridiculous, sdabayon works, open susr works but this occurs with every debian based I've tried, debian, mint, mandriva etc.

---

### Post by slawko on 2008-02-26
I have the same problem on my Acer Aspire 7520... I'm trying to fix this since yesterday... Few additional facts:

- I installed 7.10, performed a reboot (it was fine) and then chosen to load the proprietary drivers for Nvidia graphics card that were suggested (nvidia-glx-new or something) - after reboot it was dead (just as described in a post above)

- I was playing around for some time poking here and there (have other linux distro installed at the same box) and it finaly AUTOMAGICALLY booted fine... and I even had the nvidia driver working and it was fantastic, then... I installed the automatic upgrade of the system (over a hundred of packages... this was huge) and rebooted - since then I cannot bring the box back online... what the heck???

I've seen this problem around on forums but I was not able to find a clear solution - **what to do when you are in (initramfs)?** Is there a way to bring the system back online from that state?
Assumig that I can boot the system from live CD or another distro - what can I do do bring my precious Ubuntu back online?

I would be grateful for any help... this is very disappointing behavior...

Thanks,
slawko

---

### Post by bred on 2008-02-26
> **slawko said:**
> I have the same problem on my Acer Aspire 7520... I'm trying to fix this since yesterday... Few additional facts:

- I installed 7.10, performed a reboot (it was fine) and then chosen to load the proprietary drivers for Nvidia graphics card that were suggested (nvidia-glx-new or something) - after reboot it was dead (just as described in a post above)

 well slawko I had the same problem on my notebook 2 weeks ago, I've downloaded a lot of updates, installed all of them, except nvidia drivers and network driver which was the last drivers for my installation... now it works... try to install all updates before the network and nvidia drivers...at least it worked for me:)

---

### Post by slawko on 2008-02-26
shane2peru - unfortunately changing root to /dev/whatever does not help that much... the boot process goes slightly further and hangs anyway... it displays ALERT that my /dev/sda3 is not present and ends up in initramfs anyway after couple of minutes of hanging - I check /dev and there is no such device indeed. How is it possible? The computer is running something which is stored on disk, right?

The drive-led is constantly on for all the time... not blinking

Strange issue...

---

### Post by slawko on 2008-02-26
> **bred said:**
> try to install all updates before the network and nvidia drivers...at least it worked for me:)

Thanks bred :) I will try this if there is no other way to bring it back without reinstalling the system, because this is the way if I understand :) Definately I will keep that option in mind :)

---

### Post by slawko on 2008-02-26
It seems like keeping the box in GRUB menu for more than 10 seconds is a workaround for the issue :)

The less interactive solution is described here - [http://ubuntuforums.org/showpost.php?p=4394099&postcount=131](http://ubuntuforums.org/showpost.php?p=4394099&postcount=131) but it didn't work for me. Just waiting in GRUB is fair enough.

Thanks!

---

### Post by shane2peru on 2008-02-27
> **slawko said:**
> shane2peru - unfortunately changing root to /dev/whatever does not help that much... the boot process goes slightly further and hangs anyway... it displays ALERT that my /dev/sda3 is not present and ends up in initramfs anyway after couple of minutes of hanging - I check /dev and there is no such device indeed. How is it possible? The computer is running something which is stored on disk, right?

The drive-led is constantly on for all the time... not blinking

Strange issue...

Slowko,

     Yes, this only works if it is an official grub issue of not loading because the UUID is not set correctly.  However, this is clearly not the issue here.  You guys seem to have a real issue with drivers and loading order.  I wish I could help more, however I just don't know what to tell you.  

Shane

---

