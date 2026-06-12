---
title: "Live CD help"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by moebob24 on 2007-06-10
Does burning the 'iso' file to a CD in boot format make it a live CD or is  that just to install the OS itself?

---

### Post by starcraft.man on 2007-06-10
> **moebob24 said:**
> Does burning the 'iso' file to a CD in boot format make it a live CD or is  that just to install the OS itself?

No, burn the image you downloaded as a regular ISO/data disk. You don't need to do anything to it to make it bootable.
[URL="https://help.ubuntu.com/community/BurningIsoHowto"]
Here you go.[/URL] Be sure to check md5 sums please to ensure good burn.

---

### Post by Swab on 2007-06-10
Which version of the iso do you have?  If it is ubuntu-7.04-desktop-I386.iso then yes burning it will create a live CD from which Ubuntu can be installed to your hard disk if you choose to do so.

---

### Post by moebob24 on 2007-06-10
this isnt to install right? i just want to run an experiment on booting from CDs and i want to  see what ubuntu looks like for myself...thanks for the link

---

### Post by moebob24 on 2007-06-10
> **Swab said:**
> Which version of the iso do you have?  If it is ubuntu-7.04-desktop-I386.iso then yes burning it will create a live CD from which Ubuntu can be installed to your hard disk if you choose to do so.

so i burn it as just a data disk and it will work out ok?

---

### Post by starcraft.man on 2007-06-10
> **moebob24 said:**
> this isnt to install right? i just want to run an experiment on booting from CDs and i want to  see what ubuntu looks like for myself...thanks for the link

The Live CD both contains the Live environment (which you can play around with) and all the installer files needed to put it on your desktop. When you boot into the live CD you will find an icon called "install" on your desktop. Double click it and off you go installing it to your computer IF you want to :).
[URL="http://www.psychocats.net/ubuntu/installing"]
Oh and here is a guide to live install if you want.[/URL]

I have confidence you will feel a want to install it after trying ;).

Edit: yup, burn as a regular data disk from the ISO. The Ubuntu folks took care of all the work making it bootable.

---

### Post by Swab on 2007-06-10
> **moebob24 said:**
> so i burn it as just a data disk and it will work out ok?

Yes that's correct.

---

### Post by viciouslime on 2007-06-10
> **moebob24 said:**
> so i burn it as just a data disk and it will work out ok?

That's right and yes, it will just be a live cd. It will come up just as a normla ubuntu system would, but there will be a link on the desktop to install. So, you can install if you want by running that, or you can just use it as a normal system, albeit slow as it is running from the CD.

---

### Post by moebob24 on 2007-06-10
> **Swab said:**
> Yes that's correct.

SWEEEEEEEEEET!...ok i just need to download this thing and ill get started...both of u thanks for the help!!!!

---

### Post by moebob24 on 2007-06-10
Ok i have run into problems. i downloaded the iso file and burned it to a disk in data format. I set up the BIOS so that it will boot from the CD drive first. Then i rebooted...
it said i was checking for a boot disk...then said no boot disk and continued to boot windows XP?
does this mean i really do need to burn it as a bootable disk? or did i do something wrong?


i really want to get this right so any help would be greatly appreciated :D:D:D:D

---

### Post by Skidpad on 2007-06-10
> **moebob24 said:**
> i downloaded the iso file and burned it to a disk in data format.

That's your problem right there - you burned it as a **data** cd and not as an ***iso image*** cd.  What are you using to burn with?

---

### Post by moebob24 on 2007-06-10
> **Skidpad said:**
> That's your problem right there - you burned it as a **data** cd and not as an ***iso image*** cd.  What are you using to burn with?

Ok i was told that if i had the ISO i could burn it as a data and it would be a 'live CD' that is my goal here...
i am using 'Roxio' but i downloaded the 'InfraRecorder'...so if i re-burn it as an image it will be a 'Live CD'???
i dont want to have it start installing the OS all of a sudden...also i hear that if it burned at a lower speed it is better....i don't know how to change to burn speed on either of the burning programs listed above...

---

### Post by moebob24 on 2007-06-10
i don't know how to change to burn speed on the infrarecorder software...where can this be done

---

