---
title: "Totally new to ubuntu, experienced xp user, wireless connection."
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by nelsland on 2007-01-21
i just install ubuntu becasue i was so sick of xp and just want to try something new

anyway, im  on a  wireless desktop, i have no lan connection, therefore i cant do any update on my ubuntu 6.10 

so on that. can anyone show me how to step to step get wireless connection to the internet?

specs.. well you can ask if you need any info. so far i have ubuntu 6.10, i have level 1 wnc 0300 wireless card (g). 

any help would be appreciated

nelson

---

### Post by mikewhatever on 2007-01-21
Try this page [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html)

If your wireless card is detected and you do have wired connection, installing gnome network manager can be a good idea.
```
sudo apt-get install network-manager-gnome
```

Once installed, an icon will appear next to the clock in the panel. Clicking on it will show networks available.

---

### Post by nelsland on 2007-01-21
thanks for that advise

but one of the problem is that this is a desktop im in and it is a big hassle to get it to a wired connection. 

can i get it connected wireless without a wired connection to start with? aka.. without downloading any parts/ or downloading any parts via window xp and sent it to Linux? (this desktop also has a slow window xp with wireless connection)

thanks

---

### Post by SendDerek on 2007-01-21
I'm not sure about this, but is Network Manager on the installation CD?  You could use that as a repository or installation source without having to connect to the internet!

---

### Post by Bachstelze on 2007-01-21
The first thing you need is to make sure your wireless card is properly detected. To do it, you can run the command :

```
sudo iwconfig
```

and if you have an entry that doesn't say "no wireless extensions".

---

### Post by nelsland on 2007-01-21
i try typing in "sudo iwconfig"

everything in there (lo wifi0....) return "no wireless extension"

except ath0 ,which give me a whole bunch of info like essid, 802.11g........ too bad i cant copy and pasted it since everytime i do this i have to restart and go to window xp to type this help message out


anyway. does that mean anything?

---

### Post by Bachstelze on 2007-01-21
Certainly, that means you have a working wireless interface, which is called ath0. Then all you have to do is :

```
sudo iwconfig ath0 essid YOU_ESSID key YOUR_WEP_KEY
sudo dhclient ath0
```

assuming your network is using DHCP of course.

---

### Post by nelsland on 2007-01-21
now here come some dumb questions
im used to the wireless connection in xp, where those software will do most of the thigns for me

so in linux, what exactly is essid, is that the ssid(network name) in window xp?

and if im have  a wpa2 security in the router, what do i type in in the password, 

my connection is assigned by dhcp , thank you

---

