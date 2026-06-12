---
title: "Wireless, fixed IP and WinXp"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by stena on 2008-04-17
Hi, 

It is a question for Ubuntu :). I have a desktop running on WinXP. It has 1 Ethernet and 1 wireless card. The idea is to use WinXP as an Access Point for my laptop (dualboot WinXP and Ubuntu Gutsy) and also have Internet through it's Ethernet card. I also gave a static IP to both connections and bridged them. On my laptop running WinXp I also gave a static IP (same network, same subnet) to my wireless connection. Everything works fine. But, I do not want to use WinXP any more, I want to use Ubuntu.

However, when my wireless (Ubuntu) is in Roaming mode, it finds a network, it even connects to it but no internet. The IP I get from desktop WinXP machine is 169.254.23.121 or something (I know that IP comes from XP). If I try to give static IP to my wireless card, it doesn't connect at all (and I do not see that it tries at all). Wireless under Ubuntu, by the way, works perfectly in Roaming mode in all other cases (regular access points around).

So, how to setup static IP on my wireless card under Ubuntu and how to make it work? And, can this combination (with XP) even work under Ubuntu? If so, what do I have to do?

Thanks in advance.

stena

---

### Post by zackf on 2008-04-17
Hi Stena,

Are you dual-booting or running Ubuntu on a Virtual Machine?

---

### Post by stena on 2008-04-17
I have a dual-boot (from GRUB), but no, I do not run Ubuntu on VM. Pure Ubuntu :)

---

### Post by zackf on 2008-04-18
The 169.254 ip range is a default when computers can't find a valid IP. So that leaves me with two more questions. Is your XP machine set up to share it's internet connection, and what type of router are you using?

---

### Post by OffAxis on 2008-04-18
I'm confused about the setup.
> On my laptop running WinXp I also gave a static IP (same network, same subnet) to my wireless connection. Everything works fine. But, I do not want to use WinXP any more, I want to use Ubuntu.

Do you want to trash the XP install on the desktop or the laptop?

And in XP the bridging on the desktop machine (wired to wireless) works correctly with the laptop's xp / wireless networking setup. Is that right?
It's when you flip over to the ubuntu side on the desktop that there's a breakdown?

---

### Post by stena on 2008-04-21
OK this is the case.

I have WinXP on my desktop (bridging wireless and ethernet). On my laptop I have dual-boot, XP and Ubuntu. I want to use the bridged connection on my desktop to access internet from my laptop (basically, I want to use my XP desktop as an access point).

Setup is like this: all IPs are DHCP on XP desktop - wireless and ethernet and of course, since I bridged it, now bridge has an IP address from DHCP router. On my laptop I setup DHCP on XP and UBUNTU. When i boot in XP on my laptop everything works smoothly, but I can not do anything in Ubuntu. In Ubuntu it connects, but no internet connection. I tried to setup default gw manually, but it doesn't work as well.

I hope I am clear no. Sorry if it wasn't a case before.

Thanks,
Vladimir

---

### Post by zackf on 2008-04-21
I wonder if it's more an issue with your wireless drivers in Ubuntu. For me I was using the stock Broadcom drivers but had to switch to ndiswrapper because I was having similar issues. Have you tried connecting to any others wifi access points with Ubuntu?

---

### Post by stena on 2008-04-21
Yes I did try to connect to other wireless points, and everything works just fine.

Vladimir

---

### Post by zackf on 2008-04-21
Vladmir,

Have you tried a Static IP on the Ubuntu machine? I'm not sure that's the solution here as it sounds like it's not able to contact the router for an IP, but it's worth a shot.

---

### Post by stena on 2008-04-21
Well, yes I did try with static IP on my Ubuntu. The problem is that I can not see that Ubuntu is even trying to connect in that case). Actually, I would like to make it with static IP, but it just doesn't work.

Thanks,
Vladimir

---

