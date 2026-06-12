---
title: "Wi-Fi wierdness...."
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by GeordieJedi on 2008-03-23
Hi again, sorry to bother anyone, but Im having a spot of wierdness with trying to get my Wi-Fi working.

Right, I suppose a little bit of background might help.
I currently dual boot between Win-XP (sorry) and Ubuntu 7.10.

My Equip =
Router =  Linksys =  WRT54GC
USB dongle = Linksys = WUSB54GC 

I'm able to surf the net ok with XP (and thats where the original wi-fi was set up, + adding the WPA encryption/passwords and such).

So after messing around briefly with the network manager on Gnome, Im able to get online! but its using an open/un-protected system.

Whenever I try and use the encryption it asks for the password (i put in the one I origionally set up in XP) it then has a think about it, and then brings up the following dialogue box =

"nm-applet (/usr/bin/nm-applet) wants to accsess the default keyring but its locked"

Its then asking for a password, but which one?

Is it my personal password that I use to login to Ubuntu (and make system changes with),

Or the text password/passphrase of the router or

The WPA encrypted hexadecimal key thats created when I first set the router (which is the same as the main password thats just that hexadecimal gibberish)....??


So my questions are =

1. Which password am I supposed to be using?

2. Will Ubuntu use the same (WPA)-settings as I originaly set up
in XP?

3. If I need to change these settings for Ubuntu, will it affect my
settings for XP?

4. If I can get online using the "Open" system, does that mean,
my wi-fi is unprotected? (And as a result open to exploits)

5. My wi-fi signal keeps dropping out, (every 30-60 mins?) i've never
had this problem with XP (Not having a dig at Linux at all btw)
I seem to recall this is a bit of a known problem with Linux, is there
anything I can do to resolve this?


Sorry if this is a no brainer, any help would be greatly appreciated.
Thanks in advance.

---

### Post by notwen on 2008-03-23
> 1. Which password am I supposed to be using?

2. Will Ubuntu use the same (WPA)-settings as I originaly set up
in XP?

3. If I need to change these settings for Ubuntu, will it affect my
settings for XP?

4. If I can get online using the "Open" system, does that mean,
my wi-fi is unprotected? (And as a result open to exploits)

5. My wi-fi signal keeps dropping out, (every 30-60 mins?) i've never
had this problem with XP (Not having a dig at Linux at all btw)
I seem to recall this is a bit of a known problem with Linux, is there
anything I can do to resolve this?

1.  The first time you attempted connecting to any wireless access point you were prompted to create a keyring pass, use this.

2.  Ubuntu will connect just fine, just specify your WPA settings w/ Network Manager.

3.  You shouldn't need to change any settings on your router.

4.  ???

5.  What wireless card are you using?  Type the following command in a terminal and paste the output here:

```
lspci
```

---

### Post by ugm6hr on 2008-03-23
There is something a bit weird here.

If you use Ubuntu 7.10, the Gnome "keyring" is default identical to the Ubuntu login password.  So you shouldn't be prompted to enter it at all.  How it became "locked" I have no idea.

Intermittent dropped signals have been known to happen with some chipsets with Network Manager with secured (but I didn't think unsecured/open) networks.

It might be worth trying Wicd (see link below) instead of NM, cos it doesn't use the "keyring", and tends to be more stable.

But it might also be worth having a think about these issues rather than just finding a way around them.

---

### Post by GeordieJedi on 2008-03-24
Thanks very much ugm6hr and  notwen. Its much appreciated.

I'll try a few things and let you know.

Cheers

---

