---
title: "Wireless only works in LiveCD"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-08-02
Hey folks. I see that this issue has been covered before, but I'm hoping for a good discussion on this so that I can understand my specific issue a little more. I appreciate all input.
I have a HP nc8000 with an Intel 2200BG wireless card. I did a fresh install of Dapper and had a wireless connection after some playing around. Then, I upgraded to Edgy, and after a couple days, I lost the connnection completely, and I only just recently got anything to respond, but still no luck with a connection. 
So after many frustrations in trying, I decided to run the LiveCD to do a fresh install and see if that would do anything for me. I found that the LiveCD allows me to connect without any changes at all, but the Dapper install is behaving the same as Edgy was previously. 
I'd really like to finally enjoy my wireless freedom, but I have no means of data transfer (no dual-boot, no disc of any sort). Is there any way to fix the problem?

---

### Post by ugm6hr on 2007-08-03
From the LiveCD and your HD installation - try:
```
lshw -C network
```

Only thing I can think of is that a different driver is being used following installation...  If so - the bit that says driver=... will be different in the 2 situations.

---

### Post by dca on 2007-08-03
Same problem I had w/ a Dell laptop and Intel ipw2200bg.  I had to revert back to 6.06LTS....

---

### Post by Hospadar on 2007-08-03
you might try hunting down the latest version of your drivers, building them from source and installing them.  you may also need to blacklist the old drivers so they don't accidentally load instead.  There are some tutorials around on how to do this, it will probably be specific to your card.

Alternatively, will your card work on fiesty?

also, have a look-see at your /etc/network/interfaces file and see if it is different between when you are using the livecd and on your actual install.  This is the file that determines how your network is set up.

also are you using software that pings for connections (like wifi-radar) on your install, but not on the livecd? sometimes these softwares can cause connection problems.  you may have better luck removing them and using a static connection setup.  I had to uninstall the default gnome wifi daemon to get my wifi working.

---

### Post by CheshireMac on 2007-08-05
Okay, this is getting weird, but kind of pleasant. I have it working on the install, and all I did was switch on the card and change the channel. I've done these things before, but it wouldn't work. I think my computer is pissed at me and only works when it wants. ~LOL~

---

