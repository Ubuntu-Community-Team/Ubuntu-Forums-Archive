---
title: "Beetel ADSL+2 PPPoe &amp; Ubuntu 6"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by lucky_chouhan on 2006-12-04
I am recently installed Ubuntu 6 and successfully analyze my Lan Card & My Adsl Modem. i can ping my xp client in Ubuntu so  tell me the ADSL setup step by step.

---

### Post by kvonb on 2006-12-04
Your ISP uses PPPoE connection? 

Open a terminal and type:

```
pppoeconf
```

This is an automatic script that will ask you questions like username and password.

If you are using Ubuntu machine for Internet Connection Sharing, then make sure you set the MTU lower than 1500, I think it will suggest 1492, I run 1412.  If you get this wrong you will find that secure webpages will not load, like hotmail.com.


Once you have done that, turn on sharing, open a terminal and type:

```
sudo gedit /etc/sysctl.conf
```

Look for the following lines:

```
# Uncomment the next line to enable packet forwarding for IPv4
#net/ipv4/ip_forward=1
```

...and remove the # from the bottom one.  Save and exit gedit.

Next restart the network:

sudo /etc/init.d/networking restart

Next download and install the pppoe desktop controller (if you want a simple icon interface):

```
sudo apt-get install gpppon
```

Make an icon on your taskbar or desktop using the command "gpppon".

To connect to the net just click the icon, select the provider fron the drop box and click on "ppp-on".

That should do the trick!

Also make sure you set the gateway on the other computers to be the IP address of the Ubuntu machine.

Regards, Kev :)

---

### Post by lucky_chouhan on 2006-12-05
thanks for your reply giveme some time for testing.

---

### Post by lucky_chouhan on 2006-12-06
Thank you very much finally i got the internet on my Ubuntu.

Thank you all of the Ubuntu forum users. such a great community.
i love this forum -

[http://img2.freeimagehosting.net/uploads/1102e2dd2d.png](http://img2.freeimagehosting.net/uploads/1102e2dd2d.png)

---

