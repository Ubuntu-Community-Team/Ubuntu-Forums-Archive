---
title: "Scrolling is laggy on iBook G4"
date: 2011-02-20
forum: Apple Hardware Users
---

### Post by ownaginatious on 2011-02-20
So I recently installed Ubuntu 10.04 on my 800 MHz iBook G4 with a Radeon 9200.

After messing around with the xorg file, I was able to get compiz working well - but now the only problem I'm having is that scrolling in any window is ridiculously choppy - comparable to scrolling a window of a computer over remote desktop.

Anyone know how to get rid of this issue?

Thanks..

---

### Post by FoxEWolf on 2011-02-21
I am pretty sure that this is being caused due to the limited Graphics Memory available in that iBook G4. The Raedon 9200 chip on that model has 32MB of memory. Considering that you may be running Gnome desktop items, it may be just too much for that 32MB. Now I am not going to say that I know *that* is the cause for the slow scrolling, because I have not tried to install Ubuntu on my iBook G4. 
 
What are the specs on that iBook G4? (I already gathered the CPU speed)
 
What I can recommend to try is to (if possible): Reload the iBook G4 with a less graphic and resource environment like Xubuntu (XFCE Desktop environment) If it can run smooth on my HP Pavillion ze1230 (256MB Ram, 1.3GHz processor), then I am sure it will run smoother on your iBook.
 
Let me know about the specs and keep me updated on what you carry out with the iBook.

---

### Post by rsavage on 2011-02-21
I see from your other post that you've already done the most important thing which was to disable KMS (putting radeon.modeset=0 in yaboot.conf).  You don't need to do a lot to your xorg.conf as most of the default options are good.  My iBook is newer, but I have the same video card.  All I have in my xorg.conf is:

[FONT="Courier New"]Section "Device"
   Identifier   "Radeon9200"
   Driver       "radeon"
   BusID        "PCI:0:16:0"  
   Option       "GARTSize"                   "16"   
   Option       "AccelMethod"                "EXA"  
EndSection[/FONT]

Setting "AccelMethod" to EXA will sort out your choppy scrolling.  I set "GARTSize" to 16 because the default 8 causes silly colours. 

If you want to experiment with your xorg.conf settings then I suggest you follow the manual [http://manpages.ubuntu.com/manpages/lucid/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/radeon.4.html) because most of what you see written about xorg.conf on forums is rubbish.  I've experimented with most (if not all) of what is suggested and you never see vast improvements in glxgears.

Having said that, you can see biggish improvements by reducing the number of colours.  I don't do this, but you can give it a go:

[FONT="Courier New"]Section "Screen"
   Identifier   "StandardScreen"
   Device      "Radeon9200"
   DefaultDepth   16
EndSection[/FONT]

Another thing that will speed things up is to turn on HyperZ.  This isn't done in xorg.conf, but in a ".drirc" file in your home folder.  Install Driconf from the software centre so that you can turn it on using the applet.

I'm happy with the performance of Ubuntu on my iBook, but as the previous poster suggested a more lightweight distribution maybe more suitable for your specs.  This thread seems to be missing the plug for MintPPC which I have yet to try!  I'm sure setting AccelMethod to EXA is all you need to do though.

---

### Post by rsavage on 2011-02-21
Just had a thought.  If you're playing with your graphics card then make sure that the fan module is loaded during boot so that your iBook doesn't over heat.

At a a terminal type:

[FONT="Courier New"]sudo gedit /etc/modules
[/FONT]
In the file that opens, add to the list

[FONT="Courier New"]therm_adt746x[/FONT]

You can also remove the duplicate line

[FONT="Courier New"]snd-powermac[/FONT]

---

