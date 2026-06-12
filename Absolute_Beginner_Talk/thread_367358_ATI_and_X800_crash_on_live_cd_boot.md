---
title: "ATI and X800 crash on live cd boot"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by dodgeygeezer on 2007-02-22
morning

my ATI X800 graphics card causes the live cd of edgy to die on boot - get a green line right across the screen. my mate who has the same card has the same thing too.

a semi fix is to boot with feisty (7.04?) and that works fine.

anyone know how I can boot to edgy and install it ? or should I just wait til april?

---

### Post by mahy on 2007-02-22
Try downloading the 'alternate' installation CD and install Ubuntu in text mode. It not that hard! :)

---

### Post by aberry5555 on 2007-02-22
You don't need to use the alternate cd as it doesn't help, though it is fairly easy to fix it, I had the same problem myself, the reason for it is that it's using the wrong graphics drivers. When the live cd starts up press F6 and delete the "quiet - splash" ending and type in "break=bottom" then boot with this. This will get rid of the ubuntu splash screen and stop half way through booting with a command prompt (ignore any error messages for now).

When you get to the prompt type in the following:

```
chroot /root nano /etc/X11/xorg.conf
```

this will let you edit your graphics configuration file. Using the arrow keys scroll down to the heading called "Device". Under this it should have "Driver" to the left and beside it the driver in inverted commas. The driver more than likely selected at the moment is "ATI".
For some reason this driver is always loaded for the X series cards and it never works. delete "ATI" and try either "radeon" (the drivers that are supposed to work) or, if those don't work "vesa" (the most basic graphics drivers. 

Once you've done this press ctrl+O then ctrl+X to save and exit the text editor.

This will bring you back to the command line, simply type:

```
exit
```

and, fingers crossed, ubuntu should boot.

P.s. for future reference could you tell me if the "radeon" driver works for your card as I've only ever tried "vesa" then moved on to ATI's proprietary drivers.

Cheers, good luck!

---

### Post by kubu79 on 2007-02-23
Very very good! A real genius at last!

Thank you ever so much...I followed exactly your suggestions and it worked...
but now at first reboot it says "unmounting temporary filesystems"...it seems freezed...is it normal?

What has to be done now?

---

### Post by Think first on 2007-02-25
Beutiful!!!
Tested this on the Mint Bianca live cd and it worked - have sought this solution quite a while now

---

### Post by jkeyes0 on 2007-02-25
I've got an ATi X800 as well, and had to use the method defined earlier to get the install working. I'll warn you all now, do not, and I repeat DO NOT install the ATi 8.34.8 driver. Use the 8.28 or 8.24, but do NOT use 8.34. The system will most likely lock up every time you attempt to shut down, log off, restart, or do anything that will impact the X server.

(experience pays off).

---

### Post by aberry5555 on 2007-02-27
jkeyes I might be wrong but it sounds like your xorg.conf file might not have been created properly, try running sudu ati-config and let ati organise your settings for you.

---

### Post by Brant on 2007-02-27
aberry5555: I also have the Radeon x800. Your fix worked for me as well. Just to answer your question, the "radeon" driver worked. 

Thanks for the info.

---

### Post by aberry5555 on 2007-02-28
Thanks, no problem :)

Good luck with Ubuntu!

---

### Post by astrolabio on 2007-02-28
Look i dont know if this can help but i report my experience.

I have an Acer laptop with a X700. I got problems too.

I solved them using the alternate cd to install in text mode and Envy to install the ati drivers. Now it works and i can play games like Enemy Territory and Savage.

---

### Post by VimesUK on 2007-02-28
Hello 

Thanks to aberry5555 for the solution to the installation problems with an ATI 800 card, like I have got. However when I use the break command I get a prompt with this in brackets...
(initramfs)
I then type in as suggested chroot /root nano /etc/X11/xorg.conf and yet it can't find (???) or do what I have typed - sorry I can't remember the exact message.

If it helps I downloaded this...

ubuntu-6.10-desktop-i386.iso

and I have an ATI XT850 PCI-E graphics card.

Any help as to what I'm doing wrong please...?

---

### Post by juanvm on 2007-02-28
> **VimesUK said:**
> Hello 

Thanks to aberry5555 for the solution to the installation problems with an ATI 800 card, like I have got. However when I use the break command I get a prompt with this in brackets...
(initramfs)
I then type in as suggested chroot /root nano /etc/X11/xorg.conf and yet it can't find (???) or do what I have typed - sorry I can't remember the exact message.

If it helps I downloaded this...

ubuntu-6.10-desktop-i386.iso

and I have an ATI XT850 PCI-E graphics card.

Any help as to what I'm doing wrong please...?
--------------------------------------------------------------------------------------
Go here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by VimesUK on 2007-02-28
Thanks for the link - I sorted that problem, it was a matter of the syntax being wrong. I missed out a space...!!!! However I did get it to boot with a Vesa driver and now I'll continue to scratch my head a bit more and try and get the ATI driver to install, oh hum :)

---

