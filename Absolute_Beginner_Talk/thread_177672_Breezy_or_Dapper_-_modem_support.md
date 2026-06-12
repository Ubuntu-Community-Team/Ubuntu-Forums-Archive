---
title: "Breezy or Dapper - modem support"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by learning on 2006-05-16
Just wondering which version I should be going with.  I am totally new to Linux. 

I have installed Breezy and so far love it.  I'm still having a few problems learning the new system, and have a lot to learn, but I like it.  My goal is to be totally ms free in the next few months.

I can not get my modem drivers installed though.  I followed the instructions in the [wiki]("https://wiki.ubuntu.com/DialupModemHowto#head-cc17ea0ff3df391406e74527f1aed569be04709f"), exactly.  but when I get to the end, it says:

FATAL: module lt_serial not found.

so I tried the "fix" for hoary (maybe I shouldn't have but nothing else was working).

Alas, my modem still does not work.  

We also have a Linksys wireless router I could use instead of the modem.  I hate to buy stuff for a project if I can't do it though.

Would it be easier for me to just buy a wireless card?  If so which one?

Thanks!

btw.. it is a Lucent/Agere modem

---

### Post by Sef on 2006-05-16
> Just wondering which version I should be going with. I am totally new to Linux. 

Dapper will have better support for modems; however, it is still in beta until 1 June.  It is fairly stable now, but there are still bugs to be worked out.  

> Would it be easier for me to just buy a wireless card? If so which one?


No.  Wireless is more problematic.

---

### Post by towsonu2003 on 2006-05-16
[QUOTE=Sef]Dapper will have better support for modems[/QUOTE]
I have to disagree. as far as I can see, (win)modem support seems to be the same in both releases (read: almost none)... Even documentation about setting up modems aren't offline, showing how small is the number of Dapper devels who actually use winmodems and know the limitations (like, not being able to go online)... 
[quote=learning]
Would it be easier for me to just buy a wireless card? If so which one?[/quote]
it's pretty much the same (wifi may be easier to make it work). I would go to a store which **guarantees** that they will take an opened item without questions and give you full refund. Than you can
[list]
[1] research on the web to find which is **likely** to work
[2] buy from that store
[3] return and get refund / another one if it doesn't work. [/list]
[quote=learning]FATAL: module lt_serial not found.[/quote]
you can try to see if you have the restricted modules installed (copy-paste in terminal): 
```

sudo apt-get install linux-restricted-modules-`uname -r`
```
than try 
```
sudo modprobe lt_serial
sudo modprobe lt_modem
```

if that doesn't work, paste the contents of your ModemData.txt (scanmodem) contents here. maybe someone can make sense of it. 

[quote=learning]
Linksys wireless router 
[/quote]
I think almost all linksys routers have one or more ethernet ports (cable). you could use that with ubuntu too.

---

### Post by ed_d on 2006-05-16
As far as modems go. I have had the best luck with external serial US robotics and Multitech. Seems anything else is just a pain.

---

