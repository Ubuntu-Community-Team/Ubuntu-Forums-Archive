---
title: "Install - 6.06 - Screen Rez and Partition issues."
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by coldstatue on 2006-11-19
I am finally installing Ubuntu for the first time on a Gateway DX210X. More technical specs will follow my problem.

I am installing with the 6.06 Live CD.
My screen resolution in ubuntu live is 640 X 480, and that is the only option in the screen resolution settings.
It makes it pretty difficult to feel confident during an installation when I can't see the buttons on the install windows. I can hit enter, but when I get to the partition bit, it's a bit frightening... Here's why - another problem.

My system has a 150 GB HDD with 2 partitions. One is only 5 GB, and that's the one I want to install ubuntu on.
The problem is, that ubuntu isn't showing me this partition. It just sees the whole drive.
Now, the other partition came as the Gateway restore partition. I don't want their restore stuff on my system so I deleted everything that had to do with it.
This is a real partition, right? It shows as Drive D:\ in Windows.

I want a dual boot system, and don't want to fiddle AT ALL with partition size, because I've had Windows problems in the past because of it. There is no way I can afford any Windows problems.

So am I just missing something in the ubuntu setup, and it's actually seeing the 5 GB partition? It's hard for me to know, because I can't see the whole screen. I'll install another drive if need be. I have one.

Here's some info on my video

It's integrated in the MB. Windows sees it as "ATI RADEON XPRESS 200 Series". Windows sees the monitor just as "Plug and Play Monitor".

I don't see anything recognized as a display adapter in the ubuntu system devices.

So, that's it. 2 problems I need to address in order to move on. Resolution is the top priority, but I fear I won't have a chance to fix that until I can get installed and on the Internet. Which will also be a problem. My wireless was not recognized last time. I tried this install a few months ago, and gave up without seeking help because I simply CANNOT fudge with the partition. But as I said, I will add a second physical drive though, if that will fix that problem.

I'm sure there's someone here who knows exactly what to do, but if not, I'd appreciate  any suggestions.

Thanks for your help.

---

### Post by ReaderRat on 2006-11-19
Is this a laptop/desktop? How much RAM? If you want a good bootable Partition Editor disc d/l  [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)  It may help with the rez problem, for the moment. checkout your system on it and see what you have, and where it is.

---

### Post by coldstatue on 2006-11-19
It's a desktop with 384 MB of RAM. 512, but 128 go to the graphics card. I'm looking at Gparted page you sent. I'll download it and get started. I'll come back with the info as soon as I can. 

Thank you

---

### Post by ReaderRat on 2006-11-19
Plenty of RAM. Yes, you may have better rez with the gparted disc. The disc will let you manipulate/resize partitions and set things the way you want. It's a good backup partition disc. I use it often.

---

### Post by bodhi.zazen on 2006-11-19
> **coldstatue said:**
> It's a desktop with 384 MB of RAM. 512, but 128 go to the graphics card. I'm looking at Gparted page you sent, and I'm not sure I understand 2 things. You said it may help my rez issues. You mean that there's a chance that the graphics in Gparted might fit in better with what my screen is currently showing? And secondly, are you saying that I need to create a partition, or that this program will just help me to make the second partition I have visible to ubuntu? or, just to see if it's really a REAL partition? I'll download it and get started.

Thank you

You will need a minimum of 2 free partitions for ubuntu: One for the root partition and one for swap.

After reading your first post, I would advise you get a second HD. They are not too expensive, 5 Gb is on the small side for Ubuntu, and, more important, it sounds as if Windows is "mission critical" for you. for most the install, including resizing your windows partition, will go without problems. But....

Second try looking at these two links:

