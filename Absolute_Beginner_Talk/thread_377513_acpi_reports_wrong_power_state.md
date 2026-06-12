---
title: "acpi reports wrong power state"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by antanasb on 2007-03-06
Hello,

after booting laptop acpi reports correct power state but later it doesn't responds for any power change. Even when I plug off the power cable and the screen goes dim the system tray shows "on AC power".
I dunno it was related to kernel upgrade or something else.
Any help would be appreciated

ubuntu 6.06.1 LTS
Compaq nx6310

---

### Post by antanasb on 2007-03-07
strange...

today morning I started my laptop and walla! - acpi reacts for power state changes!!
To be absolutely sure that there is no more problem I restarted computer.
:(
The same problem again...

---

### Post by cbrolin on 2007-03-07
I have the same problems on a HP Compaq nx9420 with Ubuntu 6.10. Sometimes the power manager works and sometimes it doesn't, but most often it doesn't. It seems to correctly get the state (battery/AC power, charge and power) at startup, but the state  never change. The graphs are just straight horizontal lines. The event log notices when the lid is closed or opened, but it doesn't notice when the AC cable is connected or disconnected.

I have also Fedora Core 6 and Windows XP installed on the same machine, and their power managers work just fine. I think FC6 uses the same power manager as Ubuntu.

---

### Post by adrianj on 2007-03-08
Hi,

These issues are known as "bad state" problems and are experienced with HP notebooks. Check this HP forum thread for more info: 
[http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1026460&admit=-682735245+1173393562800+28353475](http://forums1.itrc.hp.com/service/forums/bizsupport/questionanswer.do?threadId=1026460&admit=-682735245+1173393562800+28353475)

---

### Post by antanasb on 2007-03-09
Thanks adrianj for pointing. 
Seems like no quick solution exists for this "bad state" problem. Recompiling the kernel is a mystery for me:(
I found suggestion on [http://emisca.altervista.org/nx7400/old/index.html](http://emisca.altervista.org/nx7400/old/index.html) and on some other sites but still can't say that it works.

---

### Post by adrianj on 2007-03-09
I am using Feisty Fawn Herd 5 with kernel 2.16.20.9 together with Hp's newest BIOS update ver F19 for my nx9420 and I now have no problem with my battery charge.  Be reminded that FF is still not released and other problems may pop up if you dist upgrade.

---

### Post by cbrolin on 2007-03-10
[QUOTE=antanasb;2270260]Thanks adrianj for pointing. 
Seems like no quick solution exists for this "bad state" problem. Recompiling the kernel is a mystery for me:(

Me too, but I solved it without recompiling the kernel. I'm using 6.10 and don't know if my fix will work for 6.06. I will show how I solved it, but first some background:

The problem according to the HP forum, pointed to by adrianj's reply, is *psmouse*. This is the program that handles the mouse pad! When the OS is shutting down, it does something bad with the computer's startup memory which the BIOS doesn't handle. The symptom is a blinking cursor at startup for several seconds before the HP logo is displayed and then a fixed battery status. To get rid of this bad state it is necessary to remove the AC power and the battery for a while, OR just boot up Windows XP and shut it down again. 

Since the Ubuntu kernel has this psmouse as an installable module and not statically linked-in module, it is possible to remove it before shutdown. I created a file:

[FONT="Fixedsys"]  /etc/init.d/rm_psmouse[/FONT]

with the following contents:
[FONT="Fixedsys"]
  #! /bin/sh
  # Avoid the HP Compaq BIOS Bad State problem (in which the BIOS boot
  # takes so long and the ACPI battery update doesn't work).
  rmmod psmouse
[/FONT]

This is just a shell script to remove the psmouse module from the kernel. Make the script executable:

[FONT="Fixedsys"]
  sudo chmod a+x init.d/rm_psmouse
[/FONT]

Create shutdown and reboot links to this script:

[FONT="Fixedsys"]
  cd /etc/rc0.d
  ln -s ../init.d/rm_psmouse S80rm_psmouse
  cd /etc/rc6.d
  ln -s ../init.d/rm_psmouse S80rm_psmouse
[/FONT]

And that was all! Try both reboot and shutdown to make sure everything work. Don't forget to get rid of the bad state first as described above! If something is unclear or doesn't work, just ask again, I will watch this thread.

My Fedora Core installation also manages to put the computer in bad state, but it doesn't suffer from it! The Power Manager (the GUI looks the same) still works. This is strange, so I have to fix it there too or maybe I just remove FC...

---

### Post by antanasb on 2007-03-11
cbrolin,

thankyou for good news!
I'll try your trick maybe tomorow and will inform you (and rest of the ubuntu world) about results.

nice Sunday!

Antanas Budri&#363;nas

---

### Post by antanasb on 2007-03-31
cborlin,

thanks a lot for the solution!
It works perfectly on my system too:

Baltix (ubuntu 6.06.1 LTS)
Compaq nx6310

One more reason for booting into Windows dissapears :)

---

### Post by the_toddster on 2007-04-27
cbrolin,

YOU ARE THE MAN!!!!!!! I can't tell you how many kernel compiles I've been through trying to fix this problem.

Please allow me to buy you a beer  :-)

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/5/57/Beer_mug.svg/50px-Beer_mug.svg.png[/IMG]

---

### Post by FrancoNero on 2007-04-27
does all this have something to do with me not having any touchpad/keyboard after returning from suspend/hibernate?

---

### Post by antanasb on 2007-04-28
Hi,

the patch is great, but it doesn't solves bad state problem in case of hybernate.

---

