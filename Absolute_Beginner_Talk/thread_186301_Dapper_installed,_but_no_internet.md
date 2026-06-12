---
title: "Dapper installed, but no internet"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-06-01
Ok, finally installed. But now the internet won't connect. It worked great on the Live CD. Since this was the first time I used the grub, it started in the topmost selection, the kernel. Was that my first mistake?

---

### Post by %hMa@?b&lt;C on 2006-06-01
Who is your ISP, and What protocal do they have (cable, ADSL, PPPoE)?
Did they give you a username and password to connect?

---

### Post by bt224 on 2006-06-01
It's Comcast cable running through my home network. I'm typing this on my Breezy Badger laptop. I installed Dapper on my desktop. It was working great running on the Live CD. After install, it quit working.

---

### Post by Rackerz on 2006-06-01
Have you checked your Network Settings in Dapper?

---

### Post by bt224 on 2006-06-01
yeah, set up as DHCP and DNS entries match laptop. I show eth0 as default. I have no idea what all the host list is showing.

---

### Post by darmot7 on 2006-06-01
i am having this problem as well. i use Comcast as well.

---

### Post by bt224 on 2006-06-01
We are not alone in this.

[http://ubuntuforums.org/showthread.php?t=182618&page=3&highlight=internet+connection](http://ubuntuforums.org/showthread.php?t=182618&page=3&highlight=internet+connection)

---

### Post by bt224 on 2006-06-01
Anyone even have a hint?

---

### Post by wastern on 2006-06-02
I'm also having this issue.  my wireless won't connect in Dapper, it worked great in previous versions

I've tried screwing with the Network setting and set it all up, but no luck.  For some reason my connection is set to 'lo' and just stuck in a loopback, i can't get it to set to eth1.  anyone know how to do that?  I tried selecting eth1 in the drop down of the network prefs as the default gateway, but it won't keep the setting

---

### Post by mrhello on 2006-06-02
I have the exact same problem!  And I think I have found a temporary solution.  Boot with the network cable pluged in (for hardlines).  When I boot without the network cable my internet goes down the tubes.  Im working on getting the wifi working, will post if I can get it.

---

### Post by apollyonis on 2006-06-02
Is this DHCP via a router (between your computer and the cable modem) or is it a straight line from your computer to the cable modem?

In the terminal, type in 
```
ifconfig
```

and post the results here.

---

### Post by bt224 on 2006-06-02
It is coming through a router.

EDIT: I can unplug the cable, plug it back in, and I have great internet for about 30 seconds. Same thing at startup. I did updates last night this way in hopes it would download a fix. It didn't. And it was no fun finding that out.

---

### Post by 11hjpphty76lkjj on 2006-06-02
Just to add to the list, my wifi works great in breezy, soon as I try and use dapper it dies..gonna stick with breezy until it looks stable in dapper.  Darn it.

Aaron

---

### Post by deadgobby on 2006-06-05
1. Power down your pc.
2. Unplug your cable modem and router. Wait at least 1 minute and plug the modem  and router back in.
3. Turn on the modem and  router. Wait for the modem do it self test.
4. Boot up your PC with the cable modem on.
 I have a cable modem and if I have the cable modem off after I boot up my pc. I will not have no internet connection. If I reboot my pc with the cable modem on. I can connect to the internet. So if you are use to turning on you modem after you boot up. Try this little simple trick.
Gobby

---

### Post by conman23456 on 2006-06-05
Should there not be a "eth0" file in /dev?

---

### Post by medya on 2006-06-05
[http://ubuntuforums.org/showthread.php?p=1099775](http://ubuntuforums.org/showthread.php?p=1099775)

---

