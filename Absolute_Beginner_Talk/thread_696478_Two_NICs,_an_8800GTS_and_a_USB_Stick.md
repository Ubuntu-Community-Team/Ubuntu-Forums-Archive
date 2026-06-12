---
title: "Two NICs, an 8800GTS and a USB Stick"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Ludaen on 2008-02-14
Just decided to try Ubuntu and I managed to install 7.10 AMD64 edition.

I have never been able to boot Ubuntu normally because of the problem with the 8800GTS.  After looking through the forums I found how to solve this problem.  However, it tells me to use the command

```
sudo apt-get install build-essential
sudo apt-get install xserver-xorg-dev
sudo vi /etc/default/linux-restricted-modules*
```

in the terminal.  I boot Ubuntu into recovery mode (which is the only way I can boot it) and use startx to bring up the GUI (which works).  However when I bring up the terminal and type in this command, the computer attempts to connect to the internet and fails.  I know I configured it correctly when installing Ubuntu, but I guess I need to make changes since my motherboard has two different NICs built in.

This brings me to the second problem.  I try to access the network configuration in administration and it pretty much says I am not allowed to access it.  I know I am a 'Privileged User' but I cannot make changes.  I don't know how to login otherwise.

Other guides have said that I should download the linux drivers from Nvidia, I did that on my XP OS and put it on a USB stick....which I cannot seem to access from Ubuntu.

I can do all of this from the Live CD but it doesn't seem to make a difference in the real installation.

Needless to say I have no idea what I am doing and any advice would be the greatest of help.  I am really interested in figuring out Ubuntu for everyday use.

I have an AMD64 X2 4400+, MSI K8N Diamond Plus, 8800GTS, 2gb RAM
Three operating systems are installed.  When I start my computer it goes to GRUB which has Ubuntu and Vista, when it goes to Vista I can select Vista or XP (if that helps at all).

---

### Post by oedha on 2008-02-14
of course to get those packages...you have to be online......
maybe you can reconfigure the NIC again, ip, gateway, and dns address

---

### Post by Ludaen on 2008-02-14
I am completely unable to make the changes to the network configuration, which includes IP, DNS, Gateway etc.  The system does not want to let me make any administrative changes to the connection.  The network stage during installation seemed to go smoothly and I entered in the exact same values used in my other operating systems.

I guess what I am asking is, how do I log in to make the changes?

---

### Post by oedha on 2008-02-14
can you open terminal ?
if yes......
sudo ifconfig eth0 ipnumber
then
sudo route add default gw ipno_gw
then sudo gedit /etc/resolv.conf
type in :==> nameserver dns_ipno
then
sudo /etc/init.d/networking restart
now...try to ping.....
i hope this helps :)

---

### Post by Ludaen on 2008-02-14
I got your suggestion to work, but I still could not fix the problem the 8800GTS has with booting normally.  When I updated and tried to restart, the OS wouldn't shutdown.  I would hit the "Quit" button and could still move the mouse, but could not click anything and would have to do a hard shutdown.

Also, the commands above for fixing the 8800GTS problem were not able to connect to the Ubuntu downloads for some reason either because of a 404 error.  After I restarted the computer it still did not boot properly and I had to redo all the connection stuff again.

--Edit--
When it failed to connect, terminal would ask for the original install CD to be inserted, but when I did that, it said that the CD was wrong and I noticed that part of the disc label was cut off.

---

