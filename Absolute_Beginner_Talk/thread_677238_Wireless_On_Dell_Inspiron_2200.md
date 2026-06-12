---
title: "Wireless On Dell Inspiron 2200"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by alistaira on 2008-01-24
I'm having trouble getting the wireless to work on my** Dell Inspiron 2200**. Others have solved this problem but being a beginer I don't know how to use their solution. He says he used a "ndiswrapper" ( not sure what this is)  them quotes the code :
[B]ndiswrapper -i <dellinfile.inf>
modprobe ndiswrapper
ndiswrapper -m[/B]
I would be very greatful with any advice on this problem.

---

### Post by CJ56 on 2008-01-24
I've got an old Dell Inspiron with a Dell 1350 wireless card which uses a Broadcom chip. I got it to work like this -

I started with a clean install of Gutsy 7.10. I also had to use a wired ethernet connection to get the downloads I needed.

Once I'd installed Gutsy and got to first boot-up, I opened the Restricted Drivers Manager. I ticked the enable box for the wireless card; Gutsy then offered to download the necessary drivers to get the card working.

I then downloaded Wi-fi Radar from Synaptic (make sure you've enabled & updated your universe and multiverse repositories first). Wi-fi Radar appeared in the Internet section of the Applications menu.

After that, I unplugged the wired ethernet. I opened up Wi-fi radar, which picked up and listed all the local connections. I picked the one we use in this house, told Wi-fi Radar to configure itself (choosing Auto in all possible drop-down menus). After a bit of thought, it connected & now works well.

It worked for me, anyway... ;)

---

