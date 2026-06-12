---
title: "call me stupid"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by splitfface on 2006-08-20
i jsut installed Ubuntu 6.06   i got a book from barna and noble about this OS,   now in the manuel it says that the sound card should be detected and working post installation.   ive got no sound at all.   i look on teh ubuntu web site,  i cant seem to find anythign that will tell me anythign about either the drivers or the preference to get it to work,   the most ive found is device manager,  but i dont know how to do nothign on this OS yet.   can someone help me.  

            ~ supreme noob          splitface

   and where are the command lines at??

---

### Post by taurus on 2006-08-20
Do you have an onboard soundcard or a PCI card?  Do you now the manufacture and model of it?

---

### Post by splitfface on 2006-08-20
pci sound blaster

---

### Post by splitfface on 2006-08-20
i went tot eh sound blaster website,  but they dont have drivers for it for linux,   does that mean ill never have sound unless i buy a new sound card.   or is there a way to fool the system into thinking i have a differnt sound card and have it still work.   god im stupid with linux right now,  im a windows master....  i feel so weak

---

### Post by HanZo on 2006-08-20
sure it is a pci soundblaster? and if yes what model? 16, 128, live? If it happens to be an ISA sb, you'll have to mount the module manually...

---

### Post by Tomosaur on 2006-08-20
I would have thought you'd be ok with sound really. Go to applications > Add/Remove, then click 'Advanced'. Once you've put in your password (same password you use to log on) try doing a few searches for 'pci sound blaster' or something. I have no idea why it wouldn't just work. Occasionally stuff like this does happen though, and more often than not there is a way to fix it. Make sure Alsa is installed too.

---

### Post by splitfface on 2006-08-20
nothing,  i have no clue what to do now

---

### Post by Haegin on 2006-08-20
Find the model of the soundcard and go to this site:
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix)
to find what driver you need and tell us here and we can guide you the rest of the way. Don't worry about the lack of sound - it's the best way to learn. Back before breezy I had to compile in my own soundcard driver and I learnt loads. Now in dapper it's already autodetected so there is definatly hope for the future.

---

### Post by splitfface on 2006-08-20
the one i need is ES1371    it has instructions,  but i have no ckue what theyre talking about

---

### Post by 5-HT on 2006-08-20
> **splitfface said:**
> the one i need is ES1371    it has instructions,  but i have no ckue what theyre talking about
To load the module try:
```
 sudo modprobe snd-ens1371 
``` You may need to adjust some settings via: ```
 alsamixer 
``` 
If that works you can have the module loaded on boot by adding it to /etc/modules. You can either add the module to the file using your preferred text editor (will need root privileges do to so...i.e., sudo), or by entering the following in a terminal (will also backup your current /etc/modules) :
```
sudo cp /etc/modules /etc/modules.backup
echo snd-ens1371 | sudo tee -a /etc/modules 
``` 
HTH

---

### Post by splitfface on 2006-08-20
i know this is probably gonan be very stupid,  but where is that program or the tool to code in,   i cant find it,    maybe that my biggest problem
  told ya i was a super noob

---

### Post by meng on 2006-08-20
Yes you asked this at the beginning and it was missed.
The terminal/console/command line is available through Applications > Accessories > Terminal if you're using GNOME.

---

### Post by 5-HT on 2006-08-20
> **meng said:**
> Yes you asked this at the beginning and it was missed.
The terminal/console/command line is available through Applications > Accessories > Terminal if you're using GNOME.

Sorry I missed that. Yes, every command in those boxes need to be entered into a terminal. The *alsamixer *step is just to change volume levels if neeed.

Based on the chipset you identified and brief look on the ALSA webpage, the module I mentioned should hopefully do the trick. If not, there are others that can be tried.

---

### Post by splitfface on 2006-08-20
sudo modprobe snd-ens1371  does not work.   im wondering if sound card is even installed at all,  becasue i looked at the device manager and say it said that the describtion was unavailible

---

### Post by splitfface on 2006-08-20
:mad:

---

### Post by meng on 2006-08-20
What about trying:
lspci
Should give a list of pci devices.
Be patient! 1 hour is not long to wait here.

---

### Post by bodhi.zazen on 2006-08-20
5-HT: Nice how to.

splitfface: If you loaded the modules from the terminal without error you very likely need to un-mute the sound. I know it sounds dumb, but that may be all there is to it.

I can't give you each step for gnome, but if I recall correctly there is a small icon in the uppre right, looks like a speaker? click on that and, as in other OS, there should be several options -> volume, etc. Make sure the "mute" button is not checked.

If you can not find the volume control button type:
```
gnome-volume-control &
```
in a terminal.



If that does not work, try alsamixer:
```
alsamixer
```
in a terminal.

