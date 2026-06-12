---
title: "wireless not cnnecting-feisty"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by pinky88 on 2007-07-03
hi,

My wireless won't connect on feisty, I've only tried to connect today for the first time,i think i've done everything correctly, i have an intel centrino a/b/g wireless card, does anyone know if maybe this is not supported by ubuntu?

---

### Post by wjp.reg on 2007-07-03
> **pinky88 said:**
> hi,

My wireless won't connect on feisty, I've only tried to connect today for the first time,i think i've done everything correctly, i have an intel centrino a/b/g wireless card, does anyone know if maybe this is not supported by ubuntu?

show us output from:

```
ifconfig
```
```
iwconfig
```

for starters

And, won't connect to what?

---

### Post by bradmayne on 2007-07-03
what brand card is it?  Try this 1st.  Make sure your card is inserted into the pcmcia slot at boot.  Then go to network manager under system> administrator> network manager.  The wireless may show up as eth1 or ath0 etc.  Then uncheck the card and check it again.  Go to properties make sure the SSID is entered correctly. IT IS CASE SENSITIVE!!! Then enter the key etc etc.  Then go to a terminal window and enter ifconfig eth1 up for example or eth2 etc.  Whatever you saw in the network manager window. Then hit me up if your still having problems ok?

don't forget to start dhcliient!! example dhclient ath0 or dhclient eth1  ( from the terminal window you must do this as sudo!!

---

### Post by pinky88 on 2007-07-03
i meant wieless won't run, i.e. i have no wireless internet on my laptop . I'm using a different computer here and the outputs for those commands are prtty long to type, but for iwconfig it says no wireless extensions, unassociated ESSID:off/any. access point: not-associated. etc.    does this mean my wireless card is not supported?

---

### Post by wjp.reg on 2007-07-03
> **pinky88 said:**
> i meant wieless won't run, i.e. i have no wireless internet on my laptop . I'm using a different computer here and the outputs for those commands are prtty long to type, but for iwconfig it says no wireless extensions, unassociated ESSID:off/any. access point: not-associated. etc.    does this mean my wireless card is not supported?

No that doesn't mean it's not supported, it means you haven't configured the wireless card as suggested above.

Just cut and paste the output from ifconfig and iwconfig, which you run on the computer with the suspect wireless :-)

Might as well cut/paste the utput from this too: 

```
sudo lshw -short | grep network
```

and

```
lsmod | grep 3945
```

in the event that it is the intel 3945abg, which I suspect it is (same as on my centrino/lenovo

---

### Post by pinky88 on 2007-07-03
ok for iwconfig eth1, that stuff about no wireless extensions doesn't come up. i don't have a clue what the problem is, i'm very new to linux, as in I only installed it 2 days ago!!!

---

### Post by pinky88 on 2007-07-03
i can't cut and paste as i'm using a different computer coz i've no internet connection on the one i'm asking questions about ;) is there a specific part u can give me that u need to see or do u need it all??

---

### Post by bradmayne on 2007-07-03
do you know what kind of chipset you have on the wirless? i.e. hermes, atheros, prism, etc etc?
that could help us narrow down the problem

---

### Post by pinky88 on 2007-07-03
for that 1st code u gave me there, output:

/0/100/1c.1/0  eth 1   network   PRO/Wirelss 3954ABG Network connection
on
/0/100/1e/0   eth1    network   BCM4401-B0 100Base-TX



For second code:
ipw3945        118816    1
ieee80211      34760   1  ipw3945

---

### Post by pinky88 on 2007-07-03
all i know about it is what i wrote in  1st msg up at top of this convo.. how do i find out what chipset??

---

### Post by liquidfunk on 2007-07-03
Why don't you save the output onto a word document, then move it on a USB Stick/CD/ Floppy or similar?

---

### Post by pinky88 on 2007-07-03
hehe can't believe i didn't thim of that! il have it in a min or two, bear with me ;)

---

### Post by wjp.reg on 2007-07-03
> **pinky88 said:**
> for that 1st code u gave me there, output:

/0/100/1c.1/0  eth 1   network   PRO/Wirelss 3954ABG Network connection
on
/0/100/1e/0   eth1    network   BCM4401-B0 100Base-TX



For second code:
ipw3945        118816    1
ieee80211      34760   1  ipw3945

Ah, so you do have the 3945abg! 

That's good, 'cause it is supported and a restricted driver 'should' automatically load when you run Feisty.  More than likely you need to follow Bradmayne's advice and configure the wireless card with the appropriate ESID and IP, if it's static, or select DHCP if your wireless router assigns the IP dynamically.  Also, if the router uses some kind of security, like WEP or WPA, you will have to input the passphrase for it to be able to log on to the router.

---

