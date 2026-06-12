---
title: "How do I remove the Ubuntu Partition and combine that space with the Windows Partitio"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by radlations on 2008-01-04
It seems my Ubuntu adventure has ended. I do not have the time to learn and fiddle with this awesome OS. I have things I must do immediately and im a busy person.

How do I remove the Ubuntu Partition and combine that space with the Windows Partition?

I originally had about 120 GB of free space for Windows. Then gave some to Ubuntu. I then dual booted with Vista and Ubuntu GG.

How do I remove the Ubuntu OS and give that free space back to Windows safely?

---

### Post by perlluver on 2008-01-04
Try GParted, you can download it and burn it to a disk, then you can move all that space to the windows partition.  You will also have to fix your MBR for Windows.  You will have to use your Windows CD for that.

---

### Post by markusf21 on 2008-01-04
Back up just incase. Run the live cd and go to system --> admin --> partition editor.
delete ubuntu partition and the select the windows partition and click move/resize and drag the bar all the way to the right
and then do like the above post says about the MBR

---

### Post by radlations on 2008-01-04
What do you mean "Fix the MBR for Windows?"

I just got finished restoring Windows to factory settings. So I have already backed up my important stuff on my desktop.

---

### Post by markusf21 on 2008-01-04
you will have to use either 1) your windows cd or 2)[[COLOR="Blue"]_ super grub disk_[/COLOR]]("http://supergrub.forjamari.linex.org/") to fix your MBR or windows will not boot

---

### Post by radlations on 2008-01-04
I don't have the windows disk. Im looking at the Supergrub link you gave me.

Youre saying this will repair my Windows MBR and allow Windows to boot?

How does one repair the Windows MBR with this Supergrub?

---

### Post by blueridgedog on 2008-01-04
When you boot currently, do you get the usual Ubuntu menu or do you go automatically into windows?

---

### Post by radlations on 2008-01-04
It automatically loads Windows. Wow that is strange.

---

### Post by bwtranch on 2008-01-05
All you have to do is put in your Windows CD and re-install. Forget about GRUB and excuse me, but this forum is for Linux users. Any problems that you might have with Windows should be taken up with Microsoft or your OEM.

---

### Post by radlations on 2008-01-05
What do I do if I don't have my Windows CD? This laptop was a gift from my sister.

---

### Post by Xavieran on 2008-01-05
You want it to automatically load windows,don't you?

You can combine the space by getting the gparted livecd iso here[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

Simply delete the ubuntu partition (if it still exists)and then resize the windows partition into the un-allocated space :)

---

### Post by Skidpad on 2008-01-05
A very good read...[Uninstall Ubuntu]("http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu")

---

### Post by bwtranch on 2008-01-05
Well, now you have a decision to make. Stay with Linux or go back to Windows. If you can't find the install CD for Windows, you are going to have to buy one. Use the Ubuntu and it's free. Like beer. To me, the decision is easy. What really is your problem, anyway? I can do anything on this machine. (and more, than any MS based machine ever thought about) What is the problem?

---

### Post by Xavieran on 2008-01-05
radlations obviously has his reasons...ubuntu is not for every one...btw have you tried Linux Mint xD...

Link:[http://ubuntuforums.org/showthread.php?t=643102]("http://ubuntuforums.org/showthread.php?t=643102")

---

### Post by radlations on 2008-01-05
Thank you very much Skidpad. I am reading it. And will make a different thread on a more specific question.

Yes I do my reasons and if you want to know them. 

There are simply too many minor issues that I do not have time to deal with on Ubuntu. Be it a website that was made for Windows, games I can't play, programs that were made for windows being unavailible.

Windows may not have freedom. But it gives the illusion of freedom and promises easy solutions. To some people that is sufficient.

---

### Post by Xavieran on 2008-01-05
That's okay...maybe in a few years (probably months...) you might try Ubuntu again...When more hardware manufacturers are releasing open-source drivers and such...

I'm glad that you at least tried though...:)

---

### Post by bwtranch on 2008-01-05
Mint is good, Mandriva on another. Fedora, ahh whatever. Ubuntu is the best. I tested this system 7.10, it's the best ever, and they just keep getting better. Keep adding drivers and the support is great. I always come back to Ubuntu. I am a

---

### Post by Xavieran on 2008-01-05
O.K...let's not turn this into a "Please come back to ubuntu" thread...
I'm sure radlations has thought this through and I'm sure he's read enough reasons of why Ubuntu is better...
Though I must agree that Ubuntu just gets better and better...:)

EDIT:Whoahoa! 200 beans and rising!!

---

### Post by bitterbug on 2008-01-05
There's a command called "fixmbr" or "fixboot" depending on what XP disks people have.
You might have it available to you from within your installed copy of windows, but I don't think it will let you do it unless you've booted from CD. It's been a while since I touched it.
If your windows is booting after the changes to the partition, that's good, but you should probably grab a CD from someone and boot to the recovery console to run fixmbr and make sure that it's 100 percent with windows. Just so something doesn't bite you in the *** later. 
It won't require a windows reinstall :)

---

### Post by radlations on 2008-01-05
It seems when I did the factory restore, It also repaired my Windows MBR. Which probly explains why Linux does not load on restart.

I then loaded the UbuntuLive CD and ran Gparted. Deleted the linux partition and resized the windows partition.

Windows Loaded without any Errors. Tah dah. This is also my last post here on Ubuntu, hopefully :P, Good bye. The Ubuntu community has been of great help to me. You guys are doing a wonderful thing and I hope you guys to continue to do better. Peace.

---

### Post by blueridgedog on 2008-01-05
> **radlations said:**
> What do you mean "Fix the MBR for Windows?"

I just got finished restoring Windows to factory settings. So I have already backed up my important stuff on my desktop.

OK, so you reinstalled windows in some capacity (perhaps a restore partition?)

> **radlations said:**
> It automatically loads Windows. Wow that is strange.

Which is what I suspected, whatever you did above removed grub, so that at least is done.

I suggest you try to boot on the live Ubuntu CD and see if you can resize the partition.  Run gparted System -> Administration -> Partition Editor

You will need to unmount your windows partition if it mounts automatically.

And, as to the forums, we are here to help with all of your Ubuntu issues, even making your system back to the way it was before you decided to give it a try.

---

