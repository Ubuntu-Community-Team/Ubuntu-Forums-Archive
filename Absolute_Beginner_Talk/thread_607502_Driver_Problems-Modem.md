---
title: "Driver Problems-Modem"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by jake9069 on 2007-11-09
Just got Ubuntu yesterday and i cant get on the internet, because i have dial-up internet and i cant  get a driver for it unless I'm on the internet, and if i cant use my dial-up modem, then i cant get on the internet, i also need to get on the internet to download my nVIDIA driver, I'm on the internet now from XP, i was wondering if theres any way to get my Linux modem driver from XP to Ubuntu.

Modem:  PCI soft data fax modem with smartCP

Manufacturer: CXT

Hope that helps

Thanks,

---

### Post by jake9069 on 2007-11-09
Any help?

---

### Post by SpiritIsReality on 2007-11-09
howdy
If you create a fat32 partition, you can swap stuff back and forth from mic to ubuntu. What I've done is use a cd disk to transfer files.
Is this any help. It's a sticky on the Networking and Wireless forum.
[http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098)
I think as far as the nvidia driver goes that a
sudo dpkg-reconfigure xserver-xorg
run in a console if you can get to that, Ctrl-Alt-F2 , or try starting in single user.You have to press Esc key when it first starts watch for the message. After Esc key, then use down arrow key to choose recover mode, then press enter.
 and choose the nv driver,. If that doesn't work then try the vesa. In recovery mode, you are root, the administrator , straw boss.
all the best
trails
thanks bme

---

### Post by bme on 2007-11-09
find out what is the chipset used on your modem. there is usually a linux modem driver for most  modem chipsets.

---

### Post by jake9069 on 2007-11-09
How do i go about getting the chipset info? thanks for posting.

---

### Post by SpiritIsReality on 2007-11-09
howdy
try to get all the info you can read on it.
and post that and we can enter it into google.com and see what we come up with.? 
trails

---

### Post by jake9069 on 2007-11-09
Ok, it mite be awhile. could you wait?

---

### Post by SpiritIsReality on 2007-11-09
howdy
take all the time it needs, pard
trails

---

### Post by SpiritIsReality on 2007-11-09
howdy
[http://ubuntuforums.org/showthread.php?t=330698&highlight=HSFi+V.92](http://ubuntuforums.org/showthread.php?t=330698&highlight=HSFi+V.92)
from here [http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22PCI+soft+data+fax+modem%22+with+smartCP+&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22PCI+soft+data+fax+modem%22+with+smartCP+&btnG=Search&meta=)
trails

---

### Post by jake9069 on 2007-11-09
Im back and i think my chipset is Intel, although i don't really know becuase i put it on my flash drive, then got on windows and some of it was missing, so i mite have to go all the way back on ubuntu and do it again.

---

### Post by jake9069 on 2007-11-09
Ok now judging from the page you sent me i have a Conexant HSF 56k HSF Modem, also this guy has the same video card as me, but hes using a old version of ubuntu

---

### Post by SpiritIsReality on 2007-11-09
howdy
Now what's that? Is it tough to switch from windows to ubuntu.? Because if you
start ubuntu and run the lspci command, we're supposed to be able to see the chip name. According to [http://ubuntuforums.org/showthread.php?t=330698&highlight=HSFi+V.92](http://ubuntuforums.org/showthread.php?t=330698&highlight=HSFi+V.92)
What do you think. What makes you think it's intel.?
I know these modems are tough nuts to crack unless you get used to crackin ...
and that's what we're doin' now. I've got a pentium II sitting here with a modem that I used to use on dialup in Alberta when I was ranchin' buffalo, but I was runnin' w98se. So I'm learnin' how to linux that modem right now. No hurry on my account. We might even get you online in the next day or two. haha! I'm just sittin' here readin' .
trails

---

### Post by natehatewindows on 2007-11-09
you have the same as me i bet. i have a toshiba satellite. Can you mount your XP partition in ubuntu? what is your exact kernel? open the terminal and do this 

```
 uname -r 
```

---

### Post by jake9069 on 2007-11-09
Yes i can mount XP on linux, but again it will take some time -.-

---

### Post by natehatewindows on 2007-11-09
if you cant get your xp to mount in ubuntu you could use a flash drive or maybe even burn it to a cd. 
once you know what kernel you have go to [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php)

click "i agree" and then close to the bottom of the page click the "HSF Driver Download Page" link.
you will see a list of linux version, ubuntu is at the very bottom.....click it.

now under "kernel version" find your exact kernel and download it.

get it to ubuntu by puting it on your xp drive (you download it with xp so its already there), or a flash drive or you can try a CD.

when you get it to ubuntu double click the .deb file and it will install.

you will most likely need to do a couple other thing to get it to work but after you install the .deb try to connect with wvdial.

search for wvdial to see how to do that and read the install instrucitons on the linuxant site for better detail.

ill help you until we get this figured out :)

---

### Post by SpiritIsReality on 2007-11-09
howdy
[natehatewindows]("http://ubuntuforums.org/member.php?u=404660") ... thankyou 
trails

---

### Post by natehatewindows on 2007-11-09
i jsut went through this with the same chipset (sounds like) and gusty....its pretty frustrating. :)

---

### Post by natehatewindows on 2007-11-09
jake,
do you have ICQ??

---

### Post by jake9069 on 2007-11-09
Ok my kernal is--  uname -r 2.6.22-14-generic

---

### Post by jake9069 on 2007-11-09
What is ICQ?

---

### Post by natehatewindows on 2007-11-09
its a chat program, it would make this lots easier but dont worry about it.
 so you have a flash drive right?
what kernel do you have?

---

### Post by natehatewindows on 2007-11-09
ok so thats the same kernel as me
go to the link i gave you and downlaod the 2.6.22.14-generic driver

---

### Post by jake9069 on 2007-11-09
YAY finally a driver, so far so good, the only bad thing is, this driver is limited to a 14.4Kbps rate, which is bad, becuase its free.

---

### Post by natehatewindows on 2007-11-09
right but as far as i know, this is our only choice. after i got mine working i bought it and now its normal speed. so download it to your flash drive. and tell me when your done ok? :)

---

### Post by jake9069 on 2007-11-09
Its done, im putting it on my flash, but you say you bought it, maybe you could give me a copy? or if you could.

---

### Post by jake9069 on 2007-11-09
If you have MSN we could talk on there.

---

### Post by jake9069 on 2007-11-09
anyone there?

---

### Post by natehatewindows on 2007-11-09
yes, [email]n.lanham@hotmail.com[/email]

---

### Post by natehatewindows on 2007-11-09
waiting for you to message me.....

---

### Post by jake9069 on 2007-11-09
Sorry lol i took a shower, ill add you on msn

---

### Post by natehatewindows on 2007-11-09
ok

---

