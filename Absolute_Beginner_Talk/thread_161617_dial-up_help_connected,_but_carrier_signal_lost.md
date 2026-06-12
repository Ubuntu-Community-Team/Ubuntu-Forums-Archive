---
title: "dial-up help: connected, but carrier signal lost"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by NomadicUser on 2006-04-17
My Modem: - US Robotics 56k External FaxModem
                - Can connect to same ISP using WinXP Pro

Using Ubuntu 5.10, and wvdial, I'm getting the following message:

--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*my ISP number*
--> Waiting for carrier
ATDT*my ISP number*
CONNECT 45333/ARQ
--> Carrier detected. Waiting for prompt.
--> Connected, but carrier signal lost! Retrying.

I've tried all the different ways to connect (PPP, etc.) but always with the same result. The modem will go through the usual process of dialing, handshake, etc. Appropriate modem lights will turn on to signal that connection has been made, but 3-10 seconds later connection will be dropped.

I also talked to my ISP's customer service. They told me other users were able to connect using other distros of linux as long as the user ID, password and ISP phone number are correctly entered. So using linux per se is not the issue. At least that's what my ISP told me.

What am I doing wrong here? Seems to me my modem and the ISP's server can in fact communicate with each other and agreed on a baud rate. Is authentication the problem?

I also tried specifying the primary and secondary DNS of the ISP in some attempts, but also get the same message with wvdial, so that's probably not the issue here either.

---

### Post by towsonu2003 on 2006-04-17
first thing, check phone cables and phone line in general (need good phone line, no noise in the background -pick up phone and listen)

second, append one of the following at the end of /etc/wvdial.conf file:
```

Stupid Mode = yes
Carrier Check = no

```

may or may not work, [trial and error] try putting first, if not working put in second take out first, if not working put in both... 

there is a higher probability that Carrier Check = no will work by itself.

PS. if this doesn't work, I'm clueless...

---

### Post by Mark_in_Hollywood on 2006-04-17
Please tell me what version of Ubuntu you are running. How did you install it? 

I can't say how much the posts of:

towsonu2003

helped me with the exact same problems. My modem would quit after an erratic amount of time. I suggest you try

 [http://www.linmodems.org/](http://www.linmodems.org/)

Being sure to notify cogent experts. I'm wrapping up my dial-up issue with one in The Czech Republic.

We should probably get together and do a little write-up/post for this forum. Anybody else want to help?

---

### Post by NomadicUser on 2006-04-18
Thank you for the response.

Re. quality of phone line
-------------------------
I'm quite sure this is not the problem for the following reasons:
1. I'm getting good connection using the same hardware set-up (modem, pc, and phone line) running under Windows XP Pro (dual-boot). In fact, I was able to download the live CD ISO of another linux distro using this set-up. The download lasted about 18 hours uninterrupted, and MD5 check was OK.

2. I had the line checked a week ago by a technician from the phone company.


Re. appending parameters to /etc/wvdial.conf
--------------------------------------------
I did all possible permutations of the 2 parameters (Stupid Mode + Carrier Ceck), so far no success.

However, your suggestion opened up several ideas for me to try:
1. It is possible that the dialer isn't waiting long enough for authentication to complete before redialing, so I will play around a bit with other parameters to lengthen the timeout period.

2. I'll compare the modem's log files while dialing-up in Windows XP to the 
messages being displayed using wvdial. If there are marked differences, I will 
try to emulate these in wvdial, hopefully by changing/appending parameters to /etc/wvdial.conf. (Is this what they refer to in other articles as writing a customized dial-up script?).

---

### Post by NomadicUser on 2006-04-18
Hi. Thanks for the response.

I installed Ubuntu Breezy 5.10 as dual-boot with Windows XP Pro to my Sempron 2400 PC. I partitioned the 80GB hard disk like this: 56GB NTFS format for WinXP, 23GB for Ubuntu, and 1GB as swap partition.

I'm not sure we're dealing with the same problem. I'm using an external hardware modem precisely to do away with winmodem/linmodem related problems.

I have 2 modems installed on my computer. My other modem is a PCTel HSP56. It is what most people here refer to as a soft modem. Even before installing Ubuntu, I already knew from initial research that this may cause problems for me. My other modem, a US Robotics External FaxModem, is a hardware modem. It's the one I'm using with Ubuntu Breezy 5.10.

True enough, Ubuntu can detect the hardware modem, but not the soft modem. I don't even have to install additional drivers for it. I asked Gnome to query the modem after installation and I'm quite satisfied that Ubuntu detected the hardware modem correctly.

My hunch is most of your connection problems may be caused by the use of soft modem. If I understand correctly, [www.linmodems.org](www.linmodems.org) is an umbrella organization to help users locate and install suitable drivers for soft modems. These sort of modems are usually attached via PCI or USB. My modem is a hardware modem attached to COM1 (serial port).

Regardless of these differences, I'm perfectly willing to collaborate with you to solve dial-up problems. I'm not sure what I can contribute though since I'm new to linux and my knowledge of networking is very limited. Whatever I know, I'm willing to share. :)