### Post by pinky88 on 2007-07-03
ok so the whole copy and pasting output thing didn' work cause open office documents won't open in windows (and i've no ubuntu OS on any other computer than the one with the problem!

in reply to the last message. i've already put in the ssid, IP address and WEP ,that's why i'm confused as to where the problem is...

---

### Post by liquidfunk on 2007-07-03
Yes it does. Save it as a .doc file. Rather than an .odt.

---

### Post by wjp.reg on 2007-07-03
> **pinky88 said:**
> ok so the whole copy and pasting output thing didn' work cause open office documents won't open in windows (and i've no ubuntu OS on any other computer than the one with the problem!

in reply to the last message. i've already put in the ssid, IP address and WEP ,that's why i'm confused as to where the problem is...

Perhaps a dumb question, but did you activate the connection in the network manager?

---

### Post by bradmayne on 2007-07-03
to find out what kind of wireless chipset you have type this command in the terminal: lspci -v
Or do this command: lspci -v | less


See if you can find something that looks like this: 

04:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d8000000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

that is an example from my wireless card.  Iet me know what you find.
remember this is just an example i promise i'll do whatever i can to help.  When i was doing this for both linux distributions i didn't have anyone to help me and it was damn near impossible without someone to help. So I'll do whatever I can to help you out! 

p.s. figuring out what kind of hardware you have is the hardest part after that it's smooth sailing!

---

### Post by pinky88 on 2007-07-03
as in, check the box beside the network? yep!

---

### Post by pinky88 on 2007-07-03
bradmayne,

no wireless anything comes up there.. is it one of the flags or something?

---

### Post by wjp.reg on 2007-07-03
here's a link to a ubuntu wiki howto with troubleshooting suggestions..

Your wireless nic should work 'out of the box', so it has to be the way it is set up (or not)

good luck.

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

---

### Post by bradmayne on 2007-07-03
from a terminal window type: lspci -v      or type lspci -v | less.  Remember don't forget the space between lspci and -v

---

### Post by pinky88 on 2007-07-03
bradmayne,

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945G Express Memory Controller Hub (rev 03)
Subsystem: Dell Unknown device 01d4
Flags: bus master, fast devsel, latency 0
Cababilities: <access denied>

---

### Post by bradmayne on 2007-07-03
ok i'll tell ya what.  Normally i don't do this but this is my screen name for yahoo: brdmayne

this is my screen name for AIM: bradf23

you can try to contact me at either of the above.  I may or may not be online tonight but i should be on tomorrow.  Let me know.

Also try going to sourceforge and get ndiswrapper.  Can you at least plug your pc into an ethernet connection for the time being?

---

### Post by pinky88 on 2007-07-03
i dont have either yahoo or AIM set up unfortunately. i have msn if you have that?? [email]karforde@hotmail.com[/email] 
if u want 2 add me there..

i'm not sure if i'll get a chance to get online tomorrow as i have something on, but i'll try. thanks a million for ur help =) my cousin will help me out if all else fails i'm sure, just i feel like i'm letting him down coz of having to set this up for his work thing! would help me get the job quicker if i could do it myself, y'know :)

Thanks again,
Pinks

---

### Post by schlagle on 2007-07-03
I just had the same problem with my new laptop. Fixed it by installing the linux-restricted-modules-2.6.20.16-386 and linux-restricted-modules-2.6.20.16-generic packages.

These provide the appropriate driver for your 3945. After you install you should be able to reboot and then check your network applet to see that your card should be running.

---

### Post by bradmayne on 2007-07-04
type lspci -v    and look for the output that would say something like atheros or hermes etc it would be in the area around ethernet.

Or try this: lspci -v | less

is the card an internal or external?  Meaning does it plug into a usb port or pcmcia card slot?  Or is in it built into your pc?  Trust me this is the hardest part! I struggled with my wireless for about a week until it all became clear now i'm using it every day!! With no problems!! I had to use madwifi drivers though as i have an atheros type chipset.  Madwifi did an excellent job though as i can place my card in monitor mode and do some things that maybe should not be mentioned in this forum.  Anyways hang in there and i'll be around tomorrow to help ya out!

---

### Post by pinky88 on 2007-07-04
hmm ok i just looked in network manager and apparently i've a network signal of 98%!!!!!! but it says the status is idle, and i still can't browse the net, it says server not found when i try using firefox, could firefox be the problem?

---

### Post by pinky88 on 2007-07-04
lspci -v


00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945G Express Memory Controller Hub (rev 03)
Subsystem: Dell Unknown device 01d4
Flags: bus master, fast devsel, latency 0
Cababilities: <access denied>

---

### Post by schlagle on 2007-07-04
So your wireless card works, at least you can see the connection you setup and it thinks it's connected but you can't get any data to your web browser. Is this correct?

If it is true then it sounds like your router might be the problem. Are you sure you setup the correct encryption type and password? How about any MAC filters or too few dhcp addresses?

---

### Post by pinky88 on 2007-07-04
problem solved =) cousin fixed it! thanks everyone so much for all your help :D

---

