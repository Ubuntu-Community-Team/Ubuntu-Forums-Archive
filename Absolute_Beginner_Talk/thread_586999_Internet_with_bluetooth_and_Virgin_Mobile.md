---
title: "Internet with bluetooth and Virgin Mobile"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Herman-Peter Cook on 2007-10-22
I have bluetooth device and cellphone.

I need to access internet through cellphone!

How?

P.S. I have Ubuntu 6.06 LTS 64bit

Herman-Peter

---

### Post by thenailedone on 2007-11-09
:confused: How sad... no answers...

Let's try again :)

I will soon be receiving Gutsy and my only means of getting on-line @ home @ present is a Samsung F300i (and later this month I will get my upgrade and will most probably be getting a SE)...
I also have a Virgin Mobile sim (cheapest data in SA below 2gb basically) and will need to use the cell either through the cable or via blue tooth to surf... is this going to be possible?  (Easy, Difficult, Impossible?)

Cheers

---

### Post by so7777777os on 2007-11-09
That's will be so slowy if it can ........

---

### Post by bithkits on 2007-11-09
> **so7777777os said:**
> That's will be so slowy if it can ........

In South Africa internet access is a sore point.

We have some of the most expensive broadband deals in the world :(

Lots of people have dial-up. The only other sort of cheap option is cellphone tech, like 3G. But that is crazy expensive per megabyte :( :( :( :(

---

### Post by thenailedone on 2007-11-09
OT: @ least Virgin gives you a 50c a megabyte option... so I can have mail at home, keep the anti-virus up to date, surf a bit and and dl a game patch every once in a while...

---

### Post by t0p on 2007-11-09
I haven't got a precise answer to this.  However:

I live in the UK and use a cellphone on the Orange network as a modem.  I connect the phone to my PC with a USB link.

I use **wvdial** to make the internet connection.  **wvdial** is an "intelligent PPP dialling program" that is included with Ubuntu as default.

You'll need to check **wvdial's** manpage for full instructions.  But to help out, below I have reproduced the /etc/wvdial.conf file that I use:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
 Phone = *99#
 Password = A
 Username = B
 Stupid Mode = 1

```

*99# is the number required by my cellphone network to establish a GPRS connection.  Obviously, your network may require a different number.

My network does not require a Username/Password to connect; but **wvdial** requires something to be in those fields - hence I use A and B.

The Stupid Mode entry is required, otherwise **wvdial** just seems to ring and ring without answer.

Hope this helps!

---

### Post by thenailedone on 2007-11-09
> **t0p said:**
> I haven't got a precise answer to this.  However:

I live in the UK and use a cellphone on the Orange network...

... Hope this helps!

Wow... thx for the info and a glimmer of hope (btw, no special drivers or anything required? :)  When using my SE K750i I had to use *99***1# and on the Samsung *99**1*1#... so it seems more phone specific than network specific...

---

### Post by thenailedone on 2007-11-13
> **t0p said:**
> I haven't got a precise answer to this.  However:

I live in the UK and use a cellphone on the Orange network as a modem.  I connect the phone to my PC with a USB link.

I use **wvdial** to make the internet connection.  **wvdial** is an "intelligent PPP dialling program" that is included with Ubuntu as default.

You'll need to check **wvdial's** manpage for full instructions.  But to help out, below I have reproduced the /etc/wvdial.conf file that I use:

```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ttyACM0
ISDN = 0
 Phone = *99#
 Password = A
 Username = B
 Stupid Mode = 1

```

*99# is the number required by my cellphone network to establish a GPRS connection.  Obviously, your network may require a different number.

My network does not require a Username/Password to connect; but **wvdial** requires something to be in those fields - hence I use A and B.

The Stupid Mode entry is required, otherwise **wvdial** just seems to ring and ring without answer.

Hope this helps!

Ok, so I edited my etc/wvdial.conf to look exactly the same as yours and when I use your number of *99# or any of those I have used in Windows wvdial has success connecting to the modem, the number is sent and then PPPD (or something) seems to send two random characters... after about fifteen seconds I get an error code 16 (which means the modem has hung up) and wvdial tries to reconnect... :(

I checked the man files for wvdial but didn't get to much help with init strings etc.  I am at a loss and without net access Ubuntu is stuck in second gear :(

Help! :confused:

[I]edit... I will be giving [this thread's]("http://ubuntuforums.org/showthread.php?t=343989&highlight=usb+modem") info a try when I get home.. here is holding thumbs :)
edit2: Tried the info on the first page on the link above and still no luck, I get the same problem of the modem disconnecting after +- 15 seconds... I won't bump the thread until I can post the exact message wvdial is giving me... :([/I]

---

