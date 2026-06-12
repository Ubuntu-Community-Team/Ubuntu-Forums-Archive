---
title: "Setting up Netscape ISP"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by WoodyMahan on 2006-12-20
I am setting up UB 6.06 for a friend.  They use Netscape dial up ISP in Win XP.  I have always had high speed at home since going over to Lin.  I have had no experience setting up dial up, nor have I had any experience using Netscape with Lin.  Has anyone out there set up a UB install using Netscape Dial Up?

---

### Post by Tarvok on 2007-01-15
I don't have any experience with Netscape in particular, but I have done dialup (my high-speed connection didn't work at first; they had to have technicians fix the exterior lines).

First thing to note: You need a real modem. There are two kinds of modems out there. The most common are what we call "winmodems," and you'll need to find some special software to get it running. Head over to linmodems.org to see if that's what you have, and how you can get it running.

The other kind is what we call "real" modems, which have all their instructions right there on the modem, itself. These you can just plug in and use.

You'll need an access number, their username, and their password. Now, you can try the app found at System->Administration->Networking. Just select the modem connection, hit "properties," click "enable the connection," enter the phone number, username, and password, and theoretically, it should connect. However, I was unable to get that working, so here's what I had to do:

```
sudo wvdialconf
```

That will look for your modem, and generate a file called "wvdial.conf" for the program "wvdial." Next, you need to edit wvdial.conf

```
gksudo gedit /etc/wvdial.conf
```

Find the lines that start with "phone", "Password" and "Username". Get rid of the semicolins at the beginning of the lines (those disable the lines) and replace things like <Target Phone Number> with the appropriate information. Your file should now look something like this:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttyS4
ISDN = 0
Phone = 5550123
Password = letmein
Username = Thatoneguy@myISP.net
```

Now, you just need to type

```
wvdial
```

and it should dial your provider.

I hope this helps. Heck, you posted three weeks ago, so I hope you're still around!

---

### Post by Brian R. on 2007-01-19
I have no experience using Netscape ISP, but i do have a PCI Netcom InModem 56V.92 Winmodem, which the system sees as a LT WINMODEM Device Agere System. I then went to Administration/Networking put in my password when requested, and there was my modem showing. Clicked Properties it was showing as a ppp0 device clicked enable that connection, input my ISP's phone number, username, and password. Clicked modem tab made modem Autoconnect, dial type Tone, then clicked Option Tab, set Modem as default route to internet, and ticked Use Internet Service Provider Nameserver. Back to Networking dialog box clicked Activate and it happily dialed my ISP and connected me. Hope this helps as I was getting a lot of conflicting advice concerning WinModems. The only thing I miss is not having an icon in the system tray to tell me i am connected. Anybody know how to do that.

---