With alsamixer, use the arrow keys to select channels and the up and down arrows to set volume. Use "Esc" key to exit alsamixer.



If that does not work, make sure the volume is not turned all the way down in your player (xmms?).

---

### Post by splitfface on 2006-08-20
ok this is what i got when i typed that in

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 735 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
[COLOR="Red"]0000:00:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)[/COLOR]
0000:00:09.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
0000:00:0d.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 300/305 PCI/AGP VGA Display Adapter (rev 90)

---

### Post by meng on 2006-08-20
Well at least you know that you have a soundcard.
I have to defer to the experts here, but would
sudo modprobe snd-emu10k1
work here?

---

### Post by splitfface on 2006-08-20
the volume thing was one of the first things i tried,  i saw that in the media tab,   so i tried it first.   i feel like a naked guy in a foriegn coutry and cant speak the language,   but hey,  ill make ya smile.  lol

---

### Post by splitfface on 2006-08-20
sudo modprobe snd-emu10k1  still isnt working,   the first time i type it in it askes for my password,  i type it in and then nothign happends,   do you think i might have to install ubuntu again,   casue i know in windows most of the time if you didnt get the right drivers on teh first install,  chances are it will backup the bad drives and youll still have the same problem

    any suggestions are great help for me at this point

---

### Post by bodhi.zazen on 2006-08-20
What makes you think " sudo modprobe snd-emu10k1" did not work? did you get error messages? Just because there was no output to the terminal does not mean "nothing happened". If there were a problem you would have gotten an error message like:
```
# sudo modprobe gibberish
FATAL: Module gibberish not found
```

I use a similar sound card and am curious about the possibility your sound card is muted as that seemed to be a problem with my card.

What program are you using for sound? xmms? other? system sounds?

---

### Post by bodhi.zazen on 2006-08-20
What makes you think " sudo modprobe snd-emu10k1" did not work? did you get error messages? Just because there was no output to the terminal does not mean "nothing happened". If there were a problem you would have gotten an error message like:
```
# sudo modprobe gibberish
FATAL: Module gibberish not found
```

I use a similar sound card and am curious about the possibility your sound card is muted as that seemed to be a problem with my card.

What program are you using for sound? xmms? other? system sounds?

I do not think a re-insatll of Ubuntu will help at all.

---

### Post by Haegin on 2006-08-21
Ok, here goes.
Open the terminal and enter all the stuff in boxes
```
like this
```
Good Luck!

1. ```
uname -r
``` will give you something like 2.6.10-5-386 somewhere in the output.

2. Enter ```
sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10 build-essential
``` and replace the 2.6.10 and the 2.6.10-5-386 with what you got from uname -r in the previous step.

3. ```
2.6.10-5-386
``` to change to the right directory

4. ```
sudo wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2
``` to download the latest alsa release into /usr/src.

5. ```
tar xvjf alsa-driver-1.0.8.tar.bz2
``` to extract the tarball you just downloaded giving you a directory called alsa-driver-1.0.8.

6. ```
cd alsa-driver-1.0.8
``` to change to the new directory.

7. ```
sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
``` to compile the alsa driver. This step will produce a lot of output that is vaguely readable. If it fails it will give you an error in which case just tell us and we can try and help you. If it all works fine then we are almost there.

8. ```
sudo make
``` to make the alsa program you just compiled. This will produce loads of output that you really won't be able to read. Don't try, it will drive you insane (like the rest of us).

9. ```
sudo apt-get install checkinstall
``` to install a program for making debs (very useful)

10. ```
sudo checkinstall
``` to finally build the deb from the compiled and made driver and install the deb automatically (if it fails just give us the error and anything that looks helpful).

11. ```
sudo gedit /etc/modules
``` to open the list of modules to edit in gedit.

12. Scroll down to the end and add the following to the end of the list (each on seperate lines as shown here)

snd-pcm-oss
snd-emu10k1
snd-mixer-oss

13. Save the file and restart the pc and hopefully you should have sound working. If you have any problems with any of this then just post the output of the last command you ran and hopefully we should be able to help. Just be patient - you can learn alot from doing this and it isn't a common procedure so don't worry about it being hard.

---

### Post by Haegin on 2006-08-21
Sorry to double post but I wanted this to be seperate.

I just realised that ubuntu may be trying to use an onboard sound card instead of your sb live. If so try going into the bios (press del at startup) and disable the onboard sound if you can. If you can't and my previous post doesn't help then it may be worth looking more into this but it is less likely.

---

### Post by encompass on 2006-08-21
And about your comment at the beginning... very few companies ever make drivers for linux... and the ones many make are poor quality and don't work anyway... linux is cool because people have madethere own drivers.  so the sound cards work out of the box rather than having to go to each and every website of the companies jsut to install every little driver when under the open source licence they build it into the kernal and no one worries.
The problem is that companies won't release the hardware information... some how that makes them money.  And the programmers undup having to play around for hours trying to get them to work.  Sad, but our drivers would be 300 times better if we hard the hardware information.

