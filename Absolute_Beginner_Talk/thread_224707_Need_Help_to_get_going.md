---
title: "Need Help to get going"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by lalit on 2006-07-28
I really need help. I have been preaty much a windows person,but when i saw ubuntu i thought i must use it. The setup went smoothly.I loaded it & cant seem to get it started. 

It says TO RUN COMMAND AS ADMIN (USER "ROOT"), USE "SUDO <COMMAND>
See " man sudo_root" for details 
lalit@ubuntu:~$

Dont know anything about linux, so pls guide me how to get this OS started 

My Comp is a IBM thinkpad 390X 500Mhz 256ram 12gb harddisk

---

### Post by Zelut on 2006-07-28
Well what are you trying to get done?  Trying to run a certain program?  Trying to login?  Can you be a little more specific please?

---

### Post by uber on 2006-07-28
What exactly are you trying to accomplish that you can't get done? Does the desktop or login screen load properly?

---

### Post by Dr. Nick on 2006-07-28
Did you download the livd cd iso, or the server iso. It looks like you have the server iso and it is just booting into the command line.

---

### Post by moma on 2006-07-28
o--->[http://www.futuredesktop.org/ubuntu6.06.html]("http://www.futuredesktop.org/ubuntu6.06.html")

---

### Post by s_h_a_d_o_w_s on 2006-07-28
It says that the first time you open the terminal. Kinda like a welcome message. The terminal is where you will do a lot of installing, modifying, etc. You should become it's friend .

---

### Post by az on 2006-07-28
> **lalit said:**
> 
It says TO RUN COMMAND AS ADMIN (USER "ROOT"), USE "SUDO <COMMAND>
See " man sudo_root" for details 
lalit@ubuntu:~$
That's the command line prompt.  It's really great, but you are not supposed to be brought there, you should be brought to a graphical desktop.  What went wrong?  Maybe you did a server install.  Maybe you selected the recovery mode boot menu entry?  Maybe your graphics hardware was mis-detected (unlikely on an older machine)

Exactly how did you install (What cd, what options, was it text-mode or graphical.)

---

### Post by lalit on 2006-07-28
Like some of you pointed out it was the sever version i downloaded my mistake.Dont know much about linux but am surely learning by the day.
Am downloading the live cd as of now.I had done a clean install (Formated entire HD) when i loaded the server version,as i dont like dual boot,now can i load the Live cd over that (server version) ? Or would the LIVE CD give me a option to format my hardisk ?

---

### Post by cmo220 on 2006-07-28
type sudo aptitude-install ubuntu-desktop
 
or something similar to that, hopefully someone will correct me if Im wrong

---

### Post by confused57 on 2006-07-28
> **lalit said:**
> Like some of you pointed out it was the sever version i downloaded my mistake.Dont know much about linux but am surely learning by the day.
Am downloading the live cd as of now.I had done a clean install (Formated entire HD) when i loaded the server version,as i dont like dual boot,now can i load the Live cd over that (server version) ? Or would the LIVE CD give me a option to format my hardisk ?

If you have a fast internet connection, you can get the GUI by entering:
```
sudo aptitude update
```
then
```
sudo aptitude install ubuntu-desktop
```

---

### Post by Qrk on 2006-07-28
You can install from the LiveCD, it gives you the option to format your harddrive. However, using aptitude to install ubuntu-desktop will also work, if you don't want to reinstall the whole OS.

---

### Post by az on 2006-07-29
> **Qrk said:**
> You can install from the LiveCD, it gives you the option to format your harddrive. However, using aptitude to install ubuntu-desktop will also work, if you don't want to reinstall the whole OS.

If you do that, be sure to install linux-386 (that's a desktop kernel,  the linux-server is a server kernel and things like your usb mouse may not work well.)

It is probably much faster to just start over using the live cd.

---

### Post by lalit on 2006-07-30
Downloaded the Live Cd & it works like a charm ! As i wanted to install it to my HD i went through the install process, but it gets stuck on 3 out of 6 [keybord layout] Well it does not freeze it just does not do anything. My prefered layout is American english. Waited for 20min on that, also tryed british layout but the outcome is same Any answers to this ?

---

### Post by Drakkor on 2006-07-31
**Did you check the disk for defects !!**

---

### Post by lalit on 2006-07-31
> **Drakkor said:**
> **Did you check the disk for defects !!**

Yes  i did ! Nothing wrong with that

---

