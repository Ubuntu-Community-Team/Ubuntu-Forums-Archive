---
title: "Trouble with wireless: linksys WUSB54G"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Atreus12 on 2006-12-03
I have been trying to get my linksys USB wireless network adapter to work with my dell desktop on Ubuntu 6.06

I've followed some guides on here, but no sucess yet. I managed to get 'ndiswrapper' installed, and I have the windows driver for the wireless adapter.

This is a working driver that I am currently using on XP.

I attempted installing the .inf file, and it gave me an error, and says invalid installation.

> agrieser@andrew:~/linksys$ sudo ndiswrapper -i wusb54gv2.inf
Installing wusb54gv2
couldn't copy wusb54gv2.inf at /usr/sbin/ndiswrapper line 135.
agrieser@andrew:~/linksys$ sudo ndiswrapper -l
Installed ndis drivers:
wusb54gv2       invalid driver!
agrieser@andrew:~/linksys$



When I go to System -> administration -> networking
A wireless connection is recognized, but it won't connect to anything. In fact, the wireless connection was recognized before I even attempted installing the driver.

Unfortunately, I am using the 'old' WUSB54G, as in version 1, not the latest version 4 where I believe they switched chipsets.

If anyone has any ideas on how to get this working, let me know.

Edit: if you are wondering why I tried installing the V2 driver, it was just me being hopeful after I got the same results trying version 1.

---

### Post by wickstopher on 2007-01-25
I'm not sure whether I have the "old" or the "new" version, but I do have the same wireless USB adapter from linksys and have had no problems with getting it to work in Edgy Eft 6.10 (and I'm a complete newbie to this linux stuff!).  I read that it is best to keep it disconnected during the install.  This may or may not help you, but this is how it worked out for me:

<ul>
<li>Installed Edgy Eft with wireless adapter disconnected</li>
<li>After the install completed, connected WUSB54G to USB 2.0 port</li>
<li>Went to menu System > Administration > Networking</li>
<li>From here, click on your wireless connection.  You're going to want to know the <b>name of</b> (not sure if this is required information, but it didn't present me with a list of wireless networks, and I entered it and it worked)) and the WEP Key or other passcode for your wireless network.  In my case, it was a 128 Hexadecimal passkey, as from what I could tell, it has no option to scan for wireless networks.  If anybody knows how to do this, reply to this thread!.</li>
</ul>

that was really all it took, and I was online.  Maybe I got lucky, but if you haven't tried this, see if it works, and let me know!

<wickstopher>

---

### Post by Atreus12 on 2007-01-25
Holy Old Thread Batman!

It seems like ages ago when I was wrestling with wireless. I have since got it to work. I think my problems were not uderstanding the way things work in linux, and not being able to use the 'make' command. 

But to answer your question, I have the really old V1 card, most everyone else has a V4, and it will not work without ndiswrapper in 6.06, although I haven't tried edgy. 

To scan for networks, go to the terminal and type
$iwlist scan
and it should spit out a list of wireless networks that your network card can 'see.'

Thanks for the tip though, I will certainly try this when 7.04 comes out.

-Andrew

---

### Post by hush on 2007-02-07
> **Atreus12 said:**
> 
To scan for networks, go to the terminal and type
$iwlist scan
and it should spit out a list of wireless networks that your network card can 'see.'

I'm having trouble getting my Linksys Wireless USB Network Adapter to work correctly as well. 
I tried: $iwlist scan, and it gave me this...
bash: scan: command not found

It works when I take the security passwords off, but If I set my wireless router up with a password, Network Manager on my Desktop PC won't show a drop down Network list. On my laptop it works just fine.. My only prob with the laptop is that the strength of all of the Networks that it finds.. are all 100% and I know that isn't right.. Is there a way to correct this?

---

