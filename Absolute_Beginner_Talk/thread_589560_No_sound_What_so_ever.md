---
title: "No sound What so ever"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by nik62790 on 2007-10-24
i just recently got a toshiba satellite laptop and im running Both vista and ubuntu.. the sound on ubuntu dosent work at all though...please help.

---

### Post by Kosimo on 2007-10-24
Can you please give us some more information?
What kind of laptop do you have?  Please post your specs and model number.

Witch version of Ubuntu are you currently using now?

---

### Post by nik62790 on 2007-10-24
its a Toshiba satellite A135-S2356, 512MB ram, 80GB sata hd, Celeron M620 1.6GHz processor....not quite sure what the sound and video specs are  and im currently using 7.04 fiesty fawn

---

### Post by The_Id on 2007-10-31
What kind of sound problems are you having? When you go to 'System - Preferences - Hardware Information' is there a sound card listed? Have you tried checking the volume. Also try going to the terminal and run > aplay -l and see what it says.

---

### Post by Jaco Du Toit on 2007-10-31
Maybe this link would help:

[http://arbitraryusefulinfo.wordpress.com/2007/06/12/configuring-ubuntu-on-a-toshiba-a135-s2356/]("http://arbitraryusefulinfo.wordpress.com/2007/06/12/configuring-ubuntu-on-a-toshiba-a135-s2356/")

---

### Post by ebeard on 2007-10-31
Post number 5 on this thread [http://ubuntuforums.org/showthread.php?t=597286&highlight=external+amplifier](http://ubuntuforums.org/showthread.php?t=597286&highlight=external+amplifier)
and similar posts fixed my Gateway laptop sound. It's worth checking.

---

### Post by Hairy Hobbit on 2007-10-31
Hi - thanks for taking the time to re-post the link.

I think, for the sake of my learning something, I'd like to find out what sound card is in here.  I've had a look in hardware information - and the only thing I've found that looks like a reference to a sound card is ;

82801G ICH7 FAMILY High Definition Audio Controller.

When I look at the Device Tab, it shows :

VENDOR   ;    INTEL CORPORATION
DEVICE : 82801G ICH7 FAMILY High Definition Audio Controller.
STATUS  :   STATUS
BUS TYPE :  PCI
DEVICE TYPE  :   UNKNOWN
CAPABILITIES  :   UNKNOWN.


THanks,
HH

---

### Post by FuturePilot on 2007-10-31
Try this.
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Add this to the bottom
```
options snd-hda-intel position_fix=1 model=3stack
```
Save and reboot.

---

### Post by Jaco Du Toit on 2007-10-31
When you type the command lsmod , do you see a module loaded called snd_hda_intel ?

Typing this command on my pc:

```

lsmod | grep snd_hda_intel

```

yields:

```

snd_hda_intel         277020  5 
snd_pcm                80772  3 snd_hda_intel,snd_pcm_oss
snd                    55684  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm

```

Now granted I don't have EXACTLY the same sound card as you (I have ICH8 family) but it is also supposed to be Intel High Definition. Now in my case my sound card worked out of the box on Feisty (7.04) but I had endless problems with it in Gutsy (7.10) which involved recompiling ALSA drivers and at one point I even recompiled my kernel (which was probably unnecessary and broke a whole lot of other things which took some time to fix)

---

### Post by Hairy Hobbit on 2007-10-31
FuturePilot....

When you said "add this to the bottom" - I assume you mean there should be some lines in the file already.

When I type the first thing you suggested, I get a blank sheet to type into.

HH

---

### Post by Jaco Du Toit on 2007-10-31
I think he meant:
gksudo gedit /etc/modprobe.d/alsa-base

---

### Post by Hairy Hobbit on 2007-10-31
Thanks for the correction JDT.

I edited the file, saved, rebooted, and still no sound.

Looks like i'm going to need to keep  my XP dual boot after all.  I can't work without sound.  Looking through google and these forums it seems there has been sound issues right the way back with Tosh's.   There seems to be lots of people saying they got it working, but none with my card - and even those with the cards that have been fixed seem to only get a 50% success rate.

To me, the test I want to be able to pass - is to do a complete new install of Ubuntu, then do the fix - and then get sound.

I dont have confidence in things that take 5 or 6 different attempts to get working, as then you never really know what fixed it.

Thanks though,
HH

---

### Post by Everywhere_at_Once on 2007-10-31
hey,
i just fixed the sound on my LG P1 again after re-installing Gutsy. That was about 2 minutes ago.
I want you to try something.
navigate to /etc/modprobe.d
is there a file in there called snd-hda-intel?

---

### Post by FuturePilot on 2007-10-31
> **Jaco Du Toit said:**
> I think he meant:
gksudo gedit /etc/modprobe.d/alsa-base

Oops. Yes that's what I meant.:oops:

---

### Post by Hairy Hobbit on 2007-10-31
Hi.

I've had a look (after learning my first 2 command line commands CD and DIR  :-)

And no, there is no file by that name.

HH

---

### Post by Everywhere_at_Once on 2007-10-31
first open gedit, and creade a file with the name "snd-hda-intel" that contains one line "options snd-hda-intel model=3stack" then save it to your home folder.
```
cd /#yourhomefolder(where file is located)
sudo cp -i snd-hda-intel /etc/modprobe.d/
```

cp is the command line copy.
the -i means interactive, it will prompt you before overwriting anything (which is good)
and you need to be a superuser to complete that task.

---

### Post by Everywhere_at_Once on 2007-10-31
Heres a wiki about your computer, with a solution to the audio problems at the bottom.
by the looks of it, if my solution doesnt work, then your gonna learn a bunch more of the command line before you can play cd's. 

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG)


whoops, that was the OP's laptop model.
o well, if he wants help, there it is.

---

### Post by georghess on 2007-10-31
Also make sure that your user has audio enabled in the groups list !

:-)

