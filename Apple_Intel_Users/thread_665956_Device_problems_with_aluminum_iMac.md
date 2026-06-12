---
title: "Device problems with aluminum iMac"
date: 2008-01-12
forum: Apple Intel Users
---

### Post by macuser2000 on 2008-01-12
I have some device problems when I install ubuntu 7.10 on my 20-inch  aluminum imac with a ATI Radeon 2600 Pro graphics. I have no sound, the airport wireless card is not working, and the graphics driver doesn't allow me to turn on compiz. Can someone give me simple, straight-forward instructions to help me fix that hardware.

---

### Post by alphaleader on 2008-01-12
I have the 24" iMac aluminum, and I am not having problems with that, but I did have problems very similar with my iBook.  I found out, though I don't believe it, and this is directly from broadcom (the manufacturers of airport chips) that AirPort Cards can only operate under Mac OS X because the chips have the capability of running at "reserved" frequencies.  Mac OS X is the only OS that blocks these frequencies. 
If found it odd, but can't find any solutions over the past year and a half or so.

Sound weird, I know, but that is what Broadcom told me.

Sorry

---

### Post by handy on 2008-01-13
I used [***_this one_***]("http://ubuntuforums.org/showpost.php?p=3697702&postcount=5") for the sound on my 24" iMac 2007 model.

For the ATi proprietary drivers I used [***_Envy_***]("http://www.albertomilone.com/nvidia_scripts1.html"), & it worked perfectly for me.

Sorry I can't help you with the wireless, as I don't use it.

---

### Post by cyberdork33 on 2008-01-13
please check the FAQ for the sound issue.

Your airport card is a broadcom card, and ndiswrapper is the solution for that.

Your video card is only supported by later ATI drivers (not by the ones in the repos still), and thus you need the newer ones from ATI. Envy can accomplish this.

There are several, several threads here with "aluminum" and "imac" in the title that will likely yield good information about your issues.

---

### Post by macuser2000 on 2008-01-13
I have a Mac OS X Leopard DVD. Can I use the Windows Bootcamp driver for the airport in ubuntu using ndiswrapper? If so, can someone post instructions on how to do it?

---

### Post by macuser2000 on 2008-01-13
Thank you Handy! I have my sound and graphics card working perfectly :lolflag:

I just have the airport to fix.

---

### Post by cyberdork33 on 2008-01-13
> **macuser2000 said:**
> Thank you Handy! I have my sound and graphics card working perfectly :lolflag:

I just have the airport to fix.
The Broadcom how-to in the FAQ should work for you. It shows you how to get a Dell driver that will work.

---

### Post by macuser2000 on 2008-01-13
Which FAQ?

---

### Post by handy on 2008-01-13
> **macuser2000 said:**
> Which FAQ?

***_[http://ubuntuforums.org/showthread.php?t=493393](http://ubuntuforums.org/showthread.php?t=493393)_***

---

### Post by macuser2000 on 2008-01-14
**[SIZE="5"]Thank you. Everything's working[/SIZE]**:lolflag:

---

### Post by macuser2000 on 2008-01-14
I have another problem. The display can go up to a resolution of 1680x1050, but I can only put it up to 1280x1024. Can someone help me? :(

---

### Post by cyberdork33 on 2008-01-14
> **macuser2000 said:**
> I have another problem. The display can go up to a resolution of 1680x1050, but I can only put it up to 1280x1024. Can someone help me? :(

Have you installed the proprietary drivers?

---

### Post by macuser2000 on 2008-01-15
yes, using Envy

---

### Post by cyberdork33 on 2008-01-15
I am not sure, I am getting similar issues on another machine I have with the latest ATI drivers. I tried a lot to get it working, but I kept having issues. You might tried installing the 7.11 version instead of the 7.12 (which Envy uses).

---

### Post by macuser2000 on 2008-01-18
How do I get the 7.11 drivers?

---

### Post by cyberdork33 on 2008-01-20
> **macuser2000 said:**
> How do I get the 7.11 drivers?
[http://ati.amd.com/support/drivers/linux64/radeonprevious-linux64.html](http://ati.amd.com/support/drivers/linux64/radeonprevious-linux64.html)

---

### Post by macuser2000 on 2008-01-20
I found a new driver released a few days ago, I try to install it, but it's a .run file, and I don't know how to install this type of file. Here's the link to the latest driver
[http://ati.amd.com/support/drivers/linux/previous/linux-rf-cat81.html](http://ati.amd.com/support/drivers/linux/previous/linux-rf-cat81.html)

---

### Post by cyberdork33 on 2008-01-20
> **macuser2000 said:**
> I found a new driver released a few days ago, I try to install it, but it's a .run file, and I don't know how to install this type of file. Here's the link to the latest driver
[http://ati.amd.com/support/drivers/linux/previous/linux-rf-cat81.html](http://ati.amd.com/support/drivers/linux/previous/linux-rf-cat81.html)It is in the same format as all the other fglrx drivers. It is a shell script.

Here is a how to:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)

---

### Post by handy on 2008-01-20
@***macuser***: You are required to uninstall the previous driver installed via Envy.  

The following is presented very clearly on the Envy site.:

[I]**WARNING:** you will have to remove the driver you installed with Envy before upgrading Debian or Ubuntu to a newer release (e.g. upgrading Ubuntu Edgy to Ubuntu Feisty or Debian Etch to Debian Lenny).

You will have to type the following command:

**sudo envy --uninstall-all**[/I]

---

### Post by macuser2000 on 2008-01-21
The wireless driver is working, but not after I start ubuntu, Every time I start I have to load ndiswrapper into the kernal by enetring this command in terminal

```
sudo modprobe ndiswrapper
```

Can someone tell how to load ndiswrapper automatically every time ubuntu start up.

---

### Post by cyberdork33 on 2008-01-21
> **macuser2000 said:**
> Can someone tell how to load ndiswrapper automatically every time ubuntu start up.

add it to /etc/modules

---

### Post by macuser2000 on 2008-01-23
Thanks!

---

### Post by macuser2000 on 2008-01-24
I got 1680x1050 resolution! Here's what I did. With the lastest ATI driver installed, I did this.

I went into the screens and Graphics control panal, I click on the model list. When the pop-up came up, I selected Apple from the Manufacturer list and under model, I selected "Cinema display 20 lcd" and I check the box "Widescreen Monitor" I tested it. and it works! It even works every time that I start ubuntu!

---

### Post by cyberdork33 on 2008-01-24
> **macuser2000 said:**
> I got 1680x1050 resolution! Here's what I did. With the lastest ATI driver installed, I did this.

I went into the screens and Graphics control panal, I click on the model list. When the pop-up came up, I selected Apple from the Manufacturer list and under model, I selected "Cinema display 20 lcd" and I check the box "Widescreen Monitor" I tested it. and it works! It even works every time that I start ubuntu!Strange that you had trouble...

Be weary of the Screens and Graphics control panel. For most it ends up making things worse! Glad it worked for you though!

---

### Post by macuser2000 on 2008-01-29
Is there a sound driver for the imac that supports headphones?

---

