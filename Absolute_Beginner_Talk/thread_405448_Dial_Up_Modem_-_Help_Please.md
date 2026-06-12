---
title: "Dial Up Modem - Help Please"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by thegood on 2007-04-09
I can't connect to the internet through my dial-up modem.

I've been following the dialup modem howto exactly for the intel-536 modem and encountered no errors but using pppconfig i have problems.
when i type "pon myprovider" nothing happens below is "plog" output

user@user-desktop:~$ plog
Apr 10 11:00:33 user-desktop pppd[6549]: pppd 2.4.4 started by user, uid 1000
Apr 10 11:00:34 user-desktop chat[6551]: abort on (BUSY)
Apr 10 11:00:34 user-desktop chat[6551]: abort on (NO CARRIER)
Apr 10 11:00:34 user-desktop chat[6551]: abort on (VOICE)
Apr 10 11:00:34 user-desktop chat[6551]: abort on (NO DIALTONE)
Apr 10 11:00:34 user-desktop chat[6551]: abort on (NO DIAL TONE)
Apr 10 11:00:34 user-desktop chat[6551]: abort on (NO ANSWER)
Apr 10 11:00:34 user-desktop chat[6551]: abort on (DELAYED)
Apr 10 11:00:34 user-desktop chat[6551]: send (ATZ^M)
Apr 10 11:00:34 user-desktop chat[6551]: expect (OK)

My modem is supported by the intel-536 driver (intel-536EP-2.56.76.0_21_09_2006)

Im running 6.10 (2.6.17-10-generic).

I also tried wvdial but that wouldnt recognise my modem.
I really hope someone can help because it's getting really frustrating.

Thanks in advance.

---

### Post by terdon on 2007-04-09
Modem support is problematic in linux. This is because internal modems are so-called soft modems and rely on various windows functions to work. Your best bet would probably be to try [www.linmodems.org/](www.linmodems.org/)

Try having a look at their site, if you are still having problems post again! :)

---

### Post by Josey on 2007-04-09
If your new to linux your best bet would be to look for a .deb for your modem.  Basically most dial up modems rely on software to work.  If you plan to use dial up with linux save yourself some time and get an external dial up modem which won't rely on software to work.

---

### Post by thegood on 2007-04-13
I manged to get it working had to edit my wvdial.conf adding 
carrier check = no
stupid mode = yes 
I then type wvdial and it dials and connects
However it sometimes drops suddenly

Is there a simple way to create a shortcut to connect?   Ive created a launcher on the desktop (command=wvdial)  but how do i disconnect - what is the command?  Is there a  better way?

---

