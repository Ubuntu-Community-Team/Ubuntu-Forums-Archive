---
title: "Xubuntu ISO file/need help opening this file"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-02-01
O.K I downloaded the xubuntu -7.10-desktop-i386.iso file last night all 566MB worth. It took about two hours to get it all.  I inserted a 700mb cd-r and burned it at 4x rate. 

Now when I load the cd into the cd rom drive it does not boot up  xubuntu. Instead I get a windows message saying "windows cannot open this file"   File: xubuntu-7.10-desktop-i386.iso  "to open the file, windows needs to know what program created it. Windows can go online and look it up automatically blah blah blah..


From reading that what have I missed and what can I re-do if anything?  I really was hoping for a problem free install but this is something I know very little about. Help.

Thank you, Neal

---

### Post by taurus on 2008-02-01
Sounds to me like you just copied that one big file from the harddrive to the CD!  You need to burn that ISO file as an image file, _not_ as a data file if you want to boot from the CD.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

---

### Post by Indy452 on 2008-02-01
O.K so I'm an idiot, I'll be the first to admit  that.

I have the download still. Do I need to install the infra recorder then to make this happen?

I thought I pressed all the right buttons the first time but I really don't understand it totally so thats why I'm here I guess because I don't know a single person in my area that knows anything about how linux works so I'm on my own with the help of this forum and the good folks who help out here.

Can I use the disc that I burned the file on or do I need to use a new disc?

Is there any other way to get xubuntu? Or is this ISO thing the only way?

Neal

---

### Post by Nythain on 2008-02-01
are you burning from linux or windows???
i would probably just use a fresh new disc (never been a fan of re-writing)
and i believe Xubuntu is only offered in downloaded iso, i dont think you can order it for free from canonical... if you had the time to wait, you could theoretically order an ubuntu alternate install cd, then when it shows up, install a command line system, then install xubuntu via download through the repos... but its much easier to just burn an image

---

### Post by bluewraith on 2008-02-01
What software are you currently using to burn cds?

---

### Post by fakhri on 2008-02-01
No, you can't use the first disc, use a new disc! and "Unfortunately, unlike the other Ubuntu derivatives, Xubuntu does not yet have free cds available for shipping due to lack of funding.". So, that iso is the only way.

---

### Post by Indy452 on 2008-02-01
> **Nythain said:**
> are you burning from linux or windows???
i would probably just use a fresh new disc (never been a fan of re-writing)
and i believe Xubuntu is only offered in downloaded iso, i dont think you can order it for free from canonical... if you had the time to wait, you could theoretically order an ubuntu alternate install cd, then when it shows up, install a command line system, then install xubuntu via download through the repos... but its much easier to just burn an image

I'm using windows xp now but I would like to try out xubuntu on an older p3 750mhz machine with 192mb of installed ram. Does this sound like a good candidate for xubuntu?

I have an external CD writer from HP 8200 series. I got it for free so I thought I'd go with it. I'm not real sure what I'm doing though. It seems pretty straight forward butI'm having a hangup on the ISO burning software thing. Do I need this infra recorder software to do the correct burn? Is it something that my cd writer will pick up and work with?

Thanks, Neal

---

### Post by Nythain on 2008-02-01
any popular burning software should have the ability to burn an iso image...
The most popular would nero burning rom or whatever its called... 

basically, in whatever software you are using to burn the cd, make sure you select Burn ISO Image, or Burn Image File, or just Burn Image, or whatever... and then select the iso.
At the moment, as said, it sounds like you are choosing something along lines of Burn Data CD or whatever, wich is just putting the iso file onto the CD... wich is different than the program taking the image file, and burning whats in it onto the cd...

You are going to need a new CD, as i dont even want to get into wether or not you're using re writable cd's with a re writable burner... its a lot easier to just use a new CD.

I wish i could help you more, but i dont have Windows, or a Burning program for it... all i can do is suggest using something, anything, that will Burn ISO Image instead of just making a Data CD...

