---
title: "port forwarding bittorrent"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by millatoe on 2007-02-13
I'am trying to het bittorrent working but iam getting really slow download speeds

i think i have forwarded the ports correctly but still no change in speeds 
hers a screenshot of what ive done
[http://ubuntuforums.org/images/uf/attach/png.gif](http://ubuntuforums.org/images/uf/attach/png.gif)

i know its gota be an easy solution but i cant figure it out

ps iam a noob

---

### Post by millatoe on 2007-02-13
i've just tried... sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

but still no joy...

---

### Post by millatoe on 2007-02-13
even a hint will do:(

---

### Post by millatoe on 2007-02-13
so noone knows how to get bittoreent working??????????

---

### Post by cieje on 2007-02-13
those settings seem fine... make sure it's the correct ports in Bittornado.

Also... are you using a router with a hardware firewall? do you have ports forwarded there as well?

Have you tried any other torrents? that doesn't seem like the best test torrent to use to test speed... 1 seed and 1 peer with 34.9% downloaded...

---

### Post by millatoe on 2007-02-13
how do i find out if i got a router with a hardware firewall?

also i've tried a few popular torent files but never get more than a couple of seeds.

---

### Post by muguwmp67 on 2007-02-13
Thats a horrible file to test with.  

This file is a link to the 6.10 Ubuntu 386 cd.  It is much more active (847 seeds on my pc right now):

[http://releases.ubuntu.com/6.10/ubuntu-6.10-desktop-i386.iso.torrent]("http://releases.ubuntu.com/6.10/ubuntu-6.10-desktop-i386.iso.torrent")

You don't say whether you've used bittorrent before.  Be aware that it can take 5 to 10 minutes for it to attach to other clients and begin downloading.   So give it a while and check your speed.

> how do i find out if i got a router with a hardware firewall?
Are you using a router?  If you are, you will need to forward its ports to use bittornado.  You will have to use the router's configuration tool to do this.

---

### Post by millatoe on 2007-02-13
muguwmp67 that torrents kicking ***, 60 kbs after 20 secs:) 

ive used bittorent a bit in windows but not alot....

how did ya know it was a crap torrent?

ps iam at 120kbs now

ps iam at 135 kbs now 

ps iam at...this could go on lol

---

### Post by cieje on 2007-02-13
> **millatoe said:**
> muguwmp67 that torrents kicking ***, 60 kbs after 20 secs:) 

ive used bittorent a bit in windows but not alot....

how did ya know it was a crap torrent?

ps iam at 120kbs now

ps iam at 135 kbs now 

ps iam at...this could go on lol

it was a crap torrent because of what I said. Not enough seeds etc.

You should still check if you have a router  if you need to forward ports etc. I think when I downloaded ubuntu alt. the other day I was getting like 600KB/s or so.

(also... note that kbps is different that KB... 128kbps = 15.6 KB/s there's a huge difference between the two...)

---

### Post by millatoe on 2007-02-13
but how do i check if i have a router?

and also the torrent site was saying the file had 30 seeds available..and loads of leechers..
is it a bad idea to go on what the site says about seed numbers?

---

### Post by muguwmp67 on 2007-02-13
Its a bit of a smartass response, but did you or someone in your family buy one?  It would be the little box with the flashing lights that sits between your pc and the your cable/dsl modem if you did.

---