### Post by Skidpad on 2007-06-10
Look in the options or something, it's there - you can see it on the screenshots page:
[InfraRecorder]("http://infrarecorder.sourceforge.net/?page_id=4")

In response to your post #12 above: yes, burn it as an image, and it will be a "LiveCd".  You will boot with this cd to an Ubuntu desktop; the desktop will have a big "Install" icon...it isn't going to install automatically, until you double-click THAT icon.

---

### Post by moebob24 on 2007-06-10
> **Skidpad said:**
> Look in the options or something, it's there - you can see it on the screenshots page:
[InfraRecorder]("http://infrarecorder.sourceforge.net/?page_id=4")

In response to your post #12 above: yes, burn it as an image, and it will be a "LiveCd".  You will boot with this cd to an Ubuntu desktop; the desktop will have a big "Install" icon...it isn't going to install automatically, until you double-click THAT icon.

thank you so much...i was scared to burn the image file because i dont want to get rid of XP just yet...lol thank you for the help

---

### Post by Skidpad on 2007-06-10
Make sure you read this: [Graphical Installation]("https://help.ubuntu.com/community/GraphicalInstall")
It has screenshots for the installation process and will ease (not eliminate!) your fears... :)

---

### Post by moebob24 on 2007-06-10
> **Skidpad said:**
> Make sure you read this: [Graphical Installation]("https://help.ubuntu.com/community/GraphicalInstall")
It has screenshots for the installation process and will ease (not eliminate!) your fears... :)

The first screen shot is what came up for me. There were numbers counting down so i let them go and then it said

"loading"
and then below that it said something about a corrupt kernal...i went to start and install and it said "error 80" and then rebooted...i did this 2 times and then chose to boot into XP to come here and ask what happened.
So...what happened?
is the iso image bad?

---

### Post by p_quarles on 2007-06-10
[COLOR=Black]Roxio always crashed on me, too. I burned Ubuntu to a CD by using

[http://fileforum.betanews.com/detail/ImgBurn/1128426215/1](http://fileforum.betanews.com/detail/ImgBurn/1128426215/1)

It's a small and powerful Windows app that is far better than Roxio. 
[/COLOR]

---

### Post by moebob24 on 2007-06-10
no Roxio didn't crash on me...i didn't even use it....i used InfraRecorder...it burned alright but i guess it is corrupt...it wont boot to the Ubuntu desktop

---

### Post by p_quarles on 2007-06-10
[COLOR=Black]Sorry . . . misread your post. 

Still, I think ImgBurn is the best and simplest burning software available for Windows. It's also very likely that the .ISO got corrupted during the download, so it's definitely worth trying to download it again, and burning it as an image to a new CD. 
[/COLOR]

---

### Post by Nekiruhs on 2007-06-10
Dont worry about installing. It just wont do anything if its not burned as an image. The CD makes it pretty hard to accidently install Ubuntu.

---

### Post by Skidpad on 2007-06-10
Two things:
Did you adjust the burn speed (slower)?  If not, try again.
Did you check the MD5 checksum prior to burning?

Edit: agreed, p_quarles ^^

---

### Post by moebob24 on 2007-06-10
> **Skidpad said:**
> Two things:
Did you adjust the burn speed (slower)?  If not, try again.
Did you check the MD5 checksum prior to burning?

Edit: agreed, p_quarles ^^

yes i set the burn speed at 4x.
I downloaded a program to check the MD5 but it kept locking up when i chose the ISO file to check. so i didn't check it. what exactly is the "MD5"

---

### Post by Skidpad on 2007-06-12
> **moebob24 said:**
> yes i set the burn speed at 4x.
I downloaded a program to check the MD5 but it kept locking up when i chose the ISO file to check. so i didn't check it. what exactly is the "MD5"
In short, it is a "key" that will ensure that the file you downloaded is identical to the source file.

In long: [Wiki]("http://en.wikipedia.org/wiki/Md5")

---

### Post by abn91c on 2007-06-12
if you still have windows XP go to [www.download.com](www.download.com) and find Active ISO burner. It will let you burn the ISO image all the way to 32X. I used it without any problems to get my linux distros. By the way it is free and has DVD burnig capability, it does not expire and has no file size limits(at least for CDR's). dont know about dvd;s since I dont have a dvd burner.

---