[Basic partitioning](http://www.ubuntuforums.org/showthread.php?t=282018)

[Monitor resolution](http://www.ubuntuforums.org/showthread.php?t=269052)

---

### Post by coldstatue on 2006-11-20
I actually have some spare drives. So, I think that's the way to go. I will still need to use Gparted to get the right kind of formatting, correct?

---

### Post by coldstatue on 2006-11-20
and thanks for the links. I will print them both.

---

### Post by bodhi.zazen on 2006-11-20
> **coldstatue said:**
> I actually have some spare drives. So, I think that's the way to go. I will still need to use Gparted to get the right kind of formatting, correct?

That is the advantage of a drive devoted to Ubuntu....

During the install let Ubuntu take over the entire drive..... It will partition and format for you.

Install GRUB into the MBR of the master drive (your windows drive).

---

### Post by coldstatue on 2006-11-20
I'm probably giving you some info you don't need, but just in case it means something, I figure I should tell you what happened. I'm basically at the "install GRUB" part like you said.

I just installed ubuntu on its own drive. At the end, it asked me to restart. I clicked the restart button and it froze for a long time. I unplugged and booted, and I didn't get any options for booting from another drive. So I rebooted, went into my BIOS boot options, and booted from the ubuntu drive. I got GRUB error 18. So, I guess you probably saw all of this coming since you told me to install GRUB in the Master Boot Record of my Windows drive. I followed all of the instructions,at least the most basic ones. I only put what was absolutely required in the boot.ini. (C:\boot\stage1="GRUB". I used the legacy version, 1.0. I then spent several hours making every sort of XP rescue boot disk I could find on the internet. Then, I rebooted, and it just went into XP. I am really feeling weary about screwing with the MBR right now, because I have some really important work to get done in teh next few days. Can I just make a CDR boot disk to get an OS option on boot? I'm looking for something pretty simple and harmless. I'm reading about GRUB 2.0, but I don't want to try anything more without advice.
Thanks again for your help.
John

---

### Post by coldstatue on 2006-11-20
I'm starting to think I will DC the Win drive and install ubuntu again. Then I can just use the BIOS selection. That's much safer for someone at my level. Man, I'm glad I did the MBR install of GRUB wrong. From what I'm reading, people like me usually end up in a bad situation doing that.

---

### Post by bodhi.zazen on 2006-11-20
> **coldstatue said:**
> I'm starting to think I will DC the Win drive and install ubuntu again. Then I can just use the BIOS selection. That's much safer for someone at my level. Man, I'm glad I did the MBR install of GRUB wrong. From what I'm reading, people like me usually end up in a bad situation doing that.

You should be just fine installing GRUB into the MBR. If you run into problems your can restore the windows boot loader.

You can do as you say, but when you re-install Ubuntu install grub into the MBR of your new drive. You can now "dual boot" depending on which drive is hard wired as primary.

Or you can install grub into your windows MBR. Thic can easily be done from the Live CD: [Restore GRUB](http://doc.gwos.org/index.php/Restore_Grub)

There seems to be "fear" of Grub growing in the forums. I can understand this as fear of the unknown, but GRUB works well. Most of the people who have difficulty with GRUB because they do not install into the MBR, although there are exceptions..

At any rate, to restore windows (if you want to remove GRUB from your MBR): > Restore windows MBR:
Yes boot from the (windows XP) cd.

Windows will come with some screens and look at "repair an existing XP" or something like that.
NOT THE AUTOMATIC REPAIR it will bring you nowhere.

You get three options,install windows,repair an existingt XP or quit.

Yust choose repair you get a black screen where the existing install [a number] is displayed.

Choose that number and then it asks for your administrator password.

Type in ADMINISTRATOR if you don't know otherwise and pray it's the right one.

Then you get a prompt.
Type fixboot and see what it tells you.
If this doesn't work type fixmbr and you get a warning about messing up things,but ignore,and proceed.

This should make your windows bootable again.

[print this out]

---

### Post by coldstatue on 2006-11-20
Well, I guess I'm extra lucky that I didn't jack up the MBR. I have no Xp disk. Just some gateway restore disk that is totally useless. All it can do is take the machine back to the state it came from the factory in. Seriously. It's crazy. Guess I need to do a lot more reading before trying much else. Thanks for your help. I'm going for the MBR on drive 2.

---

### Post by bodhi.zazen on 2006-11-20
> **coldstatue said:**
> Well, I guess I'm extra lucky that I didn't jack up the MBR. I have no Xp disk. Just some gateway restore disk that is totally useless. All it can do is take the machine back to the state it came from the factory in. Seriously. It's crazy. Guess I need to do a lot more reading before trying much else. Thanks for your help. I'm going for the MBR on drive 2.

LOL :lol: you do not need a windows xp disk to restore your MBR. Microsoft is more then happy to provide such a utility at no cost.

See [this site](http://www.eddieoneverything.com/windows-xp/uninstalling-the-ubuntu-linux-boot-manager.php) for a how-to and link to the microsoft utility.

---

### Post by coldstatue on 2006-11-20
But the only MS page I found said that after you make the 6 disks, you need your XP disk for the last part. Can you tell me the name of the utility, or where I can find it? Maybe I was looking at the wrong thing.
Thanks.

---

### Post by bodhi.zazen on 2006-11-21
See [this thread](http://ubuntuforums.org/showthread.php?t=303765)  Post #5 (Sorry to have given your the run-around, I am not so familiar with Microsoft).

---

### Post by coldstatue on 2006-11-21
No runaround, thanks for your help. I too hope one day to be unfamiliar with Microsoft. I've been thinking about loading ubuntu on the second disk with the MS disk unplugged, then making the Windows disk slave and the ubuntu disk master. I don't see how this could cause any problems, and even if it does, I can just switch them back, as no damage will be done to the Win drive. I'm not worried about the ubuntu drive. I can reformat and install on that as many times as necessary. I don't even expect wireless networking and my display to be working for quite a while.. so who cares what happens to that?

---

