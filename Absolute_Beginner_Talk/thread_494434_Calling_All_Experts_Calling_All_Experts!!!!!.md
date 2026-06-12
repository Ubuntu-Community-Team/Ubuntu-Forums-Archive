---
title: "Calling All Experts Calling All Experts!!!!!"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by Korea91 on 2007-07-06
Alright Im New To This Linux Kernal Program. Actually New To Linux In Total.

My Sound Does Not Seem To Work And Neither Does My Graphics In A Way I Have Ati Mobility Radeon X700

Well If U Are A Expert Plz Put Ur Email Or Some Way Of Contact Down Or I Will Privalty Send Msg To U From This Forum If U Just Reply Hi Im An Expert, Plus Could U Tell Me All The Info I Would Need To Put Down About My Computer And How To Get That Info Like The 
Sudos Or Watever For The Terminal

Also I Have Tried Some Guides And They Dont Seem To Work So Plz If U Could Just Inform Me Of Wat U Need And That U Are An Expert.

Thank You

---

### Post by steveneddy on 2007-07-06
If you want serious help, please don't post in Leet Speak, or whatever that is called now. 

And the post questions should be here so someone with the same problem can find a solution if you come to a solution. don't ask for IM's. Someone else may have the same problem.

You will need to post your hardware

Type and brand name of PC
Type of sound card.
Any details about your system.

Have you searched the forums for your answer?

---

### Post by AlexenderReez on 2007-07-06
> **Korea91 said:**
> Alright Im New To This Linux Kernal Program. Actually New To Linux In Total.

My Sound Does Not Seem To Work And Neither Does My Graphics In A Way I Have Ati Mobility Radeon X700

Well If U Are A Expert Plz Put Ur Email Or Some Way Of Contact Down Or I Will Privalty Send Msg To U From This Forum If U Just Reply Hi Im An Expert, Plus Could U Tell Me All The Info I Would Need To Put Down About My Computer And How To Get That Info Like The 
Sudos Or Watever For The Terminal

Also I Have Tried Some Guides And They Dont Seem To Work So Plz If U Could Just Inform Me Of Wat U Need And That U Are An Expert.

Thank You

your psot look fancy but at the same time look funny...hahah....if you really need help then just ask in forum.....many people will try to solve it....

---

### Post by Korea91 on 2007-07-06
alright for some reason my sound doesnt seem to work 

my pc is sony vaio
the model VGC-VA11G it is a desktop

the type of sound card im not sure it says sigmatel high def or audio in my windows xp system

yet i think it is a ATI 
also when i did lspci.

lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
02:0b.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:0b.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
02:0d.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)



00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

so with this info i hope u guess can help me thx

hope this helps SigmaTel High Definition Audio Codec

Location 65535 (Internal High Definition Audio Bus)

---

### Post by Nythain on 2007-07-06
Ok.
A. as for the main question... im not quite getting what you are wanting... there are lots of experts that use these forums, so just ask an actual question and you should get an actual answer, sometimes it takes a bit so dont bump bump bump every few minutes cause no ones helping. right now though i dont see much of a question as i do a request for a bunch of people who probably dont want to mess with im to im you.

B. your sound and graphics shouldnt have a whole lot ot do with altering your kernel, the generic ubuntu kernel pretty much covers almost everything anyone could have... its pretty effen generic... so the graphics problem probably lies in having the appropriate proprietary drivers installed for your ati card, wich i cant help with because i have a nvidia card... and your sound problem might be as simple as unmuting some stuff in asla mixer (i hope i spelled that right, i get all my acronyms mixed up sometimes)

C. to some of the others... if you can understand the question, then help without the added commentary would be nice... if you cant understand the question, then just ignore the thread. A lot of people (particularly younger, but quite a bit of older also) in todays society get used to typing like that. Between oldschool buffer limits on instant messages to the non stop text messaging of todays youth... it becomes subconsious habbit... asking someone to stop typing like that would be like asking a southerner to speek with a boston accent, or asking a court stenographer to use a "real" keyboard, or asking a career secretary to write in longhand print

---

### Post by steveneddy on 2007-07-06
> **Nythain said:**
> 

C. to some of the others... if you can understand the question, then help without the added commentary would be nice... if you cant understand the question, then just ignore the thread. A lot of people (particularly younger, but quite a bit of older also) in todays society get used to typing like that. Between oldschool buffer limits on instant messages to the non stop text messaging of todays youth... it becomes subconsious habbit... asking someone to stop typing like that would be like asking a southerner to speek with a boston accent, or asking a court stenographer to use a "real" keyboard, or asking a career secretary to write in longhand print

