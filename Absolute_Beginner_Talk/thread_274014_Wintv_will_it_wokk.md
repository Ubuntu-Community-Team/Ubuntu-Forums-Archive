---
title: "Wintv will it wokk?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-10-09
Hello ive got an Wintv express PAL-B/G 44804 how to set it up under ubuntu? Will it work at all this wintv sounds like windows only :P

---

### Post by Kateikyoushi on 2006-10-09
LinuxTV supports some Hauppage wintv cards see the list [here]("http://www.linuxtv.org/wiki/index.php/Hauppauge").

---

### Post by haxer on 2006-10-09
You dont know which is the best usb digital tv reciver for ubuntu?

---

### Post by Kateikyoushi on 2006-10-09
I wish I knew, I am also looking for one. :-k

---

### Post by The_Apprentice on 2006-10-09
If I am bored enough tonight I will set about getting my WinTV-NOVA-T USB2 working.

Saying that I may be playing the Battlefield 2142 demo,

---

### Post by haxer on 2006-10-09
Dont know really what you mean but if i have read i correct you will try to setup the usb tvcard thing you got and you will post a how to? but this wont happen if you will play battlefield demo? Just so i understand

---

### Post by The_Apprentice on 2006-10-09
That is correct.

I will investigate if I can install the TV card, but I am a Linux n00b.
If it is too difficult I will play games.

I will let you know how it goes, and what I did if I succeed.

---

### Post by The_Apprentice on 2006-10-10
I did some investigations last night trying to find some "How Tos" the TV card without any success.
What I did find seems a bit complex and incomplete, so I did not bother trying very hard.

If I do jump in and actually try it I will let you all know.

EDIT:
I have just found this link - [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) - which maybe of some help.

---

### Post by Kateikyoushi on 2006-10-10
I am not really surprised to hear that.
I have 2 pci tv tuners and one came with really bad drivers. It was a real hassle to install it, so I can imagine how could it be without the drivers... :cry:

---

### Post by anaconda on 2006-10-10
> **The_Apprentice said:**
> If I am bored enough tonight I will set about getting my WinTV-NOVA-T USB2 working.

