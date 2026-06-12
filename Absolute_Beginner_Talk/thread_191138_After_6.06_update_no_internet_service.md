---
title: "After 6.06 update no internet service"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by rmaier on 2006-06-07
After updating to 6.06 online, I cannot access the internet. Error message says can't find server, check firewall and proxy.](*,)  I tried to shut down and reboot without success. I noticed during the reboot, one system failed...PCMCIA services.  I called my cable service, and no one there was familiar with linux or ubuntu but they said my USB modem was working and sending service.   What to do?   I have the disk for 5.01 version, should I try to reload it and will it even take it over the 6.06v. The update looks great, but not much value if I can't access the internet which is my lifeline.   I will appreciate help from anyone. ](*,) I had to go to a friends house to use their computer to access ubuntu forums.

---

### Post by Flyn on 2006-06-07
Is the cable modem connected to a PCMCIA lan port?
If it is, I'm not really sure what I can do to help.
If it isn't try checking in System->Administration->Networking to see if your device is recognized there and write back and we'll se what we can do ;-)

---

### Post by noelsanidad on 2006-06-07
I had the same problem and my lan interface was screwed up when I upgraded to 6.06, I had to reinstall 5.10 again just to use my dsl modem. I guess they are working on this problem, I hope that they can fix everything.

---

### Post by eboo on 2006-06-07
Hi 

try the following and please display your results here:

we are going to try pinging an external ip address:

open a terminal type the following:
ping 196.25.1.200

I had a similar problem. The problem was that my modem was not forwarding the right DNS addresses to Ubuntu. to fix this I had to get the IP addresses of the DNS servers from my ISP and update my Ubuntu with them.

first try the ping so we can see if this is indeed the problem

---

### Post by rmaier on 2006-06-07
you suggested i open a terminal and type the ping line....where do i type the ping line...sorry to be slow..still learning...thanks rmaier

---

### Post by rmaier on 2006-06-07
when you reinstalled 5.10 did you have to do anything special other than put the cd in the drive.....any step by step direction is welcome...still learning...thanks a lot.

---

### Post by xyz on 2006-06-07
[QUOTE=rmaier]you suggested i open a terminal and type the ping line....where do i type the ping line...sorry to be slow..still learning...thanks rmaier[/QUOTE]

Hi-
Go Application>Accessories>Terminal and click on it.
Then you'll see something like: yourname@ubuntu:~$ **right here**, just type: ping 196.25.1.200
No worries...

---

### Post by xyz on 2006-06-07
[QUOTE=rmaier]when you reinstalled 5.10 did you have to do anything special other than put the cd in the drive.....any step by step direction is welcome...still learning...thanks a lot.[/QUOTE]

How about this one...fairly clear and step-by-step with pictures:

[http://www.ccs.neu.edu/home/jabra/breezy-docs.html](http://www.ccs.neu.edu/home/jabra/breezy-docs.html)
Hang in there!

---

### Post by eboo on 2006-06-08
Hi rmaier

Have you resolved the problem yet? otherwise please post the result of that ping

:)

Eboo

---

### Post by DougC on 2006-06-08
Hi rmaier,

Try issuing the following command:

sudo /etc/init.d/networking restart

and see if it then works.

There are a few issues already like this. Check thread:

[http://www.ubuntuforums.org/showthread.php?t=191231](http://www.ubuntuforums.org/showthread.php?t=191231)

for more info.

---

### Post by rmaier on 2006-06-20
Still having some problems after tryng to reload Breezy 5.10. 

I get an error that says Failed to start X Server your prahphical interface. It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem. select YES

X window sys V 7.0.0
Release Date: 21 Dec 2005
X Protocol Version II, Revision 0 Release 7.0
Build Operating System Linuz 2.6.12 i686
Curent Operating Sys: Linux ubuntu 2.6.15-23-386 #1 Preemp
May 23  13.49:40 UTC 2006 i686
 X server is now disabled
Restart GDM when configured correctly

Fail to initialize core devices
GLcore - module failed

xf86 open serial

then it goes to a command asking for user name:  typed user
password requested: typed password

Ubuntu 6.06 LTS ubuntu ttyl

command line user@ubuntu: "$

have tried several words on the command like run, load, install, etc. but no success. 

To send and receive email messages I have to go to a friends house to get on their computer, take the directions and go back to my house to try them on my computer.   

Thanks for your help.

---

