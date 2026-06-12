---
title: "KPPP dialer problems, need help."
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by djsoss on 2007-07-29
](*,) When I open the kppp internet dialer the error doesn't show up any more but I still can get the darn thing to dial out! the kppp dialer comes up just fine and seems like it's going to work but then when I hit connect, it just hangs there. It just says modem read & then it says initializing modem and it just stays there. I opened the log box and all it says is ATZ ATZ ATZ and some weired characters like []|v0 or something like that. Also the dialer box keeps saying script timed out.  Please help.

---

### Post by Bachstelze on 2007-07-29
What kind of modem do you have. Most likely, it will be much, much, much more complicated than that to get it working.

---

### Post by nick.inspiron6400 on 2007-07-29
Have you got the ISP number set up yet? I am using Gnome PPP at the moment, and before the number it has ATZ.

What Internet provider are you trying to connect to?

Nick.

---

### Post by Bartender on 2007-07-29
Yeah, dj, we never talked about what kind of modem you've got.

Also, if you can, it might be helpful to copy the text you get in the dialer log and paste that into an e-mail

---

### Post by djsoss on 2007-07-30
> **nick.inspiron6400 said:**
> Have you got the ISP number set up yet? I am using Gnome PPP at the moment, and before the number it has ATZ.

What Internet provider are you trying to connect to?

Nick.
The name of my internet provider is ISP.Com. I tried to install the Gnome PPP Package after downloading it but it won't install. I'm have the 6.06 version of Kubuntu if that helps.

---

### Post by djsoss on 2007-07-30
> **HymnToLife said:**
> What kind of modem do you have. Most likely, it will be much, much, much more complicated than that to get it working.
I realy don't know what kind of modem it is. I just took an old windows box and installed Kubuntu on it. I've heard of winmodems, do you think I might have one of those? or Might it be the modem it's self?

---

### Post by oilchangeguy on 2007-07-30
what's wrong with getting a highspeed connection? any idea how much you are missing because you want to use dial-up? most phone and cable companies now have entry level high speed packages available. with prices at or near those of dial-up.

---

### Post by Bartender on 2007-07-30
oilchangeguy -
Perhaps you don't understand how good you've got it.
I'm on a rural road.  A mere 3.5 miles from the main Qwest phone switch house.  Qwest keeps sending me ads - "Sign up for DSL!!  You'll be so happy!"  So I call them, knowing what the answer will be.  "Oh, I'm sorry, sir, DSL is not available at your location."  Yeah, thanks.
And I'm not paying $60/month for satellite. 

dj - 
Yeah, chances are very high that you have a winmodem.  You need to identify it and maybe someone can help.

---

### Post by Bartender on 2007-07-30
> **djsoss said:**
> I've heard of winmodems, do you think I might have one of those? or Might it be the modem it's self?
Yes to both.  A winmodem is a bare-bones modem that does very little actual work, passing that off to the main processor.  In order to pass the buck, the winmodem needs to communicate with the CPU via Windows.  Windows + cheap modem = winmodem.

---

### Post by djsoss on 2007-07-30
Yeah, I've actually tried getting DSL set up from like 3 diffrent companies and they asked me for my phone number and zip code, they flat out told me that I wasn't within the service range for DSL. and I realy don't have enough funds for broadband. I'm going to go home and take out the modem card and see what kind it is; will keep you guys posted and thanks for all of your help.

---

### Post by F_r_e_d on 2007-07-30
Go to [www.linmodems.org](www.linmodems.org).  That's where I started.  Once you identify your chipset, go to the chipset manufacturer's website and see if there are Linux drivers for your modem.  If you have a conexant chipset, you may be in luck since they have generic drivers.

I know you can get this running on dial-up.  I did, but it does take some work!

---

### Post by djsoss on 2007-08-06
I've tried everything and nothing; that scan moden utility just told me to disable the the operating system from controlling the modem in the BIOS & when i did that it still didn't do anything. It also told me that I would be better off using a serial modem. I thought that Linux was supposed to be better & more stable than Widnows? what's the deal? I starting to think I sould just uninstall Kubuntu.

---

### Post by Bartender on 2007-08-07
Linux IS better & more stable.  Dial-up is just one problem area.  Those stupid winmodems have been the standard for the last decade, so computers all over the world are  infested with them.  If the winmodem manufacturers wrote Linux drivers things would be much better.  With big players like Dell entering the field, we may see some improvement in that area.

And it's possible that modem manufacturers are starting to see a market.  I'm thinking Zoom's new 3095 USB modem, if it works as they claim.

So all you can do right now is accept that dial-up is one of the few trouble spots, and that you're in it, and you have to make a decision.  Linux is still worth the effort.

---

### Post by tagginannie on 2007-08-10
> **Bartender said:**
> 

So all you can do right now is accept that dial-up is one of the few trouble spots, and that you're in it, and you have to make a decision.  Linux is still worth the effort.



WRONG!! DIal up is one of the easiest things to set up in Linux Ubuntu just makes it hard for people who have dial up to get it working.:smile:


Dj, make sure that you have a "resolv.conf" in your etc folder if not right click on kde desktop and choose the run command and type in konqueror than click options-run as different user you see root in the user field just type in your password. I find running Konqueror as root makes it a little bit easier when I need to admin. tasks. Just make sure to close it when your done. now go in to the "etc" folder and look for a file called "resolv.conf" if there isn't one just right click and choose new text file, now just save as the file you looked for. Now while in the etc folder go in to PPP folder and edit the "options" file  go down to the line, 

# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
auth

"#" before "auth" if there is not one al; ready there now save  

Get get an external modem because they work with every distro, CompUsa has them starting at $30

---

