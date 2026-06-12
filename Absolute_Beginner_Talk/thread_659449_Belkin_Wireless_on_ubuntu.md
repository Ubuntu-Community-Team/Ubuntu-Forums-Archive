---
title: "Belkin Wireless on ubuntu"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by JimmyLimRG on 2008-01-05
Hey Guys

I am new to ubuntu and linux in general ... i installed ubuntu 7.10 fine .. no probs, and i installed my belkin FSD7050 reciever using ndiswrapper and it worked fine ... now everytime i load up ubuntu it works fine untill i attempt to connect to my router ... at that point the reciever becomes unresponsive (e.g the light no longer flashes) and it just goes round and round in circles, asking me for my WEP key every so often, which i enter, and it still attempts to connect, even though my wireless reciever isnt doing anything

being new to ubuntu i dont have a clue ... i dont even know where to be begin so any help would be greatly appreciated

Jimmy

---

### Post by eolson on 2008-01-05
The wep key is the encryption key to your router.  Try looking on the back or the bottom of the rounter for a tag with a number (other than the serial number)  it will PROBABLY be 10 digits.

---

### Post by JimmyLimRG on 2008-01-05
oh no .. i got that lol, all i am trying to explain is that even though my reciever is not sending or recieving any signals it is still trying to connect ... i insert my wep key everytime and still nothing

---

### Post by AndyCooll on 2008-01-05
In effect it's asking you for your password to access the router. You "WEP key" is your password. It will be the same one you will have used for any of your other pc's that you have previously connected to the router.

:cool:

---

### Post by JimmyLimRG on 2008-01-05
im gonna have to edit my first post .... i have my wep key ... my wep key is good ... im trying to tackle the unresponsive reciever problem lol .... i dont know where to start or what the problem could be cos i am using it fine in wondows right now to post all this

---

### Post by eolson on 2008-01-05
What I would do as a first step is disable the encryption on the router and see if I could connect that way.

---

### Post by JimmyLimRG on 2008-01-05
i cant ... its not the router, im connected to it now, from the same computer using the same wireless card but through windows (i have two hard drives, windows on one and ubuntu on the other)

i am fairly certain that my belkin reciever is the problem

---

### Post by eolson on 2008-01-05
O.K.  Fire up Ubuntu

Do you get the network icon in the upper right corner.  To me it looks like stacked terminals.  Unless your connected then it's like signal bars on a cell phone.  Or maybe you get the arrows going roundy roundy.

---

### Post by JimmyLimRG on 2008-01-05
i get the roundy roundy arrows ... when i first installed it i got the signal bars but now it doesnt go past connecting (roundy roundy)

---

### Post by eolson on 2008-01-05
right click on the roundy roundy's ....  You should get a listing of available networks.  You may have to click on wireless or some such also.

If after all that you don't get anything ... you're right you Belkin is bad OR  I've run out of talent.

---

### Post by JimmyLimRG on 2008-01-05
i have done that too lol, i get my network and a signal strength next to it ... i try connecting that way but get the same response ..... i have tried manually configuring ... that didnt work .... the whole time my wireless card doesnt respond ... the light on it doesnt flash once ... so i know its not doing anything

i just dont get why my wireless card works with windows, and yesterday it worked with ubuntu but today...nothing on ubuntu

its strange

---

### Post by eolson on 2008-01-05
If it's seeing your router,  it's working I'm pretty sure.  something in your config?  Time out while I think.  Maybe somebody else has an idear?

---

### Post by JimmyLimRG on 2008-01-05
cheers anyway ... it truly has me stumped ... i just tried loading ubuntu with it in a different usb port ... still same problem ... it works long enough to find my router then stops working the moment i try to connect

---

### Post by eolson on 2008-01-05
If it's initially connecting then dumping you,  it must not like your encryption key for some reason.  Kind of like on dial-up when you have the wrong password and  get a connection to your isp, the modems handshake, and everything goes quiet (except for the click when it hangs up).

Lets see,  what are the options.  64 bit, 128 bit,  hex, octal, decimal;  I think that's about it for WEP.

---

### Post by JimmyLimRG on 2008-01-05
my key is fine too ,,, it worked yesterday ... same settings today ... the wireless curs out before it asks for key

---

### Post by eolson on 2008-01-05
Well ..... SCREAM ..... :):):)

I know, it ain't funny,   but I'm out of ideas.   Well one last one.  Turn everything off.  Unplug the Belkin, wait a half hour or so.  Plug the Belkin back in and restart the computer.

Told you I was desperate.

---

### Post by JimmyLimRG on 2008-01-05
believe me ... i know how ya feel ... i have been at it all day

---

### Post by eolson on 2008-01-05
I've used up the better part of a 12 pack of Lone Star so it's time for me to give it up. :)

Sorry.

---

### Post by JimmyLimRG on 2008-01-05
no worries, im going to bed anyways, maybe twill like me more in the mornin

---

