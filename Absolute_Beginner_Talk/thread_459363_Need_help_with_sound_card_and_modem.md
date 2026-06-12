---
title: "Need help with sound card and modem"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by mixtri on 2007-05-30
Hi there. I am a newbie to ubuntu which i managed to successfully install on my pc which dual boots between win xp.
I have had problems trying to get sound out of a cd i am playing.
Ubuntu recognises my soundcard  Creative (EMU 1212m) as it lists it in the device manage module.
I have tried the sound test function which begins testing, shows a progress bar which marks with two bars then stops. No sound nothing! oh! and it also gives me the option to close the screen with no feedback whatsoever.
I can't install any codecs i need an internet connection - which as you may have guessed is not working to.

Tried connecting my modem by entering all the required details in networking via system admin - but nothing.
Again, like the soundcard, ubuntu detects the modem as i have queried the terminal and got confirmation there.

I am told to install the firmware which comes with the driver - details here: [https://help.ubuntu.com/community/UsbAdslModem/AccessRunner](https://help.ubuntu.com/community/UsbAdslModem/AccessRunner)
this article assumes that the person following the instruction is a certified ubuntu expert, which I'm Not!!

All most all direction i get seems to make this assumption. 
Why can't i seem to get a complete step by step guide to performing an action?

Example - (EXTRACT:  from link above)
===================================================================
Now, to find the firmware. One way to do this quickly is to use the drivers provided by the manufacturer of your modem on their website (yes, the windows drivers). Another way is to look for them in the CD that came with the modem. In both cases, we expect the correct filename to be CnxEtU.sys. In the CD that came with my modem, the path was: /media/cdrom1/driver/Wan/CnxEtU.sys. I had a /media/cdrom1/driver/Lan/CnxEtU.sys, but the two files were identical.

To extract the firmware:

cp /media/cdrom1/driver/Wan/CnxEtU.sys ~/

cxacrufw-extract ~/CnxEtU.sys ~/cxacru-fw.bin

sudo cp ~/cxacru-fw.bin /lib/firmware

Make sure that the firmware is installed as /lib/firmware/cxacru-fw.bin or else the modem won't work. 
===============================================================

1. I tried typing the message in terminal and got an error on second line - does not recognise cxacru-fw.bin as a command. so where do u place cxacru-fw.bin so that the terminal recognises it.

2. Theres no clear instruction how to get the firmware using this file other than compiling a lot of code someone generously added as a link on the directions page. Where do I get a compiler to do this and how?

Its things like these are frustrating me and quickly eroding my will to persevere with this OS.

I can't seem to understand why there are no features in ubuntu to make things easier for virgins like me. 
In windows u would get a detected hardware wizard which would guide u thru the process of sorting these issues out i am yet to find something like that in ubuntu.

Can anyone help - close to giving up - very frustrated Ubuntu virgin!

---

### Post by chamberlain2006 on 2007-05-30
Well, sorry to hear that you're having problems.  Can you post whatever your questions are again, in a simpler way, it's kind of hard to tell what's a question and what's not.  Then we can get busy!

---

### Post by aysiu on 2007-05-30
I've retitled the thread to give people an idea of what problems you need help with.

---

### Post by phr0ze on 2007-05-30
I'm not sure what his questions are but I get that his sound card doesn't work at all (even though he seems to indicate it just doesn't work with CDs)

Also his modem (winmodem maybe) isn't working either. 

He appears to have run some command which shows that his devices exist in the system.

Note to poster: Sorry to hear about your problems, however the sound issue is strange as ubuntu seems to have no problems with other sound cards. Just cause windows detects your sound card, doesn't mean it's easier all around. I have plenty of devices which need me to download drivers to use in windows. In fact I have to download and install more drivers by hand in windows than in ubuntu.

---

### Post by daimaru on 2007-05-30
:-k what are you trying to install? wireless ? sound ... may switch to OSS ,  if i knew what ur trying to install module-assistant might do the trick just like windoze does. plz post some detail on what hardware ur using what your trying to get to work etc.

---

### Post by mixtri on 2007-05-30
thanks Chamberlain

1. I am trying to get sound out of the system. No sound when i play cd's, or files converted to ogg on the harddisk.

What i have done - 
a. checked device manager - ubuntu detects my soundcard. its a Creative sound EMU1212m PCI card
b. tried the sound test: No sound.
c. Volume not muted or turned down.
d. Soundcard works well in winXP
e. typed a command in the terminal which gave me details of the sound card as detected by ubuntu.

2. Cannot get ADSL USB modem to work (generic E-tec modem using connexant chipsets)

What I have done - 
a. downloaded appropriate driver for my card: unable to install
b. checked device manager as well as run a command on terminal: result- detected USB ADSL modem. The modem clicks and light switches on upon booting into ubuntu.
c. tried to retrieve firmware details using cxacrufw to extract file as per following link - [https://help.ubuntu.com/community/UsbAdslModem/AccessRunner](https://help.ubuntu.com/community/UsbAdslModem/AccessRunner). Failed.
d. I do not have a network card so using pppoe command in terminal responds with no ethernet card detected.

Hope this helps.

U on MSN?

---

### Post by chamberlain2006 on 2007-05-30
Yes, I have MSN if that is easier.

---

### Post by mixtri on 2007-05-30
phr0ze  all i am saying is so far it does not appear to be a simple enough task downloading a driver, installing  and getting it to work in ubuntu. this obviously has a lot to do with the fact that i am new to this OS.
However, regardless of what OS one uses in this day and age u expect simple mundane tasks such as the ones i am trying to do be simple enough and not take hours; Simple as in not having to bother with  lots and los of codes, terminals and extracting files from hardware.etc. 
 
I am not that much of a technical person, the idea of me having to learn a lot of programming commands etc to carryout what should be simple tasks is scary and off-putting.  Whenever u ask someone a question you seem to get a list of code that needs to be stuck in a terminal. which in my short experience has not yielded much; simply because i do not know what i'm doing.
Therefore, I think ease of use should be considered when developing software for uses by novices like myself.

---

### Post by mixtri on 2007-05-30
my msn is [email]stevemarcel@hotmail.com[/email] - I will log in right now - thanks.

---

### Post by chamberlain2006 on 2007-05-30
The sound might be a problem, but I can help you follow the commands for your modem.  The problem is that there just isn't always somebody to develop the GUI.  But like I said, I can help you with your modem.

---

### Post by mixtri on 2007-05-30
thats great Chamberlain. Sorry if i'm coming accross as an ignorant person! im just a little frustrated with trying to get this to work since saturday afternoon.

---

### Post by n00utkast on 2007-06-19
Well i just need help with sound...My speakers are not making any sound whatsoever...

02:09.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: Voyetra Technologies Santa Cruz
        Flags: bus master, slow devsel, latency 64, IRQ 20
        Memory at fe2ee000 (32-bit, non-prefetchable) [size=4K]
        Memory at fe100000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>

thats the driver i have installed...i played around with alsamixer but to no avail...i m new to ubuntu so i really don't know why the sound is not coming out when the driver is installed any clues?

thnx in advance

---

