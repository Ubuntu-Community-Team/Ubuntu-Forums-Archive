---
title: "Samsung series 5 laptop problem linux mint"
date: 2012-10-03
forum: Any Other OS
---

### Post by Filee on 2012-10-03
I posted this on the linux mint boards aswell but there seems to be more users here for a faster awnser.

Good day,

So yesterday I got my new Samsung NP530U3C-A01SE laptop. I installed linux mint on it instantly via usb on the SSD hybrid part. Now I want to install windows on the non hybrid part. The problem is now I cant enter bios which is the f2 button because gnu grub loads to fast and the f2 push is not counted, even tried with an usb keyboard. Now my boot priority when I installed was usb so it should still be. But now it just ignores the usbs and they are powered off until Linux mint has booted.. tried all slots with different usbs. 

So I decided to remove the hard dive, well it still boots the OS? So I thought maybe its an secondary hard drive for the samsung fast boot feature, or its loaded onto some ram that is powered by the battery. Since the bios "press f2" screen blasts even faster by with the hdd removed I decided to remove the battery. But I dont want to open it since I don't know if I will break it. Removed all the screws and it seems to be stuck. It appears there was a little button for a pin where you could disconnect the battery from the ram or whatever it does. Did this and the computer wont boot unless you plug the charger in, so I decided now it must have cleared the fast boot thing. But no the computer still boots into linux mint without a hard dive and being without power.

Anyhow I am pretty sure its some kind of temporary drive inside that has the os on it, since I wanted to check the disk size in linux mint and its about 4gb ( some files cant be read). However I wanted to go into windows to erase the drive, so I plugged it in and tried to erase everything on the ssd but no, not possible -_-.

Summary:
Want to install windows on hybrid drive.
Cant enter bios due to fastboot feature, shows gnu-grub screen.
Wont boot from usb due to fastboot feature.
Still boots into linux mint with hdd removed and battery disconnected(via pinhole).

So does anyone know what I can do, or has any knowledge about the fastboot, or what I can do? Right now I am trying to drain the battery dead.

//file

---

### Post by Perfect Storm on 2012-10-03
Moved to Other OS/Distro Talk.

---

### Post by mips on 2012-10-04
There must be a way to bypass the fast boot to get into the BIOS. Check the manual I would say or try pressing f2 as you press the power button or maybe you have to hold the power button depressed or something like that.

The ssd portion is on the motherboard, either as a plugin module or soldered onto the board but I suspect it's a pluggable module.

Did you format the hard drive with the existing windows OS on it?

Edit: I just read that the fast boot feature must be disbaled from within windows via the samsung software.

---

### Post by mips on 2012-10-04
Try pressing ESC as soon as you've hit the power button and if you get the samsung screen press f2.

If the above does not work you can erase the iSSD but this involves opening the laptop and unclipping the main battery (not cmos battery) from the motherboard. 1 or 2 minutes should be plenty to erase it.

The above info was passed on to me from a tech at the local samsung service center.

Good luck.

In future install windows on the HDD first and then afterwards install linux on the iSSD. The iSSD gets used as a cache drive so you can wipe/format it and install linux.

---

### Post by Filee on 2012-10-04
Ok thanks a lot for the awnsers, really! I shall try it out tomorrow :)

---

### Post by mips on 2012-10-05
> **Filee said:**
> Ok thanks a lot for the awnsers, really! I shall try it out tomorrow :)

Let us know how it goes ;)

---

### Post by mips on 2012-10-07
Did you come right?

---

### Post by Filee on 2012-10-08
Actually did not try it yet due to not finding the time, I will do it later this week and report in. The only issue right now is how I take the computer apart, since it seems there are some latches holding it down even if I remove all the screws. I don't want to break any plastic either so I am trying to find the correct way of doing it. If I cant find a way of doing it I will most likely send it in for repair.

Another alternative I want to try is to reset the cmos but that would also require me knowing how it is built and how to take it apart. Anyhow I will report my progress!

---

### Post by mips on 2012-10-09
You need to try and find a service manual for the laptop or a teardown video.

I doubt resetting the cmos would help but it's worth a try.

---

### Post by Filee on 2012-10-09
Did not find a manual, but somehow I got it open. There were a lot of latches. Anyway, this is the inside of the computer. I think I know which one is the cmos battery. Dont know which one is the issd. There seem to be 3 cables from the motherboard to the battery.

Here is an imgur gallery of how it looks inside. Do you know what the issd could be?

