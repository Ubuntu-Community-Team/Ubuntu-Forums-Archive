---
title: "Dialup Connection onto Ubuntu???"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by Future Proof on 2007-03-30
How would I go about adding a dialup internet connection to Ubuntu? I've been to the network settings already and i've added the details (number to dial, username, password etc.) but when I click on Firefox nothing happens.

Am i missing something?
:confused:

---

### Post by zvacet on 2007-03-30
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=dial+up&titlesearch=Titles]("https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=dial+up&titlesearch=Titles")

---

### Post by Future Proof on 2007-03-30
Since i have an old model dial up modem, it doesn't look like i will be using it with Ubuntu any time soon.
Thanks anyway :)

---

### Post by Chilli Bob on 2007-03-30
I'm using an old dial up modem, and as long as it's an external modem, it should be easy to set up. Look this [URL="https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9"]
_[COLOR="RoyalBlue"]page[/COLOR]_[/URL] and try  "Alternative Way 1 (using wvdialconf & wvdial)". 

After set up the config, here's the trick. Unlike Windows, where opening Explorer or Firefox automatically launches the modem dialer, in Ubuntu you have to do it yourself. You can do it from administratio menu, but I just open a terminal and type "wvdial". This will call up your ISP and log you in. Then just minimise it out of the way and open Firefox (or whatever you like). When you are finished, just go back to the terminal and type Ctrl-C and it will hang up. 

It's a couple more steps than in Windows, but works fine.

If you have a built-in modem, that's a whole other world of hurt.

---

### Post by Future Proof on 2007-03-30
> **Chilli Bob said:**
> I'm using an old dial up modem, and as long as it's an external modem, it should be easy to set up. Look this [URL="https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9"]
_[COLOR="RoyalBlue"]page[/COLOR]_[/URL] and try  "Alternative Way 1 (using wvdialconf & wvdial)". 

After set up the config, here's the trick. Unlike Windows, where opening Explorer or Firefox automatically launches the modem dialer, in Ubuntu you have to do it yourself. You can do it from administratio menu, but I just open a terminal and type "wvdial". This will call up your ISP and log you in. Then just minimise it out of the way and open Firefox (or whatever you like). When you are finished, just go back to the terminal and type Ctrl-C and it will hang up. 

It's a couple more steps than in Windows, but works fine.

If you have a built-in modem, that's a whole other world of hurt.

Yes, I have an external modem and I've just tried typing wvdial into the terminal and this is the response i got:
Cannot open /dev/modem: No such file or directory

Have i missed something?

---

### Post by unisol on 2007-03-30
sudo wvdialconf /etc/wvdial.conf. try this see if it recognizes your modem.you could also try system-adminstration-networking, fill in the info make sure your external is on ttyS0 or ttyS1.

---

### Post by Future Proof on 2007-03-30
> **unisol said:**
> sudo wvdialconf /etc/wvdial.conf. try this see if it recognizes your modem.you could also try system-adminstration-networking, fill in the info make sure your external is on ttyS0 or ttyS1.
I'm very confused about the command you mention at the start of your post:
wvdialconf /etc/wdial.conf
do I write etc or should i replace it with something else

---

### Post by phidia on 2007-03-30
To set up ppp correctly you need to open a terminal and do:
> sudo pppconfig running that will create the files you need for ppp to work correctly. 
Use pon (your providername) to dial out and poff to end the connection.
Once you have a connection you can apt-get install gnome-ppp

---

### Post by Bartender on 2007-03-30
Are you using Dapper?  It's broken in Edgy, but in Dapper I entered the correct values in Networking, then right-clicked on the top panel, went into "Add to Panel", put the Modem Monitor (the icon that looks like a phone) on the top panel, then when I click on the Modem Monitor it tells the modem to start dialing.  It's not particularly obvious that you're online - the modem will stop squawking and the activity lights will be randomly flashing.  I click on Firefox and it opens to my home page.
I don't even know how to set up wvdial.  Never had to.
Oh, yeah, Dapper will "Auto-detect" the external modem (usually tty01 I believe) when you're in Networking.  Edgy won't.

---

