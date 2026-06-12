---
title: "Problem with the GRUB location after installing Ubuntu 12.04.2 on a MacBook Pro 7.1"
date: 2013-05-29
forum: Apple Hardware Users
---

### Post by Egon058 on 2013-05-29
Hi everybody !

I'm an Ubuntu newcomer and I request your help for a little installation problem.

I tried to install Ubuntu 12.04.2 on my Macbook Pro 7.1 (mid 2010) in Dual Boot with OSX Mountain Lion, following this [tutorial]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation"). And… It worked ! :D But when I started my computer, instead of having this [rEFIt menu]("http://img.gawkerassets.com/img/17w1q2tzcwh6wjpg/ku-xlarge.jpg") (Thank to LifeHacker for the picture) I had this [one]("https://dl.dropboxusercontent.com/u/3476346/2013-05-28%2008.39.31.jpg"). :confused: I don't really care if our great friend Tux is missing, but I'd like to understand why the icon is this one, first, and more, why the GNU GRUB is located before MacOS and why the GNU GRUB is default selected instead of MacOS ?

More, if I select the GNU GRUB, I have this [menu]("https://dl.dropboxusercontent.com/u/3476346/2013-05-28%2008.40.05.jpg"), and when I select Mac OS X 32 or 64 Bits, I have a black screen. So, this can maybe explain why the icon is not Tux, because there are more than one OS in this GRUB. But I still can't understand the GNU GRUB location. So my question is: did I install the GNU GRUB at the wrong place ? If yes, how can I correct this ? And if it's not the explanation, what could it be ?

Some final informations about my situation : During the install, just before launching the processes, I had to go in this ["Advanced" menu]("https://dl.dropboxusercontent.com/u/3476346/AdvancedGrub.png") according to the tutorial I followed ([Here]("https://dl.dropboxusercontent.com/u/3476346/AdvancedGrubText.png") you can find the text corresponding to the picture), in order to select the right location for the GNU GRUB. But I couldn't find this option during the install, and I left Ubuntu to decide. Hoping this might be helpful...

My last question would be: If I want to erase everything and reset my Boot informations, what should I do ? Is it enough to erase the whole hard drive from a Live CD for example ?

Hoping I was clear enough, 

Thanks a lot for your help !

Egon

---

### Post by ohnonot on 2013-05-29
welcome to the forums!
> **Egon058 said:**
> Hoping I was clear enough, 
i'm afraid it wasn't for me.
is there anyhting actually Not Working or are you just wondering about the icons and different boot screens?

---

### Post by Egon058 on 2013-05-30
Sorry for the mess... :(

Actually, everything is working&#8230; But at the wrong place ^^. The GRUB has  been installed by Ubuntu in sda, instead of sda4 I guess  (see my [internal hard disk report]("https://dl.dropboxusercontent.com/u/3476346/2013-05-29%2023.05.51.jpg"))), and I have now the option  "Boot EFI\ubuntu\grubx64.efi from EFI" showing up in rEFIt (as shown in  the [picture]("https://dl.dropboxusercontent.com/u/3476346/2013-05-28%2008.39.31.jpg")).

Trying to find a solution, I found a very interesting [thread]("https://discussions.apple.com/thread/3109456?start=0&tstart=0")  yesterday night. The guy who started it (thank to him) had the same  problem with his GRUB location. The last message (from BigLuiz) provides  the solution remove the GNU GRUB ("Boot EFI\ubuntu\grubx64.efi from  EFI") from sda :
 
"Boot OSX and in the terminal write:
mkdir mnt ; sudo mount -t msdos /dev/disk0s1 mnt
Will show a new drive EFI
open this drive and open the folder EFI. Inside you will have the folders APPLE and UBUNTU
just delete the UBUNTU
restart and enjoy !!!!!!"

But I still don't know how to locate the GRUB in sda4... How should I do ? Please ! :confused:

A  last question : As you could see it in my internal hard disk report, I  also have an option at the right of my OSX boot disk, wearing the  BootCamp icon, and named "Mac OS X legacy". I can delete it and  everything is still working ok. But if I try to boot on it, it says  "Missing operating system". Does someone know what is this "Mac OS X  legacy" part ? :confused:

Sorry again for disturbing !

Egon

---

### Post by ohnonot on 2013-05-30
i'm sorry to say i don't know nothing about efi.
maybe you should inform yourself about master boot records, bios, efi, grub and whatnot.
i'm sure ubuntu documentation has helpful pages.

if you yourself say you're a newbie, and otherwise everything is working fine, why bother making changes that are beyond your abilities (i'm saying this as someone who's roughly on the same level in these things)?

you said "everything is working, but in the wrong place" - what do you mean?
it seems to me you're bothered because mac os is not booted by default. i'm sure this can be changed in the efi bootloader settings or whatever it actually is.

---

