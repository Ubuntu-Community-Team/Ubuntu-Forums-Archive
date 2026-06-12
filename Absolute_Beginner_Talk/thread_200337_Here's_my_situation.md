---
title: "Here's my situation"
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Jaiden on 2006-06-20
I have Windows XP Home Edition, and would like to Install Ubuntu on this Computer. I have made a backup cd of all the important files I have, and would like to do a dual boot with Ubuntu and Windows. I have burned the ISO file to a disc, like in the instructions, and want to know how to try out the LiveCD, then if it's good, install. I mean, Windows is great, in my opinion, but I am getting bored of Windows and would like to use another OS, even to try it out. So I have rebooted and above all the ram messages is a little message that says "F12  for Boot Menu" or something, so I press F12, and select CD, then the thing comes up and says 4 options, and a place that says something like <A>\... and where I can type one in, but when I randomly type one of the things next to them (one of them is something=ON), it says invalid command. So basically, I want to know how to boot the cd, try out ubuntu with the LiveCD, then install it. And please don't just say "Boot the CD". I really haven't even seen the Install Screen yet! (PS: The computer does have all the requirements).
- Jaiden

---

### Post by DSn0wMan on 2006-06-20
Have you set the bios to boot to CD?

On my PC you hold the "delete" key while rebooting, and it should give you a bios menu that will allow you to set your boot preferences.

---

### Post by xyz on 2006-06-20
Hi Jaiden,
This is a good one:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
With BIOS set to boot on CD-Rom, I never encountered problems with LIVE-CD's.

---

### Post by cidica on 2006-06-20
I would download a stricly livecd iso version. Set BIOS to boot from it. There are so many live cd's out there. It great to try something live before installing it to your hard disk. Linux is all powerful my friend. I was stuck in the windows enviroment for so long. Linux opens up a new world. A world where you can configure, edit, and recode just about anything. But agian.. that is only my opinion. I will never go back to windows. Only time it gets touched is for the masses at work.  Which secretly linux would work better in there set up!

---

