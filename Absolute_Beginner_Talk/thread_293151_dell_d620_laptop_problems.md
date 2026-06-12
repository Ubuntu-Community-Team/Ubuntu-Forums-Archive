---
title: "dell d620 laptop problems"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by spud42 on 2006-11-04
Hi guys and gals,
                 I have installed ubuntu 6.06 and it was working ok except for i am unable to get it to run in the native 1280 800 mode. I have read several threads and still either dont understand properly or it just didnt work. It seem to only allow 1024 768 which is blury and stretched. Also it didnt show both cpu's. So i upgraded the kernal to dual core and that works ,however i now have lost the wireless network. As far as i can see it doesnt show up in device manager or under networking. I am new to linux  so i dont know my way around it yet. I followed some threads to dual boot the laptop to either XP or Ubuntu and thats working fine, i edited the boot menu to default to XP (sorry its a work laptop)and i removed the old kernal start lines from the menu. Yes i wish i hadnt now :-) . could any one show me how to fix my only 2 problems? to get my wireless network back (it worked before i upgraded the kernal)and to fix the display ?
thanks  tim

---

### Post by %hMa@?b&lt;C on 2006-11-04
for the display, have you tried 
sudo dpkg-reconfigure xserver-xorg 
when youdo that make sure to chose your proper resolutio.

---

### Post by ReaderRat on 2006-11-04
You can, in  Terminal, do:
```
sudo dpkg-reconfigure xserver-xorg
```
And go through the video setup. When it reaches the resolutions, just pick the ones you need with the spacebar.

---

### Post by Papa-san on 2006-11-04
You should start a second thread for the wireless problems. I have a Dell C 610 and managed to get wireless working initially. Once I upgraded to Dapper, it went Kaput. Managed to wrestle her into submission, finally. (Now I am trying to re-configure for DSL fron Cable) LOL!

Check the wireless link in my signature. It goes to a pretty nice walkthrough of most wireless issues.

---

### Post by spud42 on 2006-11-04
thanks for the prompt replies. i had tried the "sudo dpkg-reconfigure xserver-xorg" but i dont remember being given resolution options. i will try it again. also thanks for the wireless help link i will go read it now.

---

### Post by spud42 on 2006-11-04
ok i ran "sudo dpkg-reconfigure xserver-xorg" 

i did it twice, it gave me the option of 1280 800. this was the only one i selected. still when i restarted it was still in 1024 768 and the only difference is that i now have 800 600 and 640 480 options that i didnt have before. help ???!!!???

---

### Post by Papa-san on 2006-11-04
Take a look at ```
gedit /etc/X11/xorg.conf
```This should show what resolutions you are able to set yours to. (Write down the  command you used above to 'fix' the res. If you reboot after editing xorg.conf and it says there is a problem, get to a command prompt and type it in... It should at least get you back to where you are now. (The gedit command above is read-only unless you type 'sudo gedit /etc/X11/xorg.conf' )

---

### Post by spud42 on 2006-11-05
xorg.conf shows only 1280 800 and various colour bit depths from 24 bit default down to 1 bit. but the screen resolution still reports 1024 768 , and is a bit blury compared to XP running at 1280 800.

any other ideas?

---

