---
title: "anyone try installing ubuntu on a g4 sawtooth?"
date: 2006-07-11
forum: Apple PPC Users
---

### Post by macgig on 2006-07-11
it works fine for me, but the text is blurry. menus, icons, filenames... even the text in the web browser. 

help! any other mac users have this problem after installing?

---

### Post by macgig on 2006-07-11
works now. got it. had to change screen resolution. :)

---

### Post by macgig on 2006-07-11
one thing I will mention that may? help other Mac/OSX users.... the **alternate** install was the ONLY one that worked for me (ubuntu 6.06). 

the first one I tried didnt work at all. :cool:

---

### Post by meshica7 on 2006-07-16
Hey there!
 I am also running Ubuntu on a Sawtooth G4! I am actaually dual booting OS X and Dapper (got rid of OS 9 Classic).
 I have been able to get Ubuntu to recognize my Airport Extreme card and Networkmbut I still have no internet.Have you gotten your internet access to work yet?If ya have,I need some help. :-k 

thanx
 Juan

---

### Post by macgig on 2006-07-16
the networking worked fine for me, didnt even have to do anything special to set up after installing. Im on dsl using a dsl modem/router via dhcp.

---

### Post by meshica7 on 2006-07-16
> **macgig said:**
> the networking worked fine for me, didnt even have to do anything special to set up after installing. Im on dsl using a dsl modem/router via dhcp.

i am also on DSL.What exactly did you have to configure,if you don't mind me asking?
Juan

---

### Post by macgig on 2006-07-16
I dont mind your asking. :)

I honestly didnt do anything. during the install, a screen came up saying that it's setting up dhcp networking... something like that... and walla. it just worked. I dont know if this is the norm or not? But I didnt have to do any tweaking at all. I just worked for me.

---

### Post by meshica7 on 2006-07-16
In the words of the immortal Napoleon Dynamite...

"Luck-eeh..."

I don't recall that process during the install for myself.[-( Hmmm...I need to check into this.I am at a lose as far as setting this up.It's not llike the Prefs in OS X.I copied down the settings (IP Address,etc) from my OS X prefs and punched them in where I believe they "fit" in the Network panel of Ubuntu but no connection yet.
 If ya think of anything,please let me know.:KS 

Thanx,

Juan

---

### Post by macgig on 2006-07-16
your using ethernet? I was looking at my settings.... .thought i'd mention some of them here... see if it helps you. :)

under system> administration> networking

under the connections tab, select ethernet... then click properties. enable this connection is checked, pull down menu is: dhcp. 

under the dns tab, I have dns servers. both appear to have ip's that are used with my modem. again, this was all done automatically for me during the install. ;) 

If need be, I could perhaps send some screenshots or upload here, if that would help.

---

### Post by meshica7 on 2006-07-16
> **macgig said:**
>  

If need be, I could perhaps send some screenshots or upload here, if that would help.


 That would be great!
thanx again

juan

---

### Post by macgig on 2006-07-16
heres where im putting some pics, screenshots. check em out. 

[http://flickr.com/photos/macgig](http://flickr.com/photos/macgig)

---

### Post by meshica7 on 2006-07-16
The screenshots helped me out.Thanx!
I got on the Verizon site (my ISP) and got my DNS #s and Domoin info.I plugged all this into the Networking app and away I went
 Now when I type in a url into firefox it actually takes abit of time (about 20secs) before I get the "Cannot retrieve the requested URL" error.Before it was instantaneous.
 So,I believe that all the info is correct.The problem may be that my Airport Station is not being recognized.Although WiFi Radar states that it is recognizing my network and the IP address is correct,the signal is strong,and the port appears to be detected as well. In the Networking Active/Deactive pane I have chosen the Wireless card option since I am using an Airport Extreme card to connect to my Airport Station.Both my station and DSL modem are working in OS X and all the status lights are on in Ubuntu.Should I choose the "Ethernet Port" option instead and make that active?:-k 
What do ya think?

 Thanx again!
Juan

 By the way,I need to put up some screen shots of my Macintosh Plus running System 6.0.1!:-D

---

### Post by macgig on 2006-07-16
i've never used wireless/airport, so im not sure about that... but im glad the other stuff helped you. :)

---

### Post by meshica7 on 2006-07-20
Macgig,

As it turns out,my Airport *is* being recognized afterall.

I ran


** iwconfig**

 And the resultant code informed me that the card was recognized at

 eth01

 Wif Fi is getting a strong signal.Now I'm back to configuring the network settings.I punched in all the DNS' IP'Gateways" etc that I got from the Verizon DSL site.

 Where did you get the "Search Domain" from ?

[IMG]http://static.flickr.com/64/191018168_95ccbe3cb6.jpg?v=0[/IMG]

Thanx again

juan

---

### Post by macgig on 2006-07-20
all the info I had was already there. entered automatically... so im not sure what the purpose of the search domain is.

---

### Post by meshica7 on 2006-07-21
Well...I'm online anyway!
I used my ethernet port to connect to my DSL modem and a USB line to connect the DSL Modem to my Airport Station.Now OS X uses it;s wireless card to pick up the Airport Station and Ubuntu uses the ethernet port to pick up the DSL modem.

Software fix:Tricky for a newbie
Hardware fix:Easy
Surfing the net in a dual boot environment: Priceless :-D 

Thanx for your help,I do appreciate it!
Now,if I can only get Scype to work in Ubuntu....:-k 

Juan

---

