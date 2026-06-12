---
title: "Back to 6.06 from 7.10"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Imre Mehesz on 2007-08-01
hello,

I tried to install 7.04 and even 7.10 (which couldn't even reconize my CD drive !?) so I decided to go back to 6.06 which was working perfectly for a long time.

I have an old compaq laptop and I use a linksys wg54 something wireless network card. I've been looking for a solution for a long time, and here is where i am right now:

- the wireless card power LED is on (good)
- i installed ndiswrapper-utils and also the card driver (which was working fine with many linux distribs (debian3.1, DamnSmall Linux, Ubuntu, Kubuntu, Xubuntu 6.x etc) (also good ;) )

- lspi -> i can see my network card Texas Instrument ACX 111 ... okay

- ifconfig - it only shows the lo local loopback (!?) no wlan0 or eth0 or anything like it, however

- iwconfig - shows the lo and wlan0 essid:MYESSID ... etc (seems fine)

- ifup wla0 - IGNORING UNKNOWN INTERFACE wlan0=wlan0

- /etc/network/interfaces - i only have iface lo inet loopback and nothing more :( if I put auto wlan0 -ignoring interface again ... :(

I am pretty sure it is something minor i just couldn't get it right . (as I said it was working before :( )

- I installed the server version of 6.06 and I don't have any kind of GUI just the command line!

Thank you guys very much,

iM

---

### Post by scrooge_74 on 2007-08-01
Sometimes the newest thing wont work. 

Why you dont have a GUI? You dont need one? There are a couple of light ones you could try

---

### Post by Imre Mehesz on 2007-08-01
i am an old fashioned one :) do you think that could solve the problem?

i

---

### Post by scrooge_74 on 2007-08-01
Probably going to a more stable version should fix things.  I usually i am not looking for the newest thing.  In fact I was pretty happy with Debian, but changed since I got my self a laptop and Debian stable did not wanted to run on it.

Another example this laptop i am using right now is on 6.06 and will remain like this for at least another year. But another one i had was giving problems so I went to 6.10 and then to  7.04  In order to go to Gutsy i need to be sure there is going to be an advantage for me to do so.

---