Not trying to start a flame here, but i could understand if we were using cell phones or PDA's to post here, but the OP DID post in readable type after my comment.

I meant no harm, just type in as good English as you can, granted some don't use English as a first language, just trying to get some forum etiquette to make it easy for everyone to read the post and try to understand what the OP is trying to convey to the readers of his/her thread.

**To the Original Poster: **

What exactly is your issue with the sound and video on your machine?

---

### Post by AlexenderReez on 2007-07-06
before this i having problem with sound in one of laptop that i try to install.....firstly check has you setting

open terminal.....

> gnome-volume-control

then try to set your setting.....see is there any error sign given in terminal......

---

### Post by steveneddy on 2007-07-06
Not an expert on ATI graphics, but the sound issue, have you played with the volume settings.

Changed the output to front, or tried different settings on the volume control GUI?

Do you get sound through the if you use headphones?

---

### Post by Nythain on 2007-07-06
ok, googling around for alittle bit points out this is a pretty common problem for your sound device...
so far the most informative and probably helpfull thread i have found is here:
[http://mepislovers.org/forums/archive/index.php/t-4721.html](http://mepislovers.org/forums/archive/index.php/t-4721.html)
by the end of it the user has resolved most of teh problem, following his instructions might help you with your problems too

---

### Post by Korea91 on 2007-07-06
> **Nythain said:**
> ok, googling around for alittle bit points out this is a pretty common problem for your sound device...
so far the most informative and probably helpfull thread i have found is here:
[http://mepislovers.org/forums/archive/index.php/t-4721.html](http://mepislovers.org/forums/archive/index.php/t-4721.html)
by the end of it the user has resolved most of teh problem, following his instructions might help you with your problems too

im sorry but could u tell me what exactly to put in the terminal because i think i did it and it doesnt seem to work so maybe i put the wrong thing in

---

### Post by Nythain on 2007-07-07
Go to /etc/modprobe.d/snd-hda-intel and comment out the following line:
options snd-hda-intel position_fix=2

After rebooting sound worked fine. Worth a try if at least.

first lets make sure you have that file... i dont, but i dont have your sound card so thats probably why... open your file manager/browser (i think thats nautils in gnome) and browse to /etc/modprobe.d/    and look for a file called snd-hda-intel
if its there, then in terminal type
```

gksudo gedit /etc/modprobe.d/snd-hda-intel

```
put in your password and it should open that file up in gedit.
look for a line that reads
```

options snd-hda-intel position_fix=2

```
and comment it out with a # like this
```

#  options snd-hda-intel position_fix=2

```
save the file (it shouldnt give you any problems since you opened it with gksudo
reboot and hope that your sound problems are fixed... if not you could try to compile the latest alsa driver yourself... lets try this first and see if it helps, if not i will look up detailed instructions on compiling the alsa driver

and as i said about your video problems, i would suggest searching these forums with "install proprietary ati driver" or search for "fglrx"... im not much help in this department, i sold my ati for a nvidia shortly after installing linux (i know thats not an option for you, i believe you have onboard ati)

---

### Post by eternalsword on 2007-07-07
I believe with ubuntu, you want to comment that option out  in /etc/modprobe.d/alsa-base if it's there.  I do not believe an /etc/modprobe.d/snd-hda-intel file gets created.

---

### Post by Nythain on 2007-07-07
thanks... i wasnt sure on that... i pulled the directions from a mepis forum, but i was hoping it would be close enough... it was teh best advice i could find at the time

---

### Post by Vague on 2007-07-07
Not totally sure on your sound issue, but my guess is that your video issue is driver related.  If you don't have the fglrx driver, you should get it.  It's pretty painless to install, especially if you're running Feisty.  More info here:  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The open-source radeon driver might work, too, but I don't have much experience with it, and last time I checked, 3D support for most of the X-series cards was "experimental."

---

### Post by macogw on 2007-07-07
> **steveneddy said:**
> If you want serious help, please don't post in Leet Speak, or whatever that is called now. 

There's no 1337 5P34K there.  The OP used capslock for the whole thing and the forum software filtered it into capitalizing the first letter of every word.  I've seen people get around that with a post that looks like this:
> THIS IS MY POST AND IT IS ALL CAPITALS BECAUSE I DON'T KNOW HOW TO NOT SHOUT ONLINE AND I DON'T KNOW HOW TO TURN OFF CAPS LOCK ONCE I TURN IT ON

x

---