### Post by Jaiden on 2006-06-21
here is a picture of what comes up: 
[[IMG]http://img153.imageshack.us/img153/6952/00002087el.th.jpg[/IMG]](http://img153.imageshack.us/my.php?image=00002087el.jpg)
(Click on it to make it bigger)
Any help?

---

### Post by cidica on 2006-06-21
[QUOTE=Jaiden]here is a picture of what comes up: 
[[IMG]http://img153.imageshack.us/img153/6952/00002087el.th.jpg[/IMG]](http://img153.imageshack.us/my.php?image=00002087el.jpg)
(Click on it to make it bigger)
Any help?[/QUOTE]

Okay my question is when you hit F12 to boot from the CD this is what you see? When you hit F12 to boot from CD does the CD-ROM drive start spinning like its reading it?? The screenshot you put up is DR-DOS which is an embedded DOS system.  Which you can do certian memory stuff with. The CD is not being booted. You not bringing up anything that is ubuntu. When you start your computer have you made it into BIOS? For me I have to press the DEL key to enter it in. Set it to boot from CD-ROM **before** harddrive? If so and your getting this DR-DOS stuff (which I'm sure you installed) then your ISO image is bad. Also do you see this DR-DOS stuff when you just start up the computer normal.. i.e. no cd in drive?? Try reburning a ISO image using the "burn ISO image" that is on many many burner programs. Also check the md5 of the image make sure it matchs the real one. If it doesnt its a bad image. [http://shots.osdir.com/slideshows/slideshow.php?release=659&slide=4&title=ubuntu+6.06+screenshots]("http://shots.osdir.com/slideshows/slideshow.php?release=659&slide=4&title=ubuntu+6.06+screenshots")
that should be the first thing you see when the CD boots up. Depending on what you download. I suggest downloading your image from [http://www.ubuntu.com/download/]("http://www.ubuntu.com/download/")

---

### Post by Jaiden on 2006-06-22
OK, please someone tell me how to enter the BIOS settings. I have a Dell Laptop, could that be a problem? I only see two things that tell me how to change anything like that: F12 for boot menu (doesn't work), and F2 for Setup, which I can't really find anything about BIOS in there. So... I guess I'll reburn the disc, bootable, try stuff like DEL, etc., and hope it works :confused:
Please tell me how to enter BIOS,
- Jaiden

---

### Post by Jaiden on 2006-06-22
ok, well I guess having the cd as the last thing to boot from was a problem, but so I fixed that (BIOS settings was right in front of my eyes, in setup), but it still comes up with the same screen, so I will try burning again. :)
- Jaiden

---

### Post by Jaiden on 2006-06-22
sorry for the triple post (I don't know if that is allowed here or not), but I think I'm okay, apparently I was just burning the ISO file and it was just being burnt as a file which wasn't bootable. So now I'm burning it the proper way :) I'll post again, or edit to report if it worked :)
- Jaiden

---

### Post by Jaiden on 2006-06-22
Uh oh... It boots, but when I try to run it, it says "Disc Error - Reboot" :(
- Jaiden

---

### Post by ifokkema on 2006-06-22
[QUOTE=Jaiden]sorry for the triple post (I don't know if that is allowed here or not), but I think I'm okay, apparently I was just burning the ISO file and it was just being burnt as a file which wasn't bootable. So now I'm burning it the proper way :) I'll post again, or edit to report if it worked :)
- Jaiden[/QUOTE]
No, I think your problem is just the other way around. The stuff you see on screen is the crap your burner software put on the CD. You should burn the ISO directly to the CD, no modifications. The ISO is bootable and will boot up the Live CD. There was another thread with the same issues. I'll post the link if I find it.

Edit: Here's the link: [http://ubuntuforums.org/search.php?searchid=6252277](http://ubuntuforums.org/search.php?searchid=6252277)

---

### Post by cidica on 2006-06-22
[QUOTE=Jaiden]Uh oh... It boots, but when I try to run it, it says "Disc Error - Reboot" :(
- Jaiden[/QUOTE]
Try just burning the ISO with the burn CD image option. Dont go the length of making it bootable and such. That will work fine.

---

### Post by Jaiden on 2006-06-22
I went file > burn cd from ISO file, and selected the ISO file, then pressed burn. So I guess I will just burn it, no modofications, with the normal burner?
:(
- Jaiden

---

### Post by Brunellus on 2006-06-22
[QUOTE=Jaiden]I went file > burn cd from ISO file, and selected the ISO file, then pressed burn. So I guess I will just burn it, no modofications, with the normal burner?
:(
- Jaiden[/QUOTE]
yes.  just as long as you're actually burning the ISO and not just a CD that happens to have a .iso file on it.

---

### Post by Jaiden on 2006-06-23
ok, let me explain. I used the suftware suggested on the wiki, and went to file > burn ISO image (it doesn't say anything about if I want to make it bootable or not, so no mods). Is this correct? The first time I was doing it simply by Burning the cd normally, and saying to make it bootable, but neither worked. :( ??
So basically, I'm just doing what you said above...
- Jaiden

---

### Post by Jaiden on 2006-06-23
anyone?

---

### Post by ifokkema on 2006-06-23
[QUOTE=Jaiden]I used the suftware suggested on the wiki, and went to file > burn ISO image (it doesn't say anything about if I want to make it bootable or not, so no mods). Is this correct?[/QUOTE]

Sounds good!

---

### Post by Jaiden on 2006-06-23
well thats what I did, and it doesn't work <_<
I guess I can try again... >.<

---

### Post by Thundercat on 2006-06-23
Do you get a different screen when you boot from the CD now? It should have a ubuntu logo on it and a bunch of options below, if you are getting that screen, one of the options should be to check the CD (I think it was the last or second to last on the list IIRC) If you aren't getting a logo, what files do you see on the CD when you look at it in windows?

---

### Post by Jaiden on 2006-06-23
yeah I see the ubuntu logo, and a little menu under it, and at the bottom of the screen are some options for something. I do see the check cd, and it doesn't work either, it just says "Disc Error [reboot]" ([reboot] being a button)
- Jaiden

---

### Post by Thundercat on 2006-06-23
Sounds like it might be worth downloading the image again and re-burning it.

---

### Post by Jaiden on 2006-06-23
o0 no way, it took all night to download.

---

### Post by Thundercat on 2006-06-23
I'd assume the disc error its talking about is the CD. So it may be worth just attempting to burn the image you already downloaded again, possibly use a different burner program in case it has done something odd, I used Nero if that helps? 

However if the problem is that the image you downloaded is corrupt it will be a wasted CD. If it toook all nigth to download, it might be worth risking a CD.

---

### Post by Jaiden on 2006-06-23
ok I think the cd was scratched a bit, but I burnt it again, and I have my fingers crossed. :)
- Jaiden

---

### Post by Jaiden on 2006-06-23
*BUMP*
Didn't work...

---

### Post by e_james on 2006-06-23
Jaiden
I think you said you were using Nero to burn the CD. When the burn starts there sholud be a check box to the bottom left of the window which says verify data. It's a good idea to use this if the quality of the disc is at all important. I have had situations where, on average, 1 in 2 CDs / DVDs failed to verify. I know people who burn CDs for data backup without verify. I think they could be in for a nasty shock.

Another possibility. An all night download implies a slow connection e.g. dialup. Slow connecions are more likely to have data errors. In these circumstances a dowload manager is a big help. I understand that XP has a download manager. I think it comes with Service pack 2. If the connection is interrupted, it allows XP to continue a download rather than start again from the beginning.

The ubuntu download sites have lists of MD5 sums which can be used to verify a good download. If you don't have it already you will need a little bit of software to do the check. I believe there are several choices available but the one I use is "md5sums-1.2.zip" (instructions included). Just copy the name into Google and pick one of the results. It's a tiny download.

---

### Post by aysiu on 2006-06-23
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html) shows you (with screenshots) how to verify an MD5 sum and burn a disk image properly (at a slow speed).

---

### Post by e_james on 2006-06-23
aysiu

I followed your link above and I notice that CDBurnerXP doesn't seem to have a verify option. I tried DeepBurner recently and it likewise doesn't seem to verify. Maybe it's just that Nero isn't very reliable, but I don't trust any disc that hasn't been verified. I have even rejected a few by personal tests after Nero said they were OK. In a batch of 50 discs I consider them to be of excellent quality if I have less than about 4 rejects.

---

### Post by aysiu on 2006-06-23
That's why I also have the ISO verified *before* it's burned and encourage users to burn the disk at a slow speed--the slower the speed, the less likely the disk is to be corrupted during burning.

You can always verify the disk's post-burn integrity when you boot up Ubuntu.

---

### Post by BoyOfDestiny on 2006-06-24
[QUOTE=aysiu]That's why I also have the ISO verified *before* it's burned and encourage users to burn the disk at a slow speed--the slower the speed, the less likely the disk is to be corrupted during burning.

You can always verify the disk's post-burn integrity when you boot up Ubuntu.[/QUOTE]

Yep, it's worth mentioning if the file is damaged, you don't have to download it from scratch. Bittorrent will help you there (basically it will repair/fetch the missing parts) so even if you have dialup won't be too bad...

---

### Post by e_james on 2006-06-24
BoyOfDestiny

That makes sense but I never thought of it before. Thanks.

---

### Post by Jaiden on 2006-06-24
if it helps, when I run the cd while still in windows, this comes up:
[img]http://img224.imageshack.us/img224/5306/picture5cv.png[/img]
but then nothing happens...
- Jaiden :(

---

### Post by aeto on 2006-06-24
actually one should try just inserting the cd/dvd n then rebooting. because the BIOS is set such that it will find a boot disk..well for my old pentium 3 866 its that way. so i guess all PCs should have it. it would automatically detect the cd n boot frm there. if ur using a livecd, try it out while in windows. u can also try it after rebooting..just click on "start or install", or somethin like that. the cd boots up n u can find the install icon on the desktop. frm there just carry on. dual-booting needs partitioning..for that visit wikipedia or wikibooks..great source. If u have problem burning, like others have said, always burn at a slow speed. RW or R, for DVDs 2x. For CDs, 8x (current CDs can handle speeds of upto 52x so 8x is enough perfection).

---

### Post by e_james on 2006-06-24
After a few seconds you should get another window with a message about booting from the CD to try Ubuntu. If you don't it suggests the CD is faulty or just possibly your firewall is blocking the web access necessary.

There is another problem. Only the Live / Install CD does this. Feel free to correct me anybody, but I believe you will need to download the Alternate CD for an actual installation if you want dual boot. There are comments to the effect that the Live / Install CD could wipe your windows partition as it expects to use the entire drive. The Live / Install CD does provide a good graphical partition manager which you can use to prepare your drive for the install. You could do the same with the Linux Rescue CD which I think is a much smaller download.

I just realised that you may not be connected to the net when you test the CD. In that case what you are getting is probably correct.

---

### Post by Jaiden on 2006-06-29
well... I don't

---

### Post by cjm5229 on 2006-06-29
You need to burn the disk as slow as your burning app will allow you, 2x or 4x if possible.

---