---

### Post by Hairy Hobbit on 2007-10-31
Hi.

Everywhere, is that the same as I did for Future Pilot?

FP -  I tried your suggestion and it didn't work unfortunately.

Everywhere, I'm afraid I don't know how to do what you suggest - I've never used a command line before but it looks like I just type GEDIT and then choose where to save it.  The bit I dont know about (yet) is the home folder and the file structure of Ubuntu.  I havent got around to creating an docs yet as without sound I won't be bothering :-)


HH

---

### Post by Hairy Hobbit on 2007-10-31
Everywhere - that link was for 2 previous versions of Ubuntu - and for a different laptop to mine.  Mine is a Toshiba P100 PSP4AE.

---

### Post by Hairy Hobbit on 2007-10-31
ok, i created the file saved it in HOME/DAVE and can see it in there....

I typed the rest of what you said, was asked for my password - but then nothing else happened.

Still no sound though.

---

### Post by Everywhere_at_Once on 2007-10-31
my /home is on a different partition, so mine may not be in the same place as yours..
but here goes.
just save the file you created to /home/#yourusername

then in terminal
cd /home/#yourusername

---

### Post by Hairy Hobbit on 2007-10-31
ok thanks.

I did it.  I was asked for my password, but then no other feedback.

Is there anything I need to check now?

Also, rebooted, and no sound still.

:-(

Thanks for all your efforts though everyone.

HH

---

### Post by Everywhere_at_Once on 2007-10-31
you typed in your password and pressed enter, right??

just making sure. :P

click system/preferences/sound
then the device dropdown.

does it say anything?
list any hardware?

---

### Post by Hairy Hobbit on 2007-10-31
It shows the same few that it always shows after a clean install..  

It's set to AUTODETECT, but the drop down lists:

CONEXANT digital
Conexant analog
ALSA
ESD
OSS

If I plug in my headphones, I get an extra drop down called USB Headset or something like that, after selecting thatone then the TEST sound works ok.

HH

---

### Post by Everywhere_at_Once on 2007-10-31
try selecting conexant, long show but hey sometimes the easiest solution is the one that works.

if not;
[linky-conexant cards]("http://www.linuxquestions.org/questions/susenovell-60/howto-fix-acpi-ich7-family-conexant-driver-on-toshiba-p100105-series-531575/")
find out what sound card you have. 
```
cat /proc/asound/card0/codec#0 | grep Codec
```
you'll need that information.

here is a bug on launchpad as well where other users in your situation are posting.
[Linky-Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469")

good luck with this!

---

### Post by Hairy Hobbit on 2007-10-31
I've tried selecting all the sound sources - still no output.

I've tried about 8 different solutions now, and no sound.  Without sound, I can't do the things I need to do and that was my ticket away from XP - as I am fortunate enough that I only need a PC for net access, skype, MSN, basic stuff.  I thought I was a prime candidate to stick one on the Evil Empire.

I can't get into typing in 5 pages of command line like the smart guys in that link - my eyesight isn't good enough and I don't really want to.  I know that with something like Ubuntu you have to configure to get stuff working but there is a limit for old timers like me :-)

I'll keep on hoping it's fixed, everyone is a great help with good intentions and a wonderful approach but it may be a case I have to wait for future updates.  I'm not hopeful though, as this has been an issue since way back and its seems a low priority.

Cheers!
HH

---

