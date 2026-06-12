---
title: "[SOLVED] Help! Lost GDM!"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Speedoo on 2007-07-14
I've been using Ubuntu Feisty on my Toshiba Satellite laptop for some weeks now.  It's been stable, and the machine has been living in hibernate mode when not in use.  This morning, I needed to boot to Windows and leave Ubuntu.  Upon returning to Ubuntu, ,my x server wouldn't load.  I found a thread here that suggested removing and reinstalling the GDM.  Remove worked fine (!), but when I tried to install, I'm unable to connect to us.archive.ubuntu.com.  SO I'm stuck with no GDM.  
What can I do?
Thanks!

---

### Post by regomodo on 2007-07-14
is that computer connected to the web?

do a 

$ sudo apt-get update

if you get any errors let us know

---

### Post by Speedoo on 2007-07-14
I wasn't sure if the wireless driver was working, so I ran a spare Ethernet cable from my router to the laptop just to be sure.  Since I have no gui, I don't know how to verify if I'm connected.
I ran sudo apt-get update and got the following:
(as I started to copy the screen, it scrolled and I can't get back to the beginning, but basically, it seems to be a long string of errors like this:)

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'

There are apparently several pages of these errors, indicating that my internet connection isn't working.  How can I connect (either wired or wireless) from the command line?

---

### Post by BobCFC on 2007-07-14
To test a connection to your router use PING such as

ping 192.168.0.1

and then press crtl-c to quit. It will either say time in ms or host unreachable.

If you can reach the router try

ping [www.google.com](www.google.com)



To see what network interfaces you have running type ifconfig. eth0 is wired and wlan0 is wireless.


To reset a dodgy wireless link and try and get a new ip adress bring it down and up again:

sudo ifdown wlan0
sudo ifup wlan0


EDIT: normally you can press shift-pageup/pagedown to scroll back in the console but if it goes too far back you can always pipe the results to a text file such as

somecommand  >  textfile.txt

then you can read the file using *more* or your favourite editor such as nano

---

### Post by BobCFC on 2007-07-14
also you can get into X without using the GDM.  Once you are logged into the console type startx

---

### Post by Speedoo on 2007-07-14
ok, ping showed no reception (no connection.)
ifup wlan0 shows Error while getting interface flags: No such device
ifconfig shows UP BRODCAST RUNNING MULTICAST MTU:1500 Metric:1
I'm guessing this means there's a connection, but I can't ping to it.  I had wireless access about an hour ago, and I'm currently sending from another machine wired to the same router as my laptop.  I don't understand how shutting down Ubuntu and then rebooting can cause the gui to go bad?
I'm so confused.
To make matters worse, I'm leaving town for a week in about an hour, and I really need my laptop.  I could revert to Windows, but now I'll lose 3 weeks of current data which is locked up in Ubuntu.
Talk about Murphy's Law!  This is the worst possible timing for linux to fail me.

---

### Post by Speedoo on 2007-07-14
Wow.  I just, (in complete despairing frustration) retyped sudo apt-get install gdm, and IT WORKED!!!!
Now I just need to find the command to restart the gdm.  (something like /etc/init.d/ gdm restart)
Thanks for listening!

---

### Post by regomodo on 2007-07-14
in my experience the ping command is never the best method when it comes to wifi. sometimes it never works even though i know the device is online.

i use the **route** command although i think that's only suitable to dhcp. i may be totally wrong.

to get gdm to restart whilst in the terminal type

$ sudo /etc/init.d/gdm start

---

