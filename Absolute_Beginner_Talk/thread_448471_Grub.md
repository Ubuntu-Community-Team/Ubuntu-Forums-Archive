---
title: "Grub?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by bobbyDSM on 2007-05-19
Where do I install GRUB? Under what partition I mean.

What is GRUB?

---

### Post by Outrunner on 2007-05-19
GRUB is the bootloder(you use it to choose what OS to start when you power on the computer). There's a guide about how to reinstall GRUB in the Tutorials section of the forums and you should look for it there.

EDIT: How to install GRUB from a livecd ->> [http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

Just wondering, how come you need to do this when you don't even know what GRUB is? Did you set it up wrong somehow or is it something else?

---

### Post by bobbyDSM on 2007-05-19
So if I don't want daul-boot, then don't install it?

If I choose to wipe out prev. partition, and reinstall, will it still install GRUB?

---

### Post by Najand on 2007-05-19
It should be installed under your linux partition but you must let it overwrite your computer MBR to enable it booting the computer. Look at Ubuntu Community documentation for more help: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Najand on 2007-05-19
You need to boot your linux. And linux need a bootloader like grub or lilo (grub is more popular these days and it is the default one under ubuntu). So you need to install it.

---

### Post by Outrunner on 2007-05-19
Yes it will install GRUB anyway, and that's good because you need a bootloader to start up an operating system. If you wipe out the whole hard drive and install Ubuntu then you don't need to worry about GRUB because it will boot it up automatically for you without you needing to select anything anyway

---

### Post by bobbyDSM on 2007-05-19
So what partition do I install Ubuntu to?

So I just install GRUB to the same Ubuntu partition?

---

### Post by Najand on 2007-05-19
If you are using the live CD it will install it automatically on your computer. If not, I need more inforamtion about the case. What is the output of:
```

sudo fdisk -l

``` in the terminal?

---

### Post by Outrunner on 2007-05-19
You don't need to worry about this because it will be installed automatically while installing Ubuntu.

---

### Post by bobbyDSM on 2007-05-19
One last question: I purchased this item:
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=250115175722](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=250115175722)

IT says it comes with NDISwrapper. Is that possible? To already have it installed?

---

### Post by Najand on 2007-05-19
When it says it has ndiswapper, then it must have it... Did you feel it is not included?

---

### Post by bobbyDSM on 2007-05-19
I'm unsure.

I just don't understand how you could make a live CD with other app.s on it....

---

### Post by Najand on 2007-05-19
Making Live CDs are not very difficult these days... Let me check it out and I will tell you if it is included or not.

---

### Post by Najand on 2007-05-19
It seems to me it is identical to the original ubuntu CD from canonical. Well... ndiwrapper-utils is included in ubuntu cd too... You can also install it through Ubuntu Official Repositories.

---

### Post by bobbyDSM on 2007-05-19
How?
And what is that?

---

### Post by Najand on 2007-05-19
> **bobbyDSM said:**
> How?
And what is that?

Well... I cannot understand which part of my reply was unclear... Please be more specified.

---

### Post by bobbyDSM on 2007-05-19
How do you install from Official Repos. if you have no internet?

And many people  say item was as described. How can you tell it is identical

---

### Post by Najand on 2007-05-19
Hmm... Size of the CD-ROM.... However... I said "it seems to me".... It might be different. 
You can always download packages from a computer that has internet and take it to the other computer using a flash disk,,,
However I hope it is included in it... As I said, making live cds is not a difficult task these days.

---

### Post by Outrunner on 2007-05-19
Well, assuming the CD has ndiswrapper availabe on it you can just add the CD as a repository

```
sudo apt-cdrom add
```

and then install ndiswrapper
```

sudo aptitude install package
```

---

### Post by Najand on 2007-05-19
> **Outrunner said:**
> Well, assuming the CD has ndiswrapper availabe on it you can just add the CD as a repository

```
sudo apt-cdrom add
```

and then install ndiswrapper
```

sudo aptitude install package
```

Nice... Outrunner is right... However you need to update apt after addding cd-rom to the sources list. O you need to do ```
 sudo apt-get update 
``` after using apt-cdrom command.

---

