---
title: "Ubuntu/Windows xp"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by jake550 on 2007-10-17
Hi, 

Today i complety reinstalled windows xp on a partion of my hard ddrive, i then installed ubuntu on the other partion for a dual boot. I then tested windows and it works fine i turn the computer on get the dual boot menu then boot into windows. 

The problem is when i try to boot into ubuntu the logo comes up the orange bar loads then the screen goes completly black and after 1 minute displays 'Mode Not Supported' I have tried installing my drivers for my g card when i was logged into windows also tried all different resolutions. Also i tried putting a live ubuntu cd in and booting from that and it works fine just my installed version doesnt!

 I am completely stuck any help would be great!!

Thanks!!

---

### Post by dward526 on 2007-10-17
Is there data on your ubuntu partition that you need to keep, or is it fresh?  Yes, thats right, I am talking about the less the graceful clean install.

---

### Post by jake550 on 2007-10-17
no data on it i need, was a completely fresh install for both windows and ubuntu

---

### Post by jake550 on 2007-10-17
bump

---

### Post by ghost_ryder35 on 2007-10-17
reinstall Ubuntu

---

### Post by jake550 on 2007-10-17
lol fair play ill try that

---

### Post by Jezprice on 2007-10-17
Cant help you sorry, only to say that you are not the only one with this issue, i have the exact same problem and i saw 3 posts besides mine yesterday reagrding the same issue!!

This is my post and i have seen no answers that help me so far. Maybe i do have to do a clean install though i dont see how this will be any different to my first install?

[http://ubuntuforums.org/showthread.php?t=577606](http://ubuntuforums.org/showthread.php?t=577606)

---

### Post by jake550 on 2007-10-17
yeah that sounds like the same sort of thing, i have never used ubuntu before today and im determined to get it working, did you reinstall ubuntu in the end im about to give it a try......

---

### Post by troy1of2 on 2007-10-17
Yeah, I'd have to go with what others have said here too. Especially if it was a clean install and you have nothing to lose, go ahead and try the install again. I've read that others have had similar issues but they try installing again and it goes fine.

---

### Post by LowSky on 2007-10-17
you could have made a bad Live CD, what speed did you burn the disk at. Its reccomended to burn the CD as slow as possible to avoid errors

---

### Post by morticiaskeeper on 2007-10-17
Do the reinstall, at least it won't take as long as XP!!

I had that happen to me twice over last weekend.  I physically unplugged the hard drive that had XP on it, hoping I could use my bios to select the boot sequence. Also that would reassure me that my dat would remain safe.

When I went to do a reinstall, I forgot about unplugging again, so now I have a gbug boot selector, but at least it defaults to Ubuntu.

Be careful about trying the KDE desktop.  I tried it once, then uninstalled it, prefering Fuzion on Gnome.  Now I have Kubuntu splash screens.

---

### Post by Jezprice on 2007-10-17
Okay i tried a re istall from scratch and get the same error, if i insert the live CD and do a cd error check none show up?

If i select to start with safe graphics from the list (from live cd menu) incase my graphics is the problem as some people mentioned this is the error message i get:

/bin/sh: cant access tty job control turned off
(initramfs) [34.370075] ata 3.00: failed to set xfermode (err_mash=0x44)

I dont think its a graphics thing though as i have never had a problem with htem before and the live cd works fine?

---

### Post by jake550 on 2007-10-17
thread hijack? lol joking, cheers for all your help guys ill give the install a go again and let you know what happens......

---

### Post by Jezprice on 2007-10-17
Sorry Jake!!!

Just to let you know i think the best idea yet is to re burn the CD and try agian, before you do a re install though run the check CD for errors on your cd and see if you get an error message, its worth trying.

I will wait to see what the results are from you before i try re burning.

---

### Post by jake550 on 2007-10-17
no worries, ok ill give it a go when i get home in a lil bit....and let you know

---

### Post by jake550 on 2007-10-17
i reinstalled it, i used the same cd and now it works fine, i only thing i did differently this time was making sure my graphics card and resolution were set large using windows before i started the ubuntu live cd goodluck with yours i would say i'd help more but you probably know more than me on linux anyway!!

---

### Post by bodhi.zazen on 2007-10-17
LOL

If you are having problems with your video it would help if you posted some additional information ...

video card ?

monitor ?

---

### Post by Flying caveman on 2007-10-17
remember this command or write it down > sudo dpkg-reconfigure xserver-xorg

it could save you alot of time next time

---

### Post by Niniel on 2007-10-17
> **jake550 said:**
> i reinstalled it, i used the same cd and now it works fine, i only thing i did differently this time was making sure my graphics card and resolution were set large using windows before i started the ubuntu live cd goodluck with yours i would say i'd help more but you probably know more than me on linux anyway!!

Setting *anything* in Windows will not impact Ubuntu at all. :)

Glad to hear you got it to work. I had a similar problem in that the live CD I burnt seemed to be working fine as a live CD, but after I installed to the hd, I was unable to login. Something was damaged. A new CD did the trick for me, although getting it was the biggest pain ever with regards to burning CDs. They should start using error correction or something. :)

---

### Post by Jezprice on 2007-10-19
Okay my re install didnt work Jake, i treid the graphics change trick you tried but it did nothing either. Glad yours is now working though, how are you finding it?

I am desperately trying to get mine to work so:

Niniel what rate did you burn your CD at as it wasn't mentioned.

---

### Post by digital_exhaust on 2007-10-19
> **Jezprice said:**
> Okay my re install didnt work Jake, i treid the graphics change trick you tried but it did nothing either. Glad yours is now working though, how are you finding it?

I am desperately trying to get mine to work so:

Niniel what rate did you burn your CD at as it wasn't mentioned.

Always burn images on the slowest setting available, and verify the burn afterwards.... and as mentioned above, tweaking settings while using your Windows install will do absolutely nothing, it will not make any changes to your Ubuntu install..... 
 in assisting 
And as asked above, system specs would be very helpful...

---

### Post by Niniel on 2007-10-21
Actually, I burnt my CD at max possible speed, 25 x or something.
Initially I had used a CD/RW which had been burnt at 4x. 
In my experience, burn speed didn't seem to have an impact. I messed up other ISOs [other distributions] at 16x before it worked eventually at that speed. I guess I could have had a couple bad CD/Rs too.

---

### Post by Jezprice on 2007-10-23
I have done nothing to my system since installing ubuntu except used the live CD a couple of times.

Now all of a sudden my ubuntu installation is working!!!! I have no idea why but HERE WE GO..................... whoo hoo.

---

### Post by bardic on 2007-10-23
I had the same problem, but I was told to hit alt+ctrl+backspace. This command restarts(???) xserver and will try to load a default graphic driver for you ... I think. I had to do this for the live cd and when I installed! 

So here is what I did (someone else suggested this. I am a totally noob to linux but it worked for me.

I installed normally. I booted and when x started, my screened died, but I could still hear Ubunutu booting. I waitied for it to finish loading and hit alt+ctrl+backspace.  It did something and it worked ever since. I only need to do it the once. 

Hope it helps.

---

