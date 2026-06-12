---
title: "Unable to Connect to ADSL Internet in Ubuntu"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by todd1049 on 2007-07-13
I am unable to connect to ADSL internet in Jordan using a Thomson SpeedTouch 510v6 modem.  I admit that I am totally new to Ubuntu, so I am not even certain my internet connection is set up under System | Administration | Networking.  I would greatly appreciate any suggestions folks might have for establish a first-time connection that go beyond the standard help file.  I have tried the sude pppoeconf command in the "terminal" application and that seemed to work -- or at least it did not indicate that nothing was wrong.  Thanks!

---

### Post by boldexplorer on 2007-07-13
You have presumably set up the moden under System> Administration > Networking 
this includes the number on the side of your modem.

Then in Firefox you need to Edit your Preferences and set the Connection Setting to Auto-Detect. 
This is what I did on my computer and it worked fine so I hope this helps!

ciao!

---

### Post by todd1049 on 2007-07-14
Thanks for your reply.  About setting up the modem -- do you mean I should do this under System | Admin | Network or System | Admin | Network Tools?  Under System | Admin | Network, the system (Ubuntu 7.04) appears that it will only let me  configure a traditional dial-up modem through its "Modem Connection" option.  Without a phone number to dial, this option doesn't work.  And I don't have a phone number (or don't know it) on my ADSL system.  Under Network Tools, should I be looking at the Ethernet Interface eth0?  Also, you mentioned a number on the side of the modem.  Would this be a serial or model number?  The modem does not have any IP address on it.  Were you referring to the Modem Access Code?  Thanks again for your help.

---

### Post by roachk71 on 2007-07-14
Another thing you could try is opening a terminal window and typing
```
sudo ppoeconf
```Give your user password at the prompt. This tool will then guide you through setting up the modem with your DSL username and password, etc.

The networking controls in the GUI unfortunately don't offer DSL options, but if yours is a cable modem, you could use the Networking control panel to set up a DHCP connection through your network card.

---

### Post by kvonb on 2007-07-14
When you ran "pppoeconf" it should have searched for the modem and found it connected to one of your ethernet cards (eth0 if you only have one).  If it found it, it would then go on to ask you for your username and password, then a few other questions.

If it didn't find the modem, then I suggest making sure that your ethernet card IP address is set to the same range as your modem, for example, my "modem" is at address 10.0.34.34, so my network card is set as static IP 10.0.34.99 (the last number shouldn't matter as long as it is not lower than your modem's, or .255).

Once done, you can try to ping the modem:

```
ping 10.0.34.34
```

you should get a response (if the modem supports that)

To start the pppoe connection, open a terminal and type:

```
sudo pon dsl-provider
```

...yes use the name "dsl-provider"

to disconnect, type:

```
sudo poff
```

To use pppoe like a dial-up connection, (start and stop from the desktop rather than terminal) run Synaptic and install "gpppon", it is a GUI frontend to "pon" and "poff".

Hope that helps :)

---

### Post by Andy_240707 on 2007-07-24
Hi Guys,

I'm a complete beginner with Linux, so please bear with me.

I've installed 64 bit Ubuntu 7.04 from the CD first, just to see what it's like.  I like it a lot, so the next step is the Internet connection, and that's where i'm having problems.

I've got a Speedtouch 546 Ethernet modem that is plugged in and works under windows XP fine.

The help function in Ubuntu tells me to run pppoeconf - i do this with sudo pppoeconf and i get a text gui.  It sees that something is connected to eth0 but on the next step i get an error message saying the Access Concentrator can't be found or doesn't respond.

I have no idea what this is, or what i should do next.

The problem being described in the thread is the closest i've found so far.

Any ideas??

Cheers,

Andy.

---

