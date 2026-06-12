---
title: "No internet"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by nonpareilpearl on 2006-11-20
Hello again :) I posted a bit ago about Ubuntu not recognizing my ethernet card and thus I do not have internet access. When I am in Windows everything functions normally and I do have internet access  (both wired and wireless).

I was asked if I was using eth0 or eth1, and I said eth0 because I only have one ethernet card in there. Truth be told, though, when I enter ifconfig in the terminal it doesn't mention either eth0 or eth1 and when I enter ifconfig -eth0 (as I believe this is the proper command) it gives me an error. From looking in the Device Manager in the Windows section I know it is a Broadcom card, but I am not sure what other information you need. Help? ](*,)

---

### Post by PartisanEntity on 2006-11-20
Are you behind a router?

---

### Post by carlosqueso on 2006-11-20
what's the output of ifconfig?

---

### Post by kiyometane on 2006-11-20
try the command "sudo dhclient"
i had a symillar problem and it worked
let me know if that work for u as well

---

### Post by nonpareilpearl on 2006-11-20
**PartisanEntity:** no router
**carlosqueso:** > Link encap: Local Loopback
inet addr: 127.0.0.1 Mask: 255.0.0.0
inet6 addr: ::1/128 Scope: Host
UP LOOPBACK RUNNING MTU:16436 Metric: 1
Rx packets:18 errors:0 dropped:0 overruns:0 frame:0
TX packets:18 errors:0 dropped:0 overruns:0 carrier: 0
collisions: 0 txqueuelen:0
RX bytes: 1284 (1.2 KiB) TX bytes: 1284 (1.2 KiB)
**kiyometane:** when I run the command it gives me a bunch of "failed" lines, as below:> SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:14:bf:3a:1b:91
Sending on   LPF/eth1/00:14:bf:3a:1b:91
Listening on LPF/eth0/00:0d:56:3b:eb:92
Sending on   LPF/eth0/00:0d:56:3b:eb:92
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
grep: /etc/resolv.conf: No such file or directory
chown: failed to get attributes of `/etc/resolv.conf': No such file or directory
chmod: failed to get attributes of `/etc/resolv.conf': No such file or directory
bound to 192.168.1.101 -- renewal in 39937 seconds.

I should also note that I have tried going to System->Administration->Networking several times and while it lists wireless (when my card is in) and Ethernet connections when I try to enable either of them it seems to "think" for a moment before "enabling". Then when I reopen the window nothing has changed and I still can't access anything.

---

### Post by nonpareilpearl on 2006-11-20
Anyone with any thoughts please let me know.. I've been trying to get this to work for a week. Feel free to IM me if I'm on as well.

---

### Post by bootfinder on 2006-11-21
I have the same problem (I'm very new to Ubuntu, only installed it yesterday). Although it says that eth0 is active, when I plug a cable between the PC and my ethernet hub, the light does not glow on the hub.

---

### Post by maximouse on 2006-11-21
Can you post the output from "sudo scanpci"?
It might give something to go on.

---

### Post by bootfinder on 2006-11-21
I have tried to copy the text from the Ubuntu PC to this Windows PC using a USB memory stick, but I just get an empty text file! There's too much text to copy-type it. Is there something specific I should look for... I can recognise the sound car, graphics card, but there are several Intel cards too.

---

### Post by maximouse on 2006-11-21
> **bootfinder said:**
> I have tried to copy the text from the Ubuntu PC to this Windows PC using a USB memory stick, but I just get an empty text file! There's too much text to copy-type it.

Yes, ofcourse. I didn't think of that.

Try "sudo scanpci|grep net", or just look for something that looks like a network card.

Also, you said you have both wired and wireless. Is a laptop you have, and if so what make/model?

---

### Post by bootfinder on 2006-11-21
OK, thanks, now I get:
"Silicon Integrated Systems [SiS] SiS900 Fast Ethernet"
(and the line before is:
"pci bus 0x0000 cardnum 0x0b function 0x00: vendor 0x1039 device 0x0900")

It's an ATX desktop, and I do not have wireless, just an ethernet port.

---

### Post by maximouse on 2006-11-21
> **bootfinder said:**
> OK, thanks, now I get:
"Silicon Integrated Systems [SiS] SiS900 Fast Ethernet"
(and the line before is:
"pci bus 0x0000 cardnum 0x0b function 0x00: vendor 0x1039 device 0x0900")

What do you know, that happens to be exactly the same card I have on this machine. :)
Check if the module is loaded "cat /proc/modules | grep sis900". It should return 1 or 2 lines.
If it doesn't try "sudo modprobe sis900", if it does, see if there is an uncommented line in /etc/iftab and comment it out.
Then add:
auto eth0
iface eth0 inet dhcp
to /etc/network/interfaces (see that there are no other lines containing eth0).
then try "sudo /etc/init.d/networking restart".

That might fix it. It's not an exact approach, I'm just trying to cover everything I can think of that might be wrong with it.

---

### Post by maximouse on 2006-11-21
Ok, wonder where I left my head today. I just noticed that there was two different people with network problems on this thread.

---

### Post by bootfinder on 2006-11-21
Thanks for your help... Firstly, when I enter the "cat..." command I get:
> sis900 22912 0 - Live 0xd09a9000
mii 5888 1 sis900, Live 0xd098d000

Secondly, when I try to edit and save either of the 2 files you mentioned, I cannot because they're read-only, and I can't change the properties because they're owned by root, and I don't know how to log in as root (I really am very new to Linux!)

---

### Post by bootfinder on 2006-11-21
sorry, probably me that's confusing you!

---

### Post by Henry Rayker on 2006-11-21
try a 
sudo gedit /etc/iftab
that should let you edit that file, then a
sudo gedit /etc/network/interfaces
to edit the interfaces file.

---

### Post by maximouse on 2006-11-21
Ok, the modules are loaded properly then.
You had the problem that the light on the hub does not glow. Do you dual boot to windows with the machine, and if so do the network work then?

What result do you get when you run "ifconfig | grep eth"? Do you get nothing, or a line starting with eth0, or eth1 or something else?

You can edit the files with the command "sudo gedit filename" or "sudo nano filename" if you don't have X (graphical desktop). Or just "sudo gedit" and then open the file from the editor. The sudo command runs things as root. If you want to "login as root" you can type "sudo su -", but this is not a good idea if you don't know what you are doing, since you might delete the entire HD by mistake, or something along those lines. :)

---

### Post by bootfinder on 2006-11-21
thank you ***very much*** for your help. I have got it working now, and I'm afraid I have to report ([COLOR="Red"]very shamefacedly[/COLOR]) that I discovered the CAT5 cable wasn't properly plugged in!

---

### Post by maximouse on 2006-11-21
> **bootfinder said:**
> thank you ***very much*** for your help. I have got it working now, and I'm afraid I have to report ([COLOR="Red"]very shamefacedly[/COLOR]) that I discovered the CAT5 cable wasn't properly plugged in!

I had a feeling it might be a cable problem, because the light should go on as soon as the module is loaded. :)

---

### Post by nonpareilpearl on 2006-11-21
to **bootfinder**: you said at one point that you were having difficulty copy/pasting text between Windows and Ubuntu via text document. Ubuntu's text editor is *not* compatible with Notepad (as you have noticed). The way to do what you tried to do is to open Open Office Word Processor (Ubuntu comes with Open Office, it is in the Accessories menu-i.e. the far left) and save as either .txt or .doc (I went with .doc myself, you didn't link I typed all that out by hand did you? ;))

---

