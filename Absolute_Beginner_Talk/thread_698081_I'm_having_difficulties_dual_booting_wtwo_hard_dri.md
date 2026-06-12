---
title: "I'm having difficulties dual booting w/two hard drives (pic included)"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-02-15
Any advice on getting my slave drive which is xp to boot up on the menu when I fire the computer up.

My master drive is Ubuntu which I loaded on there and the slave has xp which was pre installed from another machine (meaning I just simply added the drive with xp already loaded)  I then installed Ubuntu 7.1 on the master and re-started the computer.

I get this screen after entering the xp boot selection.
[IMG]http://i187.photobucket.com/albums/x152/Indy452/00001.jpg[/IMG]

Kinda fuzzy (sorry)

Thanks for the help.

Neal

---

### Post by oilchangeguy on 2008-02-15
are you sure you jumpered the drives correctly? and what happens when you select one of the options in the list?

---

### Post by Presto123 on 2008-02-15
That is going to lead to a whole mess of trouble for you. The reason why is because you took it out of another computer that had it pre-installed and your hardware differences are probably leading you to this. Also, you will end up having to re-install Windows with a new key since it is a totally different computer.

As it stands now, if you want dual-boot, you really need to just re-install Windows onto that HD. Also, you may have some issues while re-installing it, because Windows will try to partition the whole system and boot loader.

There are some online guides that can help you install it without having to go through it deleting your Ubuntu partition, though.

You will need two things at least: 1)XP install disk and 2)a new key (Which you will have to buy).

---

### Post by Indy452 on 2008-02-15
I 'm pretty sure the jumpers are correct. The first (ubuntu) is master and the other (w/xp) is slave. 

When I enter "start windows normally"  The screen goes blank and then the computer re-boots and then I'm back at the menu to select which boot I want.

---

### Post by oilchangeguy on 2008-02-15
> **Indy452 said:**
> I 'm pretty sure the jumpers are correct. The first (ubuntu) is master and the other (w/xp) is slave. 

When I enter "start windows normally"  The screen goes blank and then the computer re-boots and then I'm back at the menu to select which boot I want.

don't be pretty sure. check the jumper settings on the hard drives. and try last known good configuration.

---

### Post by louieb on 2008-02-15
Yea that happens to me about half the time after resizing the windows partition. All I ever do is let it boot to safe mode. Then turn around and boot normally. 

Yours is different in that you didn't resize your window partition.
so like oilchangeguy suggested check you Master/Slave/Cable Select jumper setting.

IF thats ok then check file /boot/grub/menu.lst your windows entry should look something like this ( the map lines are to fake XP into thinking its on the master drive ).
```

title Win XP Home
      map (hd0) (hd1)
      map (hd1) (hd0)
      rootnoverify (hd1,0)
      makeactive
      chainloader +1
      boot

```

---

### Post by Indy452 on 2008-02-15
> **Presto123 said:**
> That is going to lead to a whole mess of trouble for you. The reason why is because you took it out of another computer that had it pre-installed and your hardware differences are probably leading you to this. Also, you will end up having to re-install Windows with a new key since it is a totally different computer.

As it stands now, if you want dual-boot, you really need to just re-install Windows onto that HD. Also, you may have some issues while re-installing it, because Windows will try to partition the whole system and boot loader.

There are some online guides that can help you install it without having to go through it deleting your Ubuntu partition, though.

You will need two things at least: 1)XP install disk and 2)a new key (Which you will have to buy).


I used this guide here [http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)

 I don't have an install disc am I screwed? What do you mean buy a new key?
Does microsoft not allow hardware upgrades with their os?

Now I don't know what to do. All I wanted was that xp for my wife and 14 y/o to use cause they are sooooo used to it. Any suggestions?

Neal

---

### Post by oilchangeguy on 2008-02-15
> **Indy452 said:**
> I used this guide here [http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)

 I don't have an install disc am I screwed? What do you mean buy a new key?
Does microsoft not allow hardware upgrades with their os?

Now I don't know what to do. All I wanted was that xp for my wife and 14 y/o to use cause they are sooooo used to it. Any suggestions?

Neal

read post #5

---

### Post by oedha on 2008-02-15
what if you just boot xp in safe mode ?

---

### Post by Indy452 on 2008-02-15
O.K I'll shut her down and check it again. I'll take a picture and you all can verify for me if it looks O.K.  The windows drive does have a little funnier jumper setting so It could be that one.  Thanks for the fast assistance and look for my reply here in an hour or less.

Neal

---

### Post by Indy452 on 2008-02-15
I guess I'll say that none of the boots other than the Ubuntu boots worked.  So safe mode windows was the same as normal mode (nothing).

---

### Post by oilchangeguy on 2008-02-15
> **Indy452 said:**
> I guess I'll say that none of the boots other than the Ubuntu boots worked.  So safe mode windows was the same as normal mode (nothing).

unplug the ubuntu drive, set the windows drive to master. and see if it will boot.

---

### Post by Presto123 on 2008-02-15
> **Indy452 said:**
> I used this guide here [http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)

 I don't have an install disc am I screwed? What do you mean buy a new key?
Does microsoft not allow hardware upgrades with their os?

Now I don't know what to do. All I wanted was that xp for my wife and 14 y/o to use cause they are sooooo used to it. Any suggestions?

Neal

Well...you may have to pay for a whole new XP key AND disk. Microsoft is limited in their hardware upgrade abilities and since you switched it over to a new computer, it would buck. BUT...you COULD make a call to Microsoft and see what you could do. I would prefer you to make the call yourself instead of taking MY word for it.

But, I will say this...I switched several parts of my computer around and the Motherboard was one...basically, it became a new computer and XP would boot up, but, after a restart, it prompted me for a key. I entered in the key from before, and it was a no-go.

Here's a thread I started when I first came here about dual boot with the same type of problems:[http://ubuntuforums.org/showthread.php?t=591711&page=1](http://ubuntuforums.org/showthread.php?t=591711&page=1)

---

### Post by torgrot on 2008-02-15
Are these IDE drives?  If so does the cable to connect the drives have three different color connectors on it?  If yes then you need to jumper them for cable select.  The drive at the end of the cable farthest from the controller is the master and the one connected to the middle of the cable is the slave.  If no then you can use the master/slave jumper settings.  I have been burned more than once due to this.  Verify, Verify, Verify.

torgrot

---

### Post by Indy452 on 2008-02-15
The jumpers on the xp drive are a little funky. I have it set as slave but there are sooo many options.

The jumper on the Ubuntu drive is master and quite easy to understand. These are older units I'm using so nothing new as far as hardware is concerned.

here's a pic of the two together [IMG]http://i187.photobucket.com/albums/x152/Indy452/computer%20stuff/00012.jpg[/IMG]

Here is the xp drive as close as my camera will allow. In the top left hand of the jumper guide (sticker) I'm using that guide because it was a master at one time and the master setting was in that guide. [IMG]http://i187.photobucket.com/albums/x152/Indy452/computer%20stuff/00008.jpg[/IMG]

And the Ubuntu drive. [IMG]http://i187.photobucket.com/albums/x152/Indy452/computer%20stuff/00007.jpg[/IMG]

As far as I can tell the jumpers are set correct.

I guess if all else fails I can put the xp drive back into its original computer and buy a router I guess but I'd rather not. As far as I'm concerned I'm through with windows.

---

