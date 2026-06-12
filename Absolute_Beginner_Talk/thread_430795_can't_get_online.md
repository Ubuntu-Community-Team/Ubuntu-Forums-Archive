---
title: "can't get online"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by puckjock on 2007-05-02
I have xunbutu 7.04 installed. I have a cable modem directly connected to my ethernet..no router involved.
I have gone into system>network and set up the wired connection to dhcp..but i can not get online. Do I need to download anything?? I am new to Linux. Any step by step help would be great.

---

### Post by starcraft.man on 2007-05-02
Hmmm, seems like it should work automatically. What modem model is this? Did you install any software from your provider on your old mac/windows computer? Also, what network card are you using? An integrated wireless on your mobo? or an external dlink/other?

Also, just IMO, but soon as you get it working you should put a router on it, direct connection to the internet is dangerous nowadays. NAT Router is your friend.

Edit: *wonders if a little parot penguin is following him around* :p

---

### Post by Cypher on 2007-05-02
[SIDEBAR]It is always a smart idea to have a router in between any PC and cable-modem, direct connection provides an avenue for security breaches[/END SIDEBAR]

Does your ISP require some specific software to be running before you can access the Internet on Windows? With your PC plugged into the cable-modem and running, power-cycle the cable-modem and re-do the network config in Ubuntu and see if you get anything.

---

### Post by puckjock on 2007-05-02
I have a linksys modem. It works fine with my XP computer. I uninstalled it from my XP computer to try it on this linux setup. I was trying to use wireless setups with linux, but i wanted to get down to basics going directly to my modem. 
This computer was my main XP computer(now linux) it worked fine..i will have to open it up to see what network adapter is installed..if that makes any difference.

---

### Post by lamalex on 2007-05-02
post the output of ```
sudo lspci -vv
``` and make sure your computer recognized the card and also it will list what type it is

---

### Post by puckjock on 2007-05-02
I know I need a router I have one installed on my xp machine. This linux setup is temporay until I get it working correctly. What exactly do you need from the lspci-vv command ...its a long list. I'm on my laptop hookedup tothecablemodem next to the linux machine. I took off the linux ethernet and connectedthe cablemodem to my laptop so i can go online.
I've noticed all my cards  are on IRQ 9 or 11.... is that a problem

---

### Post by starcraft.man on 2007-05-02
Just paste the whole output from the above command.

Also, I'm a bit at a loss... you have a Linksys Modem? Linksys supplies modems for ISPs? Are you sure its not your phone/ISP companies hardware? Should be written on the bottom of the hardware.

---

### Post by puckjock on 2007-05-02
Its a Linksys BEFCMU10 modem. I purchased this modem 3-4 yrs ago, so I would not have to pay the monthly fee. Right now I'm going to take the ethernet card out and try to change the IRQ setting.

---

### Post by puckjock on 2007-05-02
Its a Linksys Lan 10/100 ethernet card. No settings to change.
Also, how do I paste it to my laptop????

---

### Post by lamalex on 2007-05-02
most ISPs have mac address blocks, as in you can't just plug into your router a different card without calling your isp and having them add that mac to a whitelist. put your router back in and try it

---

### Post by oilchangeguy on 2007-05-02
turn off the modem. wait about 30 seconds and plug it back in. hook it up to your linux box, reboot, and you should be able to get online. when you use your windows box, follow the same steps, or it won't be able to get online. each computer has it's own ip address. if you use a router you won't have to turn the modem off each time. the router has an ip address.

---

### Post by puckjock on 2007-05-02
I took the modem off my active xp machine(has a router) and now using it on my laptop(w/o router) without calling my isp.
I could put the router on the linux machine, but i wanted less hardware to test it out first.

---

### Post by oilchangeguy on 2007-05-02
please read post #11.

---

### Post by puckjock on 2007-05-02
All this mac address talk, ip address talk, calling isp.... all I do to get online is, unplug the Linux ethernet cable, and plug in the xp laptop ethernet cable and I'm online. No rebooting, no resetting, no calling isp, no mac address config, no ip config...I just plug it in and get online!!! This modem came off my main XP machine. This laptop has never seen this modem, and I still connect.
 There is something between xubuntu and communicating with the modem that is not working...................

---

### Post by femto_x on 2007-05-04
hey ....
i m very new to linux...
i installed ubuntu 7.04 on my Presario V 4000 laptop....

i need to connect with LAN connection....

but i cant able to connect with internet....

its shows eth0.....in the devices..
i configured tht but not connected....entered all the IP add and subnet mask and DNS add...
still not working....

dont know the reason...
anybody can expalin step by step....coz i never used Linux yet now....i dont know anything abt it...plz help me to connect internet...

---

