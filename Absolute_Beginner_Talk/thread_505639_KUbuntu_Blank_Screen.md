---
title: "K/Ubuntu Blank Screen"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by RightFoot on 2007-07-20
So, I've decided to run a server on my laptop, and since my installed OS is Vista, I decided *MAYBE* I should get a Linux distro ;P. Anyway, I decided to try Ubuntu out since I've been told it's relativly new-linux-user friendly.

Anyway, here's the problem I'm having:

I boot up K/Ubuntu (I've tried both) v7.4.0 and they'll start to boot up, (giving me some errors a long the way..) which eventually leads to a blank screen where I can do nothing.

I've tried editing the 'Start Ubuntu', by removing splash and  adding break=bottom to the boot, which allows me to edit xorg.conf, there I tried changing the Driver to 'vesa' instead of 'nv'. I'm not quite sure what to do after that though, I rebooted, and nothing happened, then re-edited and tried to reboot from console which.. um, didn't work.


Uhh, so, I've tried to be as 'technical' as I could, if you'd like me to try and write down the errors I get while trying to run the Live CD, I'll try :D!


Thanks for the help? in advanced!



PS: Here are my specs :O.

AMD Mobile Turion 64 X2 2.2Ghz
2GB RAM
Nvidia Geforce Go 7600

---

### Post by ReaderRat on 2007-07-20
Have you tried this?:

```
sudo dpkg-reconfigure xserver-xorg
```

It will let you set the resolution & refresh rate.

I had a wrong refresh rate and had the same problem.

Go to your monitor's manual for the info to input.

---

### Post by adamklempner on 2007-07-20
Have you tried booting in safe mode (or what ever they call it) on the live cd?  I have to do that with my desktop, and then once booted, install the real nvidia driver.  Once I do that, I don't get stuck at the blank screen.

But yeah, writing down those errors and posting them here will probably help the most. :cool:

---

### Post by RightFoot on 2007-07-20
> **adamklempner said:**
> Have you tried booting in safe mode (or what ever they call it) on the live cd?  I have to do that with my desktop, and then once booted, install the real nvidia driver.  Once I do that, I don't get stuck at the blank screen.

But yeah, writing down those errors and posting them here will probably help the most. :cool:

Yeah, I have tried booting in safe mode on the live CD, it does the exact same thing. :(.

Also, to ReaderRat, like I said I'm on a laptop.. I'm not really sure if I saved any documentation on it. But I'll look or maybe the HP site will have it.

Anyway, I'll make a new post with the errors in a minute! Thanks for the responses guys!

---

### Post by RightFoot on 2007-07-20
Okay, so I wrote down the errors I got when trying to boot up, I get the same errors on safe mode and on normal.

First, I get a failed to allocate mem resource. While searching for how to fix my current problem I read that this is normal, so I'm guessing that's not the problem? Unless I was misinformed.

Next, I get several errors about a firmware helper while trying to 'Load hardware drivers:', these go by pretty fast on the screen, but what I got out of it was that they were in /var/lib/firmware/, 'Error Microcode', and 'bcm43xx'. I'm not really sure what any of that means.. but okay.

Finally, I have several files missing when loading the Network Interfaces, they're located in /var/lib/acpi-support/. There are about five or six, I didn't write down the names though.

And that's it.. sometimes it freezes when trying to boot up.. but most of the time it gets by and just sits on a blank screen. I've actually left it on overnight, only to wake up to the same screen :P. So I'm pretty sure it's not loading and I'm just being impatient or anything.

Thanks for any help you can give me and I apologize for the bump!

---

### Post by RightFoot on 2007-07-21
No answers..? 

](*,)

Normally I only go to forums and ask for help in a last resort, finding the solution has normally been relatively easy for me just by searching Google, but I am, to say the least, stumped on this one. I sincerely apologize about the constant bumps, but I'm sure someone has to had have an issue similar to mine?

I'd appreciate any help at all! Thank you!

---

### Post by Krosis on 2007-07-21
> **RightFoot said:**
> Okay, so I wrote down the errors I got when trying to boot up, I get the same errors on safe mode and on normal.

First, I get a failed to allocate mem resource. While searching for how to fix my current problem I read that this is normal, so I'm guessing that's not the problem? Unless I was misinformed.

Next, I get several errors about a firmware helper while trying to 'Load hardware drivers:', these go by pretty fast on the screen, but what I got out of it was that they were in /var/lib/firmware/, 'Error Microcode', and 'bcm43xx'. I'm not really sure what any of that means.. but okay.

Finally, I have several files missing when loading the Network Interfaces, they're located in /var/lib/acpi-support/. There are about five or six, I didn't write down the names though.

And that's it.. sometimes it freezes when trying to boot up.. but most of the time it gets by and just sits on a blank screen. I've actually left it on overnight, only to wake up to the same screen :P. So I'm pretty sure it's not loading and I'm just being impatient or anything.

Thanks for any help you can give me and I apologize for the bump!

I believe the bcm43xx error is caused by your Wireless Card.  I too had this problem on my Laptop.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

That link should help you with that error.

---

### Post by RightFoot on 2007-07-21
> **Krosis said:**
> I believe the bcm43xx error is caused by your Wireless Card.  I too had this problem on my Laptop.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

That link should help you with that error.

But would this cause the blank screen?

..Or is that error just telling me that it can't recognize my wifi card and I need to install drivers for it?

Or both |: ?

---

### Post by ReaderRat on 2007-07-21
Do you have a switch on the front (or side) of the laptop that turns OFF wireless?  Just a shot in the dark, but you might try to install with the wireless OFF.

Are you sure you got good burns on your CDs? Did you use good (NOT no-name) media to burn on?

---

### Post by davidjmayo on 2007-07-21
see if this helps you
[http://ubuntuforums.org/showthread.php?t=474769](http://ubuntuforums.org/showthread.php?t=474769)

Read all 4 pages as it may cover some of what you tried already. I don't have this kit but the bcm43xx error reminded me I saw this before. I searched the forum for bcm43 and this seems yorr best shot. If not feel free to search the forum again and you may find something better

---

### Post by RightFoot on 2007-07-21
> **ReaderRat said:**
> Do you have a switch on the front (or side) of the laptop that turns OFF wireless?  Just a shot in the dark, but you might try to install with the wireless OFF.

Are you sure you got good burns on your CD's? Did you use good (NOT no-name) media to burn on?

Well, I did have the wireless switch on :P! I'll try again with it off, also, I used FUJIFILM CD's.. I'm guessing that was the wrong choice? I have some completely blank no name CD's to burn on. Maybe that will help?

Also, for your Monitor Refresh Rate idea, I found mine was 60Hz, but since I can't get into the Live CD, and using break=bottom, I'm stuck with (initramfs)? Which.. for some reason won't let me use many commands.. so i was unable to 'sudo dkpg-reconfigure xserver-xorg'.

I guess I'll try to re-burn the .iso to a no-name CD. Then post back if I still have the problem. 

Thanks for the help so far guys :D!

---

### Post by Krosis on 2007-07-21
Have you tried using the alternate CD at all?  Installs in text instead of graphical.  Did you check for CD errors?  Did you check the [md5Sum]("https://help.ubuntu.com/community/HowToMD5SUM")?

---

### Post by RightFoot on 2007-07-21
> **Krosis said:**
> Have you tried using the alternate CD at all?  Installs in text instead of graphical.  Did you check for CD errors?  Did you check the [md5Sum]("https://help.ubuntu.com/community/HowToMD5SUM")?

No, I haven't tried the alternate CD, although I've read many people suggesting it. Yes, I did check the CD for errors, and no I didn't check the MD5SUM.

Well, I'm redownloading the .iso as we speak to burn on a no-name CD.. hopefully that will just magically fix everything :P. If not, I'll try the alternate CD, since this is about the fifth person I've heard recommending it.

---

### Post by Krosis on 2007-07-21
> **RightFoot said:**
> No, I haven't tried the alternate CD, although I've read many people suggesting it. Yes, I did check the CD for errors, and no I didn't check the MD5SUM.

Well, I'm redownloading the .iso as we speak to burn on a no-name CD.. hopefully that will just magically fix everything :P. If not, I'll try the alternate CD, since this is about the fifth person I've heard recommending it.

Yeah, sounds like the right way to go.  Just make sure to check the md5Sum when your download is finished.  I had to you the Alternate CD with my Laptop, so that might be the fix for you too.

Hope you get everything worked out.

---

### Post by RightFoot on 2007-07-21
> **Krosis said:**
> Yeah, sounds like the right way to go.  Just make sure to check the md5Sum when your download is finished.  I had to you the Alternate CD with my Laptop, so that might be the fix for you too.

Hope you get everything worked out.


Yeah, I downloaded that tool to check MD5sums on Windows :). Thank you!

---

### Post by davidjmayo on 2007-07-21
please look back to page 1 of your thread.. I suspect you missed my post at the bottom of the page. The more I read it sounds the same problem.  If it is irrelevant apologies in advance.

---

