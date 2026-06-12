---
title: "Dapper can't connect to ISP"
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by Madmat on 2006-07-01
I have installed Dapper Drake onto a computer that is networked to WinXP and Win98.  I have dialup and have configured the modem to dial out (dialup connection only) but can't get it to connect to the ISP.
I have disabled the LAN connection, tested the modem (query), changed handshake protocols from PAP/CHAP to PAP, and CHAP, but still don't get connected.
After the dialup and contact, connection is terminated with the Exit Status: 1 error code and the log file giving the following message:

    Jun 25 16:26:03 ubuntu pppd[7600]:  The remote system is required to
    authenticate itself but I couldn't find any suitable secret (password) 
    for it to use to do so.  (None of the available passwords would let it use
    an IP address.

I am using the same username and password as I would for my Windows connections.
I could use some suggestions.

---

### Post by editrix on 2006-07-02
Hope I'm not insulting you for suggesting this, but somewhere* in your setup for connecting to your ISP is a box for whether the ISP requires authentication. You may have inadvertently checked this when it should be unchecked, or vice versa.

*I can't check my KPPP right now, as I'm online. and it won't let me get into the configuration section.

---

### Post by Madmat on 2006-07-02
Thank you,
I don't think it's possible to insult me when it comes to something that I know almost nothing about.
I have been through all the configuration areas that I can find, which is not a lot.
Have posted a couple of threads asking for help using different titles, but haven't gotten much help.
Apparently, though, there is some problems with Dapper connecting to the internet through dial-up.
After some more work I have the following script from konsole when I try to connect via ppp:
______________________________________

mshearne@ubuntu:~$ kppp
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()
Opener: received SetSecret
Opener: received SetSecret
Opener: received OpenLock

Opener: received OpenDevice
Opener: received ExecPPPDaemon
Kernel supports ppp alright.
pppd: The remote system is required to authenticate itself
pppd: but I couldn't find any suitable secret (password) for it to use to do so.
pppd: (None of the available passwords would let it use an IP address.)
In parent: pppd pid 5255
Couldn't find interface ppp0: No such device
It was pppd that died
pppd exited with return value 1
Sending 5251 a SIGUSR1
Opener: received RemoveSecret
Opener: received RemoveSecret
Opener: received OpenResolv
Opener: received OpenResolv
Opener: received RemoveLock
Opener: received PPPDExitStatus
Opener: received PPPDExitStatus
~ScimInputContextPlugin()
mshearne@ubuntu:~$
____________________________________________
If you or anyone else can decipher this I would really appreciate it.

---

### Post by hajk on 2006-07-02
[QUOTE=Madmat]I have installed Dapper Drake onto a computer that is networked to WinXP and Win98.  I have dialup and have configured the modem to dial out (dialup connection only) but can't get it to connect to the ISP.
[snip]
I am using the same username and password as I would for my Windows connections.
I could use some suggestions.[/QUOTE]

How did you configure the modem? Dapper is set up to do that via the System -> Administration -> Networking menu.... you should have a ppp0 interface show up there. 

If yes, all you need to do is to highlight ppp0 and hit the Properties button and enter the sort of information that you already know from your Windows setup. 
There are several tabs that you will have to attend to. When all information is entered hit OK, and you can then activate the interface and you should hear it dialling, etc. 

The configuring that Dapper does for you can also be done manually, of course, but it's easy to forget a thing here and there. Use of wvdial is also possible, not difficult, but not as easy as doing it the Dapper way.

---

### Post by Madmat on 2006-07-02
Network settings only show eth0.
This may explain why I can access my XP computer, but not get online.
I set up the configuration through the KPPP GUI.  This detected the modem (I thought) and assigned it an address at /dev/modem .  When I queried the modem, it was found and tested.
When I run ppp, it says "Modem detected" and I can hear it dialing out.

---

### Post by hajk on 2006-07-02
Yes, now I understand: your Dapper computer is only connected to your local network (LAN), hence the eth0 interface. Your modem can only be configured from the (Windows?) computer it is attached to (and it probably already is); that computer must also be configured to be a gateway and DHCP server for your network (sorry, can't help you with  that, never used Windows). The dial-out must be initiated from the Windows computer. 

Nothing much needs to be done on your Dapper computer, eth0 is probably already set up for DHCP.

---

### Post by Madmat on 2006-07-02
I should have clarified.  I have installed a modem in my Dapper computer and I prefer to connect to the internet through each computer independently.
I am not using DHCP for my internet access.
The ISP address for each computer on the LAN has been manually set because using the wizard on my XP computer couldn't do what I wanted and made assumptions.
How can I create a ppp0 in my Dapper machine?

---

### Post by hajk on 2006-07-02
You should first look at the boot messages, with the dmesg command in a terminal, for clues as to why the ppp0 interface is not available. You should also check the make of your modem and the chipset it uses -- some modems are so-called Winmodems that require special drivers when used in Linux.

---

### Post by Madmat on 2006-07-02
Thank you,
Further research in System info has shown that this is a Winmodem.
wvdialconf has found the modem at ttyLTM0, but this address is not shown when I try to configure through the GUI.  But, it does seem to recognize the link to /dev/modem.
I would like to find an Application from the K-menu that would allow me to setup a new modem, but I can't find one.
Still reading.

---

### Post by editrix on 2006-07-03
Wow, this was getting too complicated for me, until you said "Winmodem." Try this:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by Madmat on 2006-07-03
Thank you,
I have tried the options given for the Agere/Lucent modems and got a FATAL error, modules not found.
After more searches I have found that there are a lot of others with the same problem.
It seems that the more I dig, the deeper I get...and my head is starting to hurt.
Mostly it's trying to decipher the language of Linux, which is pretty foreign to me so far.
Maybe I'll just get a different modem.
or
Maybe I'll dig some more.

---

### Post by editrix on 2006-07-07
> **Madmat said:**
> 
It seems that the more I dig, the deeper I get...and my head is starting to hurt.
Mostly it's trying to decipher the language of Linux, which is pretty foreign to me so far.
Maybe I'll just get a different modem.

Sorry to be so long replying. First off, I know exactly what you mean, and so does everyone else here :-) 

If you can get hold of an external modem. They always work. In fact, you can sometimes find used ones ridiculously cheap. Where I live, a local church has a community yard sale 4 times a year for old parts and such. Also, Google your town/city/county and Linux Users Group. They're all over the world, and often have old hardware to sell.

---

### Post by Madmat on 2006-07-08
Thank you,
There is a serial external modem on the way and I can't wait to get it and continue my education with Linux.:)

---