Hauppauge WinTv NOVA-T USB2 is well supported and really easy to get working.
(but WinTv NOVA-T (usb-)stick doesn't have linuxdrivers yet. Confusing how they name different models so close to each others..)

All you need is to download file: dvb-usb-nova-t-usb2-01.fw and copy it to folder /lib/firmware

then reboot and install kaffeine (KDE tv-watching program) And you can start watching tv. after selecting your area and scanning all available TV/radio channels..

Here is a link to the firmware:
[http://thadathil.net:8000/dvb/fw/dvb-usb/](http://thadathil.net:8000/dvb/fw/dvb-usb/)

So far I have only tried the dvb-usb-nova-t-usb2-01.fw and it works well.. however I think the ..-usb2-02.fw is newer And will propably try it sometime.. I read from somewhere that if you use the ..-02.fw then you may have to rename it to ..-01.fw to get it to work..

Everything works nicely with the ..01.fw execpt that in remote-controller the only buttons that work are volume-control and numbers.. (so no ch+ ch- buttons.. which is a shame)

---

### Post by anaconda on 2006-10-10
> **haxer said:**
> You dont know which is the best usb digital tv reciver for ubuntu?

I dont know what is the best, but "WinTv NOVA-T USB2" works very well.. it is a bit more expensive (~84€) and bigger than some other models, (cheapest small USB-sticks here are about 50€) and some of them also work well.

I bought mine because I knew it works well with linux..

---

### Post by The_Apprentice on 2006-10-10
anaconda - Just wanted to say a big thank you for the heads up.

Part of my investigations last night said it should be identified, but then got lost in the comments about firmware.
Thanks for the link and the heads up.

---

### Post by The_Apprentice on 2006-10-10
Mkay, this could not possibly be easier :)
I had myne up and running with in 10 minutes.

So:
1.  Download the file: dvb-usb-nova-t-usb2-02.fw and copy it to folder /lib/firmware.  You can get it from [http://thadathil.net:8000/dvb/fw/dvb-usb/](http://thadathil.net:8000/dvb/fw/dvb-usb/) - Thanks to anaconda
2.  Rename the file to dvb-usb-nova-t-usb2-01.fw
3.  Install Kaffeine - mine was already installed under Gnome
4.  Shutdown you machine
5.  Plug in Hauppauge WinTV Nova-T-USB2
6.  Power up the machine
7.  Fire up Kaffiene - it will prompt you to configure DVB - you need to select your TV broadcast source (mine was UK-Crystal Palace)
8.  Click OK and Kaffiene will open
9.  Select the DVB tab
10.  Press C
11.  The Channels dialog should appear
12.  Click Start Scan
13.  When it has finished select all the channels you want on the right and  click Add Selected, so they move over to the left.
14.  Click Done.

It is now all configured and ready to watch TV.


Troubleshooting:

About the only place anything can go wrong is that the card is not detected.
Open /var/log/dmesg and search for NOVA-T, you should see that it has been recognised.
Mine did not work the first time because it wanted the firmware file to be called dvb-usb-nova-t-usb2-01.fw.  Once I changed the name and rebooted it was fine.

As your system boots up you should see the red LED on the NOVA-T-USB2 light up if it is detected.

If you have problems with sound in Kaffiene then you will have to search else where in the forums.

---

### Post by haxer on 2006-10-10
Thx guys love this forum always nice respond :)

---

### Post by pobice on 2006-11-19
Anyone else find that their computer won't shutdown or hibernate properly unless you unload the module dvb_usb_nova_t_usb2 first?  For both it locks up and I need to hold on to the power button to shut it down.

I'm using the firmware from here: 
[http://thadathil.net:8000/dvb/fw/dvb-usb/](http://thadathil.net:8000/dvb/fw/dvb-usb/)

```

[17293447.392000] usb 5-4: new high speed USB device using ehci_hcd and address 49
[17293447.528000] usb 5-4: configuration #1 chosen from 1 choice
[17293447.528000] dvb-usb: found a 'Hauppauge WinTV-NOVA-T usb2' in cold state, will try to load a firmware
[17293447.636000] dvb-usb: downloading firmware from file 'dvb-usb-nova-t-usb2-01.fw'
[17293447.908000] usb 5-4: USB disconnect, address 49
[17293447.908000] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[17293449.660000] usb 5-4: new high speed USB device using ehci_hcd and address 50
[17293449.792000] usb 5-4: configuration #1 chosen from 1 choice
[17293449.792000] dvb-usb: found a 'Hauppauge WinTV-NOVA-T usb2' in warm state.
[17293449.792000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[17293449.796000] DVB: registering new adapter (Hauppauge WinTV-NOVA-T usb2).
[17293449.796000] dvb-usb: MAC address: 00:0d:fe:95:95:95
[17293449.796000] i2c_adapter i2c-0: SMBus Quick command not supported, can't probe for chips
[17293449.800000] dib3000: Found a DiBcom 3000P.
[17293449.800000] DVB: registering frontend 0 (DiBcom 3000P/M-C DVB-T)...
[17293449.800000] input: IR-receiver inside an USB DVB receiver as /class/input/input19
[17293449.800000] dvb-usb: schedule remote query interval to 100 msecs.
[17293449.800000] dvb-usb: Hauppauge WinTV-NOVA-T usb2 successfully initialized and connected.

```

The device itself appears to work fine, the only issue I have with it is the shutdown issue.

---

### Post by The_Apprentice on 2006-11-20
Sorry I did not reply to this earlier, I forgot :$

Anyways, I have had no problems with shutting down and hanging.
The log you have posted clearly shows it fires up fine.
When you close down, does it hang on a particular process when stopping it?

Sorry, but I do not know enough about Linux to help you diagnose it.

I hope this bump's your question.

---

### Post by The_Apprentice on 2007-01-26
Arrrrggghhhhhhhh!

I have rebuilt my box and now can not find a copy of dvb-usb-nova-t-usb2-02.fw

Can someone please email me a copy to ubuntu at easy-it in the company of uk.

Many thanks in advance

---

### Post by anaconda on 2007-02-20
I tried the new ubuntu (Feisty Fawn 7.04) and it wants the firmware to be called "dvb-usb-nova-t-usb2-02.fw" so with feisty there isn't any need to rename it. Unless you have the "...-usb2-01.fw" then you must rename it to "...-usb2-02.fw" and it will work.

And if you still have problems with getting the firmware just PM me.  


I sometimes have had problems with shutting down .. hope this gets fixed.. not important however. Because it hangs in a point when it has already unmounted everything and is ready to shutdown.. I think the last message is "Will now halt!" and then it is OK to shutdown with the powerbutton. 
Interesting that reboot always works. 

.

---

### Post by The_Apprentice on 2007-02-20
Thanks for the offer, I forgot to update this thread, though I did update another thread. - [http://ubuntuforums.org/showthread.php?t=348707](http://ubuntuforums.org/showthread.php?t=348707)

---

