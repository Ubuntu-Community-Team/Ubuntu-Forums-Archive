---
title: "Do worms affect dual-boot systems (Windows &amp; Ubuntu)?"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by christina_svats on 2007-10-03
I have a dual-boot system (Windows XP & Ubuntu) and my antivirus detected a worm. I am not sure whether the problem is healed. Don't worms distroy my hard disk? If so, will this affect in some way my Linux system?
 I guess I can always format the partition in which Windows are, without this having anything to do with Linux, right?

---

### Post by REDISISTone.nl on 2007-10-03
Hard to say,

lets take this as situation:

You have windows xp and Ubuntu, both on a diffrent HD...Grub is installed on the first one where XP is installed, your worm destroys only the first HD, so only the XP HD is gone, and it will not start, but when you choose to boot from that HD again, it will...

Hmm I hope this is any help to you....

---

### Post by nowshining on 2007-10-03
what's the worm?

---

### Post by christina_svats on 2007-10-03
My HD is 80 GB. I had windows already installed and then ubuntu. So, during the intstallation, I chose 35 Gb for Windows and the rest for ubuntu and swap. I guess this means I have grub installed on the windows partition?

---

### Post by Officer Dibble on 2007-10-03
Don't format your Windows drive if you are dual booting Windows and Linux otherwise you will loose Linux too. :)

Worms mostly target networks, but if you know the name of the virus or some description of it given by your Anti-virus (AV) software we could tell you what it will try to do.

As it has been picked up by your AV and you haven't told us about anything dire happening such as an inability to boot-up or use your computer there is the very good possibility it will be removed without too much suffering, if any at all.

This is of course if it is a worm. AV's are prone to false-positives, or basically being paranoid - what has your AV suggested doing with it? Do you have any Anti-spyware, (AS) and is your AV up to date?

It appears your problem is isolated to Windows, and as Windows is so very prone to this sort of thing there are a variety of established ways of sorting it out... but sadly it is usually the resource laden method of prevention via a million and one apps running in the background. Sorting it out afterwards involves finding a reliable AV or AS package to hunt down the offending little tike and then the waiting game of letting it do its searches and monitoring.

For future reference I'd suggest using Windows for the games that won't run on Linux, and use Linux for proper computing. :)

---

### Post by christina_svats on 2007-10-03
This is my little visitor:Trojan-Downloader.VBS.Small.bo

I followed the AV 's instructions, but I never really trusted them. I only use Windows for some gis programs, this little thing came via a usb flash of a friend... 
Why formatting windows will erase ubuntu as well? They are supposed to be on different partitions, right? Could you please elaborate?

---

### Post by nowshining on 2007-10-03
what is ur AV by the way? - as for the other I don't use a dual-boot but i'll give a guess at ur question, because windows will overwrite everything since it will not see the ext3 partition, and or it will overwrite the GRUB menu and may if not the can't see ext3 thing write a bunch of junk onto it.. - just guesses...however the grub menu is for real so that's less likely a guess.

---

### Post by philinux on 2007-10-03
> **christina_svats said:**
> This is my little visitor:Trojan-Downloader.VBS.Small.bo


Its only a google away [http://www.viruslist.com/en/viruses/encyclopedia?virusid=137868](http://www.viruslist.com/en/viruses/encyclopedia?virusid=137868)

you can check from this if the AV did its stuff.

---

### Post by Officer Dibble on 2007-10-03
It seems a straight forward Trojan to remove and if you keep your AV up to date then it would have removed this safely - but read through this link all the same as it will give you some good advice on the simple steps of removing it manually or checking to make sure your AV has removed it properly.

[http://www.viruslist.com/en/viruses/encyclopedia?virusid=137868](http://www.viruslist.com/en/viruses/encyclopedia?virusid=137868)

As for formatting your Windows partition, well Ubuntu uses that partition in a very small way to boot from too because of it being _**the**_ 'Active' partition. If you wipe your Windows partiton with a view to reinstalling Windows then you will lose access to Ubuntu unless it is repaired via Supergrub.

[Supergrub]("http://supergrub.forjamari.linex.org/?section=documentation")

Once again, the virus you had is easy for your AV or you to remove, and I would feel confident in saying after checking out the virus that your AV has done this considering its ease of removal. You will be creating a lot of work for your self by taking the drastic action of wiping your Windows partition. But on the other hand, you will also learn a lot by doing this as it is quite likely you may need to do it again in the future with possibly a more drastic virus - because of Windows.

Your call my friend. :)

> **christina_svats said:**
> This is my little visitor:Trojan-Downloader.VBS.Small.bo

I followed the AV 's instructions, but I never really trusted them. I only use Windows for some gis programs, this little thing came via a usb flash of a friend... 
Why formatting windows will erase ubuntu as well? They are supposed to be on different partitions, right? Could you please elaborate?

---

### Post by christina_svats on 2007-10-03
AVG detected the virus, I have also avast, but it didn't say anything. I think that windows can see the rest of the partiotions as uknown, so, if I choose the ntfs partition for formatting and reinstalling windows, why would it affect the other partitions? Except, if it erases grub... Any way to get around this?
Sorry for being such a newbie...

---

### Post by christina_svats on 2007-10-03
Ok, thanks everybody for the useful advice!
I think I will ban my friends from using my Windows, or, any Windows at all!

---