### Post by terdon on 2007-04-13
Depends,  do you have to create a symlink for your modem before dialing? (if you don't know what that is, then probably not :) )

If all you need to do is run wvdial, then, the easiest would be to run it from the command line. Just open a terminal, run wvdial and then Ctrl+C to disconnect.

However, if you can use wvdial, chances are you can also use a graphical tool such as kppp.

---

### Post by Matchless on 2007-04-13
If you have wvdial working, try using gnome-ppp as a launcher, it is actually a frontend for wvdial

---

### Post by F_r_e_d on 2007-04-13
Try going to [www.linmodems.org](www.linmodems.org) if you can get onto the internet from another computer.  That's where I started, and I eventually got Edgy to recognize my modem.  Also, try your internet provider's home page, or, there may be a forum associated with your ISP that might help.  I NEVER thought I would get my dial-up modem running, and it was frustrating, but I finally did.

Just be patient and keep reading and asking questions.  Barnes and Nobels has a book called the Beginner's Guide to Ubuntu Linux.  It may be at other book stores, too.  There is a chapter in there on connecting to the internet that helped me.  You don't have to buy the book -- just browse and take notes.

---

### Post by MichaelSM on 2007-04-19
Hello to all. One final problem with Edgy. I'm setting up a box for my Mum and she can only access dial-up. I've followed all the threads and posts I can find, and followed instructions.
I have a working US Robotics serial 52k modem. I've run the install in System>Admin>Networking. The modem is detected at /dev//ttyS0 and all the correct telephone numbers, passwords etc have been added. For ease of use, I've got Gnome PPP on my panel with the same data entered. I've compared the wvdial files and they are matched so far as I can tell.
BUT. Nothing is any different from what it was, as in: launch Gnome PPP, hit Connect; it goes through the noisy rigmarole in the modem and authenticates and registers the connection but no connection is actually achieved. Well, the box reads 'Connected', and the clock starts ticking over, but when I click on Details in the Gnome PPP window, and attempt to raise Firefox, the status line flickers from Send/Receive to Idle a couple of times, then sets itself at Idle, with maybe 6 packets sent and 5 received. If I wait long enough eventually the Can't Find Server box pops up. 
As usual, there will be something incredibly simple which must be done, but I can't figure it out. 
Any help greatly appreciated. Mike.
PS. The connection is ticked and enabled in Networking, and set as default. Whenever I try to connect dial-up, I disconnect the telephone line from my DSL modem, which seems sensible.
One last thing which might be important. The entries in the wvdial files mention PPPD rather than PPPO. Could that be the problem? I don't wanna edit something I don't understand!

---

### Post by traveller on 2007-04-19
Do you have an external modem? 
Try again. You may need  an external modem: a serial one, not usb. And you don't have to spend much because as far as I know some really cheap modems are very Linux friendly. 
Just keep trying and you'll probably manage to connect to the Internet. It just takes some time at the beginning. :)

---

### Post by terdon on 2007-04-19
Could you post the relevant config files (/etc/wvdial.conf) so we can see what's going on. Also, please state which one works!

---

### Post by MichaelSM on 2007-04-19
OK Posting that would give away my passwords etc so I'll edit it.

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <,xxxxxxxxxxxxxx>
ISDN = 0
; Password = <xxxxxxxx>
New PPPD = yes
; Username = <xxxxxxxxk>
Modem = /dev/ttyS0
Baud = 115200

Hope that helps both you and me!
Thanks so much for your reply.
Michael.
And, nothing actually WORKS! It seems to, then it stops.....

---

### Post by Michl on 2007-04-19
Not all internal modems are winmodems.  US robotics 5610b is flawless
and there are others.

As mentioned, get gnome-ppp.  Unfortunately it is a multiverse application
so you need to check multiverse when you check software sources.
Once you have it, installation is a breeze.  If your modem is compatible
with linux, it will detect it, too.

But you need to edit your init stings in set-up to take care of it dropping
out.  The command S19=0 took care of this for me.   This disables the
timer that shutsdown the modem when there is data inactivity.  Since in
most dialup situations there is plenty of intermittent data inactivity, you
want this off.

Good luck.  Dial-up works fine in edgy once you get past the early
hurdles.

Good luck.
Michl

---

### Post by terdon on 2007-04-19
OK, but in your last message you said you compared the relevant wvdial files. Compared with what? What happens if you connect using wvdial so you can see the error messages?

---

### Post by Michl on 2007-04-19
> **MichaelSM said:**
> OK Posting that would give away my passwords etc so I'll edit it.

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <,xxxxxxxxxxxxxx>
ISDN = 0
; Password = <xxxxxxxx>
New PPPD = yes
; Username = <xxxxxxxxk>
Modem = /dev/ttyS0
Baud = 115200

Hope that helps both you and me!
Thanks so much for your reply.
Michael.
And, nothing actually WORKS! It seems to, then it stops.....

You need to delete the semicolons before phone, password and username.
ALso, add S19=0 to the Init2 string.  I also like to add &U30 so that it does
not connect below 45333bps.  &U33 is at 50666bps if you want a higher
threshold.

If you have gnome-ppp you have an easy graphic interface.  Of course it
is pretty easy to do ti from the terminal with nano or gedit.  Just make sure
you save a copy of what you have before you edit:

Again, good luck.
M
Michl

---

### Post by MichaelSM on 2007-04-19
Hello Terdon. If this is any help:

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- OK
ttyS0<*1>: ATQ0 V1 E1 Z -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttyS0<*1>: Modem Identifier: ATI -- 5601
ttyS0<*1>: Speed 4800: AT -- OK
ttyS0<*1>: Speed 9600: AT -- OK
ttyS0<*1>: Speed 19200: AT -- OK
ttyS0<*1>: Speed 38400: AT -- OK
ttyS0<*1>: Speed 57600: AT -- OK
ttyS0<*1>: Speed 115200: AT -- OK
ttyS0<*1>: Max speed is 115200; that should be safe.
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
Modem Port Scan<*1>: S2   S3   

Found a modem on /dev/ttyS0.
Modem configuration written to /etc/wvdial.conf.
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"

Any help?
Regards, Michael

---

### Post by MichaelSM on 2007-04-19
Thanks for the replies. I just had a look at /etc/wvdial.conf. and there's nothing there at all, and it was filled with stuff earlier. Actually That's wrong....why? Doing sudo gedit it's an empty file, but looking at it through Home and File systems there's this: which I think I've put up before....

Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = 0
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/ttyS0
Baud = 115200

All the stuff is already entered in Admin>Networking. And in Gnome PPP.

I saw this a few times before, but couldn't figure out how to input the various passwords etc.

As for editing INIT. I'm a bit uncertain about that. 

I'm delighted to get replies. I'll work on this until it HAPPENS!

Your friend, Michael.

---

### Post by terdon on 2007-04-19
Hmm.. no, I don't see anything useful in the messages. Maybe someone else?

As for the empty file, if you can see the contents when you do```
cat /etc/wvdial.conf
```
then you're ok.

What you should do is copy this file to a new one and then edit the init values as suggested:
```
sudo cp /etc/wvdial.conf /etc/wvdial.conf.old
sudo gedit /etc/wvdial.conf
```

Good luck!

---

### Post by MichaelSM on 2007-04-19
All done as suggested. Everything is hunky-dory and I've checked it over a lot, believe me! I even edited PPPD=yes into PPPO=yes just in case that made any difference; it didn't, so I changed it back. No luck either way. I hate giving up but it's 2.40 am and I have to work in a few hours. Just so you know what's happening, here's the latest from terminal:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 S19=0
Modem Type = Analog Modem
 Phone = <xxxxxxxxxx>
ISDN = 0
 Password = <xxxxxxx>
New PPPD = yes
 Username = <xxxxxxx>
Modem = /dev/ttyS0
Baud = 115200

Dunno what else to do.

'Night. Michael.

---

### Post by MichaelSM on 2007-04-20
Hi Terdon. If you get the chance, tell me how to attempt connection using wvdial with terminal. I think I tried wvdial>enter once but nothing happened; as you said, it would be nice to see what actually occurs, rather than the graphical interface, which doesn't give a complete picture.
This is all a learning curve for newbies like me.
Thanks for your help,
Michael.

---

### Post by terdon on 2007-04-20
Hi Michael, 
    well, in principal all you should need to do is, as you said, just open a terminal, type wvdial and hit enter. Try that again and let me know what exactly "nothing" is ;)