once you have the image burnt, its all just a matter of rebooting with the disc in the cdrom drive, and making sure your BIOS is set to boot from CD or USB CD or whatever BEFORE booting from IDE Harddrive or whatever, and following some simple instructions.

Yeah, your pc sounds like a perfect candidate for Xubuntu, it will run much better than Ubuntu or Kubuntu with your current RAM specs

---

### Post by Drathas on 2008-02-01
Do you have a USB pen drive?  It's a bit hairy, but it's possible to boot and install from that but it requires some "screwing" to do it.

---

### Post by Reuben3901 on 2008-02-01
a good program is imgburn, free to download and use.

---

### Post by Nythain on 2008-02-01
unless wickedly updated, the odds of a BIOS on a Mobo runnin a p3 isnt going to be able to boot from usb device... wich theoretically could cause problems to begin with, depending on how the bios interprets a USB external CD drive

---

### Post by bluewraith on 2008-02-01
Along with the other items mentioned, a quick google search brought up this software, which seems to be just what you are looking for. I haven't used it, but there is a tutorial for it as well. Seems very new-guy friendly.

[http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")
[http://isorecorder.alexfeinman.com/HowTo.htm]("http://isorecorder.alexfeinman.com/HowTo.htm")

Have fun, and good luck!


Also, if the computer does not automatically boot from the CD, you will have to go into your BIOS settings (watch your screen when it starts. Usually it will tell you what key to press to get into the settings) and look around in there for boot device selection. Make sure that your CD drive is top of the list, save and exit/reboot. After that, it should be pretty easy going.

---

### Post by linux phreak on 2008-02-02
Burn the downloaded Xubuntu Iso file as an  image at a slower speed and then boot from that CD.Your CD burning software will most likely have an option to 'Burn image to Disc'.

---

### Post by lnk5700 on 2008-02-02
[QUOTE=bluewraith;4252792]Along with the other items mentioned, a quick google search brought up this software, which seems to be just what you are looking for. I haven't used it, but there is a tutorial for it as well. Seems very new-guy friendly.

[http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")
[http://isorecorder.alexfeinman.com/HowTo.htm]("http://isorecorder.alexfeinman.com/HowTo.htm")

is there some more site ??    the 2 are no effect

---

### Post by stalkingwolf on 2008-02-02
check out [http://frozentech.com/]("http://frozentech.com/")  they have xubuntu 7.10
cds.  the price is exorbatant. .99 for the cd and 1.99 shipping.    they also have many other distros.
I usually go there if I want to play with other distros and am to lazy or tired to download and burn them.
But thats just me.:lolflag:

---

### Post by Indy452 on 2008-02-03
> **Reuben3901 said:**
> a good program is imgburn, free to download and use.

Thanks Reuben, I downloaded imgburn and it was a breeze from there out. Plus imgburn was an easy program to use and understand.

Does the xubuntu live cd work a little slower than it would if its installed on my computer?

Also when I go to install, on installing the OS should I select use partial disc or the whole disk on the partition question? I don't even know what "partition" is.

Thanks, Neal

---

### Post by lswest on 2008-02-03
well, first off, yes it runs slower than it would if it was installed, as it's running off a CD.  And, is there anything else you want on the PC? if not just choose "use whole disk", if there is, then you need to partition (e.g. create seperate "slots" for linux/windows or whatever else is on that PC) and, if you need to create partitions, say so and i'll post a more thorough description of how to do so.

---

### Post by Indy452 on 2008-02-03
> **lswest said:**
> well, first off, yes it runs slower than it would if it was installed, as it's running off a CD.  And, is there anything else you want on the PC? if not just choose "use whole disk", if there is, then you need to partition (e.g. create seperate "slots" for linux/windows or whatever else is on that PC) and, if you need to create partitions, say so and i'll post a more thorough description of how to do so.

By partitions, you mean run more than one OS? If so I only want one OS so I should choose whole. I don't want any recolection of w/98 on that disc at all I want to wipe it clean and use xubuntu for a learning experience.

Thanks for replys, Neal

---

### Post by lswest on 2008-02-03
then, yup, use whole partition is for you^^ and glad we could help.

---

