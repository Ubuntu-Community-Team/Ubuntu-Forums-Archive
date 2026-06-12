---
title: "AOL and Ubuntu 5.10"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by zonta on 2005-12-18
i have just installed the OS on HDD after trying the liveCD. Lovely feel and i got to terms in no time, the logic seems straight forward.

But, How do you get online with AOL using the ADSL Thompson SpeedTouch 330 usb.

I dont know if i can install the AOL cd into Ubuntu, i'll try

This is the onyl thing holding me to using WinXP PRO.

Please please please help, any info would be regarded

---

### Post by Weasel on 2005-12-18
I think you can do it with pppoeconf. I _think_.
```
sudo pppoeconf
```

---

### Post by JediHalo on 2005-12-27
I am getting ready to duel-boot [ubuntoo] on a Win98SE box, my main holdback is the ONLY connection to the internet on this dang box is AOL. (It is a computer I use for a volunteer job.) 

I am thinking if I can install and run it under WINE just for the dial up capabilities and avoid using any other AOL feature I should be fine... right? Has anybody done this yet? Succsess? Avoid? HELP!?!?!?!?
:confused: :confused: :confused: :confused: :confused: 

Much thanks!

~~JediHalo

[QUOTE=zonta]i have just installed the OS on HDD after trying the liveCD. Lovely feel and i got to terms in no time, the logic seems straight forward.

But, How do you get online with AOL using the ADSL Thompson SpeedTouch 330 usb.

I dont know if i can install the AOL cd into Ubuntu, i'll try

This is the onyl thing holding me to using WinXP PRO.

Please please please help, any info would be regarded[/QUOTE]

---

### Post by rooster on 2005-12-27
[QUOTE=JediHalo]I am getting ready to duel-boot [ubuntoo] on a Win98SE box, my main holdback is the ONLY connection to the internet on this dang box is AOL. (It is a computer I use for a volunteer job.) 

I am thinking if I can install and run it under WINE just for the dial up capabilities and avoid using any other AOL feature I should be fine... right? Has anybody done this yet? Succsess? Avoid? HELP!?!?!?!?
:confused: :confused: :confused: :confused: :confused: 
[/QUOTE]

When you have AOL as an ISP you don't have to use the AOL-software for connecting to the Internet, but you need the data (Telefone number, user name, PW for dial-in or the username/PW for DSL (normally sent by mail)).

So it depends on your situation - when you go broadband try "sudo pppoeconf" (PPP over Ethernet), when dialing try to use gnome-ppp.

Rooster

---

### Post by JediHalo on 2005-12-28
[QUOTE=rooster]When you have AOL as an ISP you don't have to use the AOL-software for connecting to the Internet, but you need the data (Telefone number, user name, PW for dial-in or the username/PW for DSL (normally sent by mail)).

So it depends on your situation - when you go broadband try "sudo pppoeconf" (PPP over Ethernet), when dialing try to use gnome-ppp.

Rooster[/QUOTE]
I tried this, And it kept disconnecting me over a dial-up TCP/IP, giving invalid username/password. Is there any certain way or suffix to use?

Thanks for all the help!

~~Jedi Halo

---

### Post by ryy705 on 2005-12-28
Hi, 
I am also trying to connect to AOL and I am using penggy to do it.  But the terminal keeps displaying "Can't open device /dev/ppp0: No such file or directory (2) Fatal error, exiting". Does anyone know what I have to do?

---

### Post by LostBear on 2006-01-06
Hi Guys,

You do not need anything special to use AOL and a speedtouch 330 other then what is decribed in the speedtouch howt else where in the forum. I know since i am using AOL and badger without anything such as pengy (this is only for dialup if i remember rightly.

---

### Post by mips on 2006-01-06
[http://ubuntuforums.org/showthread.php?t=112094](http://ubuntuforums.org/showthread.php?t=112094)

---

