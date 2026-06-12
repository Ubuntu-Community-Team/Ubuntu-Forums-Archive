---
title: "Slow boot - Suspect it's a hardware issue"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by showgun1 on 2007-07-16
Hi, I'm having an issue where it's taking a REALLY long time for me to boot up. I was having this problem with my windows installation, which is one of the reasons that I installed Ubuntu in the first place, but the problem is still there.

Anyway, I'm new to Linux, and to be honest not really sure how to solve this in windows either (obviously), so I'm hoping someone here can help me track down the problem.

When I boot up, I see a the BIOS check, and it takes me to the GRUB menu pretty quickly (haven't timed it, but I'd guess 10-20 seconds).

At the GRUB menu I select the Ubuntu installation, and I get the following:
Starting up...
Please wait... (or something like this)

Then my screen goes totally blank for about 3-4 minutes (BTW. I'm using a Samsung DLP tv as my monitor, and I've got a Sapphire X800 video card, set up with the proprietary driver)

After 3-4 minutes, I get the login screen and hear the sound that goes with it. After that everything works just fine.

I've checked the system logs for when I restarted, and this is what I got

Jul 16 20:41:28 the-mack gdm[5105]: Restarting computer...
Jul 16 20:41:30 the-mack init: tty4 main process (4422) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty5 main process (4423) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty2 main process (4426) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty3 main process (4433) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty1 main process (4436) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty6 main process (4437) killed by TERM signal
Jul 16 20:41:37 the-mack exiting on signal 15
Jul 16 20:46:33 the-mack syslogd 1.4.1#20ubuntu4: restart.
Jul 16 20:46:33 the-mack kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jul 16 20:46:34 the-mack kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Jul 16 20:46:34 the-mack kernel: Symbols match kernel version 2.6.20.
Jul 16 20:46:34 the-mack kernel: No module symbols loaded - kernel modules not enabled. 

So that's almost 5 minutes from the time I hit the restart button to the time it logs that restart.

Can anyone help me diagnose this?

For anyone who knows Windows well, I've got an XP Media Centre edition installation also, and when I boot that one, it's the "Windows loading" screen with the moving bar that takes the 3-4 minutes to get through (in case provides any clues)

---

### Post by rodo-&gt;dave on 2007-07-16
I had a problem with my boot time on Feisty and found this to be the solution to my problem.

When I would press ALT-F1 while booting I noticed the "network configuration" would hang for several minutes.