If that doesn't work post the output of this command:```

cat /etc/wvdial.conf
```

And I'll see if I can help.

cheers

---

### Post by Bartender on 2007-04-20
Michael -
Unless you have a lot of time put into Edgy you might want to try installing Dapper.  Dapper "just worked" with my external USR Sportster (model #0701).
I didn't use wvdial or gnome-ppp.  No terminal work at all.  Just set it up in Networking, then added the Modem Monitor to the upper panel.  Click on Modem Monitor to dial.
I tried the same thing in Edgy and it didn't work.  Edgy keeps setting "Tones" to "Pulse".  It's sad to see that us poor dial-up users are being abandoned.
EDIT: How are the  little dipswitches set on the back of your USR?  On mine, #3, 5, and 8 were in the "down" position.

---

### Post by terdon on 2007-04-20
That may well be a good idea, but perhaps you should go for Feisty Fawn (Ubuntu 7.04 ) which was just released yesterday

---

### Post by Bartender on 2007-04-20
terdon -

What do you think are the chances they went back and fixed what was broken in Edgy?

It'll take me a few days, but will download Fiesty, install to a spare drive, and report back.

---

### Post by terdon on 2007-04-20
Bartender:

Well, I don't know, I've only just moved to ubuntu with edgy but I've been using redhat and suse for years and they do tend to imporve this sort of bug with each new version. So, I would expect it to be better yes...

---

### Post by Bartender on 2007-04-20
OK, I'll be back in a few days with a report on Fiesty, my USR 0701 external and the GUI interface.

One of these days I'm gonna have to try and make sense of wvdial and gnome-ppp...

---

### Post by MichaelSM on 2007-04-22
Hello Bartender and everyone else who offered advice. In the meantime I found an old Connexant winmodem and visited linuxant where there was a deb.zip which fitted the profile SCANMODEM detected. I'm just about to re-start and try it. Trying to make sense of the external serial  USRobotics modem was driving me completely mad. This other approach could easily be worse ,..... 

Back again. OK some good news. Through Linux-ant I downloaded and installed the deb.zip file relevant to the PCI modem as mentioned above. A re-start detected the modem at /dev/ttySHSF0 which was great! I inputted all the relevant data into Gnome PPP and tried to connect. Similar to the external serial USR modem I was trying to use at first, the PCI modem tried to get on track; it managed to make a dial tone, but no number was dialed, and after several seconds it made a 'busy' tone. Unfortunately I can't use that particular box at the moment which makes things hard.

The main thing is that the Gnome PPP says 'Carrier not found,'  I can't give you a terminal run-down right now, but Gnome PPP contains all the XXX=0, SP=0 strings but the wvdial conf file just lists:
Dialer Defaults
Phone Number
Password
Name etc.  

There were no Init strings listed there so I put them in as sudo under the line Dialer Defaults, and next time I tried to connect, terminal showed ATZ, followed by a doubled-up version of the Init2 strings, if you know what I mean. In other words, there are no Init entries in wvdial conf (I removed the ones I probably shouldn't have put in anyway) so it's a bit tricky. 

Trying to connect, now, terminal shows ATZ (Init1 I guess) which is NOT followed by Init2 (with all the bells and whistles) so it has no hope of connecting. 

In other words; if I put the Init1 and Init2 strings into wvdial conf, it doubles-up (as in repeats the Init2 string) which is obviously hopeless when i try to connect. If I don't, terminal displays only the ATZ with no follow-up. Is that fair enough?

Maybe another way of approaching this might be through Admin>Networking. It's one thing to enable a Dial-up conection there, but I've never known how to make it connect once it's all set up, which it is at the moment. The modem's recognised, the username and password are there, the phone number to dial is there, and it all looks great, but where's the 'Connect' button? The connection's enabled, the ticks are in the right boxes, and it's the default connection ....

Yours in cheerful confusion, 
Michael

---

### Post by kadath on 2007-04-23
I just did a clean install of Fiesty, and I'm hoping someone in this thread can help me.

On my previous Edgy install, I had my winmodem working with the sl-modem-daemon package and wvdial. However, I can't get it to work with Fiesty. I'm using the exact same wvdial.conf as I did with Edgy, but all I get is the following:

```
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDTXXXXXX
--> Waiting for carrier.
ATDTXXXXXX
NO CARRIER
ERROR
--> No Carrier!  Trying again.
```

It gives me the "No Carrier" error over and over until I CTRL+C. I don't recall ever having this problem with Edgy.

Here are the contents of my wvdial.conf:

```
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 115200
New PPPD = yes
Modem = /dev/ttySL0
ISDN = 0
Phone = XXXXXX
Password = XXXX
Username = XXXX
Carrier Check = no
Stupid mode = on
```

Any help would be appreciated.

---

### Post by terdon on 2007-04-23
Could it be that you have the ISP's phone number written with a "-" in your wvdial.conf file?

Can you hear a "handshake" (that weird screaming noise that modems make when they talk to one another)?

---

### Post by kadath on 2007-04-23
> **terdon said:**
> Could it be that you have the ISP's phone number written with a "-" in your wvdial.conf file?

Can you hear a "handshake" (that weird screaming noise that modems make when they talk to one another)?

No, I don't use a dash. I also don't hear any connection noise, but then again I never did with Edgy either (I may have turned it off, can't remember).

AFAIK, I have the exact same setup I had with Edgy, so I'm confused :confused:

---

### Post by terdon on 2007-04-23
Sorry to state the obvious but just in case, you are running slmodemd first to create the symlink at /dev/ttySL0 right?

---

### Post by Bachstelze on 2007-04-23
kadath > please run scanModem and post your ModemData.txt

---

### Post by kadath on 2007-04-23
> **HymnToLife said:**
> kadath > please run scanModem and post your ModemData.txt

Well, here it is:

```
 Only plain text email is forwarded by the  DISCUSS@linmodems.org List Server.
 Do use the following as the email Subject Line:
           SomeName, YourCountry Ubuntu 7.04  kernel 2.6.20-15-generic 
 This will alert cogent experts, and  distinguish cases in the Archives.
 YourCountry will enable Country Code guidance.
 Occassionally responses are blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at http://www.linmodems.org .
 Local Linux experts can be found through: http://www.linux.org/groups/index.html
