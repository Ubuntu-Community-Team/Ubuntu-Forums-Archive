---
title: "Wireless Internet?"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Sporkmaster on 2007-04-07
Because I never entered a password, it's obvious that my new Xubuntu machine is now connected to one of my neighbors' networks. How can I tell Xubuntu to connect to MY hidden-SSID, WPA encrypted network?

---

### Post by LaurelLynn on 2007-04-07
Dear Sporkmaster,

If you go to the Menu option:   System->Administration-> Networking

Click on you wireless card then the properties button.  The settings should be in there.

Laurel Lynn

---

### Post by brn on 2007-04-07
You might have done this already but here is the only procedure I know:
 [LIST]
[*]System > Administrattion > Networking brings up the Network Settings window
[*]  One of the selections should be "Wireless connection", click  it.
[*]  Select "Propeties" and enter  the SSID and WEP (displayed on the bottom of your router?)
[/LIST]
My modem/router hss WEP but not WPA.  I don't know if this works the same for yours.

I have a FLASH router and found that I can access all sorts of configuration and status information on it by accessing 10.0.0.2 with my browser.  It requires a user name and password which for the FLASH device is "admin" and "zoomadsl"  One of the options here is to hide the SSID to prevent others from using my WLAN.  I haven't tried it though.

---

### Post by Sporkmaster on 2007-04-07
It's not WEP, it's WPA... different kind of security :confused: 

Do I need to download something for it to work?

---

### Post by brn on 2007-04-07
> It's not WEP, it's WPA... different kind of security  

Do I need to download something for it to work?
Here I can't  help.  WPA has stronger security than WEP but the latter is what my router  has and  my system (Dapper  v6.06) mentions only WEP in the setup dialog.  If  yours is the same, you might try simply entering  your WPA key where  *Network  Manage*r says WEP and see what happens. (Hint:  Mine seems to be hex, not ASCII.)  I'll speculate that Wireless security is entirely contained between  the router and your NIC, in which case either key might work.  Interestingly, I also have Windows XP on this machine where the WLAN setup was completely automatic.

---

### Post by Sporkmaster on 2007-04-09
I tried that and it would not connect... Does anyone know how to connect via WPA?

My dad seems to think we need 12 layers of security... meanwhile there are about 10 neighbors around us with completely unsecured networks. THAT's our security :mad:

---

### Post by Sporkmaster on 2007-04-09
bump

---

### Post by mand0 on 2007-04-09
> **Sporkmaster said:**
> I tried that and it would not connect... Does anyone know how to connect via WPA?

My dad seems to think we need 12 layers of security... meanwhile there are about 10 neighbors around us with completely unsecured networks. THAT's our security :mad:

Do you have the WPA package installed? Go to Synaptic Package Manager and search for "WPA".

---

### Post by Sporkmaster on 2007-04-09
It turned up kviewshell and wpasupplicant. I'm gonna put wpasupplicant on now... do i need kveiwshell too?

---

### Post by mand0 on 2007-04-09
> **Sporkmaster said:**
> do i need kveiwshell too?

I don't think so but I am not 100% sure.

---

### Post by Sporkmaster on 2007-04-09
Ok, i downloaded it and installed it, tried again, and nothing. It won't connect. It's not the SSID. I have the right key. I have the right static IP...

What is the problem? It wouldn't connect even with almost all the security off.

---

### Post by Sporkmaster on 2007-04-09
Bump

---

### Post by Austin_KW on 2007-04-10
Why are you hiding your ssid, it has no security value, and you are not really hiding it your ap is just not sending it in beacon frames.
You are just creating problems for yourself, and you neighbours will end up choosing the same channel because they can not see your AP.

What adapter/chipset are you using, You should be able to specify the access point using the wireless MAC and the ap argument to iwconfig on the command line or with preup iwconfig wlan0 ap xx:xx:xx:xx:xx:xx. But you may also need to specify the essid to properly hash the wpa PSK.

edit not really mad, its just substituting my xx:

---

### Post by Sporkmaster on 2007-04-11
> **Austin_KW said:**
> Why are you hiding your ssid, it has no security value, and you are not really hiding it your ap is just not sending it in beacon frames.
You are just creating problems for yourself, and you neighbours will end up choosing the same channel because they can not see your AP.

What adapter/chipset are you using, You should be able to specify the access point using the wireless MAC and the ap argument to iwconfig on the command line or with preup iwconfig wlan0 ap xx:xx:xx:xx:xx:xx. But you may also need to specify the essid to properly hash the wpa PSK.

edit not really mad, its just substituting my xx:

Ok I will try to answer every question that made sense to me
1) I unhid the SSID with no luck
2) Adapter? Chipset? Intel(R) PRO/Wireless 2200BG Network Connection. I don't know what a chipset is in that context (Sorry. I'm walking in unfamiliar territory here.)
3) I completely lost you at ap argument

Here's what I put into the wireless config box, the same info that i put into Windows:
(My ssid)
ASCII
*************
STATIC IP
192.168.1.103
255.255.255.0
192.168.1.1

also the WPA is TKIP security if that helps... are there any other boxes I should put input into?

---

### Post by Austin_KW on 2007-04-11
Ok, I suggest you leave your ssid unhidden
> Here's what I put into the wireless config box, the same info that i put into Windows:
Where are you putting this config, what manager are you using? How are you configuring the WPA suplicant?

If you enter static IP you need to configure both the default gateway and dns server to  192.168.1.1  Why not use dhcp and all this is taken care of for you.

Whenever you have wireless config problems you can temporarily disable wireless encryption and verify that you can connect to your network. Once you get the simple case working then reenable encryption

---

### Post by AndrewNi on 2007-04-11
Borrow your neighbour's connection for a second (or use a wired connection) and pop this into a console:

```
sudo apt-get install gnome-network-manager
```

Restart the machine. You will get an icon in the tray panel for connecting to wireless networks. You can then choose to 'connect to other wireless network' (as your SSID is not being broadcast), fill in the information and hope for the best. I use the network manager to connect to my WPA-enabled WLAN.

Note that as mentioned earlier, disabling SSID broadcast is probably making life more difficult for yo,u as all it takes is someone with some wireless network tools to watch the traffic to see it.

---

### Post by Sporkmaster on 2007-04-11
As of now, I've been using applications> system> networking.
DHCP is, unfortunately not an option here. I'll try the gnome wireless manager. :)

EDIT 1:

******************:~$ sudo apt-get install gnome-network-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-network-manager

Got the error twice. I'm definitely connected via a neighbor right now because I'm typing this up.

EDIT 2: I'll try getting it with the synaptic package manager

---

### Post by Austin_KW on 2007-04-11
That's a typo should be network-manager-gnome

---

### Post by Sporkmaster on 2007-04-11
Well, I just installed network-manager-gnome with synaptic package manager

But nothing in my system tray

---

### Post by chili555 on 2007-04-11
Here is a rather well done tutorial on WPA: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

