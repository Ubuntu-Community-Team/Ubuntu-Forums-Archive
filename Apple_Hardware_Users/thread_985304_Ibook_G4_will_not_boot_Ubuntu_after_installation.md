---
title: "Ibook G4 will not boot Ubuntu after installation"
date: 2008-11-17
forum: Apple Hardware Users
---

### Post by tygoerlitz on 2008-11-17
Hi I have a Ibook G4 and recently I upgraded it to leopard. When installing leopard I partitioned the hd and allowed 10g of free space for Ubuntu. installed ubuntu and everything went fine there, except when i restart the comp and try and boot into ubuntu everything loads, I get the white screen then that goes away to a blank screen and just sits there. Need help just want to get Ubuntu up and running, help is greatly appreciated.

Ibook G4 1g ram 40g hd
Ubuntu 8.10 intrepid ppc version

---

### Post by stream303 on 2008-11-17
When you get to the second stage boot: prompt, hit TAB to stop the countdown.  Then issue

```
Linux video=ofonly nosplash
```

and see how far that gets you.  It is likely you'll need to create a custom xorg.conf file with the drivers, video freqs, etc for your G4 ibook.

Be sure to see these two faqs to get started:

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
and
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

---

### Post by tygoerlitz on 2008-11-17
Hey that worked out great ubuntu fired right up thank you very much. One question, what does the video=ofonly nosplash do and is there something that I can do to not have to do that everytime i boot?

---

### Post by stream303 on 2008-11-17
Wow!  Glad to hear you didn't have to edit your xorg.conf as well.  For reference, which G4 ibook do you have?

[http://www.everymac.com/systems/apple/ibook/index-ibook.html](http://www.everymac.com/systems/apple/ibook/index-ibook.html)

What those are are additional kernel parameters that you temporarily add at boot time to give additional instructions to get around hardware issues, such as no splash screen, which has been known to cause problems (there is a way to fix it if you really want to see a graphic rather than boot messages).

When you find a combo that works, you place those additional parameters in both of the **"append ="** lines in /etc/yaboot.conf, and then make the system aware of the change (important).

Edit your /etc/yaboot.conf as root:

```
gksudo gedit /etc/yaboot.conf
or for text mode
sudo nano /etc/yaboot.conf
```

(if you use nano, CTRL-O to save, CTRL-X to exit)

Here is the relevant section of *my* yaboot.conf with it's own special append= lines:

```
image=/boot/vmlinux
	label=Linux
	read-only
	initrd=/boot/initrd.img
	append="quiet nosplash"

image=/boot/vmlinux.old
	label=old
	read-only
	initrd=/boot/initrd.img.old
	append="quiet nosplash"
```

Now you have to make the system aware of the changes you made:

```
sudo ybin -v
or fully-qualified:  sudo ybin -v -C /etc/yaboot.conf
```

Now when you reboot, you won't have to be bothered with the parameters any more.

It would be interesting to see if you only need nosplash, and not video=ofonly as well.  Try passing just "nosplash" at the second stage boot: prompt and see if everything still comes up.

Also check to see if you are really at native resolution, ie if your monitor is spec'ed at 1024x768 for example, and you aren't currently running at 800x600 - as an example.

Let us know!

---

### Post by tygoerlitz on 2008-11-17
Thanks for the reply, but im a bit confused are these things that need to be done in a terminal when ubuntu is running or on the boot screen. Also I noticed you said something about a graphical boot loader, that would be really nice to have, could you help me out with that? I am relatively new  to Ubuntu. As far as my screen goes how is that checked to see what im running at. Computer wise its a G4 1.33ghz 1g ram 40g hd

---

### Post by stream303 on 2008-11-18
Well, let's fix your yaboot.conf first.

1) Boot up, and when you get to the second stage of the boot: prompt, hit TAB to stop the countdown.  Now, like you did before, enter

```
Linux video=ofonly nosplash
```

Now your machine should be up and running, but we want to automate this process.

2. Go to Applications > Accessories > Terminal to bring up a terminal.

3. In the terminal, enter

```
gksudo gedit /etc/yaboot.conf
```

This will bring up the gedit editor with temporary root priveleges, which you need to edit and save the yaboot.conf changes you are about to make.

4. Add
```
video=ofonly nosplash
```
to both of the **append=** lines.

5. Save the file, and exit out of Gedit.

6. You should now still be in the terminal.  We need to let the bootloader actually know about those changes.  So at the terminal prompt again, enter

```
sudo ybin -v
```

7. Exit the terminal by typing *exit* or just closing the terminal window.

8. Now, you can reboot, and you shouldn't be bothered with having to stop the boot process anymore to put those special boot time parameters in anymore.

---

### Post by tygoerlitz on 2008-11-18
Hey ya I got that working great thanks a bunch. Can I configure yabot to be a graphical bootloader? Could someone help me get my airport working, I have searched around and have tried various things but they don't seem to work

---

### Post by stream303 on 2008-11-18
1) If you want a graphical splash screen, first you'll have to change "nosplash" to "splash" from your yaboot.conf, and once again do a *sudo ybin -v*

2) Then, you'll have to edit /etc/usplash.conf as root with the video parameters of your monitor, ie for 1024x768 add or change these lines:

```
xres=1024
yres=768
```

3) Then, you'll have to make initram aware of it:

```
sudo update-initramfs -u
```

Note that this is covered in this faq:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Although it is listed as "LCD Brightness and Contrast" - this has been known to restore brightness and contrast controls *for some*.  Unfortunately, it doesn't appear in the contents listing on that faq.

And, there is the chance that it could still look ugly, but try it if you want.

---

### Post by tygoerlitz on 2008-11-19
Hey thanks for all you help. I did what you said, but nothing happened, no big deal thanks so much for all your help! Now on to my wireless issue.

---

### Post by stream303 on 2008-11-22
I forgot to ask something.  When I had my G4 iBook, I had severe problems with Network Manager eating up 100% of the cpu from Gutsy forwards.  I had to take evasive measures to prevent it from eating all those cycles. :)  --but only my G4 iBook, everything else was fine.

This probably isn't the case with Intrepid now, but it would be wise to check with top or some other resource manager.

(First thing I do after an install is run top or htop)

---

### Post by tealio on 2008-11-22
I was able to get my Airport Extreme card working very easily... activate the universe and multiverse repositories in */etc/apt/sources.list*, or it can be done through the GUI package manager... either way, once that's done find and install a package called *b43-fwcutter*.  When i installed this package, it automatically downloaded and installed the proper firmware.

Next, to get connected to your wireless access point, edit */etc/network/interfaces*. Mine looks like this:

```

# The Airport Extreme Card

iface eth0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid JKT

auto eth0

```

That is a pretty basic static IP setup.  Enter *man interfaces* in a terminal for more info on setting that up.  When you've made changes in */etc/interfaces* you need to restart the interface.  To do this enter *ifdown eth0 && ifup eth0* in a terminal window.

All terminal commands should be entered in a root shell, or using *sudo*.

Good Luck!

---

### Post by tygoerlitz on 2008-11-23
Hey thanks for the help but I cant even install the b43-fwcutter, when I try and install it from the package manager, it tells me to insert the cd, when I insert the cd it still doesnt work.. I need some help please!

---

### Post by ElectricBlue on 2008-12-18
This has proven successful for me as well. I needed to add video=ofonly to my yaboot.conf

---

