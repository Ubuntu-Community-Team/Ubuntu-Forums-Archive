---
title: "Dialing out from command line?"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Gyrotwister on 2006-08-23
I have that broken xserver thingy happening on my pc.  From what I can gather my task will be to download the updated update (10.4) from the text screen.  Have already seen the main thread about this.   

I’m on dialup with a functional winmodem and I have a spare external modem in my bottom drawer which I can connect to a serial port if the internal one won’t work.  

How do I connect to my isp from the text screen?  

Are there any commands I should know about to dial out?

---

### Post by az on 2006-08-23
> **Gyrotwister said:**
> I have that broken xserver thingy happening on my pc.  From what I can gather my task will be to download the updated update (10.4) from the text screen.  Have already seen the main thread about this.   

I’m on dialup with a functional winmodem and I have a spare external modem in my bottom drawer which I can connect to a serial port if the internal one won’t work.  

How do I connect to my isp from the text screen?  

Are there any commands I should know about to dial out?

If your winmodem worked at the desktop (with X) then it will still work for you without X.

I think the gnome dialer uses wvdial.  

Try

sudo wvdial

and I think the default connectino will dial for you.  CTRL-ALT-F2 to switch to another VC, since I think it occupies your console while connected.

Otherwise, I used to use pppconfig

sudo pppconfig
and then config your connectino with username and password - Use Dynamic settings and take the default for everything else.

save and exit.

sudo pon (name)

to dial.

sudo poff 
to hang up.

---

### Post by Gyrotwister on 2006-08-23
Have printed out instructions and will try it now.  
Back soon; I hope.

---

### Post by Gyrotwister on 2006-08-23
Well, that was less than straight forward!  
My internal modem didn't work.  
pppconfig was unable to scan serial ports to find my external modem so I tried each port in turn about 3 or 4 times.  
Then I left it on the port which I thought it was and rebooted.  It dialled on bootup (no command issued by me) and I was able to downgrade xserver.  For whatever reason the updated update for xserver was not available.  

Azz,  thanks for helping me out.  

I wonder how many Ubuntu participants have unexpectedly had their time wasted by this update error?  The mind boggles.

---

### Post by confused57 on 2006-08-23
You may have been able to downgrade without an internet connection:

```
sudo dpkg -i /var/cache/apt/archives/xserver-xorg-core=1:1.0.2-0ubuntu10.deb
```

---

