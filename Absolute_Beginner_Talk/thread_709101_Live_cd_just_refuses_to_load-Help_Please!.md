---
title: "Live cd just refuses to load-Help Please!"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by wolfwatcher51 on 2008-02-27
Brand spanking newbie. I want to try the live cd to see how I like it. I have d'loaded ubuntu 7.10 desktop twice and burned to dvd+r,then tried again at slower speed,then tried with different brand dvd-r,then a cd-r. Then I switched to Kubuntu 6.06.1 desktop and burned iso to another brand of cd-r. In windows xp pro, I can look at the contents of the discs get numerous files so I know it burned the iso.

The problem is that when I restart the computer and boot from the optical disc, it generally loads the kernel and then goes to a blank screen with a blinking cursor in the upper right. All of the d'loaded isos were md5 checked and were good. One time I did get one dvd to boot into ubuntu, but hung up when I was looking at a video setting and must not have had an internet connection and it seemed to freeze, so I rebooted w/o the disk to get back to windows.

I have been reading around on the forums and ubuntu site and I believe I am doing this correctly, there must just be something I missed. Any and all help will be greatly appreciated.

I built the computer two months ago. Intel 2.0gig dual core allendale, 4GB ddr2-800 memory,Abit IP35 motherboard,xfx nvedia 8600GT video card, one WD 160GB SATA 3.0 and one WD 500GB Sata 3.0 harddrives. Asus CD-DVD burner. Could it be possible that the live cds need ide drives rather than sata?

One last question please. When I get to the point of going with dual booting and I set up the ubuntu partitions, I think I will go with the /  and /home and possibly the/boot partitions. The /boot would have to be a primary, would the / and /home be logicals? Thanks a million in advance, Chris.

---

### Post by jan quark on 2008-02-27
do you have tried to install via the alternate CD?

it is worth a try

---

### Post by housam on 2008-02-27
Did you burn it as an image or just as a normal data You can use [[COLOR="Red"]_this guide_[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto")
> **wolfwatcher51 said:**
> 
One last question please. When I get to the point of going with dual booting and I set up the ubuntu partitions, I think I will go with the /  and /home and possibly the/boot partitions. The /boot would have to be a primary, would the / and /home be logicals? Thanks a million in advance, Chris.

Also you need a swap partition ( 1 GB ) beside the root partition ( / ) and the /home one.

---

### Post by Sceiron on 2008-02-27
Have you tried to start upwith the Ubuntu-live CD in safe grafics mode?

This is a very basic approach, but if you haven't tried it then you really should.

---

### Post by wolfwatcher51 on 2008-02-27
I did burn the iso file as an iso dvd/cd.

I have not tried the alternate iso because I do not want to install it, just "try it out". I thought that that is what the desktop iso (live cd) is used for.

When I reboot the computer with the live cd/dvd in the optical drive, I usually get a blank screen with blinking cursor. Once or twice it has gone to the ubuntu menu, but the arrow keys do not work and when it tries to start, blank screen with blinking cursor.

How can I try to start it using the limited graphics suggestion, please?
Thanks in advance, Chris.

---

### Post by Sceiron on 2008-02-27
Hm, i suppose since u get the "ubuntu menu" you have gotten the burning correct. 
When you get the "ubuntu menu" you have to use arrow key down, and select the second line in the menu, this is the "Safe Grafics Mode"

What kind of keyboard do u have, bluetooth, wireless ?
i would try a keyboard with wire if you have one lying around, and fix the other later if this is the problem...

Edit: and yes, thats is what the ISO live CD is for.
Edit: have you set your bios to Boot from CD ?

---

### Post by Sceiron on 2008-02-27
> **wolfwatcher51 said:**
> 
Could it be possible that the live cds need ide drives rather than sata?


For solutions on this problem you could read the first chapter of this Hotwo:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_(Feisty_Fawn)_on_a_ThinkPad_T61)

but on the other hand this is for lenovo laptops.... but its maybe worth a try, but you do it on your own risk..... pls tell if u find a solution.

---

### Post by wolfwatcher51 on 2008-02-29
Thanks for the comments.

BIOS is set to boot cd before hdd

I only got to the ubuntu screen twice. First time the arrow keys did not work so I could not select anything. When it tried to start/install ubuntu, a window came up saying loading kernel, 100%, then the screen went blank with cursor blinking in upper left corner.

Second time it got to menu, arrow keys were working and I select check cd for errors, and it went to blank screen with cursor again.

ALL the other attempts were the same, the disc spun up, the screen went blank with blinking cursor in upper right, after a while the disc spun down and stayed down. The screen stayed blank with the cursor flashing.

Maybe the prioblem is my nvidia graphics card, but I have to get in to fix it, right? In windows I use a dual monitor setup. Would this have anything to do with my difficulties?

I am open to anything right now. Thanks, Chris.

---

### Post by Sceiron on 2008-02-29
The safe grafics mode is there so u can use it without the restricted drivers for your grafics card. Try get the menu again until u get it (maybe use a wired KB)....skip all test etc just get to the menu.
I cant help you any further,


on the other hand you have the alternative CD wich someone else suggested, but since you just wanna try it, the Safe Grafics Mode is still your best way to go (from my point of view)

---

