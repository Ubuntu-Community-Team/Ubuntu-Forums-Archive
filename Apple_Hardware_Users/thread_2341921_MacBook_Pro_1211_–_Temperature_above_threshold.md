---
title: "MacBook Pro 1211 – Temperature above threshold"
date: 2016-11-02
forum: Apple Hardware Users
---

### Post by 666.axel on 2016-11-02
Hi all,

I am trying to install Ubuntu 16.04.1 LTE in my old MacBook Pro 1211 Intel Core 2 Duo but after booting from USB and selecting install or Live I get this message and cannot continue:

```
[COLOR=#111111][FONT=Consolas][ 1466.805429] CPU0: Core temperature above threshold, cpu clock throttled (total events = 1)
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas][ 1466.805429] CPU1: Core temperature above threshold, cpu clock throttled (total events = 1)[/FONT][/COLOR]
```

The numbers within "[]" are different each time I try and the ones I typed above are just placeholders to show you the structure of the message. 


Find below the things I have tried so far:

- Clean every grain of dust, clean thermal paste and re-apply new thermal paste. Heat sink is pristine now.
- I have used rEFInd[SIZE=2] to boot and als[/SIZE]o the regular boot holding alt down.
- Trying to isolate the problem I left the laptop cooling down for several hours and then tried to install Ubuntu and I got the same problem. I got the message around 20 seconds after booting up and the laptop was cold at touch.
- Tried to boot with keyboard disassembled to get extra air out.
- Tried hoovering air from the exit of the heat sink to get extra air out.


I believe it could be a software problem as my cpu is not hot when the message pops in.


I hope this makes sense. 

Thank you all,
Axel.




[SIZE=4]UPDATE:

[SIZE=2]I followed [this]("http://www.macworld.co.uk/how-to/mac/how-install-linux-on-mac-3637265/") guide and it worked! The key is to edit the boot entry. After editing the boot entry I could go to live Ubuntu and install from there. 



[/SIZE][/SIZE][SIZE=4]NEXT ISSUE:
[SIZE=2]
After the install it has to restart and it hungs in the first boot on the purple screen. I have followed multiple threats in this forums about the purple screen but I am unable to get GRUB, I have tried pressing shift, sift+F2 etc... 
Anybody knows how to install the drivers for my Nvidia if I don't have access to GRUB or Ubuntu?


[/SIZE][/SIZE]
[SIZE=4]UPDATE2:[/SIZE][SIZE=4][SIZE=2]

It seems like I have a graphic's problem but found I way to deal with it:
Press shift+esc as soon as you get the purple screen then press 'e' to edit the boot options. Look for 'quiet splash' and replace it with 'quiet splash nomodeset'. Then press F10 and it should boot without any problems.




I hope this is useful for other people with the same issue. 



 Cheers,
Axel.
[/SIZE]
[/SIZE]

---

### Post by howefield on 2016-11-02
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by sdansmith on 2016-11-02
I don't have a specific answer for you, but I just installed 16.04 a few days ago and I too have noticed that my MacBook Pro 2012 is running warm. Mine hasn't returned any errors, for which I'm grateful, but I will be following this in the hopes of a resolution.

---

### Post by 666.axel on 2016-11-03
Hi sdansmith,

Bear in mind that the heat sink is placed on the lower case so that area will always feel warm. Make sure you track the temperature with a monitor software to be sure but warm should be normal. 

Cheers,
Axel

---