--------------------------  System information ----------------------------
CPU=i686,  Ubuntu 7.04 
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2007_April_23
The modem symbolic link is /dev/modem -> ttySL0
The slmodemd set symbolic link is /dev/ttySL0 -> /dev/pts/0

USB modem not detected by lsusb

Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1f.6	8086:24c6	14e4:4d64	Modem: Intel Corporation 82801DB/DBL/DBM 

 Modem interrupt assignment and sharing: 
  7:        125    XT-PIC-XT        eth0, Intel 82801DB-ICH4, Intel 82801DB-ICH4 Modem

 --- Bootup diagnositcs for card in PCI slot 00:1f.6 ----
[    6.946907] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[    6.946916] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   39.529985] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[   39.530327] PCI: Setting latency timer of device 0000:00:1f.6 to 64

 The PCI slot 00:1f.6 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to discuss@linmodems.org
 if help is needed.
 

 === Finished modem firmware and bootup diagnostics section. ===
 === Next deducing cogent software ===

ALSAversion 1.0.13
The audio card is not a modem hosting type.
 For candidate modem in PCI bus:  00:1f.6
   Class 0703: 8086:24c6 Modem: Intel Corporation 82801DB/DBL/DBM
      Primary PCI_id  8086:24c6
    Subsystem PCI_id  14e4:4d64 , 14e4 is an ALSA compatible identification
    Softmodem codec or Vendor from diagnostics: BCM64, a Broadcom type.
                              from    Archives: BCM64, a Broadcom type.
                        

 Lacking a dsp (digital signal processing) chip, the modem is a software 
 intensive or "softmodem" type. Its primary controller manages the traffic 
 with the CPU. But the software needed is specified in the Subsystem.
 -----------------------------------------
