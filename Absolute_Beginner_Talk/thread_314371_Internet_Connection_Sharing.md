---
title: "Internet Connection Sharing"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Elpram on 2006-12-07
So I have an xbox thats right next to my computer, and my ubuntu box is connected to my router wirelessly.

What I want to do is plug my xbox into my ethernet card on my computer and have it take the connection from there (I don't feel like buying a 130$ wireless adapter)  I had this running on windows, but am attempting to make the switch over to linux; any help would be greatly appreciated.

---

### Post by ajgreeny on 2006-12-07
If your router is nearby why not wire it direct to the xbox?  It surely has 4 wired ports as well as wireless output.

---

### Post by lemonsCC on 2006-12-07
This would require a second network card...

---

### Post by ajgreeny on 2006-12-07
Why?  If you want to wire the xbox to the computer and use that as a router, why can't you wire the xbox direct to the router?  As I said before it must surely have a network wired port (or 4) to wire to.

Perhaps I'm just misunderstanding your setup, or maybe your original question.  If so, I apologise.

---

### Post by Elpram on 2006-12-07
Well the point is that its a wireless router that isn't nearby, and I'm not about to string cables around my house.

My computer has a wireless card (connected to the internet) and an open ethernet port.

---

### Post by lemonsCC on 2006-12-07
Good answer...  The following may be of interest:
[HowTo:  Share Internet Connection]("http://ubuntuforums.org/showthread.php?t=91370")
[Internet Sharing]("http://www.linuxforums.org/forum/linux-networking/41307-internet-sharing.html")

---

### Post by Elpram on 2006-12-07
Well I tried the first link, but when i get to step 2 and put in
# echo 1 > /proc/sys/net/ipv4/ip_forward
it tells me
bash: /proc/sys/net/ipv4/ip_forward: Permission denied

So I don't really know what to do.  I tried running it under gksudo and sudo (although im not entirely clear what the difference is)

---

### Post by lemonsCC on 2006-12-07
You may need to look for that sites nomenclature.  # may mean run as sudo.  so the command you would use would be ```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```

---

### Post by lemonsCC on 2006-12-07
Just went back and read the forum.

> Note: Type all the following commands in a root terminal, DO NOT use sudo.

To use root terminal I believe the command is ```
sudo su
```

---

### Post by Elpram on 2006-12-07
well that let me put in all the commands nicely, however the instructions don't seem to have had any effect whatsoever :(

---

### Post by lemonsCC on 2006-12-07
did you reboot?

Also you will need to specify your ip address on the Xbox.  read the following posts on the forum.

---

### Post by louieb on 2006-12-08
You may have missed it. You need a crossover cable between your PC and  your xbox. A regular cat 5 cable won't do it.

---

### Post by Elpram on 2006-12-08
Well I was using a regular ethernet cable when I was running windows, so I don't understand why it wouldn't be possible on linux.

I tried rebooting, and all that did was make it so that my internet no longer worked, so I had to uninstall those 2 programs.

I read something about Firestarter, but it didn't seem to work either :(

---

### Post by Elpram on 2006-12-09
Bump, does anyone happen to know any good front-end programs that might help me?

---

### Post by Elpram on 2006-12-11
Well, I figured it out, in case anyone wanted to know, i used this thread:
[http://ubuntuforums.org/showthread.php?t=74925](http://ubuntuforums.org/showthread.php?t=74925)

I needed a DHCP server, and for firestarter the key was to put my routers IP under the DNS Server field instead of dynamic.  Hope this helps someone. (In my case firestarter still greyed out the DHCP option even after it was installed and symbolically linked; i just put it in in the preferences after the wizard closed)

Thanks for everyones help in getting me up and playing xbox!

---

