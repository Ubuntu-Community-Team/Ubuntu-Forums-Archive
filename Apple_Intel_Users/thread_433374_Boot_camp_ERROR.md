---
title: "Boot camp ERROR"
date: 2007-05-04
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-04
After following this guide: [http://www.cs.helsinki.fi/u/jzshen/install_feisty.html](http://www.cs.helsinki.fi/u/jzshen/install_feisty.html)

(past the Utildisk part)

I cant start up bootcamp assist like the apple guide says I get this "The Startup disk cannot be partitioned or restored to a single partition". 


I'm using rEDIT and someone burned the windows drivers for me (exact same computer).... should I be able to still install or what do I do.. there is obviously something wrong (with my comp or that guide).

---

### Post by ronocdh on 2007-05-04
> **The_Giver said:**
> After following this guide: [http://www.cs.helsinki.fi/u/jzshen/install_feisty.html](http://www.cs.helsinki.fi/u/jzshen/install_feisty.html)

(past the Utildisk part)

I cant start up bootcamp assist like the apple guide says I get this "The Startup disk cannot be partitioned or restored to a single partition". 


I'm using rEDIT and someone burned the windows drivers for me (exact same computer).... should I be able to still install or what do I do.. there is obviously something wrong (with my comp or that guide).
Interesting. I just tried to start Boot Camp Assistant and I couldn't, either. I guess it's because you partitioned out of order. Anyway, the Windows Driver CD is necessary only if you want to install XP. If that's the case, then yes, theoretically you could use a drivers CD burned with another computer, but the problem is the hardware must be *identical*. This is a tricky issue because even the same models change hardware over time without the differences being published, so purchasing the same model weeks apart can actually result in small changes.

You could if you want delete the other partitions you've created using something like iPartition and then use Boot Camp Assistant normally, but you also have the option of proceeding as is. Remember, either way, back up **ALL** your data! ;)

---

### Post by The_Giver on 2007-05-04
Well now i'm confused as to how to install ubuntu:

My macbook pro is not the same.... as this: [http://www.cs.helsinki.fi/u/jzshen/install_feisty.html](http://www.cs.helsinki.fi/u/jzshen/install_feisty.html)
nor this:  [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

Why couldn't just someone make one for the new macbook pro!


I'm split between following either guide.... no idea what I should do... my main confusion comes from what to do with swap.... since that seems to be an important but really blurry step on both guides


(BTW how do i know if the windows drivers worked???)

---

### Post by The_Giver on 2007-05-04
I guess I dont understand this: 


9.       Double click the installer then go through. At the partition step, choose &#8220;Manually&#8221; to do the partition. When the partition table come, just edit mount point &#8220;/&#8221; at &#8220;/dev/sda3&#8221; and click &#8220;reformat&#8221;. As to the windows partition, I don&#8217;t choose to mount it automatically. Later, you will see the reason. Click &#8220;forward&#8221; button and ignore the warning of no swap!

**How do I edit the mount point... w/e w/e.. what does that actually mean?**

10.   DO NOT migrate from some account from Windows XP, which may cause problems!


**No idea what the above is supposed to mean whatsoever...**

11.   Fill the box as you want, then go the &#8220;ready to install&#8221; page. Click &#8220;Advanced&#8221;, change &#8220;(hd0)&#8221; into &#8220;(hd0,2)&#8221; to just install the grub on the Linux partition not MBR, which means that you don&#8217;t have to synchronize the GPT and MBR during the first start after installation. Because I had so much unhappy experience about failure on synchronization operation in rEFIt, this way should be much safer, which have little chance to mass the whole triple boot systems. This unsynchronized GPT and MBR is also the reason of my not mounting the windows partition automatically, otherwise, you would get error message from fsck ( file system check ) everytime you boot your Ubuntu. However, you can mount it any time you want while using!

**What is this "Fill the boxes"?????? what is this talking about...  is this after/ during installation? **

---

### Post by ronocdh on 2007-05-05
Step 9 is telling you to choose your partitions carefully; in other words, you don't want to overwrite your Windows and/or OS X partitions while installing Ubuntu. /dev/sda3 should be where you want to install to, as /dev/sda4 will be Windows XP and /dev/sda2 OS X. This is how I have it; YMMV. Very important that you do NOT use a swap partition. You can always create a swap file later, and that's much better for our purposes here.

Step 10 is referring to the Windows Migration Assistant which is new in Feisty. When the installer asks you whether you want to import a profile from Windows XP, just politely decline.

Step 11 says "fill in the boxes" and means type in your desired user info, such as real name, username, password, etc.

I personally didn't have to make any other changes, such as those listed in the rest of step 11. My Windows partition mounts just fine in Ubuntu. Good luck.

---

### Post by The_Giver on 2007-05-05
So did you actuallly carry out any other step besides 11? I dont get what you mean

---

### Post by The_Giver on 2007-05-05
What ... i mean is... if I skip the test of step 11.. (so only fill out my info).... what other step do i have to skip?


Also, are you saying I should mount windows automatically?... on step 9?

---

