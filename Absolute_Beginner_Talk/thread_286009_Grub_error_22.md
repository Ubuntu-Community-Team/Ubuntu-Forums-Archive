---
title: "Grub error 22"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Tharbad on 2006-10-27
After I formated the Linux partition that what I get. How do I fix that so Windows will start normaly?

---

### Post by Iarwain ben-adar on 2006-10-27
Hi,
pop in your Windows (XP i think) cd in,
and boot from it.
Then go to reparation .. something (don't know that, sorry)

So you just have to type```
fixmbr
```

Normally Windows should boot back then :D


Iarwain

---

### Post by Tharbad on 2006-10-27
Ok. I tried the fixboot yesterday and then when I came to try the fix mbr I got message that said that this option my destroy my data, Are there any other sulotions?

By the way the right name is: Recovery Consol.

Another thing (for further use), I runnig Linux from the Cd Currently and this is quite slow so I'm wandering is it possible to set a swap partition that Linux and Windows will use (without windows slowing down because of this)?

thanks

---

### Post by Bigbluecat on 2006-10-27
Sounds like you have wiped your linux install.

Grub works from the master boot record (MBR) and points to a file (menu.lst) for instructions as to where it should look for boot files. By reformatting your linux partition I suspect you have wiped this file hence grub is confused.

I'm not aware that you hvae any alternative but to run fixmbr. I have done this and survived OK.

A more long winded approach would be to re-install linux but it does not sound like you want to do this.

Needless to say always back up important data before any format operation. There is always an element of risk.

Hope it all works out.

---

### Post by Tharbad on 2006-10-27
Thanks. 
First I thing I'll copy a folder from one partition to another. How can I do this? or how can I zip it so I'll be able to upload it to my gmail?

---

### Post by Bigbluecat on 2006-10-27
I think we need a little more information on exactly what is going on here. Can you explain from the beginning.

You hvae a windows machine.
One hard drive or two?

You have a Ubuntu LiveCD

Did you actually install Ubuntu on the HD. Was the install successful?

When and how did you format your linux partition?

Might seem a bit of a pain but we don't want to go messing with your system without a clear picture of what is going on.

Lastly what data are you trying to copy (windows or linux). If you are simply copying it from one partition on a HD to another on the same HD that may not be protection enough. Formatting is a risk to the HD. To protect data properly you need to get if off of the HD to be formatted to another HD or CDROM.

---

### Post by Tharbad on 2006-10-27
Details:
I have one Hardisk of 20GB. I formated Linux partition and the Linux swap because I need Diskspace and I didn't used Linux. The format took place yesterday using Norton Partition Magic, the I merged the Linux and the Linux swap with D. I have Windows XP.
I have 2 partition, both FAT32: C is where I installed Win XP, D is where all my data is.

The folder I want to copy is my windows favorits, better will be to compress it and upload to gmail.

The ubunto install was succesful but I don't have time to learn how to use it...

---

### Post by Bigbluecat on 2006-10-27
OK.

Getting out of my depth now. So you had Ubuntu installed and decided to recover the disk space. 

Used Norton Partition Magic from Windows to eliminate the Ubuntu partitions and merge them with your windows data partition. 

You may be able to mount your windows partitions from the liveCD and copy some data. I've never done this so don't just take my word for it.

If you search the forums for mount windows drive there are a lot of posts.

---

### Post by jd65pl on 2006-10-27
You may find [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") link useful in recovering grub inorder to boot windows. I know it doesn't describe your exact problem but you could use it to fix your problem.

---

### Post by Tharbad on 2006-10-27
I know how to mount. The problem is how to compress the folder as I'm unable to write on this partitions (C and D). Therfore I think that I'll need to do it using the terminal.

---

### Post by Bigbluecat on 2006-10-27
Hi jd65pl,

Not sure what I was missing but could not see a link in your post to help recover grub. Maybe just my poor eyesite

I'm not sure that he can recover grub as he has reformatted his old linux partitions to FAT32 so menu.lst will no longer exist.

---

### Post by jd65pl on 2006-10-27
Oh sorry missed that bit! The link was on the word "This". Here is a link to microsofts knowledge base with some information on removing linux you might find useful.

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

Once you have booted using the windows XP boot/install disk enter recovery console and do:

```
fixboot
fixmbr
```

---

### Post by Bigbluecat on 2006-10-27
Hi Tharbad,

OK. If you are comfortable with mounting you can try it.

I found the following thread which may help:

[http://www.ubuntuforums.org/showthread.php?t=92161&highlight=mount+windows+drive](http://www.ubuntuforums.org/showthread.php?t=92161&highlight=mount+windows+drive)

Apparently windows drives are mounted read only. About half way down the post there is some info from Chayak on how to make it writeable.

---

### Post by Tharbad on 2006-10-27
Thanks for your help!! 

It didn't work so I copied the favorits to the flopy drive and the restarted with the Win XP CD and uesd the fixmbr command.

---

### Post by Bigbluecat on 2006-10-27
OK.

As long as you are up and running. I'm sure you will be welcome back to Ubuntu when you have more time to learn and have fun.

---

### Post by jkvv_1973 on 2006-10-27
I used to have the same error but my grub was fine...found out that the USB printer was on so I turned it off...if that didnt work I would have used the SUPER GRUB DISC to restore my MBR

---

