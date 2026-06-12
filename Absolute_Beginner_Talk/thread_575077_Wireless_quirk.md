---
title: "Wireless quirk"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2007-10-13
I was trying to install usb Wirelessnetwork adapters on my kids computers. On my Ubuntu box, I was in the router controls. My box has worked flawlessly with this router for over a year. I was unable to get the girls' systems to configure with the WEP, so from my ubuntu laptop, I simply turned off the security (WEP key) and clicked 'save'. The girls systems immediately hooked up. 

I went back to my laptop and noticed I had lost my connection to the router... No internet. So I went up to the wired system and logged into the router. I re established the WEP security. Nothing changed: same ESSID and same 10 digit ascii WEP key. However, nothing I do will alow my box to connect. 

Has anyone dealt with this kind of thing?  If so, what makes it happen like this? 

Now, eve with the WEPback on, the windoze machines are all connected, but Ubuntu is DOA... :confused:

---

### Post by Tteddo on 2007-10-13
So, to  be clear you turned the WEP back on in the router, but the kids are still connected?

---

### Post by Papa-san on 2007-10-13
Yes... Go figure!
The same thing happened to my benefit the first time I got mine working a year ago.

---

### Post by Tteddo on 2007-10-13
Right, so since you don't have WEP setup on the kids, it cannot be set on the router. I have seen that with various routers (DLink and Netgear for instance) where you try to set it but it doesn't take on the first try. Your computer is still set for WEP, that's why it can't connect. At least that's what is sounds like to me.

---

### Post by Tteddo on 2007-10-13
Or...it has saved your WEP settings, but it isn't activated. DLinks are setup like that, or at least they used to be.

---

### Post by michiel.patrick on 2007-10-13
I would completely reset your router and start from scratch. There should be a pinhole on the back. Push that in and hold for.... I believe about 10-30 seconds and then shut power off and turn back on.

---

### Post by Tteddo on 2007-10-13
He just needs to turn off the WEP on his computer and it should work for all, then he can work on resetting the encryption. If the kids are working, and they don't have WEP enabled then the router doesn't have it enabled either.

---

### Post by Papa-san on 2007-10-13
Yeah, that's what it was at first. I used my 'Connection Manager' which, at first, showed both secured and unsecured signals. when refreshed, only unsecured showed. I couldn't connect, they could...

It's a Westell DSL wireless router/modem. I believe, because I had entered the proper WEP keys for them, whatever computer gremlins that be made them work as soon as it came back on secured..
I have doublechecked the router, and it is as I said... WEP back on. The router sees my laptop, and my laptop sees the router... theyre just speaking different languages again. 

When I run iwconfig, My ESSID is now "off/any" and access point is "Not-Associated".

---

### Post by Papa-san on 2007-10-13
Looks like something mesed up where my box is trying to receive a DHCP offer in the wrong place. The subnet it should be querying is 255.255.255.0 (Which is the sub for my host IP: 192.168.1.1) However, when it is in the act of making the query, it is looking to get the DHCP from 255.255.255.255 which is the subnet for my ISP IP, beyond the router...
anyone know where I would change this?

Also, when I do go to my network settings GUI, it never has anything in the default gateway device box...

---

### Post by Tteddo on 2007-10-13
But, the point being is that your kids do not have WEP set, and they are connecting fine. Therefore logically the router is not set for WEP no matter what it says. So, I would disable WEP on the Ubuntu machine just to see if it works, then the next step would be to reset the router like michiel.patrick said because it looks like it is confused. The problem with that is depending on your ISP (like if you have Verizon) you are going to have to setup your DSL connection info inside the router again. That can be a giant pain.
Maybe power cycle the router and go back in and see what it says then?

---

### Post by Papa-san on 2007-10-14
Right... That would follow logic, except that their computers DO have the WEP set and functioning. I did describe this earlier. If you were to bring a laptop into this house and I were to give you the exact ESSID and WEP key, you would not be able to connect with the internet. I do not know why this is, but it is. At that time, I would have to go into the router settings and change them once and back again to allow it.Nothing else works, and I have had several people try. 

Sometimes it requires both pieces of hardware to go through this dance a couple of times, but with the exception of my ubuntu box, it always works. The Ubuntu typically requires a re-format and re-install to do it. For whatever reason, it will hold old networking  information on the hard-drive and access it rather than the new information I enter into the GUI's. After a significant amount of editing various files through terminal or gedit, I have had it work out twice.. Other than those two times, it's a re-install.

However, I am currently dealing with a problem where a networking GUIactually changed my systems name, and won't allow me to open any administrative programs.

---

### Post by Tteddo on 2007-10-15
Sounds like your router is flaky....
I have had pretty good luck with [WICD]("http://wicd.sourceforge.net/") on both of my laptops. It can do all the forms of encryption. and can manage all your network connections, replacing the Gnome one.
I had a router one time that was really flaky with WEP, like you describe almost, but when it was set to use WPA it worked great. I think it was a Linksys.

---

### Post by Austin_KW on 2007-10-15
> **Papa-san said:**
> I...Nothing changed: same ESSID and same 10 digit ascii WEP key. However, nothing I do will alow my box to connect. 

10 digit is **hex**[0..9,a..f] not ascii. (ascii for wep would be 5 or 13 ascii characters for 40 or 104 bit keys respectively)

---

### Post by Papa-san on 2007-10-29
Sorry... Meant hex. :-D

Oh... I wouldn't call it a viable solution, but re-installed Dapper and wicd. Wireless works, and you can look at other threads of mine to see which problems I am dealing with again in regards to the system freezes... Eventually, as I continue to blindly tinker in my xorg.conf file, I might hit something usable! LOL

---

