---
title: "Grub go where ??"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by thoeng on 2007-04-10
Hi All,

I have just finished installing feisty fawn yesterday and plus beryl it is simply stunning !!

But because of my work i still need windows ( what a shame )

Anyway, after installing windows i can not boot on ubuntu anymore.

normally i instal windows 1st and ubuntu next and grub displayed windows and ubuntu but now there is no GRUB anymore and i don't know where to boot to ubuntu anymore.

please help

---

### Post by fobnicat on 2007-04-10
I could very well be wrong being that I am still pretty new to all of this, but my thoought would be taht because ubuntu was installed on a blank hard disk, it didnt install grub or configure grub to run on boot..  ill search around and see if i can't find some more info on it... maybe someone who knows more will come along with a solution before i do.. good lu ck

---

### Post by Obor on 2007-04-10
There might be an easier way but [here is one option]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_restore_GRUB_menu_after_Windows_installation")

---

### Post by Nythain on 2007-04-10
sounds more like windows overwrote grub... windows doesnt play well with others... re-installing grub (i forgot how) will fix the problem... yeah, from now on you should install windows THEN anything else :)

---

### Post by reality_hunter on 2007-04-10
> **thoeng said:**
> Hi All,

I have just finished installing feisty fawn yesterday and plus beryl it is simply stunning !!

But because of my work i still need windows ( what a shame )

Anyway, after installing windows i can not boot on ubuntu anymore.

normally i instal windows 1st and ubuntu next and grub displayed windows and ubuntu but now there is no GRUB anymore and i don't know where to boot to ubuntu anymore.

please help

Hi, 
did you install the windows on the same hard disk or a separate/slave disk?
if you installed windows on a separate disk, then try to boot from the other disk where windows is installed on.

If they are on the same disk let me know, and i will post some useful links that worked for me.

---

### Post by fobnicat on 2007-04-10
I could be very wrong, but you might consider trying 

```
Use the command map, to exchange BIOS drives virtually, like this:

grub> root (hd1,0)
grub> chainloader +1
grub> map (hd0) (hd1)
grub> map (hd1) (hd0)
```

this might not work, but could also try instead of (hd0) (hd1) use the  partition reference # 


to get to grub command line just enter terminal and type grub.. takes a minute or two... but it will come up


im not sure.. i found your post interestinga nd though it woudl be a good chance to look into somethign and try to learn some more.. dont trust my suggestion 100% its only speculation..

---

### Post by zvacet on 2007-04-10
[http://ubuntuforums.org/showthread.php?t=358183&highlight=grub]("http://ubuntuforums.org/showthread.php?t=358183&highlight=grub")

---

### Post by reality_hunter on 2007-04-10
> **Nythain said:**
> sounds more like windows overwrote grub... windows doesnt play well with others... re-installing grub (i forgot how) will fix the problem... yeah, from now on you should install windows THEN anything else :)

THOENG, yeah also try what Nythain has said...heres how to install grub if you cannot boot into UBUNTU..



basically, put the live CD to and start a live cd session and once inside goto the terminal and type:

```

sudo grub
#now the grub command prompt will come up and then type this to search
find /boot/grub/stage2
root (hd0,0)
setup (hd0)
#note that hd0 and 0 should be replaced by whatever the search shows and if there 
#are more than one, select the one that the OS is booting from
quit / exit

```

hopefully that works

---

### Post by thoeng on 2007-04-10
Yay !! what a great community... i like it !!

Now my computer works  fine with direct booting to ubuntu.
OK I am planning to 100% work on ubuntu hence/even i have to learn more and more.

Here's more issue to build my Perfect linux.

1. how to add windows booting to grub after installing windows (my ubuntu is installed 1st)
2. How to enable NTFS read/write on NTFS partition disk, i tried download via automatix2 (its called fuse i think) but after installing there is nothing happen i still can't write on NTFS, there is no menu and i don't even know if its active.


Thanks guys for helping me to migrate to linux

---

### Post by Maestro23 on 2007-04-10
> **thoeng said:**
> Yay !! what a great community... i like it !!

Now my computer works  fine with direct booting to ubuntu.
OK I am planning to 100% work on ubuntu hence/even i have to learn more and more.

Here's more issue to build my Perfect linux.

1. how to add windows booting to grub after installing windows (my ubuntu is installed 1st)
2. How to enable NTFS read/write on NTFS partition disk, i tried download via automatix2 (its called fuse i think) but after installing there is nothing happen i still can't write on NTFS, there is no menu and i don't even know if its active.


Thanks guys for helping me to migrate to linux

#2: ntfs-3g: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

*It's in the repositories as well.

---

### Post by thoeng on 2007-04-11
Great !! now i am able to write on NTFS cheers guys.

Just a small curiosity .. how can i remove mounted HD icon on my desktop wallpaper ? it really depreciate my wallpaper ?

also # 1 .... anyone know ??

---

### Post by Obor on 2007-04-11
> **thoeng said:**
> Just a small curiosity .. how can i remove mounted HD icon on my desktop wallpaper ? it really depreciate my wallpaper ?

also # 1 .... anyone know ??

Alt+F2
gconf-editor
navigate to apps-nautilus-desktop-unclick volumes_visible

---