---

### Post by steve.horsley on 2006-08-21
Do you see a little icon of a loudspeaker on one of your panels? I hope so. Two things:

Firstly, if you double-click it, you get a bigger mixer pop up with lots of sliders to experiment with.

Secondly, if you use the manu and go System->Preferences->Sound you get to see some options. Make sure that you have the right sound card selected. On my last PC, it defaulted to the built-in sound card on the motherboard although my speakers were connected to my soundblaster live PCI card. An easy fix once you know where to look. And I didn't need to insatll any drivers - SB live is fully supported.

---

### Post by splitfface on 2006-08-21
mike@ubuntu:~$ like this
bash: like: command not found
mike@ubuntu:~$ uname -r
2.6.12-10-386
mike@ubuntu:~$ sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10 build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.10-5-386
mike@ubuntu:~$ 2.6.10-5-386
bash: 2.6.10-5-386: command not found
mike@ubuntu:~$ 2.6.10-5-386
bash: 2.6.10-5-386: command not found
mike@ubuntu:~$ sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2)
--20:10:44--  [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.9rc4a.tar.bz2)
           => `alsa-driver-1.0.9rc4a.tar.bz2'
Resolving ftp.alsa-project.org... 160.217.9.25
Connecting to ftp.alsa-project.org|160.217.9.25|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/driver ... done.
==> PASV ... done.    ==> RETR alsa-driver-1.0.9rc4a.tar.bz2 ... done.
Length: 2,016,263 (1.9M) (unauthoritative)

100%[====================================>] 2,016,263     47.26K/s    ETA 00:00

20:11:26 (49.86 KB/s) - `alsa-driver-1.0.9rc4a.tar.bz2' saved [2016263]

mike@ubuntu:~$ cd alsa-driver-1.0.8
bash: cd: alsa-driver-1.0.8: No such file or directory
mike@ubuntu:~$ cd alsa driver-1.0.9rc4a.tar.bz2
bash: cd: alsa: No such file or directory
mike@ubuntu:~$ sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
sudo: ./configure: command not found
mike@ubuntu:~$ sudo apt-get install checkinstall
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package checkinstall
mike@ubuntu:~$ snd-pcm-oss
bash: snd-pcm-oss: command not found
mike@ubuntu:~$ snd-pcm-oss
bash: snd-pcm-oss: command not found
mike@ubuntu:~$ snd-emu10k1
bash: snd-emu10k1: command not found
mike@ubuntu:~$ snd-mixer-oss

    i dont think it worked,  im about to restart though.  brb

---

### Post by bodhi.zazen on 2006-08-21
You need to enable a few sources. Perhaps:

```
sudo synaptic
```. 
enable universe repository.

You can install the Linux headers from synaptic as well.

Try again, one step at a time. For example, you forgot:

tar xvjf alsa-driver-1.0.8.tar.bz2.

Finish one step before moving to the next. If you get an error or unexpected response problem solve before proceeding.

From the start:

sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10 build-essential

should read:
```
sudo apt-get install linux-headers-2.6.12-10-386 linux-headers-2.6.10 build-essential
```

"2.6.10-5-386" is not a command to be entered, but the numbers to be inserted into the above command.

wget is OK

DO NOT FORGET TO 

```
tar xvjf alsa-driver-1.0.8.tar.bz2
```

Everything else looks fine.

---

### Post by Haegin on 2006-08-22
Very sorry but I got the wrong version number in the commands for extracting and working with the alsa drivers so instead of 1.0.8 it's 1.0.9 so just replace the old (1.0.8) version number with the new one (1.0.9)

---

### Post by Paul133 on 2006-08-22
I know this is really off topic but I've been reading this thread and I'm curious as to how you make those boxes (NOT how to bring up the terminal, but how to make the terminal code boxes in a post). How do you do that?

---

### Post by Haegin on 2006-08-22
Just put the text you want in between [code ] and [/ code] (without the spaces) like this:
```
See
```

---

### Post by nickpaton on 2006-08-22
> **Paul133 said:**
> I know this is really off topic but I've been reading this thread and I'm curious as to how you make those boxes (NOT how to bring up the terminal, but how to make the terminal code boxes in a post). How do you do that?

Above the box where you actually type in your message you'll see "#".
Insert Code between the **"**```
code icons!
```**"**

---

### Post by Paul133 on 2006-08-22
```
 Like This? 
```

Thanks!

---

### Post by baldy1324 on 2006-08-23
for your terminal question - you can go to the terminal by typing ALT-F2 and then entering gnome-terminal then you can type commands like everyone is telling you.

---

