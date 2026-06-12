---
title: "cant connect to interenet using ubuntu livecd"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Luffypsp on 2008-03-07
^^^^^

so how??

---

### Post by Tatty on 2008-03-07
Can you give us some more info?

Are you trying to connect wirelessly or via ethernet cable?
What happens?

Please be as descriptive as you can.

---

### Post by Luffypsp on 2008-03-08
sorry for not being specific,i'm using a hardware router,and everytime i boot into my vista it usually will auto connect the internet,but when i'm on the ubuntu live cd the icon showed as not connected,hence the  
'x' symbol....so how do i make it auto - connected on the live cd??

---

### Post by handy on 2008-03-08
It may be as simple as an IPv6 problem with Firefox.

IPv6 Quick (Firefox) Fix

If you can't access the web through Firefox, though you know you have an internet connection via your modem/router, OR you find it very slow to move between servers, after which browsing that server is as fast as it should be? Try the following:

Enter ***about:config*** in Firefox's address field.

Enter ***ipv6*** in the new ***Filter***: field.

Double click on the line left in the display window to change it's boolean value to ***true***.

Restart Firefox.

---

### Post by PeterJS on 2008-03-08
You still haven't told us if it's a hardwired connection, or wireless, this is kind of an important detail. Hard wired connections should Just Work (tm), and we can trouble shoot other non-connection elements (dns, etc). Where as wireless it really depends on the card, some of them (mostly intel) work out of the box, Broadcom's can be made to work using either the bcm43xx driver, or the ndiswrapper. And beyond that'd you'd probably have to look up the documentation specific to your card.

---

### Post by Luffypsp on 2008-03-08
i dont know what kind of connection i have but definitely its not wireless because,there isnt any at my place.so i guess i have the hardwired one??

---

### Post by handy on 2008-03-08
> **Luffypsp said:**
> i dont know what kind of connection i have but definitely its not wireless because,there isnt any at my place.so i guess i have the hardwired one??

Do you have a cable going from your router to your computer?

---

### Post by Luffypsp on 2008-03-08
yeah of course because i dont have wireless....btw i just boot into knoppix and also cant connect the internet.when i type sudo pppoeconf ,both distros said no working ethernet card was found.....

---

### Post by jan quark on 2008-03-08
please post the results of these terminal commands:
```

sudo lshw -C network
```
```

lspci
```

---

### Post by uberlube on 2008-03-08
I have found in some live CD distros you actually have to go into the network options/internet options and scan for a connection, be it wired or wireless. Then you just activate it.

---

### Post by Luffypsp on 2008-03-08
btw i have bigger problems,but seriously i did it the normal way as i always did to boot ubuntu,but i tried last night,it showed the loading screen and "input not supported" appear in the middle of my monitor,then its blinking a few times until this message appear - [[ The Display Server has been shutdown about 6 times in the last 90 seconds.it is likely that something bad is going on.Waiting for 2 min before trying again on display ]]

so i wait for two minutes and itss blinking again and gave this maessage again.i trited a few times but no success.so i tried booting linuxmint and knoppix.linux mint gave the same result as ubuntu but knoppix run normally....

so please help again....

---

### Post by uberlube on 2008-03-09
input not supported means that you have to specify what your vga is during the boot try adding vga=791 into the boot procedure of the live cd.

---

### Post by Luffypsp on 2008-03-09
but why i was succesfully to boot it twice before this happened??

---

### Post by Luffypsp on 2008-03-09
can you tell me how to add that??i cant see any place to add anything....

---

### Post by jan quark on 2008-03-09
> adding vga=791 into the boot procedure of the live cd.


see here
[LIST]
[*][https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[/LIST]

---

### Post by uberlube on 2008-03-09
While 'start or install ubuntu' is highlighted, press F6 and delete 'quiet splash' and add 'vga=791' then press enter.

---

### Post by Luffypsp on 2008-03-09
i see,i'll try again....does it matter what number of VGA i use??will it give any side effects??

---

### Post by uberlube on 2008-03-09
Yes it does matter what number you use. They are relevant to your resolution and color depth.

---

### Post by Luffypsp on 2008-03-09
ok i get it to work.i didnt do anything,seriously...i shutdown my computer and open it again.i forgot to add the vga thing and hit the start ubuntu menu,i was thinking on restarting it but it just working again...so the only thing i cant access is the net.....and thnxs guys...

---