[http://ubuntuforums.org/showpost.php?p=2419738&postcount=16](http://ubuntuforums.org/showpost.php?p=2419738&postcount=16)
Check out this post (thread).

---

### Post by Ralob on 2007-07-16
I also had an extremely slow boot time. come to find out, my HD was on the fritz. once I installed a new one, everything worked fine. I honestly do not know if this is the case for you, so don't buy a new HD based off my experience. but I will say it is possible that your hardware may be going downhill. or I could be talking out of my....inexperience :P

---

### Post by Fitzy_oz on 2007-07-16
> **showgun1 said:**
> Hi, I'm having an issue where it's taking a REALLY long time for me to boot up. I was having this problem with my windows installation, which is one of the reasons that I installed Ubuntu in the first place, but the problem is still there.

Anyway, I'm new to Linux, and to be honest not really sure how to solve this in windows either (obviously), so I'm hoping someone here can help me track down the problem.

When I boot up, I see a the BIOS check, and it takes me to the GRUB menu pretty quickly (haven't timed it, but I'd guess 10-20 seconds).

At the GRUB menu I select the Ubuntu installation, and I get the following:
Starting up...
Please wait... (or something like this)

Then my screen goes totally blank for about 3-4 minutes (BTW. I'm using a Samsung DLP tv as my monitor, and I've got a Sapphire X800 video card, set up with the proprietary driver)

After 3-4 minutes, I get the login screen and hear the sound that goes with it. After that everything works just fine.

I've checked the system logs for when I restarted, and this is what I got

Jul 16 20:41:28 the-mack gdm[5105]: Restarting computer...
Jul 16 20:41:30 the-mack init: tty4 main process (4422) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty5 main process (4423) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty2 main process (4426) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty3 main process (4433) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty1 main process (4436) killed by TERM signal
Jul 16 20:41:30 the-mack init: tty6 main process (4437) killed by TERM signal
Jul 16 20:41:37 the-mack exiting on signal 15
Jul 16 20:46:33 the-mack syslogd 1.4.1#20ubuntu4: restart.
Jul 16 20:46:33 the-mack kernel: Inspecting /boot/System.map-2.6.20-16-generic
Jul 16 20:46:34 the-mack kernel: Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.
Jul 16 20:46:34 the-mack kernel: Symbols match kernel version 2.6.20.
Jul 16 20:46:34 the-mack kernel: No module symbols loaded - kernel modules not enabled. 

So that's almost 5 minutes from the time I hit the restart button to the time it logs that restart.

Can anyone help me diagnose this?

For anyone who knows Windows well, I've got an XP Media Centre edition installation also, and when I boot that one, it's the "Windows loading" screen with the moving bar that takes the 3-4 minutes to get through (in case provides any clues)

Do you have a USB card reader built in to you're system, for whatever reason some of these can casue abnormally long boot times due to the system trying mount them with no media in them...

---

### Post by showgun1 on 2007-07-16
> **rodo->dave said:**
> 

When I would press ALT-F1 while booting I noticed the "network configuration" would hang for several minutes.



OK, Well, I tried restarting and hitting ALT-F1 right when I saw the "Starting Up" message, and the first thing that it said had something to do with resuming, not being able to find a resume partition or something, then I got a very verbose output of activities (apparently it does fail to mount my external USB hard drive, but that's not what's slowing it down), and it takes me to my login screen in about 20 or 30 seconds. 

So ALT-F1 interrupted whatever was taking so long, and sped up the boot time.

BTW. I ran a hard drive diagnostics program on my windows installation, and it never came back with anything bad. I'm wondering if it's one of the other pieces of hardware.. maybe my motherboard's giving out or something. Does anyone know how to run hardware diagnostics in linux?

---

### Post by randytuggle on 2007-07-16
If you want to test your hard drive, you can use fsck. If you want to test your system memory, you can use the Ubuntu live CD and run a memory test from the CD. Let the memtest86 program run for a good while (at least an hour). If you see errors highlighted in red, you have a memory problem (or bios settings issue). You can also run a program called badblocks to test your drive in terminal. Look for info on these programs and you'll get details I can't even explain.

---

### Post by showgun1 on 2007-08-22
Hey guys, so I ended up taking my computer in to a repair shop, and it turned out that my mobo was causing some problems, so got it replaced. Now windows loads up in a snap, but ubuntu still takes a long time.

Another thing is that when booting, I don't see the splash screen. It just goes black for a few minutes, and eventually asks me to log in. The log in screen has a weird thing going on with with resolution (like it's squished) but once logged in, the resolution corrects itself.

I've got an ATI x800 video card, using a DVI out to my HDTV, and I'm pretty sure that has something to do with all this, but I'm not sure how to fix it.

Anyone have some suggestions?

---

### Post by bdmp on 2007-08-22
I have the same issue. Hangs at the beginning and then boots quick.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
i think video card problem sadly I dont know were to start

---

### Post by showgun1 on 2007-08-23
Interestingly, before bringing my computer home from the shop, I tried rebooting it there, while it was plugged into another monitor using the VGA out, and I actually got the "Loading" splash screen, and it booted up pretty quickly. I'm not sure why having it plugged into the TV would make a difference.


Another thing that I'm dealing with is trying to get some desktop effects going, and while reading one of the "how to" guides, it mentioned something about selecting a session when logging in.

Unfortunately, I'm not given any options for some reason. It just asks me for my name and password, and starts up gnome.

If I go to System > Administration > Login Window

There's a "Default Session" option, with a dropdown containing "Gnome", "Gnome with XGL", "Run Xclient Script", and a couple of others. I tried unchecking the "Default Session" check box, but it still puts me straight into gnome.

This might be worth starting a different thread for, but it could be related, so I'm posting it here.

---

### Post by glotz on 2007-08-23
Maybe it's this problem [http://ubuntuforums.org/showthread.php?t=254263&page=10#post3062492](http://ubuntuforums.org/showthread.php?t=254263&page=10#post3062492)

---

