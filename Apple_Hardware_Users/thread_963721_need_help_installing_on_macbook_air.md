---
title: "need help installing on macbook air"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by twoodcc on 2008-10-30
hi. i have a macbook air, and would like to dual boot leopard and ubuntu. now, i made a bootcamp partition, burned the 8.10 alternate cd last night, and booted the cd.

i then erased the bootcamp partition and made a new partition on "/". 

it then seemed to install fine, but i can't boot to it. if i hold down 'alt', on startup, it does not show the partition, only the leopard partition.

please, can someone tell me what i did wrong? i tried to go along the instructions i found by searching, but still can't get it to boot.

thanks

---

### Post by cyberdork33 on 2008-10-30
Install rEFIt and sync the partitions. This is a known issue and still has not been fixed.

[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by twoodcc on 2008-10-30
thanks for the reply

ok, i installed rEFIt, and i rebooted, but it did not start the bootloader. how do i sync the partitions?

---

### Post by twoodcc on 2008-10-30
ok, i got rEFTt to work. but when it boots, i only get a command prompt.

---

### Post by cyberdork33 on 2008-10-30
> **twoodcc said:**
> ok, i got rEFTt to work. but when it boots, i only get a command prompt.
So it booted Ubuntu? 

Maybe you chose to install a commandline system? (That option is available on the alternate Installer). Can you login at the commandline? Any helpful information there?

---

### Post by twoodcc on 2008-10-30
i can login at the command line. but that's it. does this mean that i installed the wrong version?

---

### Post by cyberdork33 on 2008-10-30
> **twoodcc said:**
> i can login at the command line. but that's it. does this mean that i installed the wrong version?

Sounds like you installed the server edition or a commandline-only system.

---

### Post by twoodcc on 2008-10-30
well, i thought i didn't, but anything is possible. so i downloaded the desktop version today, and am burning it. so when i install it this time, do i have to install grub? or just skip it?

---

### Post by twoodcc on 2008-10-30
ok, so i don't know what version i installed to begin with, but it was not the version i wanted. i downloaded the one from today, and i am on it right now. 

thanks for the help. i am using a restricted driver for my wireless on my macbook air, is that fine to use? anything else i need to know?

---

### Post by twoodcc on 2008-10-30
well, i'm not sure what happened, but it just crashed. it froze, with only firefox open with 2 tabs, connected to my wireless. and i had my external dvd-drive connected, and that's it. i walked away, came back, the fans were going crazy and it was frozen

---

### Post by cyberdork33 on 2008-10-30
> **twoodcc said:**
> well, i'm not sure what happened, but it just crashed. it froze, with only firefox open with 2 tabs, connected to my wireless. and i had my external dvd-drive connected, and that's it. i walked away, came back, the fans were going crazy and it was frozen Your only other option on the wireless would be ndiswrapper.

---

### Post by twoodcc on 2008-10-30
thanks. is one better than the other?

also, my fans seem to be running all the time, even though i just have firefox running and terminal. do i need to install anything else to help that?

---

### Post by kosumi68 on 2008-10-30
> **twoodcc said:**
> thanks. is one better than the other?

also, my fans seem to be running all the time, even though i just have firefox running and terminal. do i need to install anything else to help that?

What version of MBA do you have?
```

sudo dmidecode | grep Product

```

Hope you checked this page: [https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid](https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid)

wl is working very well indeed. no need to use anything else.

The "just running firefox" could be your problem. Firefox 3 does a lot of things in the background unless you tell it not to. Try googling for "firefox prefetch".

The screen brightness makes a big difference too. Full throttle does tend to make the machine a bit hot.

The trackerd daemon might also cause a lot of activity.

If, unsure, run 'top' and watch it for a while. My system is always at 99% idle with firefox up, if I don't do anything.

---

### Post by cyberdork33 on 2008-10-30
Listen to him, he has more experience with the MBA.

---

### Post by twoodcc on 2008-10-30
> **kosumi68 said:**
> What version of MBA do you have?
```

sudo dmidecode | grep Product

```

Hope you checked this page: [https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid](https://help.ubuntu.com/community/MacBook Air 1%2C1 and Intrepid)

wl is working very well indeed. no need to use anything else.

The "just running firefox" could be your problem. Firefox 3 does a lot of things in the background unless you tell it not to. Try googling for "firefox prefetch".

The screen brightness makes a big difference too. Full throttle does tend to make the machine a bit hot.

The trackerd daemon might also cause a lot of activity.

If, unsure, run 'top' and watch it for a while. My system is always at 99% idle with firefox up, if I don't do anything.

output of what version Air i have:

```
	Product Name: MacBookAir1,1
	Product Name: Mac-F42C8CC8
```

thanks for the reply. i am around 95% idle, and my fans are running. i just turned the brightness down. the keyboard controls for brightness and eject button worked out of the box for me.

---

### Post by kosumi68 on 2008-10-30
> **twoodcc said:**
> output of what version Air i have:

```
	Product Name: MacBookAir1,1
	Product Name: Mac-F42C8CC8
```

thanks for the reply. i am around 95% idle, and my fans are running. i just turned the brightness down. the keyboard controls for brightness and eject button worked out of the box for me.

Thanks - just wanted to confirm the subversion of the machine was the normal one.

Yes, the graphics card (GMA965/X3100) is quite well supported by now. Basically, if you follow the wiki page, you should have a box with everything working 100% - except for the front microphone.

I would love to hear about any differing experiences.

---

### Post by twoodcc on 2008-10-31
well, it crashed again. i turned the prefetch setting off in firefox, and that seemed to help with the fans. but again, only firefox and terminal running, and it just froze. 

i had walked away, and the screen was black. i came back, moved the mouse to activate the screen, and it came on. i think clicked a few links in firefox and then turned away to my other computer for something, came back just a minute later, and it has froze.

---

### Post by twoodcc on 2008-10-31
ok well it crashed again. i don't know what is going on here.

here is the output from the "last" command:

```
tmac     pts/0        :0.0             Fri Oct 31 01:16   still logged in   
tmac     tty7         :0               Fri Oct 31 01:15   still logged in   
reboot   system boot  2.6.27-7-generic Fri Oct 31 01:15 - 01:16  (00:01)    
tmac     tty7         :0               Fri Oct 31 00:45 - crash  (00:29)    
reboot   system boot  2.6.27-7-generic Fri Oct 31 00:45 - 01:16  (00:31)    
tmac     pts/0        :0.0             Thu Oct 30 23:00 - crash  (01:44)    
tmac     tty7         :0               Thu Oct 30 22:44 - crash  (02:00)    
reboot   system boot  2.6.27-7-generic Thu Oct 30 22:44 - 01:16  (02:32)    
tmac     tty7         :0               Thu Oct 30 22:34 - 22:43  (00:08)    
tmac     tty7         :0               Thu Oct 30 22:18 - 22:34  (00:15)    
reboot   system boot  2.6.27-7-generic Thu Oct 30 22:18 - 22:43  (00:24)    
tmac     tty7         :0               Thu Oct 30 20:39 - crash  (01:39)    
reboot   system boot  2.6.27-7-generic Thu Oct 30 20:38 - 22:43  (02:04)    
tmac     tty7         :0               Thu Oct 30 20:36 - down   (00:00)    
tmac     tty7         :0               Thu Oct 30 20:27 - 20:35  (00:08)    
reboot   system boot  2.6.27-7-generic Thu Oct 30 20:27 - 20:37  (00:09)
```

---

### Post by twoodcc on 2008-10-31
and it crashed again last night before i went to bed. can someone help me out with this? if it keeps crashing, i'll have to just stick with leopard.

---

### Post by cyberdork33 on 2008-10-31
> **twoodcc said:**
> and it crashed again last night before i went to bed. can someone help me out with this? if it keeps crashing, i'll have to just stick with leopard.
unless you can determine what exactly is causing the crash there is not much to say...

You could try downloading / burning / installing again to ensure something didn't get corrupted, but you seem to be the only one that has been experiencing this.

---

### Post by twoodcc on 2008-10-31
> **cyberdork33 said:**
> unless you can determine what exactly is causing the crash there is not much to say...

You could try downloading / burning / installing again to ensure something didn't get corrupted, but you seem to be the only one that has been experiencing this.

is there any log files i can look at? or something so i can figure out why it keeps crashing? it crashed again, and now i'm in leopard at the moment. 

of course this would happen to me when i decide to try ubuntu again.

---

### Post by kosumi68 on 2008-10-31
There is a possibility that this problem is hardware related. You might want to run the memory test, which is an option then you boot. Don't be alarmed if there is one or two errors from that test, as there is a known problem with memtest and low memory on macbooks. Still, as cyberdork says, nobody else seems to have experienced this problem.

---

### Post by twoodcc on 2008-10-31
> **kosumi68 said:**
> There is a possibility that this problem is hardware related. You might want to run the memory test, which is an option then you boot. Don't be alarmed if there is one or two errors from that test, as there is a known problem with memtest and low memory on macbooks. Still, as cyberdork says, nobody else seems to have experienced this problem.

thanks for the reply. i can try that, but it seems that there is surely a way to show what is causing the computer to freeze. is there no command or no crash logs anywhere?

---

### Post by kristina-dev on 2009-10-17
I tried multiple times with the same result.  I got a little further by using the kernel parameter pci=bios.  It finishes the kernel stuff now, but then hangs a while and displays a BusyBox initramfs prompt that is either a) frozen or b) my keyboard doesn't work.  

Any ideas?

---

### Post by kristina-dev on 2009-10-18
Sorry, wrong thread :(

---