[http://imgur.com/a/jdvvj](http://imgur.com/a/jdvvj)

EDIT: The issd is cleared, now it just boots the samsung screen over and over, but the same problem as earlier. The boot blasts by so fast that there is no time to press f2 to get into bios. I had the cmos battery out for 2 min, did not reset the bios.

---

### Post by mips on 2012-10-09
> **Filee said:**
> Did not find a manual, but somehow I got it open. There were a lot of latches. Anyway, this is the inside of the computer. I think I know which one is the cmos battery. Dont know which one is the issd. There seem to be 3 cables from the motherboard to the battery.

Here is an imgur gallery of how it looks inside. Do you know what the issd could be?

[http://imgur.com/a/jdvvj](http://imgur.com/a/jdvvj)

EDIT: The issd is cleared, now it just boots the samsung screen over and over, but the same problem as earlier. The boot blasts by so fast that there is no time to press f2 to get into bios. I had the cmos battery out for 2 min, did not reset the bios.

Disconnect the main battery & cmos battery at the same time and leave disconnected for 2min or so. The cmos battery acts as a backup battery to the main battery I suspect so you have to disconnect both in order to clear the cmos settings.

Also check if there is no reset jumpers or buttons on the board.

Also try hitting the escape key rapidly while turning the power on. Also try the same with the f2 key.

The cmos might have a predetermined boot order set so maybe plug a usb stick in and see if it picks that up.

EDIT: I see a label in one of your picks indicating a reset button on what looks like the bottom of your laptop?

---

### Post by Filee on 2012-10-09
So this is what happend, I tapped like a maniac , every single button there was, and it went to boot from my usb xD.

It was either f8 or f9 that made it! Installing windows now :)!

---

### Post by mips on 2012-10-09
> **Filee said:**
> So this is what happend, I tapped like a maniac , every single button there was, and it went to boot from my usb xD.

It was either f8 or f9 that made it! Installing windows now :)!

Cool stuff, install Windows to the hard drive, install MS security essentials, update, install Samsung utilities and disable fast boot for now.
[http://www.samsung.com/my/support/model/NP530U3C-A01MY-downloads](http://www.samsung.com/my/support/model/NP530U3C-A01MY-downloads)

Next install linux to the ssd.

---

### Post by Filee on 2012-10-09
> **mips said:**
> Cool stuff, install Windows to the hard drive, install MS security essentials, update, install Samsung utilities and disable fast boot for now.

Next install linux to the ssd.

Yeah , though I am installing windows on the ssd now just so It boots to windows before I disable the fastboot. Then I will reinstall windows on the mechanical, then replace windows on the ssd with linux ^^

Which was fail since it does not boot anything, even if the "windows" is on the ssd now. 

F9 does always boot from the usb, gonna install windows on the mechanical now. I am using a bootable windows 7 disc that I had laying around. If this does not work I will make the samsung windows 7 disc bootable instead.

EDIT:
It simply does not want to boot from the HDD

---

### Post by mips on 2012-10-09
keep us updated.

---

### Post by Filee on 2012-10-09
So things I will do now, since it seems that it wont boot using the hdd. I assume samsung windows 7 is somehow connected to the issue, but it did boot using grub-gnu before I cleared the ssd.

I will now try to make the samsung ssd into a bootable device, after that I will install windows 7 on the mechanical and ssd drive. If it still does not boot I will install linux once again on the ssd. If linux boots, I know I have windows on the mechanical drive and from there I will add windows 7 to the bootloader.

---

### Post by mips on 2012-10-09
That fast boot feature sound more like a pain than feature to me. There should be an easier way to disable it.

---

### Post by Filee on 2012-10-09
> **mips said:**
> That fast boot feature sound more like a pain than feature to me. There should be an easier way to disable it.

Yeah its quite insane what I have to do just to install an OS... clearly something is wrong here. I think its the UEIF bios fault, guess they dont expect people to install another OS on their laptops.

EDIT: Suddenly I cant boot from the usb anymore, installed samsungs windows on the issd. Cant boot from linux or windows boot stick.

---

### Post by Filee on 2012-10-09
Well, I've spent over 12 hours on this and I cant fix it. I will have to send it to repair now. The repair will probably take weeks, which sucks. Maybe I can demand another laptop or the money back.

I think the bios is corrupt or bugged or something, thats the only explanation here. Everything else works ( worked)

Anyhow, thanks for the help!

EDIT: [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

It seems UEIF bricks the bios, so yeah, that is most likely the issue.

---

### Post by mips on 2012-10-09
> **Filee said:**
> Well, I've spent over 12 hours on this and I cant fix it. I will have to send it to repair now. The repair will probably take weeks, which sucks. Maybe I can demand another laptop or the money back.

I think the bios is corrupt or bugged or something, thats the only explanation here. Everything else works ( worked)

Anyhow, thanks for the help!

EDIT: [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)

It seems UEIF bricks the bios, so yeah, that is most likely the issue.

Bummer. That's a pretty serious bug though.

---

### Post by mips on 2012-10-10
I read that bug again and your condition seems a bit different. Those people don't get the bios screen at all and nothing works. In your case you still get a bios screen briefly and you can boot from usb in to an OS which they can't do so maybe you have UEFI disabled.

---

### Post by Filee on 2012-10-10
> **mips said:**
> I read that bug again and your condition seems a bit different. Those people don't get the bios screen at all and nothing works. In your case you still get a bios screen briefly and you can boot from usb in to an OS which they can't do so maybe you have UEFI disabled.

The thing is, I cant get into bios and I cant boot from any usb anymore. Dont know why, and the bios just ignores my hdd.

---

### Post by mips on 2012-10-12
Had any more luck lately?

Which country/city are you in?

---

### Post by Filee on 2012-11-08
The motherboard was bricked so I got it replaced for free :) The computer is on its way now!

---

### Post by mips on 2012-11-08
Good news.

---

