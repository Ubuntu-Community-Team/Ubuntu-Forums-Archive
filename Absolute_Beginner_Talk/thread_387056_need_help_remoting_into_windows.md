---
title: "need help remoting into windows"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by rat1000 on 2007-03-17
I am trying to remote into my work computer from Ubuntu.  Right now, I use WIndows to do this.  I create a vpn connection to vpn.myworkplace.com with the networking wizard.  I then log on to the vpn with my user name,  password.  I then use remote desktop to log onto my machine with the machine name.  Once it has connected, I enter my user name and password

I have read about rdesktop and terminal server client but do not know how to set this up to log into work.  Any help with this is greatly appreciated!  :)

---

### Post by racmar on 2007-03-18
Your problem is going to be the vpn client.  What vpn software are you using?  more importantly, what vpn protocol is the software using?  Once you get the vpn setup and working, you can then use the following to connect to windows remote desktop server....

you can also use krdc.  it's a kde app, but you can still install and use it just fine under gnome with:
```
sudo apt-get install krdc
```

krdc is then located under applications -> internet.  To connect to your windows desktop, use ```
rdp://computername
``` 
after starting krdc, click the examples button for information on how to use it.

---

### Post by racmar on 2007-03-18
I just found gnome-rdp that works with windows remote desktop also.  I've installed it, and it works well enough.  However, I use beryl on my ubuntu desktop, and gnome-rdp is very transparent and is almost unusable unless I switch back to metacity.  Thus, I'm sticking /w krdc.

---

### Post by cprofitt on 2007-03-18
I have to say that krdc worked fine for me.

Now I just have to resolve the issues with the VPN.

---

