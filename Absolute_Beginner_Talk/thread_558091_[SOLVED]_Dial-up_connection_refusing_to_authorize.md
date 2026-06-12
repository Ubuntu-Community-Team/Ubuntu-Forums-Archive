---
title: "[SOLVED] Dial-up connection refusing to authorize"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by MementoMori on 2007-09-23
Hi again.

I just got the full version of the linuxant drivers for my modem and am trying to connect to the internet in Linux. My modem is detected and supported, and the modem will dial and I will get a handshake, but it will immediately disconnect afterward. I looked at the log in Gnome PPP and it posts "%Authorization failed" after sending the password, when I know the username and password I'm putting in are the correct ones. What the heck?

I had the free version of the driver before getting the full version and it worked just fine for all its slowness, and with the same settings.

---

### Post by Nikitas350 on 2007-09-23
i am not sure if this is gonna work but try the following:

type the command "sudo gedit /etc/wvdial.conf"
replace the file that appears with the following

[Dialer Defaults]
Modem = wherethemodemis (the default is /dev/modem)
Baud = 57600
Phone = thetelephonenumber
Username = yourusername
Password = yourpassword
New PPPD = yes
Idle Seconds = 300

make the changes needed then save it and run the command "wvdial &" to connect. To dissconnect run the command "killall wvdial". Good luck

---

### Post by MementoMori on 2007-09-23
Thanks for the reply. Unfortunately it didn't work. I get the same error. :(

---

### Post by MementoMori on 2007-09-24
Just searched the forums again and am gonna try what this guy did.

[http://ubuntuforums.org/showthread.php?t=454420](http://ubuntuforums.org/showthread.php?t=454420)

---

### Post by MementoMori on 2007-09-24
*sigh* Consider this "To be continued". It seems I lack the libstream libraries and can't install wvdial, so I'll have to wait until I can get on my friend's broadband connection.

---

### Post by MementoMori on 2007-10-14
Okay. At long last it's working. I found the libraries, but had some difficulty getting wvdial to make. So, I found the scripts and ran them, and then reconfigured it to stop looking for a carrier signal and to ignore terminal settings.

Success!

Thanks.

---

