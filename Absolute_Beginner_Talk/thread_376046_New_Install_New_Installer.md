---
title: "New Install New Installer"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by srhegde on 2007-03-04
New Install New Installer
thinkpad, x24, kubuntu, sound, wireless, startup


Hi,
I installed kubuntu 6.10 on a thinkpad X24 (PIII 1.13G, 256MB, 30GB).
I have at least a couple of problems:
 - questions:
[LIST=1]

[*]I use a Dlink USB dongle - works fine, after using ndiswrapper and modprobe, then using wireless assistant (GUI) to connect
[*]How can I know what this wireless assistant does, so that I can use the same commands to put in a script and run it in the startup. I tried to put the modprobe command in a script and then placing in the /etc/init.d directory and creating a softlink to /etc/rc.[1-5|S].d/ directories - does not start the USB wireless device.
[*]The sound is not working. I tried amarok and kaffeine.What should I look for, do I have to install something more like alsa?
[*] The CPU switches between 731MHz and 1130MHz (I can check this by moving the mouse on the battery indicator), I am not sure why this happens. I can say that the ac adaptor is sensed because when I remove the adaptor, the brightness deceases
[*] gvim when started from a konsole terminal give the following error: X Error: BadDevice, invalid or uninitialized input device 168...... (it works after that)
[*] The system hangs if I place the laptop on the replicator/docking station or after taking it out from there. Is this a hardware problem or linux problem?

[/LIST]

Thanks in advance for any help

---

### Post by srhegde on 2007-04-14
Found the following answers myself, by browsing internet or otherwise

2. run wlassistant on the terminal, and watch ! you will see whats happening in the background
    Modify the rc?.d, then do update-rc.d
4. Sound is working now, the volume was low <<-- stupid, check basics first
5. [http://ubuntuforums.org/showthread.php?p=1264009](http://ubuntuforums.org/showthread.php?p=1264009) 
  -->  Edit /etc/X11/xorg.conf - comment the "inputDevices" for stylus, erase, cursor, and corresponding "serverLayout"

I still dont know answers for 4 & 6

---

