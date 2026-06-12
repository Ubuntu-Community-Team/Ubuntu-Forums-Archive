---
title: "Installing Ubuntu on Dell Dimension e521"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by c0rd3l1a on 2006-12-09
I am trying to install Ubuntu 6.06.1 i386 on a Dell Dimension e521 with AMD 64 x2 processor. I am having many, many, many problems. I'm posting them all together hoping that they are related and can be solved easier with a holistic approach. Please note that the Dimension e521 has no internet access. I can download things on my laptop and transfer them to the Dimension, though.

1. Every 2-5 minutes my **mouse quits working**. I have a Logitech wireless duo. The keyboard and mouse receiver connects using a single usb cable. When the mouse quits working, the keyboard will still work. Then I have to unplug, replug, and it will work for another 2-5 minutes. I tried using a wired mouse separately and it also quits every 2-5 minutes, but works after unplugging and replugging it in. After an hour or so of this, all mice and keyboards just quit responding ever.

2. When booting, half of the time I end up with "**kernel panic**" and it suggests that I boot using the "no-apic" option. So I force shutdown and turn it back on and usually it works then, except...

3. The other half of the time after booting, the computer boots just fine, but I get a "**preparing restricted drivers    failed**" error during the startup process.

4. My **wireless** card doesn't work. I bought a new one with an Atheros chipset because I was told that it should work more easily, but I'm still having a lot of trouble. I think this is because of my problems with ndiswrapper.

5. I'll have to get back to you with the **ndiswrapper** problems because I can't insert my install cd to get the ndiswrapper-utils package. When I try to mount it in terminal it says "**unknown filesystem type 'iso9660'**" but yesterday it worked all day long and I could access it through synaptic. Audio cds are recognized, however (not through synaptic, obviously).

6. When I **reboot**, the computer shuts down properly, but when it tries to restart, nothing shows up on the monitor. The box itself is still powered on, but there is no visual output. 

I have had this brand new computer sitting in my house for 2 entire months now and have spent every weekend trying to get it to work by reading through the forums. Please help me get it running!

---

### Post by c0rd3l1a on 2006-12-09
7. Randomly the keyboard becomes possessed and starts typing a character, that I haven't even touched, over and over for all of eternity until I force shutdown.

---

### Post by Liolikas on 2006-12-09
Wery strange. I instaled ubuntu into my friend's **Fujitsu Siemens** laptop few hours ago. Later I used Automatix. After all ubuntu works much better than windoze on it.

So we can blame "Dell" :D

---

### Post by LasloHollyfeld on 2006-12-10
Just in case you haven't found it already, there appear to be known problems with the E521 and USB. Here's a link to another post with more info;

[http://ubuntuforums.org/showthread.php?t=279626](http://ubuntuforums.org/showthread.php?t=279626)

It's apparently not just Ubuntu, but a bunch of other distributions as well. I was planning on picking up an E521 until I read this. Check the threads, though, there appear to be some fairly cheap workarounds that can get you by until it's fixed. I think it will be fixable, since others have mentioned a similar problem on Windows until a driver update was delivered.

---

### Post by riven0 on 2006-12-10
How about trying to install Edgy on the laptop? You may have better luck there.

---

### Post by szf on 2006-12-10
Read more about problems with this Dell series at this [forum]("http://forums.us.dell.com/supportforums/board/message?board.id=sw_other&message.id=54328&view=by_date_ascending&page=1").

---

### Post by c0rd3l1a on 2006-12-10
Wow, thank you all so much! I will sort through all of these other threads and if I find anything that works, I'll post it here.

---

### Post by magicfab on 2007-01-24
The USB keyboard/mouse seems to have been fixed with a recent update of Dell's  BIOS. see:
[https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellnSeries)

---

