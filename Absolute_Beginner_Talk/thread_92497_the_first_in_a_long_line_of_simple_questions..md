---
title: "the first in a long line of simple questions."
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by alex_klement on 2005-11-19
hi everyone.

total linux newbie here, with a lot of windows experience. which is probably a bad thing because i haven't used a command line since dos 6.22, and i want to be able to do all the cool stuff RIGHT NOW. plus i know just enough not to be of much use, but enough to do really stupid and dangerous things. i'd imagine that i am the kind of linux user that most other linux users roll their eyes at.

but i am very willing to dig myself out of this pitiful trench of ineptitude i find myself in - if you'll humour me.

right now that i've got my grovelling out of the way i have a question; i'm trying to get my wlan card to connect to my wlan using wpa. now i know i can workaround by changing my encryption to wep, but that's not really the point. i'm using an atheros based chipset.

i've looked at the howto on the ubuntu site ([here](https://wiki.ubuntu.com/WPAHowto), but when i use the command:

```

sudo apt-get install wpasupplicant

```

ubuntu tells me: "E: Couldn't find package wpasupplicant". i can't find it in the synaptic package manager either. any ideas what i'm doing wrong?

(apologies for the verbose post, but i thought i might as well explain my user level upfront)

one other question - is all lowercase posting frowned upon here?

tia.

---

### Post by DJ_Max on 2005-11-19
*wpasupplicant* is in the universe.

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)

> one other question - is all lowercase posting frowned upon here?
It would be nice to use proper sentence syntax.

---

### Post by estel on 2005-11-19
Welcome to the Linux community!

First thing: have you added the Universe repositories to apt-get?

First, in the terminal type ```
sudo nano /etc/apt/sources.list
```
Then uncomment (if you have the line) or paste in the line:
```
deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted
```

In the terminal, ```
sudo apt-get update
```
```
sudo apt-get install wpasupplicant
```

---

### Post by alex_klement on 2005-11-19
thanks a lot guys. all sorted now.

but i think i need to go do a lot of reading and come back a bit later, as i'm doing stuff, but not not fully understanding the underlying concepts. ;)

as an aside, i'm loving linux, it's great learning something new!

---

### Post by estel on 2005-11-19
Yes, that's the main reason that I got into Linux - the quest to... know more :).

I'm not too sure what you mean by the underlying concepts though; they aren't so much concepts as... ideas.

i.e. Su: You use su (or sudo) as an administrator, because this aids security in keeping administrative tasks impossible for normal users unless they have the password, but allows the admin to have a normal user account and preform admin tasks without the *potential* of messing something up.
You can only really mess something up if you SUDO, so you know when to take extra care.

---

### Post by steve.horsley on 2005-11-19
You should be able to find Synaptic from the start menu (assuming your GUI is working) - system -> Administration -> Synaptic package manager.

I can see wpasupplicant there, but I can't work out which repository it's in. You may need to go Settings -> repositories and enable the multiverse and universe repositories.

I wouldn't have noticed that you posted all lower case if you hadn't asked.

---

### Post by DJ_Max on 2005-11-19
[QUOTE=steve.horsley]
I can see wpasupplicant there, but I can't work out which repository it's in. You may need to go Settings -> repositories and enable the multiverse and universe repositories.
[/QUOTE]

It's in the universe like I said.
```
apt-cache show wpasupplicant
```

In Synaptic
Right-Click *wpasupplicant*, the click properties. Look at "Section".

---

### Post by alex_klement on 2005-11-20
hi again.

i've done the wpa_how to, found [here](https://wiki.ubuntu.com/WPAHowto), and i've hit a stumbling block. i'm struggling somewhat with the use of a configuration file. i'm used to the windows central registry and gui's, and would just like some help on this particular config file please.

now the example config file has a lot of text in it, all commented. i assume i can get rid of this info if i don't need it? is it common practice to delete it, (does it affect access times or anything), or should i just leave the comments in?

anyways, i generated my passphrase okay, and stuck this in the config file:

```

network={
        ssid="i will steal your credit card"
        #psk="this isn't really my password"        psk=27e8a1a055c878c631bf1900b34ff27f4324769879cc7eeaad66744fa838f5197
}

```

then i ran the command:

```

sudo wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi

```

the command spits this dialogue out:

```

ioctl[SIOCSIWPMKSA]: Operation not supported
Trying to associate with 00:0f:b5:b9:f8:b6 (SSID='i will steal your credit card' freq=2462 MHz)
Associated with 00:0f:b5:b9:f8:b6
WPA: Key negotiation completed with 00:0f:b5:b9:f8:b6 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:0f:b5:b9:f8:b6 completed (auth)

```

but my wifi isn't working. any idea what the problem could be?

my wifi works off the same interface as my lan internet connection, could this be the problem? i.e. - i have a netgear wireless/adsl/ethernet router.

---

