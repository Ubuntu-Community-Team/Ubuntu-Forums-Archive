---
title: "Booting problems"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by MangasColoradas on 2007-12-21
I have just done a fresh install of Gutsy and sometimes it gets no further than the logo where it will stop at 3 squares on the bar type thing...

but now when it gets past that and seems to boot up normally, I just get a black screen.

The only thing I have changed is I set the monitor refresh rate to 60hz (which is my monitor rate), in 'sys-prefs-screens and graphics cards', I also changed it to 60hz in Compiz.

---

### Post by puccaso on 2007-12-21
for the time being
when u boot up - from grub, select ur default option - press E to edit it..
and remove the words on the kernel line that say "quiet splash"

this will give u a very verbose boot up screen and you can see what exactly is causing your system to get stuck

---

### Post by MangasColoradas on 2007-12-22
Thanks, I will try that.

---

### Post by MangasColoradas on 2007-12-22
I did it but couldn't see anything wrong and it was whizzing by pretty fast too...

So, since it was a fresh install and I wasnt losing anything I re-installed using the alternate CD which I used the previous time without this happening.

I just hope it doesnt happen again. I had a perfect;y good install until I borked it by trying to follow some guide for manually installing ATI drivers...lesson learned there...if I dont know what I am doing, I will try not to do it. lol.

---

### Post by MangasColoradas on 2007-12-22
I have now installed from the alternate disk and everything was seeming fine and then I got the 'black screen' again---just the mouse cursor shows.

After much rebooting I got in with a normal screen but my keyboard settings were lost, this has happened before. 

Why is it happening?

Please help, going mad here! :confused:

---

### Post by philinux on 2007-12-22
See the link below for known bugs.

also install and run startupmanager from synaptic see if that helps.

---

### Post by MangasColoradas on 2007-12-22
I installed the startup manager but I cant see it helping as I get the black screen after login.

Nothing in the bugs section.

Its the ATI restricted driver and/or xgl, I think thats causing it.

I always lose the keyboard settings too, when I finally get in with no black screen.

I am now running with all Compiz purged and no XGL, I am using the restricted driver but it doesnt speed things up.

Is there an older version of the restricted driver I can try anywhere?

Or, how can I get Envy for the ATI driver as its not in synaptic?

---

### Post by philinux on 2007-12-22
ENVY

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by MangasColoradas on 2007-12-22
Thanks Phil, Envy hasnt fixed anything either, lol

---

### Post by MangasColoradas on 2007-12-22
Another fresh install and it seems that the fglrx driver isnt being loaded like it should, I keep getting the vesa driver.

I thought this might fix it but NO.
> 
 A possible problem with fglrx.ko conflicts

It's necessary, because sometimes this file is written by other packages, and so there's no 3D acceleration. Check that the file /lib/modules/$(uname -r)/misc/fglrx.ko has been created.

Create the following folder

sudo mkdir /lib/modules/$(uname -r)/volatile

Note: the volatile directory might already exist at this stage then simply continue with the next step.

Create a symbolic link

sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko


NOTE : On my Gutsy install, after a reboot this link was always removed automatically leaving me without an fglrx module loaded, and thus no ATI rendering. There have been several ways of getting around this suggested here, and here is the one that worked for me:

sudo gedit /etc/init.d/ati-module-fix

And put this in it:

#!/bin/sh -e

# For loading ATI display drivers

ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
exit 0


Make it executable

sudo chmod ugo+x /etc/init.d/ati-module-fix

Now, make this run before gdm

To check the gdm sequence number,

ls /etc/rc2.d/

The value for [seqno] in the section below should be the gdm sequence number -1.

sudo update-rc.d ati-module-fix defaults [seqno]


I am getting these problems again because I happened to change the refresh rate on the monitor in 'screens and graphics',

Maybe its a monitor problem?

I have a Flatron 1919s. It only works as a plug and play as there is no option for it under 'screens and graphics'.

---

### Post by MangasColoradas on 2007-12-22
It seems that there has been issues with the ATI drivers for YEARS with the 9800pro amongst others.

Why? Surely there must be a decent fix somewhere? I have tried manually installing the latest ATI driver, tried Envy too.

Now, Ubuntu wont even install, lol. It's not my week. :mad:

---

### Post by StGeorge on 2007-12-22
forget installing anything but 6.06.
i cannot beleive that this has been going on 4 over a year.

---

### Post by MangasColoradas on 2007-12-22
Even when I get it running OK, I have no direct rendering and also no changes are ever saved to the xorg.conf (or whatever it is), so it keeps going back to the vesa driver.

I have read not to install the restricted driver at all and to remove the restricted drivers manager amongst other things.

How would I set up 6.06 please St.George?

Use the restricted driver? Install xserver-xgl?

ever tried Open-Suse?

---

### Post by torgrot on 2007-12-22
Did you try reconfiguring your x-server

```

dpkg-reconfigure xserver-xorg

```

---

### Post by MangasColoradas on 2007-12-22
Hi torgot, I am not sure if I have along the way when following one of the "how-to's" but I have just re-installed a fresh Gutsy AGAIN, lol......so I am just leaving any proprietary drivers out of the equation for now.

It's not like I play games anyway, I just wanted to get it working properly and once I started it just opened a can of worms, ending in a black screen.

I have actually learned stuff along the way and I still love Ubuntu, I just cant take anymore fiddling about!

I am leaving it alone now. :)

I have also just made a backup of 'xorg.conf', I assume I did it right by adding .bak...and saving in 'X11'?

---

### Post by torgrot on 2007-12-22
That works fine.  I tried to get the latest and greatest drivers for my 9800, but it just broke every time there was a kernel update.  Envy simply made a mess of my system, and it took a while to get it back.  Now I just use the restricted driver and XGL I have compiz and Emerald and while it may not be the most cutting edge desktop it works and it is reliable.

torgrot

---

### Post by MangasColoradas on 2007-12-22
I had mine running like that too, with only one fault-the 'deleted items folder' would have a thin square line appear before the folder did. I could do that again I am sure, but I am afraid to touch anything right now! :)

---

### Post by MangasColoradas on 2007-12-22
Oh yes, the reason I am best leaving it like this is because the restricted driver forces the refresh rate of my monitor to 75hz which isnt recommended for my monitor, I think.

I could put up with the waste-bin fault otherwise and use the restricted driver. Maybe the monitor could take it, I am not sure. Its a Flatron 1919s.

---

