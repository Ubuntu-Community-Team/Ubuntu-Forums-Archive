---
title: "[SOLVED] Some Questions"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by FrOzeN89 on 2007-11-15
Hey everyone, as of yesterday I finally got around to installing Linux for the first time ever (Ubuntu v7.10), and hope to use it as my permanent desktop environment. After much searching and playing around I'm going pretty well but stuck on a few things. My hard-drive is 120Gb and I've currently partitioned it into 3 parts: 10Gb ext3 (with Ubuntu installed), 3Gb swap, 10Gb NTFS (Windows XP installed). I've setup GRUB and got that all working nicely too, and I've also installed drivers on Windows to read ext2/3 partitions. I have the following questions:

[Answered] 1. With my remaining 90Gb I want to create a 50Gb ext3 partition. Is there a command I can use in the Ubuntu Terminal to do this, or what program should I download to do it with?

[Answered] 2. My mouse wheel works fine for scrolling up/down in Firefox, but the mouse-wheel-click doesn't seem to work (where it creates a icon and allows you to scroll up/down via movement like in Windows). How do I get that working?

[Answered] 3. What do the keys Ctrl + Alt + (F1 to F12) do? Some seem to bring up Terminal, etc. I'm just curious to what they are a little more specifically. Such as the difference between what tty2, tty3, tty4 is, and whatnot.

[Answered] 4. What is the swap partition used for by linux? Can I modify/tweak it in any way to increase it's performance or whatnot?

[Answered] 5. I've never looked into GNOME or KDE before, If I were to install KDE and remove GNOME what effects would that have on my system/setup (apart from looks)? Would I need to reinstall many programs and stuff or will they manage the transaction themselves? And a bit of an odd question, if I were to do that, would it then mean I'm essentially running "Kubuntu"?

[Answered] 6. Does the file system ext3 support "hidden files"? If so, how can I toggle a file's hidden/visible properties, and how can I setup folder explorer to show/hide hidden files when browsing? I assume hidden files are possible because when you right-click in the Open File Dialog it displays the option "Show Hidden Files".

7. When you bring up a menu it disables almost all the keyboard functionality. This is rather annoying as I can't take screenshots with a menu open, and can't use my media keys to change songs and such. Is there a way to modify this functionality?

[Answered] 8. I understand that with VirtualBox and VMware you install Windows on them, and they run your Windows on another system which you can then run programs for Windows inside of them. Opposed to WINE which runs a Windows program directly on a linux system and acts as a compatibility layer. Is that statement correct? Are there any other alternatives?

[Answered] 9. I haven't yet pressed it, and don't wish too. But does the "Power" button on my keyboard shut down Ubuntu, as it would if I were on Windows? If so, how do I disable it from doing that.

10. The hotkeys Mute, Vol Up, and Vol Down seem operate on the [image](http://img89.imageshack.us/img89/3603/screenshotpl1.gif) fine, but don't actually mute the sound or change the volume through the speakers. How do I set them up?

Thanks. :)

---

### Post by hyper_ch on 2007-11-15
> Hey everyone, as of yesterday I finally got around to installing Linux for the first time ever (Ubuntu v7.10), and hope to use it as my permanent desktop environment.

Good choice ;)

> 
1. With my remaining 90Gb I want to create a 50Gb ext3 partition. Is there a command I can use in the Ubuntu Terminal to do this, or what program should I download to do it with?

Can you open a terminal, then run this command:
```

sudo fdisk -l

```
and post the output here?

> 
3. What do the keys Ctrl + Alt + (F1 to F12) do? Some seem to bring up Terminal, etc. I'm just curious to what they are a little more specifically. Such as the difference between what tty2, tty3, tty4 is, and whatnot.

[http://en.wikipedia.org/wiki/TTY](http://en.wikipedia.org/wiki/TTY)

> 
4. What is the swap partition used for by linux? Can I modify/tweak it in any way to increase it's performance or whatnot?

SWAP is virtual ram provided by your harddisk. It's like the page.sys file on windows but it's not a file but an own partition. Recommended size: Double of your ram.

> 
5. I've never looked into GNOME or KDE before, If I were to install KDE and remove GNOME what effects would that have on my system/setup (apart from looks)? Would I need to reinstall many programs and stuff or will they manage the transaction themselves? And a bit of an odd question, if I were to do that, would it then mean I'm essentially running "Kubuntu"?

Gnome, KDE, Xfce etc. are just different approaches how a graphical user interface is built up and behaves. You can additionally add the others to your system and then upon login you could select into with environment you want to boot.

> 
6. Does the file system ext3 support "hidden files"? If so, how can I toggle a file's hidden/visible properties, and how can I setup folder explorer to show/hide hidden files when browsing? I assume hidden files are possible because when you right-click in the Open File Dialog it displays the option "Show Hidden Files".

Hidden files in Linux start with a "." --> .htaccess  or  .bash.rc
And second, how you show/hide those files depends on your file manager...

> 
8. I understand that with VirtualBox and VMware you install Windows on them, and they run your Windows on another system which you can then run programs for Windows inside of them. Opposed to WINE which runs a Windows program directly on a linux system and acts as a compatibility layer. Is that statement correct? Are there any other alternatives?

That is correct. There are different virtualization products and there's also alternatives for wine (but those are $$$)

> 
9. I haven't yet pressed it, and don't wish too. But does the "Power" button on my keyboard shut down Ubuntu, as it would if I were on Windows? If so, how do I disable it from doing that.

In the system settings you can customize your keyboard. You'll just have to delete the shortcut for that action.

---

### Post by Inxsible on 2007-11-15
You have way too much swap. How much memory do you have?

1) You can use GParted which is on the Live Cd to partition drives. I would recommend creating a separate home drive of about 15-20 GB

