---
title: "Now if I could just get on MY network..."
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Mallette on 2007-06-17
So, with the help of this fine community and a lot of shoe leather, I finally got my wireless working.  I can see all the networks in the neighborhood.  However, I can not get on my own.  I can get on a neighbors unsecured net, but when I try to get on mine it pops up the password requestor, I enter it, then it goes away and says "wating for network password" and fails.  No question about the password...it works on my other machines.  

I've included it in my wpa_supplicant file but rem'd it out of the /etc/network/interfaces file as per the excellent instructions from the debianadmin.com site that got me going in the first place.  I did unrem it, but it did not help.

I think this is procedural, but I just don't know what procedure to change.

Regards,
Dave

---

### Post by Phixion on 2007-06-17
I'm not too familiar with Wireless Networking on Ubuntu, but are you sure you are using the right security mode? e.g. WPA, WPA2, TKIP, AES

If you don't use the right type you won't be able to connect.

---

### Post by Mallette on 2007-06-17
Yes, I am sure.  That part is pretty much the same as Windoze...

Dave

---

### Post by w4ett on 2007-06-17
Can you connect with the security protocols disabled?

---

### Post by Mallette on 2007-06-17
I presume you mean the network, not Ubuntu.  Hadn't thought of that.  However, since I can connect to any unsecured network (there are two around) I guess I figured I wouldn't really learn anything.  My network works fine on the other 5 machines in the house (Windoze).

What do you think?

---

### Post by wieman01 on 2007-06-17
What security protocol are you using:

WPA
WPA2
WEP

In case you are referring to WPA, have you got a WPA option in NetworkManager?

---

### Post by ugm6hr on 2007-06-17
> **Mallette said:**
> I presume you mean the network, not Ubuntu.  Hadn't thought of that.  However, since I can connect to any unsecured network (there are two around) I guess I figured I wouldn't really learn anything.  My network works fine on the other 5 machines in the house (Windoze).

What do you think?

When it asks for the password - does it list the correct encryption (I presume you are using WPA)?  And are you using Network Manager (the icon in the top right corner with 4 vertical grey/green bars) to access wifi networks?

The reason I ask is that I found Network Manager a bit hit and miss with WPA (although I think that was just me again).  Wicd is an alternative to try (use version 1.2.9 testing with Feisty) - it's a .deb from the wicd sourceforge page.  You will have to uninstall Network manager though.  If no one can help you get NM working to your satisfaction - give it a try.

---

### Post by w4ett on 2007-06-17
I was trying to brainstorm this and I would suppose, taking this to the least common denominator, disable your security on your router temporarily and :   1.  successfully ping your router with the Ubuntu box, 2. Connect to the Internet, 3. Double check your network security protocols and encryption and clone this information to your U/B and then re-attempt connection...also make sure that the router does not have the Ubuntu machine's assigned IP disabled/blocked.

---

### Post by Mallette on 2007-06-17
TIme for church here...  I'll check these out later.

However, I am running WPA-PSK AES.  I don't see anything to suggest Ubuntu is unaware of this.  I do not know what WPA2 is...

Dave

---

### Post by wieman01 on 2007-06-17
> **Mallette said:**
> TIme for church here...  I'll check these out later.

However, I am running WPA-PSK AES.  I don't see anything to suggest Ubuntu is unaware of this.  I do not know what WPA2 is...

Dave
WPA-PSK with AES is pretty much WPA2. Do you have this option using NetworkManager? Then configure it and choose WPA-PSK or WPA2-PSK together with CCMP (= AES). Then enter your password.

---

### Post by Mallette on 2007-06-17
wieman...
I don't seem to have any other options now.  Perhaps it is due to the wpa_supplicant.conf file?  It does seem that things sort of come and go with Unbuntu and I don't have enough control yet to figure out why.

My wpa_supplicant.conf file has #psk="mypassword" in it (though mypassword is really my password).

Dave

---

### Post by wieman01 on 2007-06-17
> **Mallette said:**
> wieman...
I don't seem to have any other options now.  Perhaps it is due to the wpa_supplicant.conf file?  It does seem that things sort of come and go with Unbuntu and I don't have enough control yet to figure out why.

My wpa_supplicant.conf file has #psk="mypassword" in it (though mypassword is really my password).

Dave
If you have have not got any WPA option, the current driver does not support it. What wireless adapter have you got?

---

### Post by Mallette on 2007-06-17
Well, it did at one point.  Now, WPA is the only option in Network Manager.  OTOH, under manual config, all I have is ascii/hex WEP.  NIC is a BCM4306.


OK, so suddenly other options appeared in Network Manager...duknowwhy.  

Changed to WPA2 Personal AES CCMP.  No good.  It also still waited for me to enter the pw, even though it is in the wpa_supplcant.conf file.

I tried manual config, and the net is listed but I only have ascii/hex WEP as options there.

This is very strange...

---

### Post by wieman01 on 2007-06-17
Is DHCP enabled and ESSID broadcast turned on? If the option is there, it should work given that you use DHCP. Don't configure it manually if you have NetworkManager working.

---

### Post by Mallette on 2007-06-17
Hmmm...   I have the ESSID name filled in, but I don't know about ESSID broadcast mode...  I see no settings for that.

DHCP is enabled.

Dave

---

### Post by wieman01 on 2007-06-17
> **Mallette said:**
> Hmmm...   I have the ESSID name filled in, but I don't know about ESSID broadcast mode...  I see no settings for that.

DHCP is enabled.

Dave
There is another tool called Wifi-Radar which you find in the repositories. If that does not do the job, well, then you need to think of something else. But it should work.

---

### Post by Mallette on 2007-06-17
I've seen posts that suggest that wifi radar conflicts with BCM.  I remain convinced this is some sort of procedural issue, as it would appear that everything is good technically since I can access unsecured nets.  

I saw somewhere a long, generated version of the passphrase for WPA.  As I recall, it was said to be optional and only somehow made it a bit quicker or something.  However, now I wonder...

It would be SO nice to get past this and on to the FUN part!  I keep most everything on a TeraStation fileserver, so until I can get on my own net the machine isn't much good for anything except poaching net time from the neighbors.  Really don't like doing that...

Dave

---

