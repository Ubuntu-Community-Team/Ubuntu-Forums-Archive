---
title: "Static IP at Home, but not elsewhere"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by hnaamyilkemku on 2007-07-29
Hello,

I want to set up a static IP on my laptop so I can use domains for file sharing between this computer and a windows machine at home. At the same time, I use my laptop on other networks (primarily at work), so I don't want my computer to demand a static IP address from those networks. How can I set this up? As far as I understand, I can edit /etc/network/interfaces to make the wlan static with the address I want, but I don't know if this implies that my computer will always want a static ip for the wireless connection. All insight appreciated!

---

### Post by WarholsGhost on 2007-07-29
i found this

"It would be simple if every computer that connects to the Internet could have its own static IP number, but when the Internet was first conceived, the architects didn't foresee the need for an unlimited number of IP addresses. Consequently, there are not enough IP numbers to go around. To get around that problem, many Internet service providers limit the number of static IP addresses they allocate, and economize on the remaining number of IP addresses they possess by temporarily assigning an IP address to a requesting Dynamic Host Configuration Protocol (DHCP) computer from a pool of IP addresses. The temporary IP address is called a dynamic IP address.

Requesting DHCP computers receive a dynamic IP address (think temporary phone number) for the duration of that Internet session or for some other specified amount of time. Once the user disconnects from the Internet, their dynamic IP address goes back into the IP address pool so it can be assigned to another user. Even if the user reconnects immediately, odds are they will not be assigned the same IP address from the pool. To keep our telephone telephone analogy going, using a dynamic IP address is similar to using a pay phone. Unless there is a reason to receive a call, the user does not care what number he or she is calling from. "

[http://searchvb.techtarget.com/sDefinition/0,,sid8_gci520967,00.html](http://searchvb.techtarget.com/sDefinition/0,,sid8_gci520967,00.html)

---

### Post by hnaamyilkemku on 2007-07-29
Thanks you for taking the time to make that post, but I'd like to clarify for other posters that I didn't mean I want a static IP from my provider--I'm talking about sharing files over a home network behind a *router*. That is, my router periodically receives a new IP from my ISP just because I don't want to shell out the big bucks for a static one, but I want my laptop, which connected to my home network wirelessly, needs a static IP from my router, which likewise sometimes assigns a different local address to my laptop (for example, when it's reset).

---

### Post by ugm6hr on 2007-07-29
Do you use wifi or ethernet?

Wicd can setup static IP or DHCP for each individual access point, so would solve the issue for wifi.

I think you can also set "locations" for ethernet connections with Wicd, which *should* allow you to set each location separately.  I think you would just have to select the location each time you wanted to connect to a different router.  However, I haven't tried this - so perhaps someone who has can confirm.  Otherwise, maybe try asking on the wicd forum.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
[http://wicd.sourceforge.net/phpbb/](http://wicd.sourceforge.net/phpbb/)

---

### Post by arsenic23 on 2007-07-29
Also if your router suports it, you could set the MAC for your PC up in it's Static DHCP list.  This way you can leave you machine set to DHCP, but your router will always give it the IP you specify.

---

### Post by hnaamyilkemku on 2007-07-29
arsenic23, your solution sounds interesting but I don't understand how to implement or see if I can implement it. Could you expand a bit on your recommendation? Meanwhile I'll take a look at ugm4fr's suggestion. Thanks to you both!

---

### Post by hnaamyilkemku on 2007-07-29
I tried wicd. This is awesome! At least, I think it is... how can I check to see if it worked?

---

### Post by arsenic23 on 2007-07-29
> **hnaamyilkemku said:**
> arsenic23, your solution sounds interesting but I don't understand how to implement or see if I can implement it. Could you expand a bit on your recommendation? Meanwhile I'll take a look at ugm4fr's suggestion. Thanks to you both!

Well depending on what kind of router you have, it may or may not have a 'Static DHCP' list.  You just fill in the Mac, desired IP, and name of the PC, and it makes sure that the PC gets the correct IP.  I use it extensively, but I mostly have experiences with the Linsys WRT54g v2 and the WRT54gL, so I couldn't tell you where the setting might be on your router.  But if you log into it and take a look around it should be rather easy to tell if your router suports Static DHCP.

Included below are screenshots of the setup page on two differnt firmware releases for the WRTs ( *Mac addresses and router names have been hidden*. ):
[[IMG]http://img520.imageshack.us/img520/1281/wrt54g1dc1.th.jpg[/IMG]](http://img520.imageshack.us/my.php?image=wrt54g1dc1.jpg) [[IMG]http://img294.imageshack.us/img294/486/wrt54g2er2.th.jpg[/IMG]](http://img294.imageshack.us/my.php?image=wrt54g2er2.jpg)

---

### Post by imdano on 2007-07-29
> **hnaamyilkemku said:**
> I tried wicd. This is awesome! At least, I think it is... how can I check to see if it worked?Well, if you have one profile set for dhcp and one for static, try connecting using both on your home network.  When you use the one you set up as static you should get the IP you specified, with the other you should get a DHCP assigned IP.

---

### Post by rhodry on 2007-07-29
> **arsenic23 said:**
> Well depending on what kind of router you have, it may or may not have a 'Static DHCP' list.  You just fill in the Mac, desired IP, and name of the PC, and it makes sure that the PC gets the correct IP.  I use it extensively, but I mostly have experiences with the Linsys WRT54g v2 and the WRT54gL, so I couldn't tell you where the setting might be on your router.  But if you log into it and take a look around it should be rather easy to tell if your router suports Static DHCP.

Included below are screenshots of the setup page on two differnt firmware releases for the WRTs ( *Mac addresses and router names have been hidden*. ):
[[IMG]http://img520.imageshack.us/img520/1281/wrt54g1dc1.th.jpg[/IMG]](http://img520.imageshack.us/my.php?image=wrt54g1dc1.jpg) [[IMG]http://img294.imageshack.us/img294/486/wrt54g2er2.th.jpg[/IMG]](http://img294.imageshack.us/my.php?image=wrt54g2er2.jpg)

I totally agree. This is your solution!! I have been doing this forever with laptops on Ubuntu. You simply get your connecting port's MAC address and use it to set up a fixed DHCP lease within your router. Your laptop stays a DHCP connect, which covers all other roaming, but when you connect to your home router it recognizes the MAC address and issues the same ip address to it every time; essentially creating a fixed ip address on the local lan.

You have to get to know your router better. I have a Billion 7404 and a Linksys like the one above. Works the same but is in a different spot in the internal config of the router. Each router has a web address and login (given to you when you bought it) - eg My Billion is [http://192.168.1.254](http://192.168.1.254).  Within that setup is where you set all this up. Contact your router manufacturer support if you do not know how. This works flawlessly and is independent of operating system, ie I do this on various Linux versions as well as XP. All the OS sees is an ip address provided by DHCP from the router.

Rhodry.

---

### Post by hnaamyilkemku on 2007-07-30
I looked around my router config pages, arsenic. No luck. We have the same type of router, but apparently I have an older version which does not support the static dhcp lease feature. Anyway, I tried wicd and it worked yesterday, but for some reason today I'm having some issues accessing certain web pages. I posted about that problem [here]("http://ubuntuforums.org/showthread.php?p=3107643#post3107643"). Thanks for your help! That feature would be great...

---

