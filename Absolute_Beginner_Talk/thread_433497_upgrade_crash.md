---
title: "upgrade crash"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by jctaft on 2007-05-05
I've been using dapper without incident for some time now, and I decided to update to feisty, which means I had to update in two steps, one to edgy, and then one to feisty.  After everything finished with the upgrade to Edgy, the computer restarted, and when it starts, I get the following error:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?

If I select yes, I get a whole bunch of stuff, but the main thing that seems pertinent is the following line:

Error: API mismatch: the NVIDIA kernel module has the version 1.0-8774, but this X module has the version 1.0-8776.  Please make sure that the kernel module and all NVIDIA drivers components have the same version.

and then a few more lines I'd be more than happy to post if somebody thinks it's relevant.  I'm not real linux-savvy, so I have no ide what to do.  Can somebody help me?

thanks,
j

---

### Post by DSn0wMan on 2007-05-05
If you are using the binary NVIDIA driver the upgrade will usually mess it up. Reinstall your dirver, or just use the open source one until you complete all the upgrading. You will probably need to do a "sudo dpkg-reconfigure xserver-xorg"

---

### Post by jctaft on 2007-05-05
I have no idea how to do either of those things you mentioned.  Especially since I have no graphical interface.   IF you could bear with me and be a little more explicit, I would really appreciate it.

Thanks

---

### Post by akudewan on 2007-05-05
As  DSn0wMan says, try running: "sudo dpkg-reconfigure xserver-xorg". You will be asked a series of questions. Select the "nv" driver instead of "nvidia". You'll have the X server running, then you can correct the problem easily.

---

### Post by jctaft on 2007-05-05
I went through those questions and answered them the best I could, restarted, and I still have the same problem.

---

### Post by akudewan on 2007-05-05
Ok, try this: ```
 sudo nvidia-glx-config disable 
```

If it still doesn't work, run "sudo dpkg-reconfigure xserver-xorg" again, and select "vesa" instead of nv or nvidia

---

### Post by topsites on 2007-05-17
I had a similar problem...

I tried all that bs, nothing worked, then I found a little something:

cd /var/backups
dir

And see which one of the xorg backups is the one right before it crashed, most nvidia reconfigs make a backup.
Then:
cd /etc/X11
sudo cp xorg.conf xorg.bak

(just in case)

And back to 
cd /var/backups
sudo cp xorg.conf-(date-hour-mins-sec) /etc/X11/xorg.conf

sudo shutdown -r now

And my system works again.

---

