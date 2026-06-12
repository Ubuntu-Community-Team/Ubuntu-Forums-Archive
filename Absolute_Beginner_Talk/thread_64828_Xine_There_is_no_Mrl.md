---
title: "Xine: There is no Mrl"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-12
Can someone please help with this. MRL? 

If not at least can someone tell me how to make it so Xine doesn't pop up automatically everytime i put a cd in the tray to play, especially if it doesn't work. It is annoying

If i can't use xine then i'll just have to use cd player instead

Many thx

--
sophtpaw

---

### Post by odin on 2005-09-12
[QUOTE=sophtpaw]Can someone please help with this. MRL? 

If not at least can someone tell me how to make it so Xine doesn't pop up automatically everytime i put a cd in the tray to play, especially if it doesn't work. It is annoying

If i can't use xine then i'll just have to use cd player instead

Many thx

--
sophtpaw[/QUOTE]

I think I have had that problem if I understood what you meant. 
First of all you have to create a link with:

"sudo ln -sf /dev/hdb /dev/dvd"  

(notice that /dev/hdb could change due to the IDE channel  where you pluged the dvd)

After linking your device you have to enable DMA for that drive with.

"sudo hdparm -d 1 $DVD_DEVICE"

Hope this helps

---

### Post by sophtpaw on 2005-09-12
[QUOTE=odin]I think I have had that problem if I understood what you meant. 
First of all you have to create a link with:

"sudo ln -sf /dev/hdb /dev/dvd"  

(notice that /dev/hdb could change due to the IDE channel  where you pluged the dvd)

After linking your device you have to enable DMA for that drive with.

"sudo hdparm -d 1 $DVD_DEVICE"

Hope this helps[/QUOTE]

Thank you Odin,

it is my cdplayer that i need to sort out. is it then:

"sudo ln -sf /dev/hdb /dev/cd-rom"  instead.

Given precise steps and command i can do it and willing to do any commandline maneouver. Otherwise i am a lame newbie duck though :razz: 

--
sophtpaw

---

### Post by odin on 2005-09-13
I'm not completely sure but try that,it should work.dont forget to enable dma

---

### Post by sophtpaw on 2005-09-13
[QUOTE=odin]I'm not completely sure but try that,it should work.dont forget to enable dma[/QUOTE]


Well i did and still no mrl error message.

Here is transcript:

conrad@x1-6-00-0b-6a-16-78-f0baraka:~$
conrad@x1-6-00-0b-6a-16-78-f0baraka:~$ sudo ln -sf /dev/hdb /dev/cd-rom
conrad@x1-6-00-0b-6a-16-78-f0baraka:~$ sudo hdparm -d 1 $CD-ROM_DEVICE
expected hwif_ctrl
conrad@x1-6-00-0b-6a-16-78-f0baraka:~$


what is expected hwif ctrl?

Any further suggestions and ideas welcome

--
sophtpaw

---