2) I am sorry I don't quite understand what you are talking about here.

4) You should not have more than 1 GB Swap because it won't be utilized much anyway.

6) Ctrl + H will show you hidden files in Nautilus.

9) I have my power button set up so that when its pressed, it will ask me what I want to do and show me all options like "Lock Screen", "Switch User", "Log out", "Suspend", "Hibernate", "Restart" and "Shutdown", just like what you get when you click the button in the top right corner of the default installation of Ubuntu.

---

### Post by mike555 on 2007-11-15
Reading the forums will answer most of your questions ..... as you use Ubuntu you will learn , for instance hidden files can be seen by clicking on  View (I think it is - I'm on my Mac right now)....
   your swap file use is set by how much memory you have and how much is needed ............ I like Ubuntu, but some like KDE , it's your call , KDE programs work in Gnome  and visa versa ....... I would not mess with Wine ........ better to boot into Windows or Linux , you can have both......

---

### Post by FrOzeN89 on 2007-11-15
1. The output of "sudo fdisk -l" is:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1aaf1aae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        1581     2931862+  82  Linux swap / Solaris
/dev/sda3   *        1582        2856    10241437+   7  HPFS/NTFS

2. I'll log onto Windows now and take a screenshot so I can explain it better.

4. I googled swap before I made it and heard it's ment to be about twice the size of your ram. I have 1Gb of ram, and possibly going to upgrade it to 2Gb, so I made a compromise of 3Gb swap.

Thanks so far. :)

---

### Post by Inxsible on 2007-11-15
> **FrOzeN89 said:**
> 1. The output of "sudo fdisk -l" is:


2. I'll log onto Windows now and take a screenshot so I can explain it better.

4. I googled swap before I made it and heard it's ment to be about twice the size of your ram. I have 1Gb of ram, and possibly going to upgrade it to 2Gb, so I made a compromise of 3Gb swap.

Thanks so far. :)Yeah, twice the size of RAM is just a general observation. It stops holding water when you have more than 1-2GB of RAM.

I have 2 GB of RAM and 1 GB of swap. I have never seen more than 33% of my swap being used.

So if you have 3GB of swap, you are most likely wasting that space, IMHO

---

### Post by Inxsible on 2007-11-15
Oh and I would still recommend you creating a separate home drive since you have just installed Ubuntu and are likely not to have installed much anyway. It has a lot of advantages.

---

### Post by FrOzeN89 on 2007-11-15
> **Inxsible said:**
> Oh and I would still recommend you creating a separate home drive since you have just installed Ubuntu and are likely not to have installed much anyway. It has a lot of advantages.Well the 50Gb partition I want to create will have all my music, movies, documents, etc. It's basically where all my files will be stored. I was going to use the 10Gb partitions for each Windows and Ubuntu strictly for their programs. What advantages does having another home partition offer?

2) When the mouse-wheel is clicked in Firefox (on Windows) it brings up that arrow thing. When you move the cursor up/down the page it scrolls at a speed depending on how close/far you are from where you clicked. This is also in Internet Explorer, Opera, and some other programs.
[img]http://img526.imageshack.us/img526/6360/wheelclickxy4.gif[/img]

---

### Post by Inxsible on 2007-11-15
If you have a separate home partition, then during the installation of the next OS you don't have to re-do all your user related settings.. This also helps when you have to re-install the OS, because of some problem.

---

### Post by Steveway on 2007-11-15
The middle-mouse-click has another (more usefull) use on Linux than on Windows.
You can copy and paste something that you marked with it.
So if you are following a guide and there is a command to enter in terminal, then mark the command and press the middle-mouse-button in your terminal, done.
If you really need that scroll thingie then I'm sure you can change it back in firefox.
Look into your about:config.

---

### Post by FuturePilot on 2007-11-15
You can get that working in Firefox by going Edit>Preferences. Go to the Advanced tab and Check the Auto Scrolling box. I'm not sure how to do that system wide though.

