---
title: "Can't connect to the internet"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by MiCovran on 2006-08-29
I've instaled Ubuntu 6.06 today and it works perfectly. Accept that I can't connect to the internet. I start firefox, type in an adress (say, [www.google.com](www.google.com)) and get a message "Server not found". It's becouse I haven't dialed up yet. Thought Ubuntu would ask me to configure my modem (56k), but it didn't. So, how do I do that myself? Thanks.

---

### Post by ComplexNumber on 2006-08-29
> **MiCovran said:**
> I've instaled Ubuntu 6.06 today and it works perfectly. Accept that I can't connect to the internet. I start firefox, type in an adress (say, [www.google.com]("http://www.google.com")) and get a message "Server not found". It's becouse I haven't dialed up yet. Thought Ubuntu would ask me to configure my modem (56k), but it didn't. So, how do I do that myself? Thanks.
try this:
-fire up firefox
-in the address bar, type in 'about:config'
-type in 'v6' into the seach bar
-disable IPv6

---

### Post by sbassett on 2006-08-29
> **MiCovran said:**
> I've instaled Ubuntu 6.06 today and it works perfectly. Accept that I can't connect to the internet. I start firefox, type in an adress (say, [www.google.com](www.google.com)) and get a message "Server not found". It's becouse I haven't dialed up yet. Thought Ubuntu would ask me to configure my modem (56k), but it didn't. So, how do I do that myself? Thanks.

First step would be to goto System -> Network and see if your modem is listed there.

---

### Post by ComplexNumber on 2006-08-29
> **sbassett said:**
> First step would be to goto System -> Network and see if your modem is listed there.
ahhhh, i assumed he had gone well past that stage.

---

### Post by tatimmer on 2006-08-29
Ive just gone thru setting up an external modem with Breezy.
"tomsmodemtips" may be of some help.
[www.ticon.net/~tatimmer/linux.html](www.ticon.net/~tatimmer/linux.html)

---

### Post by Bachstelze on 2006-08-29
56k "Winmodems" can be a real PITA to setup. You'll find more info at [http://www.linmodems.org](http://www.linmodems.org)

---

### Post by whizbaby on 2006-08-29
If you don't have it, get wvdial (should already be there).
type (in terminal):

sudo wvdialconf

then

sudo nano /etc/wvdial.conf

and put your provider's phone number, username and password (it's at the bottom of the file), then save (ctrl-o) and quit (ctrl-x)
finally

sudo wvdial

should get you to the net (wvdial does not need a driver,it's an intelligent 'modem whisperer')
This worked best for me (graphical network-tool didn't find my modem)

---

### Post by MaximB on 2006-08-29
if ALL this doesn't do any good for you try in the terminal :
sudo pppoeconf

---

### Post by MiCovran on 2006-08-30
Wow! I didn't expect so many answers.

I went to System - Administration - Networking. There is a phone picture with label "Modem connection" and "The interface ppp0 is not active". I clicked Properties.

In "General" tab I enabled "Enable this connection" and entered phone number, username and password. In "Modem" tab I have a problem. I clicked autodetect modem port and got the information window titled "Could not autodetect modem device" with message "Check that the device is not busy and that is correctly attached to the computer." ](*,)
Now what? I don't know my modem port, I don't even know what modem port is. I just know it's an internal modem connected to PCI. In time i bought this computer, I didn't know what I was buying so I can't give you any information about this modem. I can only tell you it works on Windows XP.

Anyway, any information would be appreciated.

---

### Post by whizbaby on 2006-08-30
Try with '/dev/ttyS0'(uppercase-S,zero). If this doesn't work (as it didn't for me) just try the wvdial-approach I explained above then your modem will be detected automatically, wvdial has all the knowledge to do it, you only need your provider'S phonenumber and login-data. No terminal-phobia, it's really not hard.(and after it your graphical tool will auto-detect your modem - stinkin but True)

---

### Post by MiCovran on 2006-08-30
Thanks for advice, whizbaby, but it didn't work. I think I know what the problem is. It's a winmodem.
I tried this scanModem from linmodem.org and it told me:

"Formal support for Conexant chipset modems are available ONLY through http://www.linuxant.com/drivers."
"Driver speed is limited to 14,400 until a key is purcased. There is NO freeware alternative." Thanks, but no thanks linuxant.

Internet is what I mostly use my computer for. Seams to me getting a new modem is the best thing to do.

---

### Post by whizbaby on 2006-08-30
Actually a lot of winmodems are supported, you seem to have a particularly nasty one...
Nevertheless 'onboard' always sounded quite like 'stowaway' to me ...

---

### Post by raggle on 2006-09-02
I'm getting the same as MiCovran, exactly. When I first installed 6.06 I was impressed by how easy and quick it was to install. USB modem wasn't detected (but shows up in device list).
Bought a new PCI internal modem (not winmodem)to fix problem. Neither is detected. ScanModem got as far as identifying Motorola but then nothing. Ihave tried all remedies here. Any more ideas?

---

### Post by makeshift on 2006-10-03
> **raggle said:**
> Ihave tried all remedies here. Any more ideas?

Well... The only good idea is to try some reverse engineering stuff regarding motorola modems, because they had gave up their hands from Linux (read as: non-profitable area of business as they think). So, You my friend forget about motorola and buy other modem. Or else get yourself DSL/ADSL over NIC and save yourself from dialup-modem-setup-hell ! I mean, how do you get all updates and software for UBUNTU over dialup connection ? 
  Anyway, there is no good idea for Motorola modems and it will never be I'm afraid so. They have discontinued support for Windows few years ago, believe me, I had some trouble even setting it up for Win2000 as I remember. Yes it's a good modem but with poor/no support.

---