---

### Post by eriefisher on 2006-04-18
Have you tried to dial out through System>>Admistration>>Networking??
If you click on the modem connection and then properties you should be able to set it up ok. The only thing I would make sure to set your eth connection to static or it will interfere with your modem connection.

I use KPPP with no problems except you have change a file in /ppp/peers (#)noauth. But I use full Kubuntu.

eriefisher

---

### Post by NomadicUser on 2006-04-18
Hi. Thank you for responding.

Yes, System>>Administration>>Networking was my first attempt at establishing dial-up connection. After reading your post I went back and checked the properties again, including eth connection. Everything seems to be in accordance with the tips I found on the wiki and help articles. But the dropped connection still remain.

Now that you mentioned it, I remember having played around with setting the noauth parameter in Ubuntu in an earlier attempt. But maybe I didn't do it right. I'll read up on it and give it another try.

Thanks,
NomadicUser

---

### Post by Mark_in_Hollywood on 2006-04-18
I have/had Windows on one side of the disk and at first, Fedora Core 4 on the other. Windows could use the modem night and day, no problem. Linux the modem constantly dropped the line, froze up, etc.

I too had a second modem as this is a Dell Dimension 4100. It came with a soft/win modem. Every time I booted, Breezy 5.10, I received a boot time message of agrserial -- no device detected. Linux did "see" the two modems. It just couldn't figure out completely what the "second" one was. I removed it. I no longer get the no device detected line. I still get the modem problem.


Regardless of these differences, I'm perfectly willing to collaborate with you to solve dial-up problems. I'm not sure what I can contribute though since I'm new to linux and my knowledge of networking is very limited. Whatever I know, I'm willing to share.

Please go to linmodems.org. There, download scanModem and run it in a terminal window. You sound like you know/understand run in a terminal. But ask if you don't.

Take the output of the scanModem and paste it into an email with the subject line of something like: Ubuntu 5.10.xx.i-386, to alert cogent experts. I am doing with with a cogent expert. It's the best advice I can give you. That .org has much to do with modems and less to do with win/soft modems. Please take a few minutes. Help is available there specifically to modems/issues.

---

### Post by towsonu2003 on 2006-04-18
[QUOTE=Mark_in_Hollywood]
Please go to linmodems.org. There, download scanModem and run it in a terminal window. You sound like you know/understand run in a terminal. But ask if you don't.
[/QUOTE]
I don't think scanmodem will be too helpful with an external serial modem. scanmodem looks for softmodems. trying won't hurt though. Maybe scanmodem has a feature that gives output about connected serial modems? Never had a serial modem, so I have no idea... 

It may be a good idea to contact wvdial developers? may be file a bug report to ubuntu malone for wvdial (looong shot)?  

eriefisher is right, make sure you deactivate all wired / wireless interfaces but the modem. System>>Administration>>Networking and all the interfaces listed should have a red X on them (means deactivated, "ifconfig down"), including modem(s).

> 1. It is possible that the dialer isn't waiting long enough for authentication to complete before redialing, so I will play around a bit with other parameters to lengthen the timeout period.
[/quote this this change anything ("customized dial-up script" is hugely over my level of experience)
[quote]
2. I'll compare the modem's log files while dialing-up in Windows XP to the
messages being displayed using wvdial. If there are marked differences, I will
try to emulate these in wvdial, hopefully by changing/appending parameters to /etc/wvdial.conf. (Is this what they refer to in other articles as writing a customized dial-up script?).

This will sound weird, but listening to the phone while modem is communicating helped me figure out what's going on with my win modem. I listened the communication in windows and in linux and compared them (namely, it was missing a piece of sound that said "identify yourself now" or similar, and thus getting a "no carrier" error <- remedy was to redial time and again). might this be helpful for you too? 

can you experiment with another ISP?

---

### Post by NomadicUser on 2006-04-19
> Maybe scanmodem has a feature that gives output about connected serial modems? Never had a serial modem, so I have no idea...

Hi. I got this information from an article about scanmodem:
> scanmodem will only detect PCI and USB modems. It will not detect modems connected through other ports.

> This will sound weird, but listening to the phone while modem is communicating helped me figure out what's going on with my win modem. I listened the communication in windows and in linux and compared them (namely, it was missing a piece of sound that said "identify yourself now" or similar, and thus getting a "no carrier" error <- remedy was to redial time and again). might this be helpful for you too?

not weird at all. :) What you just wrote actually describes my connection problems very well. My difficulties are all centered around the "identify yourself now" part of the process, that's why even on the original post I was leaning towards authentication as the potential problem area.

In windows XP, after the modem lights signaled that a connection was made, there is a brief period where my PC will pass on user and password information to the ISP. That's the part missing when I try to dial-in from Ubuntu/Gnome. The comparison of modem logs from windows dial-up process and the wvdial messages confirmed this.

I found some interesting articles online that may help solve the problem, but still don't have the time to really sit down and try them out. I'll also try to follow what you did and see what happens.

Thank you for your patience in helping solve this problem.

---

### Post by Mustard on 2006-04-19
Did you configure the modem connection using just wvdial or did you use pppconfig to set up your modem connection and connect with pon and poff commands?

---

### Post by NomadicUser on 2006-04-19
I tried both, although my first attempt was to use the gnome interface System>>Administration>>Networking. Connection was established but was dropped.

Then, pppconfig. Same problem. I tried specifying the primary and secondary DNS using pppconfig, but still no go.

Lastly, wvdial.

For the past few days, I've basically concentrated on wvdial since it provides more informational messages during the dial-up process.

In all these attempts, I followed the DialUpModemHowTo article's instructions to the letter.

---

### Post by Mustard on 2006-04-19
Ok, I've been having a bit of think about this and I'm speculating that the issue could be that the connection speed that you have set is too low.  I noticed that the connection dialog is showing the speed at 45333, this could unrelated to what you have in your settings, but I figure its worth mentioning this just in case.  Normally for a 56k connection you set it to the speed above the highest speed for your modem, which would be 115200.

---

### Post by NomadicUser on 2006-04-19
I think 45333 is the negotiated speed between my PC and the ISP for that particular dial-up session. The default settings are set to 115200 kbps.

---

### Post by Mustard on 2006-04-19
[QUOTE=NomadicUser]I think 45333 is the negotiated speed between my PC and the ISP for that particular dial-up session. The default settings are set to 115200 kbps.[/QUOTE]

Ok. Keep experimenting.  It's got to be something to do with the negotiation between PC and ISP.  I take it you tried both CHAP and PAP using ppconfig?

---

### Post by NomadicUser on 2006-04-20
yes. I tried both PAP and CHAP. Also played around with timeout settings.

---

### Post by sailor2001 on 2006-04-20
just a thought....are you using firestarter?

---

### Post by NomadicUser on 2006-04-20
no. Is firestarter a firewall?

---

### Post by Mustard on 2006-04-20
Any updates on what you have tried recently?

---

### Post by NomadicUser on 2006-04-20
tried a couple of ideas, as follows:

1. bought a cheap prepaid dial-up internet card good for 20 hours and tried connecting to that ISP. I ended up with exactly the same problem.

2. reinstalled Ubuntu Breezy 5.10 on the off-chance that the problem is caused by something I did early on in my attempt to connect. Then went through the whole process again with System>>Administration>>Networking, then pppconfig (pon, poff + plog), then wvdial. Just like what the wiki ModemDIalUpHowto said. So far, I still can't connect.

On my own, I'm left with 2 possibilities:

1. follow an article on writing a customized dial-up script I found on my google search. It was written for SUSE but looking at the commands I think I can execute them for Ubuntu. It's supposed to work where PAP and CHAP failed.

2. try connecting using the live cd of another distro. this is a last recourse since I really want to use Ubuntu.

Thank you for your continued interest and patience in helping me solve this problem.

---

### Post by woodtw on 2006-04-21
You are not alone.
I am having the same problem as you.
Same modem, works with Fedora, SuSE, Mepis but NOT ubuntu or kubuntu.
(I've even tried Hoary AND Dapper)
I wish someone could help.

---

### Post by towsonu2003 on 2006-04-21
last resort: file a bug report, may be they can find a way to fix this... not sure which package to file the bug to, I'd leave it empty if you can. if you can't, may be wvdial? they can fix that later on... link to filing bugs is [https://launchpad.net/malone/](https://launchpad.net/malone/)

---

### Post by NomadicUser on 2006-04-24
hi. I found this info on the community forum of another distro:

> US Robotics External Faxmodem will not work in Kernel 2.6, but it will work in kernel 2.4.

My limited understanding of "kernels" is that all distros (including Ubuntu) share the same basic linux kernel. So it stands to reason that my modem will not work using Ubuntu Breezy 5.10, since it is based on the 2.6 kernel.

This is probably my last post on the subject. I want to close this out by thanking everyone who spent time responding to this thread. The support provided by the community is the only positive aspect of an otherwise frustrating experience. Thank you!

NomadicUser

---

### Post by towsonu2003 on 2006-04-24
[QUOTE=NomadicUser]
My limited understanding of "kernels" is that all distros (including Ubuntu) share the same basic linux kernel. So it stands to reason that my modem will not work using Ubuntu Breezy 5.10, since it is based on the 2.6 kernel.
[/QUOTE]
you can still make it work. options would be to try to compile a kernel for yourself or get a distro that has 2.4 kernel (best known ones are Slackware and DSL I believe). 

For the compiling, it's not hard but requires reading: 
[http://www.ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel+2.4](http://www.ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel+2.4)
[http://www.projektfarm.com/en/support/howto/debian_kernel_compile.html](http://www.projektfarm.com/en/support/howto/debian_kernel_compile.html)

don't forget that compiling a 2.4 kernel is a little different (has one more step I believe), so while looking at howtos, try to find the ones that mention "do this for 2.6 kernels, do this for 2.6 kernels". you will be looking for a debian compile kernel howto (like the ones above). 

It usually takes an hour to configure the kernel to own needs (choose this, choose that) and 1-3 hours to compile it (you don't do anything, computer gets hot though ;) )

also, file a bug report to malone... [https://launchpad.net/malone/](https://launchpad.net/malone/) --good luck

---

### Post by araro23 on 2006-08-26
Am having the same issues and I dont have much time to tinker with it. Please do let me know if you are able to find a solution. Its exactly the same where after the handshake, the line disconnects. Appreciate if you can contact me through [email]ron@anodizeblue.com[/email]. Thank you again.

---

### Post by editrix on 2006-08-26
Have you commented out the line
auth
in /etc/ppp/options ?

---

