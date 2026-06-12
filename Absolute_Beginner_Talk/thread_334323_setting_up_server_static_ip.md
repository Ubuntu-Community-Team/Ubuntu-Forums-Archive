---
title: "setting up server static ip"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by chatterbabies on 2007-01-08
I installed ubuntu server 6.06 on a small pc using the alternate install. No error messages (YEAH)
I am trying to follow[COLOR="Navy"] ["The Perfect]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")[/COLOR] Setup HowTo" I get to[COLOR="Navy"] [page 3]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p3")[/COLOR] and get into the networking interfaces. I change the lines to 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.119
        netmask 255.255.255.0
        network 192.168.0.1
        broadcast 192.168.1.255
        gateway 192.168.1.1

I know the address, netmask and gateway are correct. Don't have the foggiest what the network and broadcast are for but they match what two of my other computers have. Even changed them incase they are supposed to be different. Even took those two lines out. 
I can't for the life of me figure out how to save the changes and get out of here. If I hit ESC I can get to a black line and type in what is said next "/etc/init.d/networking restart" but no matter what I do I get the same error message
E486: Pattern not found :etc
How do I save it and get out of it. I tried just shutting down and restarting. BIG No no. Wiped it out and installed again because when i tried to access that file got an error message about a crash and stuff. 
How do I save or exit editing that so I can do the restart line?
Thanks!

---

### Post by hal10000 on 2007-01-08
you have to edit your files using the sudo command, e.g. [COLOR="Red"]sudo vi /etc/interfaces[/COLOR] and restart networking with th sudo command too: [COLOR="Red"]sudo /etc/init.d/networking restart[/COLOR]. You usually always have to edit or perform commands that need root privileges with sudo.

Hope this helps

---

### Post by beercz on 2007-01-08
Or, from the terminal window try:

> sudo gedit /etc/network/interfaces

I think your network line should read something like:

> network 192.168.1.0

---

### Post by halitech on 2007-01-08
according to those who say they know better then me, we "should" be using

```

gksudo gedit /etc/network/interfaces

```

or 
```

sudo nano /etc/network/interfaces

```

so we don't mess up file permissions

(been using sude gedit myself with no problems so not sure how it messes things up but no one would give me a straight answer)

---

### Post by chatterbabies on 2007-01-08
I am logged in as root according to the tutorial. the first commands to apt-get install xxx worked fine without the sudo command since I am root. I went to go try to type what you said anyway and I can't get out of the  screen
Well I figured out how to get out of the screen I hit esc then typed ":x" and it wrote the changes. problem is my settings won't work. I restarted the network and  get
SIOCSIFNETMASK: Invalid argument
Failed to bring up eth0
if I set it back to dhcp and comment out the address, netmask, and gateway it works and I get:

Listening on LPF/eth0/00:00:e2:27:05:96
Sending on   LPF/eth0/00:00:e2:27:05:96
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.101 renewal in 38045 seconds

GOT IT!  big duh!  I was tabbing over the lines to line up like the tutorial looked. I untabbed them and put the right gateway in and it worked! Still had to hit Esc and then type ":x" to get out of that menu. I hope that is normal.

---

### Post by chatterbabies on 2007-01-08
no I didn't type in a mad smile, although it would have been appropriate it was : x without the space. Is there somewhere I can get a list of those commands? I don't have a terminal because I am running from the command prompt with no gui. I guess that is why gedit doesn't work. :-k 
Now I am worried about messing something up.
What are the network and broadcast for? I got it working without those lines but maybe I need them?

---