Support type needed or chipset:	slmodemd

 An ALSA (Advanced Linux Sound Architecture) modem driver:  snd-intel8x0m
 provides Low Level support enabling contact with the modem hardware.
 For all BUT Conexant chip soft modems (using hsfmodem software)
 complementary High Level support is through a Smartlink utility:  slmodemd

 Download from http://linmodems.technion.ac.il/packages/smartlink/ 
 the package SLMODEMD.gcc4.1.tar.gz having a compiled slmodemd. Unpack under Linux with:
 	$ tar zxf SLMODEMD.gcc4.1.tar.gz
 and read instructions therein. But briefly, the modem is setup with command:
 	sudo slmodemd -c YOUR_COUNTRY --alsa modem:1 
 reporting dynamic creation of ports:
	/dev/ttySL0 --> /dev/pts/N   , with N some number
 Read Smartlink.txt and Modem/YourSystem.txt for follow through guidance.

 Already loaded into the kernel is snd-intel8x0m and audio drivers it depends on,
 displayed by:	lsmod | grep snd_intel8x0m
Module                  Size  Used by
-------------------------------------
snd_intel8x0m          18700  5 
snd_ac97_codec         98336  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
snd_pcm                79876  8 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    54020  23 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         10888  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm


The diagnostic outputs for this softmodem section have their raw information in
folders and text files under /proc/asound/ which you can browse. The information
is from files:
	/proc/asound/pcm
