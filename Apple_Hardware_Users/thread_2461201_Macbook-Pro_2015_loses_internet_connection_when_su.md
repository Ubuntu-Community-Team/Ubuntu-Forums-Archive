---
title: "Macbook-Pro 2015 loses internet connection when suspended and bluetooth is off"
date: 2021-04-26
forum: Apple Hardware Users
---

### Post by schulzalbrecht on 2021-04-26
**PROBLEM **
Once the laptop is suspended (or lid closed) with bluetooth turned off and you resume your session back again (login again), it doesn't connect to the network anymore.
When I resume the session, I have aready tried to perform all the below steps and none of them make the system connect again to my wi-fi:

1. $ sudo service network-manager restart
2. $ sudo systemctl restart NetworkManager.service
3. When logging again, I tried to turn on the bluetooth, but it doesn't work. Once the connection is lost, turning on bluetooth doesn't help. 

This only happens when the bluetooth is turned off. _When it is turned on, I can close the lid and login back again and the internet will work as usual_.



[B]CURRENT WORKAROUND
[/B]Turn off and back on the network with _nmcli_.

$sudo nmcli networking off
$sudo nmcli networking on 

However, this is a workaround, i don't want to have to run cmd every time I close my laptop and login it back again. 


------

[B]
System information:[/B]
Intel Core i7-5557U CPU @ 3.10Ghz
x86
64-bit
Ubuntu 20.04
Kernel 5.8.0-50-generic 
BIOS version 425.0.0.0
biosdecodee 3.2

---

### Post by slickymaster on 2021-04-26
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by scorp123 on 2021-04-26
> **schulzalbrecht said:**
> 
[B]CURRENT WORKAROUND
[/B]Turn off and back on the network with _nmcli_.

$sudo nmcli networking off
$sudo nmcli networking on 

However, this is a workaround, i don't want to have to run cmd every time I close my laptop and login it back again. 


Why not auto-execute your workaround upon resume? Why do it manually when you can configure systemd to do it for you, automatically?

[https://unix.stackexchange.com/questions/124212/writing-a-systemd-service-to-be-executed-at-resume]("https://unix.stackexchange.com/questions/124212/writing-a-systemd-service-to-be-executed-at-resume")
[https://askubuntu.com/questions/1130747/run-command-after-resume]("https://askubuntu.com/questions/1130747/run-command-after-resume")

I've never tried this with a 2015 MacBook Pro but back in the day when my 2009 MacBook Pro wasn't as properly supported as it is now I also had to resort to such workarounds. And they tend to work surprisingly well.

---

### Post by schulzalbrecht on 2021-04-26
I will very likely do it, as you suggested. 
I posted the question though because I saw similar threads with different laptops/processors where the issue has been corrected with a new firmware installation. So I thought someone could give me a similar answer, as this would be a more elegant solution to this problem. 

Thanks for the links, I will definitely use them to implement a solution.

---

### Post by scorp123 on 2021-04-26
> **schulzalbrecht said:**
>  I posted the question though because I saw similar threads with different laptops/processors where the issue has been corrected with a new firmware installation. 

Over time I am sure this will happen. My MacBook Pro 5,4 (from 2009) works tip top with Linux now, out of the box. As if it was designed for Linux. Back in 2009/2010 running Linux on this thing was a nightmare, nothing worked, or needed lots of workarounds and hacks. I even needed to install a special "made for Apple machines" community version of Ubuntu to get it to boot.

Now? Nothing like that. I can use the normal x86_64 ISO like for a normal PC and everything just works on the first try. No more workarounds needed, no more hacking, no more messing with special configuration files. I boot the installer DVD or USB stick, I install .. and everything just works. And the performance is tip top.

I am sure it will be the same for your 2015 MacBook Pro sooner or later.

---

