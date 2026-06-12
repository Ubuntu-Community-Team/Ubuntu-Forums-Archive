---
title: "iBook G4 12&quot; WPA"
date: 2007-05-30
forum: Apple PPC Users
---

### Post by johng4 on 2007-05-30
Supposedly I have an Airport Extreme in this laptop, and try as I might I can't get connected to my WPA Router.  WiFi Radar picks it up, and I give it all the proper options but there is one that throws me off...

When I enable WPA in WiFi Radar, it asks for a driver... I've tried putting in the bcm43xx, and bcm43xx-fwcutter options in there, but it won't connect.  I've got xsupplicant, and wpasupplicant installed, but they seem to make no difference.

Anyone use 7.04 with an iBook able to connect to WPA?  I would perfer to keep my router to WPA since its more secure, though I have the option for 64 and 128bit WEP.

---

### Post by tcrroadie on 2007-05-30
Hi johng4,

I have never tried to configure WPA personally, I just use WEP at my home since my neighborhood is small.  

I also have Feisty installed on my ibook G4 but have never had good success with getting a wireless network connection using wifi-radar or Gnome network manager.   So I just learned how to set my wireless card using the terminal.  Is is actually very easy.  

Fist do you have wireless B support enabled on your network?  Many users have stated that they cannot get wireless G working with Airport Extreme, including myself.  

You can use a command line tool called iwlist to display information of available WAP in your area.  You can use iwlist to check the settings of your WAP.

Eth1 should be your wireless network card.  

```
sudo iwlist eth1 scanning
```

Then to configure your wireless card, you would use a tool called iwconfig.  See the manual for more information of the use of iwconfig.  
```

man iwconfig
```

To set your essid, without quotes 
```

iwconfig eth1 essid "your network"
```

To set your WPA key enter

```
iwconfig eth1 key "your key here"
```

And if you need to set your channel
```

iwconfig eth1 channel "channel of your network"
```

Then you can use ifconfig to see if your Airport Extreme card has recieved an IP address.

```
ifconfig
```

---

### Post by johng4 on 2007-05-30
I'll try that when I get home.  My router is set for b&g.  I can set it to WEP, but despite my knowledge I'm weak when it comes to wireless networking.  I've never really liked it however my network has grown beyond my wired accomodations.  Currently I've got 2 networks in my house:  General User, and my Studio, with 8 connected computer between them... got 2 or 3 wireless machines available as well.

---

### Post by APU on 2007-05-30
Forget WEP, it can be broken within 1 Minute with current techniques!

WPA does work pretty flawlessly (i use it all the time on my PowerBook 12"). I don´t have a Link to a Howto ready but just look into the Ubuntu Wiki. There you´ll find everything you need!

---

