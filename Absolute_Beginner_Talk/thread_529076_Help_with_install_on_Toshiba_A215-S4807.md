---
title: "Help with install on Toshiba A215-S4807"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by kjg1981 on 2007-08-18
I just bought the toshiba satellite A215-S4807.

I'm still having problems getting 7.04 running on my new machine though. I had to install it with the alternate cd in text mode then update my x driver using the instruction giving in the sticky.   Now unbuntu goes through all the loading process but instead of loading the desktop i just get a black screen. I think I might have selected the wrong resolution during the install.... Any help on how i can fix this would be greatly appreciated!

---

### Post by overdrank on 2007-08-18
> **kjg1981 said:**
> I just bought the toshiba satellite A215-S4807.

I'm still having problems getting 7.04 running on my new machine though. I had to install it with the alternate cd in text mode then update my x driver using the instruction giving in the sticky.   Now unbuntu goes through all the loading process but instead of loading the desktop i just get a black screen. I think I might have selected the wrong resolution during the install.... Any help on how i can fix this would be greatly appreciated!

Hi and the specs on the web say that it has a ATI x1200  graphics card, so if you have no video I would suggest that once you reach the black screen use the ctrl, alt, F1 keys all at the same time and this will bring you to the terminal where you login  and then use this command 
```
sudo dpkg-reconfigure xserver-xorg
```
and choose the vesa driver and then if you don't know the answer to the other questions leave them as the default answer given. Hopefully this will get you too the desktop.

---

### Post by kjg1981 on 2007-08-19
i tried ctrl alt F1 at the black screen but nothing happened.   I had to manually reboot.   I tried recovery mode which brought me to a command prompt.  I then used the code you gave me and went through it all but I still got the black screen.  I still think it might have something to do with my resolution.

---

### Post by kjg1981 on 2007-08-19
Ok i made a little progress.  I used the sudo dpkg-reconfigure xserver-xorg and selected ATI for the driver instead of Vesa.  I selected all the other default options and when i restarted.  Ubuntu loaded but gave me the blue screen saying the xdriver could not be found then brought me to a command prompt.  This seems better than the black screen.   I went back  and reconfigured the xserver-xorg file again and changed the horiz sync to 36-52 and vert to 36-60 but still the blue error message.  

Has anyone had this problem??

---

### Post by warped6 on 2007-08-20
I just picked up the same laptop and did finally get 7.04 installed and running. The wireless card won't work (they are working on the drivers. They say "soonish".) and the webcam won't work either.

As far as the video goes, there are 2 threads about installing ATI video cards. I followed both of these and got it up and running. The first is about installing the restricted drivers. The second is about installing XGL. I don't have the links handy (I'm at work) but if you search for installing the restricted drivers you should find the link. I would do that first. Then once that is up and running you can try installing XGL and get all of the eye candy working that doesn't work with the ATI drivers.

I'll check in later and see how you are doing.
Mike

---

### Post by kjg1981 on 2007-08-20
Thanks for your help.  I looked quickly and couldn't find those threads.   I already did the updates that are in the sticky.  I'm not sure what else to do.  Maybe once I will re install the whole thing and then do exactly  what you did....

---

### Post by warped6 on 2007-08-20
Alrighty here is what I did. It took me about a week to get this stable only because I'm kind of a n00b with Ubuntu. Only reinstalled it about 5 or 6 times before i got it right.

1. Install off the alternate CD. When it asks about valid screen sizes, I made sure that the 1280X800 was marked. It will choke when it tries to start X. Just press enter, twice I think.

2. You should end up at a black screen with a prompt saying something about login. Enter your user id and password.

3. Follow the directions under 7.04 Feisty [ link here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). It's 2 lines. Do them 1 at a time.

4. When this is done I rebooted (no idea if needed but seemed easiest)
```
sudo shutdown now -r
```

With any luck this should then bring up a nice graphically interface. Yeah! This is when you do the "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver" bit. 

If this doesn't work then follow the directions under 6.10 Edgy and that WILL install the drivers. 

Let me know if you get this much working and then we'll work on the next step. For now DON'T install Beryl. That is the second step.

EDIT: Ok I just read the STICKY Mike wrote [link here]("http://ubuntuforums.org/showthread.php?t=414194"). I wish I had seen those earlier. Anyway I would follow those. They are basically the same only better.

---

### Post by itsjustabox on 2007-08-23
I think I have finally figured it out. when I first install, I edited xorg.conf to add HorizSync and VertRefresh and to change Option. I got the blank screen like you did after update the graphic driver. So I went back and change it back to the default:

Section "Monitor"
     Id     "Generic monitor"
     Op   "DPMS"
EndSection

Section "Monitor"
    ...ATI blah blah
    ...I did not edit these stuff
EndSection

And it works well

---

### Post by stchman on 2007-08-23
> **kjg1981 said:**
> I just bought the toshiba satellite A215-S4807.

I'm still having problems getting 7.04 running on my new machine though. I had to install it with the alternate cd in text mode then update my x driver using the instruction giving in the sticky.   Now unbuntu goes through all the loading process but instead of loading the desktop i just get a black screen. I think I might have selected the wrong resolution during the install.... Any help on how i can fix this would be greatly appreciated!

On the LiveCD did you try the safe graphics mode?

---

### Post by kjg1981 on 2007-08-28
Ok I just reinstalled Ubuntu with the alternate cd in text mode.  when asked for screen sizes i check 1200X800 and left the rest as default.  When I was finished i got the x driver error.  At the command prompt I ran through the update iinstructions as explained in the sticky for ati graphics cards.  Now i get the black screen of death and no error messages!!!

Any ideas.  did you guys do anything different?

---

### Post by kjg1981 on 2007-09-01
I finally gave up and installed 6.10.  Looks the same.  Not sure what the differences are but I'll deal with it for now until the next version comes out.  Now I just need to get the wireless working.

---

### Post by shponglespore on 2007-12-28
> **kjg1981 said:**
> i tried ctrl alt F1 at the black screen but nothing happened.   I had to manually reboot.   I tried recovery mode which brought me to a command prompt.  I then used the code you gave me and went through it all but I still got the black screen.  I still think it might have something to do with my resolution.

I've figured out why Ctrl+Alt+F1 doesn't work.  For some reason when the kernel splash screen is enabled (which it is by default), it breaks text mode until the machine is rebooted.  The fix is to remove "splash" from the kernel parameters in grub.  You can try it out by pressing "e" in grub to edit the kernel command line.

For a permanent fix, you need to edit /boot/grub/menu.lst.  You'll find a line that starts with "#kopt=".  Remove the word "splash" from this line, then run update-grub.  The next time you reboot, text mode should work.

I apologize if I got any details wrong; I have my machine booted into Windows at the moment so I can't double-check everything.  Finally, here are some keywords to help Google find this post: toshiba satellite a215 ubuntu linux text mode

---

### Post by warped6 on 2008-02-17
Well after not being real happy with the 64 bit install, I decided to do a scratch install of the 32 bit Gutsy.  After that things have worked much better. So what didn't work or was flakey in 64 bit? VPN connections, wireless, IBM 5250 emulation, flash in Firefox those were the big things.

But now everything is working! Yeah! I would even recommend this laptop now. Before I was, "well it's an ok box".

---