-------------------------------
00-04: Intel ICH - IEC958 : Intel 82801DB-ICH4 - IEC958 : playback 1
00-03: Intel ICH - ADC2 : Intel 82801DB-ICH4 - ADC2 : capture 1
00-02: Intel ICH - MIC2 ADC : Intel 82801DB-ICH4 - MIC2 ADC : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801DB-ICH4 - MIC ADC : capture 1
00-00: Intel ICH : Intel 82801DB-ICH4 : playback 1 : capture 1
01-00: Intel ICH - Modem : Intel 82801DB-ICH4 Modem - Modem : playback 1 : capture 1

	/proc/asound/modules
-------------------------------
 0 snd_intel8x0
 1 snd_intel8x0m
	/proc/asound/card1/codec97#0/mc97#1-1+regs
-------------------------------
0:7c = 4243  and  0:7e = 4d64
which were translated from hexadecimal code into:  BCM64

	/proc/asound/card1/codec97#0/mc97#1-1
-------------------------------
Extended modem ID: codec=1 LIN1

and from the command:
	aplay -l | grep -i modem
card 1: Modem [Intel 82801DB-ICH4 Modem], device 0: Intel ICH - Modem [Intel 82801DB-ICH4 Modem - Modem]

----------------end Softmodem section --------------

Writing Intel.txt
Writing Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2

 Kernel-header resources needed for compiling are not manifestly ready!

 If compiling is necessary packages must be installed, providing:
	 linux-headers-2.6.20-15-generic


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-04 23:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    http://phep2.technion.ac.il/linmodems/archive-sixth/msg02637.html

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html

Read Modem/YourSystem.txt concerning other COMM channels: eth0 eth1 eth0:avah eth1:avah
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

# start/stop the daemon when the USB modem is connected
KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   lrwxrwxrwx 1 root root 6 2007-04-23 16:55 /dev/modem -> ttySL0
slmodemd created symbolic link /dev/ttySL0:  lrwxrwxrwx 1 root root 10 2007-04-23 16:55 /dev/ttySL0 -> /dev/pts/0
     Within /etc/udev/ files:
/etc/udev/rules.d/030_sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/rules.d/030_sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
/etc/udev/sl-modem-daemon.rules:# start/stop the daemon when the USB modem is connected
/etc/udev/sl-modem-daemon.rules:KERNEL=="slusb[0-9]*", GROUP="dialout", RUN+="/etc/init.d/sl-modem-daemon"
     Within /etc/modprobe.conf files:
/etc/modprobe.d/sl-modem-daemon.modutils:install slamr modprobe --ignore-install ungrab-winmodem ;  modprobe --ignore-install slamr; test -e /dev/slamr0 || (/bin/mknod -m 660 /dev/slamr0 c 242 0 2>/dev/null && chgrp dialout /dev/slamr0) 
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

```

It seems to suggest I need something OTHER than the ALSA driver, which I swear I was using before...

**EDIT:** Okay, after doing a "sudo /etc/init.d/sl-modem-daemon restart" it seems my modem is dialing and working correctly now. I'm posting this from my Fiesty install. No idea why it wouldn't work before, but it is now. This dialup crap drives me crazy.

---