---

### Post by FrOzeN89 on 2007-11-15
1. I just installed gparted and created a 50Gb ext3 partition. I can access that from My Computer fine, but it won't let me do stuff other than view it because "I don't have permissions". How do I setup that partition so it acts as if I'm the owner?

A quick "sudo fdisk -l" now gives:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1aaf1aae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        1581     2931862+  82  Linux swap / Solaris
/dev/sda3   *        1582        2856    10241437+   7  HPFS/NTFS
/dev/sda4            2857        9230    51199155   83  Linux

2. Thanks. I only need it for Firefox, I'm not fazed about it system wide. It's just I've used it so long for scrolling websites it feels unusual without it.

@Inxsible: What size partition should I create as a home drive? Do only program preferences get stored in here? (Being that my Music/Movies/Documents will be elsewhere). And if I do create a partition for it, how do I tell Ubuntu that it's my home drive?

---

### Post by Inxsible on 2007-11-15
> **FrOzeN89 said:**
> @Inxsible: What size partition should I create as a home drive? Do only program preferences get stored in here? (Being that my Music/Movies/Documents will be elsewhere). And if I do create a partition for it, how do I tell Ubuntu that it's my home drive?

I would have a 10GB Root (which you already have)
15-20 GB /home
1GB swap
rest for a shared data drive (music, movies,pics etc)
and of course what ever Windows partitions that you have.

you can use this link to set up a separate home 

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by FrOzeN89 on 2007-11-15
It says you can't create more than 4 primary partions. I currently have 4 (Windows, Ubuntu, Swap, File-Storage). So I'll just leave it as-is and back up my home preferences from time to time.

---

### Post by Inxsible on 2007-11-15
> **FrOzeN89 said:**
> It says you can't create more than 4 primary partions. I currently have 4 (Windows, Ubuntu, Swap, File-Storage). So I'll just leave it as-is and back up my home preferences from time to time.
you can always create logical or extended partitions. Linux works just as well in Logical partitions.

---

### Post by FrOzeN89 on 2007-11-15
I followed those steps and after a few complications I finally got it setup:
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1aaf1aae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        1581     2931862+  82  Linux swap / Solaris
/dev/sda3   *        1582        2856    10241437+   7  HPFS/NTFS
/dev/sda4            2857       14593    94277452+   5  Extended
/dev/sda5            2857        4131    10241406   83  Linux
/dev/sda6            4132       14593    84035983+  83  Linux

sda1 = Ubuntu
sda2 = Swap (Didn't bother resizing it, because I couldn't put the left over anywhere)
sda3 = Windows XP
sda4 = Extended
- sda5 = Ubuntu /home Directory
- sda6 = 80Gb for Storage (ext3)

What I need to know now is how do I setup permissions on the sda6 so Ubuntu allows me to read and write to it?

---

### Post by Inxsible on 2007-11-15
> **FrOzeN89 said:**
> I followed those steps and after a few complications I finally got it setup:


sda1 = Ubuntu
sda2 = Swap (Didn't bother resizing it, because I couldn't put the left over anywhere)
sda3 = Windows XP
sda4 = Extended
- sda5 = Ubuntu /home Directory
- sda6 = 80Gb for Storage (ext3)

What I need to know now is how do I setup permissions on the sda6 so Ubuntu allows me to read and write to it?Depending on whom you want to allow access to, you can simply change ownership of the mount point.

If you created the mount point, you automatically have access to it. If you want other users to have access to it, either read only or read/write or read write and execute you can do it using the chown and chmod commands.

---

### Post by FrOzeN89 on 2007-11-15
I'm not sure I even created it with a mount point. All I did was make an 80GB ext3 partition using gparted.

How about this: When I go to "/home/#me#/Storage" I want it to use the 80Gb partition at "/dev/sda6". I always want it mounted with full permissions. Pretty much the same as how "/home" comes from "/dev/sda5". How do I set that up?

[EDIT] Nvm, I added "/dev/sda6 /home/#me#/Storage ext3 defaults 0 0" to the /etc/fstab file and it works now. :)

---

### Post by FrOzeN89 on 2007-11-15
Ok, is there a way I can point the following directories (the fstab didn't seem to work?):

/home/#me/Documents -> /home/#me#/Storage/Files/Documents
/home/#me/Music -> /home/#me#/Storage/Files/Music
/home/#me/Pictures -> /home/#me#/Storage/Files/Pictures
/home/#me/Videos -> /home/#me#/Storage/Files/Videos

---

### Post by FrOzeN89 on 2007-11-15
Everything's all sorted now. Turns out I needed to use the 'chown' command to change the permissions on the Storage partition. Once I did that I was able to simply make the files I want point by using Make Link's.

---

