---
title: "[SOLVED] very nooby"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by maryjanua on 2007-09-14
hi im a very nooby i just installed ubuntu for the 1st time last night. now iv never really done any command  line stuff but i'll give it a try if needs be. my problem is i've installed evrything with no glitches except i cant get sound. the rest just installed automatically. ive got an asus 4core dual sata motherboard and it says i have realtek hd audio in xp but ive googled it and cant find anything that really helps me any1 out there know what to do? itd b much appreciated

---

### Post by overdrank on 2007-09-14
> **maryjanua said:**
> hi im a very nooby i just installed ubuntu for the 1st time last night. now iv never really done any command  line stuff but i'll give it a try if needs be. my problem is i've installed evrything with no glitches except i cant get sound. the rest just installed automatically. ive got an asus 4core dual sata motherboard and it says i have realtek hd audio in xp but ive googled it and cant find anything that really helps me any1 out there know what to do? itd b much appreciated

Hi and welcome, you can look at this thread and it may help
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
good luck! :KS

---

### Post by maryjanua on 2007-09-14
thanks very much i had just found that thread myself im gonna try it nsee

---

### Post by bobpur on 2007-09-14
If it's worked before with another OS, Windows  for instance, the connections are correct and can be discounted. Check the Volume icon on the panel (near the clock on Ubuntu) and see if it is muted or the volume is turned all the way down. 
I tore a machine apart one time without checking out the simple stuff. Needless to say, I was feeling stupid when I found out the speakers weren't powered on.
Don't forget to check out the easy stuff. We've all made that mistake a time or two:)
If you have a Staples near go get a DiamondTek soundcard in 5.1 or 7.1. They come with open source software so are linux friendly. Also, they are very reasonably priced around $30.00. I think I've seen them on [www.newegg.com](www.newegg.com) if you want to check out the specs. I have three in different machines and am very happy with them. Great sound.

                                                       Good Luck

---

### Post by maryjanua on 2007-09-14
thanks but it says: No volume control GStreamer plugins and/or devices found. and the other answer i got with all the copyin n pastin cmd line stuff isnt working either:confused: ifeel a bit dumb but ubuntu says i have a via hd audio onboard in case i made an error earlier

---

### Post by maryjanua on 2007-09-14
i really am being dumb today and looking at the wrong  mboard box its an asrock 4coredual sata2 with a via hd audio card built in. the same problem still stands . pleases help ](*,)]

---

### Post by SOULRiDER on 2007-09-14
Check out this link:
[https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

If you dont understand anything PLEASE ask, dont be affraid to do so.

---

### Post by maryjanua on 2007-09-14
i dont see how that solves my sound issues but thanx for the firewall anyway itl b handy:)

---

### Post by Vadi on 2007-09-14
:D

Um, if it says something about grstreamer... go to add/remove, and check off every gstreamer thing that comes up.

---

### Post by Vadi on 2007-09-14
Read this ([clicky]("http://www.zolved.com/synapse/view_content/27985/Setting_up_sound_in_Ubuntu")), if it might help.

---

### Post by SOULRiDER on 2007-09-14
> **maryjanua said:**
> i dont see how that solves my sound issues but thanx for the firewall anyway itl b handy:)

Im very sorry, i copied the wrong link :oops::oops::oops:
I meant to paste this:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by maryjanua on 2007-09-14
i tried what you said vad this is what it says:
billym@billym-desktop:~$ $ gedit~/.asoundrc 
bash: $: command not found
billym@billym-desktop:~$ gedit~/.asoundrc 
bash: gedit~/.asoundrc: No such file or directory
billym@billym-desktop:~$ sudo asoundconf
Password:
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card CARD
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio

billym@billym-desktop:~$ 


still no sound

---

### Post by Vadi on 2007-09-14
You missed a space:

gedit ~/.asoundrc

between 'gedit' and '~/.asoundrc'

---

### Post by Gremlinzzz on 2007-09-14
Right click on your volume icon if you have one.choose open volume control.make sure nothings muted.click edit on volume control and check all thats on the list and unmute
some good beginner  sites you should get extra repositories 

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[http://linuxcommand.org/](http://linuxcommand.org/)
should bookmark these sites come in handy

---

### Post by maryjanua on 2007-09-14
iv been at his all day to no avail. looks like im destined not to have sound in ubuntu:neutral:

---

### Post by Vadi on 2007-09-14
Try plugging headphones in. I have a friend who's too lazy to get the speakers working in his laptop, but headphones work.

---

### Post by maryjanua on 2007-09-14
sorry to be a bore but iv tried allsorts of stuff to get my sound working..silence prevails and things r getting worse i cant install java now i type the su command n it asks for a password which i duly give and it says its wrong?also my video cards acting up i cant get desktop effects just a white screen and a pointer! desktop disappears. i'll keep trying but its becoming irritating

---

### Post by shae on 2007-09-14
> **maryjanua said:**
> sorry to be a bore but iv tried allsorts of stuff to get my sound working..silence prevails and things r getting worse i cant install java now i type the su command n it asks for a password which i duly give and it says its wrong?also my video cards acting up i cant get desktop effects just a white screen and a pointer! desktop disappears. i'll keep trying but its becoming irritating

Try running that command with sudo rather than su.

---

### Post by Vadi on 2007-09-15
> **maryjanua said:**
> sorry to be a bore but iv tried allsorts of stuff to get my sound working..silence prevails and things r getting worse i cant install java now i type the su command n it asks for a password which i duly give and it says its wrong?also my video cards acting up i cant get desktop effects just a white screen and a pointer! desktop disappears. i'll keep trying but its becoming irritating

Can you please tell what video card are you using? Some cards need to be configured to work with Compiz right.

---

### Post by maryjanua on 2007-09-16
thanks shae i'll try that. iv got a radeon X1550   but ubuntu says its a radeon X1300. dunno why

---

### Post by maryjanua on 2007-09-16
jeez this is drivin me nuts any1 give me a step by step guide to installing stuff thats  explained in plain english? i know i must b buggin you but i really want to try and get this working
i cant get java or sound yet and im actually thinking of going back to windows because all these explanations that iv benn given mean nothing really none of it works for me unless im just really dumb(which is a possibilty)

---

### Post by Vadi on 2007-09-16
Here's an easy way to get Java, and Flash working:

Go to Applications, Add/Remove, and top-left, select 'All Applications' or somesuch. Then search for 'restricted' - you'll get a "Ubuntu restricted extras" package.

Install that, and you'll have your java.

I'll try searching if other people came up with a solution for your sound problem.

---

### Post by Vadi on 2007-09-16
> **maryjanua said:**
> i tried what you said vad this is what it says:
billym@billym-desktop:~$ $ gedit~/.asoundrc 
bash: $: command not found
billym@billym-desktop:~$ gedit~/.asoundrc 
bash: gedit~/.asoundrc: No such file or directory
billym@billym-desktop:~$ sudo asoundconf
Password:
Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card CARD
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio

billym@billym-desktop:~$ 


still no sound

I posted a solution after this post, but you didn't seem to reply.

When you did gedit~/.asoundrc, you missed a space after the word 'gedit' - you were supposed to do 'gedit ~/.asoundrc'.

So could you try those instructions again, with a space?

---

### Post by maryjanua on 2007-09-16
hey vadi i tried doin java via add/remove this is what it said: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by Vadi on 2007-09-16
So did you try doing dpkg --configure -a then?

---

### Post by maryjanua on 2007-09-16
yep it says this :   dpkg: requested operation requires superuser privilege

---

### Post by maryjanua on 2007-09-16
and for the sound it says theres no card when there definitely is! i wld type evrythin it says but theres loads

---

### Post by maryjanua on 2007-09-16
when i do the gedit ~/.asoundrc 
it says that the file may be old or corrupted i tried to copynpaste the entire message but the forum wont let me
by the way thanks for your help vadi id b lost without it

---

### Post by maryjanua on 2007-09-16
im about to give up. what is dpkg anyway? now i cant install anything always a dpkg error and i need to be a superuser whatever that is

---

### Post by eapache on 2007-09-16
Superuser just means put 'sudo' in front. It stands for 'super user do'.

---

### Post by Vadi on 2007-09-16
Yes, so try doing 'sudo dpkg --configure -a' then.

I'm sure we'll get it working :)

---

### Post by maryjanua on 2007-09-16
thanx ppl i used the sudo at the start and it says this : Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...
is this right?

---

### Post by Vadi on 2007-09-16
Yup. Setting up means it's... making, creating. That's a good thing!

I guess your Java should be working now.

---

### Post by maryjanua on 2007-09-16
yep it wd appear so thanx v much just my sound now:)

---

### Post by maryjanua on 2007-09-16
ive got the sound driver from via sitting on my desktop i just cant seem to open it any1 who cn help i offer my thanks in advance:KS

---

### Post by Vadi on 2007-09-16
Can you please say where did you get it from? (or the place where you got instructions for it)

---

### Post by maryjanua on 2007-09-16
heres where i got it vadi :    
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3140&SubCatID=154](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3140&SubCatID=154)

---

### Post by Maestro23 on 2007-09-16
> **maryjanua said:**
> heres where i got it vadi :    
[http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3140&SubCatID=154](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3140&SubCatID=154)

Get to wherever you downloaded it (probably your Desktop) /home/username/Desktop

In terminal:

> tar xvzf via_ubuntu_7.04_linux_hd_audio_ig_ver0.8.tar.gz

There's a .pdf file in there with installation instructions.

You can also extract it thru your GUI.  Right-click on the file, open with your archiver program.

---

### Post by maryjanua on 2007-09-16
sorry that was not it this is:    /home/billym/Desktop/via_ubuntu_7.04_linux_hd_audio_ig_ver0.8.tar.gz
but its on the same page
and the instructions r inside

---

### Post by maryjanua on 2007-09-16
yes i know its not windows maestro  i'm trying to learn because i'm so bored with windows. i know theres a pdf file in there and ive done evrything it tells me (i may be stupid but not that stupid) and it still keeps giving me error messages

---

### Post by splintercellguy on 2007-09-16
It would really help if you told us what, and what errors you get, else we cannot help you effectively.

---

### Post by Maestro23 on 2007-09-16
> **maryjanua said:**
> yes i know its not windows maestro  i'm trying to learn because i'm so bored with windows. i know theres a pdf file in there and ive done evrything it tells me (i may be stupid but not that stupid) and it still keeps giving me error messages

You said in a previous post that you had the sound driver sitting on your desktop and didn't know how to open it.  That was the instructions that I provided you with.

 > Re: very nooby
ive got the sound driver from via sitting on my desktop i just cant seem to open it any1 who cn help i offer my thanks in advance


Please provide error messages so we can help you better.

---

### Post by maryjanua on 2007-09-16
there u go the exact message :    
billym@billym-desktop:~$ /home/billym/Desktop/via_ubuntu_7.04_linux_hd_audio_ig_ver0.8.tar.gz
bash: /home/billym/Desktop/via_ubuntu_7.04_linux_hd_audio_ig_ver0.8.tar.gz: Permission denied
billym@billym-desktop:~$

---

### Post by Vadi on 2007-09-16
I think you just want "/home/billym/Desktop/".

You can't go _into_ a file, but you can go in the directory where it is. Try that, it'll work :)

---

### Post by Maestro23 on 2007-09-16
> **Vadi said:**
> I think you just want "/home/billym/Desktop/".

You can't go _into_ a file, but you can go in the directory where it is. Try that, it'll work :)

> cd /home/billym/Desktop

The when you get to the Desktop directory, type "ls" (lower-case L). Should see the driver file there.

Then use the tar command I posted earlier to extract the driver.

---

### Post by maryjanua on 2007-09-16
billym@billym-desktop:~$ /home/billym/Desktop/
bash: /home/billym/Desktop/: is a directory
billym@billym-desktop:~$ home/billym/Desktop/
bash: home/billym/Desktop/: No such file or directory
billym@billym-desktop:~$ 

i give up its there but ..........

---

### Post by splintercellguy on 2007-09-16
As mentioned in the previous post, you are supposed to cd into the directory, like:

cd /home/billym/Desktop

And remember that Linux is case sensitive.

---

### Post by Vadi on 2007-09-16
To tell you the truth, I think when you start the terminal, you're already in the home folder.

Try typing **ls**, that'll list all stuff in a folder. Do you see the file there?

---

### Post by maryjanua on 2007-09-16
sorry for soundin a bit grouchy but im trrin evrythin u good ppl say and this is what it says back:

billym@billym-desktop:~$ cd /home/billym/Desktop
billym@billym-desktop:~/Desktop$ tar xvzf via_ubuntu_7.04_linux_hd_audio_ig_ver0.8.tar.gz
Readme.pdf
VIA-HDA-v1.40-U7.04_bin.tgz
billym@billym-desktop:~/Desktop$ 

what now?

---

### Post by maryjanua on 2007-09-16
yeah i did ls  some stuff in green some blue and some red.    
 the driver names and readme files etc

---

### Post by splintercellguy on 2007-09-16
Well, you have extracted the PDF and another tarball; you can view the PDF for further instruction. To untar the .tgz file, just do what you did before to that file.

---

### Post by Maestro23 on 2007-09-16
> **splintercellguy said:**
> Well, you have extracted the PDF and another tarball; you can view the PDF for further instruction. To untar the .tgz file, just do what you did before to that file.

Exactly.  To the OP, Go back to your graphical desktop and you should see the .pdf there.  Right-click on it and open it with the document reader program.

---

### Post by maryjanua on 2007-09-16
im gonna split now if anyone reads this and can help i'll b on in the morning (its 1.40 am here now)  heres what it says when i do ls :   
billym@billym-desktop:~$ ls
alsa-lib-1.0.15rc2  Linux_HD_AudioCodec_V140.zip
city_at_night.jpg   Music
Desktop             Pictures
Documents           via-linux-audiopackV1.40
Examples            via-linux-audiopackV1.40.tar.gz
install.sh
billym@billym-desktop:~$ 
if anyone knows what to do i'll try it after ive slept ok nite folks n thanx again :)

---

### Post by maryjanua on 2007-09-16
tried it no joy

billym@billym-desktop:~$ # tar zxf VIA-HDA-v1.40-U7.04_bin.tgz
billym@billym-desktop:~$ # cd VIA-HDA-v1.40-U7.04_bin
billym@billym-desktop:~$ # sudo ./install.sh
billym@billym-desktop:~$ Backup orignal HD audio drivers.
bash: Backup: command not found
billym@billym-desktop:~$ Install VIA HD audio drivers.
bash: Install: command not found
billym@billym-desktop:~$ 

i give up for tonight but i'll rejoin the battle tomorrow

---

### Post by Vadi on 2007-09-16
The morning is always wiser than the evening.

When you get up, first of all - do all those commands one by one in the terminal, and also, do not put in the # sign! Ignore it.

---

### Post by maryjanua on 2007-09-17
morning folks now that iv had a sleep i thought things would b clearer in the morning but no luck iv been seeing sudo commands and such in my sleep i tried that hard over the weekend. still no sound and keeps saying no such file exists when i can see it on my desktop i dunno it looks like im gonna be a reluctant windows only user. at least ive tried something else i must just be too dumb to make it work

---

### Post by maryjanua on 2007-09-17
iv had it with this im going round in circles always telling me there is no such file or directory.
i thought this was going to be relatively straightforward not sitting around for 3 days trying vainly to get something working that automatically works in windows. how can people use this effectively when theres so much fiddling about involved?if anyone knows the answer  is it a secret?

---

### Post by mattmole on 2007-09-17
Hi,

Please do not give up. I have had similar problems in the past and I am now learning lots about Linux. Ubuntu is the easiest distro I have ever used. The community are very willing to help (as you have seen).

I will look through the posts again in my lunch break and try to post this aft.

Mattmole :)

---

### Post by maryjanua on 2007-09-17
thanx mattmole iv noy given up completely but i am gettin sick of goin in circles. yeah the folk have all tried to be really helpful and not just the ubergeeks puttin me down like i expected. i do like the look and feel of ubuntu but itsa a lot of work. so i'll probably stick with it and perservere til i get it right:)

---

### Post by mali2297 on 2007-09-17
Alright, I have tried to collect all commands that you need to run. Open a terminal and copy/paste each of the lines below in turn. Some of the commands might give errors, ignore them and continue.

```

sudo modprobe –r snd-hda-intel
sudo modprobe –r snd-via82xx
sudo rmmod 'lsmod|grep snd'
cd /home/billym/Desktop
tar -xvzf VIA-HDA-v1.40-U7.04_bin.tgz
cd VIA-HDA-v1.40-U7.04_bin
sudo ./install.sh
sudo modprobe snd-hda-intel

```

Post the messages that you get from the terminal.

---

### Post by maryjanua on 2007-09-17
here u go   :
billym@billym-desktop:~$ sudo modprobe –r snd-hda-intel
Password:
FATAL: Module –r not found.
billym@billym-desktop:~$ sudo modprobe –r snd-via82xx
FATAL: Module –r not found.
billym@billym-desktop:~$ sudo rmmod 'lsmod|grep snd'
ERROR: Module lsmod|grep snd does not exist in /proc/modules
billym@billym-desktop:~$ cd /home/billym/Desktop
billym@billym-desktop:~/Desktop$ tar -xvzf VIA-HDA-v1.40-U7.04_bin.tgz
VIA-HDA-v1.40-U7.04_bin/
VIA-HDA-v1.40-U7.04_bin/Ubuntu_7.04/
VIA-HDA-v1.40-U7.04_bin/Ubuntu_7.04/snd-hda-intel.ko
VIA-HDA-v1.40-U7.04_bin/Ubuntu_7.04/snd-hda-codec.ko
VIA-HDA-v1.40-U7.04_bin/install.sh
VIA-HDA-v1.40-U7.04_bin/readme.txt
billym@billym-desktop:~/Desktop$ cd VIA-HDA-v1.40-U7.04_bin
billym@billym-desktop:~/Desktop/VIA-HDA-v1.40-U7.04_bin$ sudo ./install.sh
Error: This package is only for the default kernel of Ubuntu 7.04.
billym@billym-desktop:~/Desktop/VIA-HDA-v1.40-U7.04_bin$ sudo modprobe snd-hda-intel
billym@billym-desktop:~/Desktop/VIA-HDA-v1.40-U7.04_bin$

---

### Post by mali2297 on 2007-09-17
Run these commands in the terminal and post the output:
```

uname -a
aplay -l
lspci -v

```

---

### Post by Vadi on 2007-09-17
Thanks mali for helping out =D>

---

### Post by maryjanua on 2007-09-17
sorry folks had 2 go out for a while i did those commands heres the results:
billym@billym-desktop:~$ uname -a
Linux billym-desktop 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686 GNU/Linux
billym@billym-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:1587:(snd_config_load1) _toplevel_:10:0:Unexpected char
ALSA lib conf.c:2848:(snd_config_hook_load) /home/billym/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:231: control open (0): Invalid argument
ALSA lib conf.c:1587:(snd_config_load1) _toplevel_:10:0:Unexpected char
ALSA lib conf.c:2848:(snd_config_hook_load) /home/billym/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712:(snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075:(snd_config_update_r) hooks failed, removing configuration
aplay: device_list:231: control open (1): Invalid argument
billym@billym-desktop:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: ASRock Incorporation Unknown device 0308
        Flags: bus master, medium devsel, latency 8
        Memory at f8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: ASRock Incorporation Unknown device 1308
        Flags: bus master, medium devsel, latency 0

00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: ASRock Incorporation Unknown device 2308
        Flags: bus master, medium devsel, latency 0

00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Subsystem: ASRock Incorporation Unknown device 4308
        Flags: bus master, medium devsel, latency 0

00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller (prog-if 20 [IO(X)-APIC])
        Subsystem: ASRock Incorporation Unknown device 5308
        Flags: bus master, fast devsel, latency 0

00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
        Flags: bus master, medium devsel, latency 0

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fea00000-feafffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>

00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Prefetchable memory behind bridge: fdf00000-fdffffff
        Capabilities: <access denied>

00:0f.0 IDE interface: VIA Technologies, Inc. Unknown device 5372 (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: ASRock Incorporation Unknown device 5372
        Flags: bus master, medium devsel, latency 32, IRQ 3
        I/O ports at dc00 [size=8]
        I/O ports at d880 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at d480 [size=4]
        I/O ports at d400 [size=16]
        I/O ports at d000 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07) (prog-if 8a [Master SecP PriP])
        Subsystem: ASRock Incorporation K7VT2/K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 17
        I/O ports at c480 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at c800 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at c880 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev b0) (prog-if 00 [UHCI])
        Subsystem: ASRock Incorporation K7VT6
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at cc00 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90) (prog-if 20 [EHCI])
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at fe9ffc00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. Unknown device 3372
        Subsystem: ASRock Incorporation Unknown device 3372
        Flags: medium devsel
        Capabilities: <access denied>

00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
        Subsystem: VIA Technologies, Inc. Unknown device 337e
        Flags: bus master, medium devsel, latency 32
        Capabilities: <access denied>

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
        Subsystem: ASRock Incorporation K7VT6 motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at c000 [size=256]
        Memory at fe9ff800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300] (prog-if 00 [VGA])
        Subsystem: Hightech Information System Ltd. Unknown device 3000
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at feae0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at e000 [size=256]
        Expansion ROM at feac0000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
        Subsystem: Hightech Information System Ltd. Unknown device 3001
        Flags: bus master, 66MHz, medium devsel, latency 32
        Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>

80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
        Subsystem: ASRock Incorporation Unknown device 0888
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by maryjanua on 2007-09-17
that any help? it means very little to me apart from listing my devices

---

### Post by mali2297 on 2007-09-17
I don't really know anything about these kind of sound problems, but let us try to follow the guidelines in one of the links that were given to you.  Run these commands in the terminal.
```

rm /home/billym/.asoundrc
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils 
sudo apt-get install gdm ubuntu-desktop

```
Reboot and try *aplay -l* again.

---

### Post by maryjanua on 2007-09-17
thanks mali iv done what you said and rebooted then done aplay -l and this is what it says:
billym@billym-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
billym@billym-desktop:~$ 
  
what now? if anything

---

### Post by maryjanua on 2007-09-17
i dunno why but i had sound briefly there in a java site but since i did those commands its now gone

---

### Post by maryjanua on 2007-09-17
cant believe it i had it there now iv lost it again. sound control  says iv no gstreamer or volume control.
i went into add/remove and installed everything that it had for gstreamers and its not happening. damn i wish i knew what i did earlier.
but on a plus note i managed to get java workin proerly with no install missing plugin prompts. yay! somethings going right at least:)

---

### Post by mali2297 on 2007-09-17
Try
```

aplay -vv /usr/share/sounds/login.wav

```
Do you hear anything?

If not, try
```

sudo modprobe snd-hda-intel
sudo modprobe snd-pcm-oss
sudo modprobe snd-mixer-oss
sudo modprobe snd-seq-oss
aplay -vv /usr/share/sounds/login.wav

```
Now?

---

### Post by Vadi on 2007-09-17
You know I had a weird problem where my sound dissapeared, and it would only play for a second or so when I plugged/unplugged my laptop.

It seemed to solve itself somehow though.

---

### Post by maryjanua on 2007-09-17
thanx guys but no joy
billym@billym-desktop:~$ aplay -vv /usr/share/sounds/login.wav
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:550: audio open error: No such device

i have to post in 2 parts cos it wont let me do it all at once

---

### Post by maryjanua on 2007-09-17
heres the rest:
billym@billym-desktop:~$ sudo modprobe snd-hda-intel
Password:
billym@billym-desktop:~$ sudo modprobe snd-pcm-oss
billym@billym-desktop:~$ sudo modprobe snd-mixer-oss
billym@billym-desktop:~$ sudo modprobe snd-seq-oss
billym@billym-desktop:~$ aplay -vv /usr/share/sounds/login.wav
ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:550: audio open error: No such device

---

### Post by maryjanua on 2007-09-17
i must just be exceedingly stupid cos im getting nowhere fast on this.
folk must b sick of me iv had 949 views and only a few willin to try and help 
thanks to everyone specially vadi and mali2297 but i think its maybe time to go back to crappy xp. i'll keep an eye on this thread tho just in case someone knows how to fix this:-({|=

---

### Post by maryjanua on 2007-09-18
ok nobody wanting to help now. whats happened to this supposedly very frienly linux net where everyone is freindly and helpful? at least stuff works with the other os

---

### Post by mali2297 on 2007-09-18
You said that you had the sound working for a brief moment, try to remember what you did prior to that point. Then you can try to repeat the same actions.

The next version of Ubuntu will be out in about a month. If the sound problem hasn't been resolved, make a clean installation of the new version. If you're lucky, *it will just work* as it does for most of us.

---

### Post by maryjanua on 2007-09-18
lol thanx mali i had heard about the new ubuntu next month was gonna check it out anyway i wish i could remember what i did the other day but iv been tryin everythin that has been posted on this thread to no avail for the last couple of days. for all i know iv totally screwed up this installation by puttin in all these commands that havent worked or done something else entirely.

---

### Post by maryjanua on 2007-09-18
woohoo! you know when u first start ubuntu and it says which kernel youd like to start the newest one 2.6.10  or somethin like that then u have start in safe mode then you have 2.5.10 or suchlike and safemode of that too? i started the 2.5.10 kernel and didnt really do anything xept send afew emails then i restarted the pc with the newest kernel and voila! we has sound now!!:guitar: this is mental but im not complainin:) thanks for all the help everyone its been much appreciated. specially vadi and mali2297 id have bn totally lost without your input\\:D/=D>

---

### Post by Vadi on 2007-09-18
Nice! Congrats :)

---

### Post by maryjanua on 2007-09-18
well this is officially crazy. my sounds disappeared again says i have no gstreamers and/or soundcard when i have all the gstreamers i can get. is ubuntu normally this unstable?

---

### Post by maryjanua on 2007-09-18
it let me play mp3s for about an hr eariier on today but the pcs been off since then and upon powering up again theres no sound again

---

### Post by mali2297 on 2007-09-18
Do you still have XP installed on the same computer?
... and that is running without any sound problems?
Just in case so it's not a hardware problem.

You mentioned something about **realtek hd audio**, is that the sound card? 
Can you give its full name? 
You could search the forums for info on the particular sound card.

It sounds to me like some kind of bug. :-k

---

### Post by maryjanua on 2007-09-18
yes mali i still have xp on another hdd, same pc, its not hardware. i made a mistake which i corrected a few posts later its a via hd sound card and its onboard. i dunno, sounds like a bug to me too. iv searched about a bit and found nothing but im no xpert at searching as i dont really have the time to trawl through sites for hours theres always somethin distractin me(kids etc). i'll keep tryin cos if its worked once then it will work again no doubt.  any suggestions?
again thanks

---

### Post by maryjanua on 2007-09-18
heres what it says it is:

80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
Subsystem: ASRock Incorporation Unknown device 0888
Flags: bus master, fast devsel, latency 0, IRQ 21
Memory at febfc000 (64-bit, non-prefetchable) [size=16K]

thats all it says almost everythin is unknown device including my videocard  tho its a radeon x1550 in reality ubuntu says its a radeonx1300. weird eh?

---

### Post by mali2297 on 2007-09-18
> **maryjanua said:**
> heres what it says it is:

80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
Subsystem: ASRock Incorporation Unknown device 0888
Flags: bus master, fast devsel, latency 0, IRQ 21
Memory at febfc000 (64-bit, non-prefetchable) [size=16K]

thats all it says almost everythin is unknown device including my videocard  tho its a radeon x1550 in reality ubuntu says its a radeonx1300. weird eh?

That's why I asked about the name of the sound card. Does Ubuntu give correct information on that one? What does XP say? Do you have any specs on paper perhaps?

---

### Post by Vadi on 2007-09-18
Well, I got to this page ([click]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3140&SubCatID=154"))

But I think you came to that page before too.

What happened to that .pdf with instructions on how to install the drivers?

---

### Post by mali2297 on 2007-09-18
> **Vadi said:**
> Well, I got to this page ([click]("http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3140&SubCatID=154"))

But I think you came to that page before too.

What happened to that .pdf with instructions on how to install the drivers?

This is what happened:
> 
billym@billym-desktop:~/Desktop/VIA-HDA-v1.40-U7.04_bin$ sudo ./install.sh
Error: This package is only for the default kernel of Ubuntu 7.04.


@maryjanua:
Did you check the sound when you booted the older kernel? (You mentioned that you were writing emails...)

---

### Post by maryjanua on 2007-09-18
yeah i checked the sound when i was in the other kernel i hadnt tried it before and i wondered if it was any different ie. sound working.
so i did a few emails then booted up the original kernel and the sound worked str8 away at logon then i managed to listen to mp3s for an hr, even wrote a dvd with the devede program then i shut the pc down and went out.
when i resarted the pc there was no sound so i thought id repeat what i did earlier and no joy. 
its worked twice now so theres hope:)

---

### Post by Vadi on 2007-09-18
So I guess you should just use the old kernel, since the driver is specifically tied to that.

I don't know what changed in the new version of the kernel, but nothing that I personally noticed.

---

### Post by maryjanua on 2007-09-18
theres no sound in the old kernel either. the drivers are still on my desktop and the stuff the readme file says doesnt work. i even appear to have the drivers all unpacked on there cos they r folders with bin at the end also tar.gz-files

---

### Post by maryjanua on 2007-09-18
yeah i have the specs, iv got the motherboard manual, i fitted it myself im just so dumb i didnt think of looking in there:oops::oops:
specs say:  7.1ch windows vista premium level hd audio
                   alc888 audio codec
 grr manual says supports various msoft os's nothin about linux

---

### Post by maryjanua on 2007-09-18
xp says : REALTEK HIGH DEFINITION AUDIO
                 driver v.5.10.0.5377
the kernels of ubuntu i have are 2.6.20.16 generic
                                                           2.6.20.15 generic if that means anything

---

### Post by Vadi on 2007-09-18
I think we should try asking on Launchpad this.

go to launchpad.com, click on ubuntu bottom-left, and file a question - an expert will help ya out.

---

### Post by mali2297 on 2007-09-18
You can try to search this forum and perhaps other resources, using the keyword *alc888*. 

I made a quick search here. It seems that there have been some others with similar problems. Unfortunately, those problems have been left unsolved.

---

### Post by maryjanua on 2007-09-18
u sure? when i google launchpad.com i get a training site certified by msoft and not really any use theres no mention of ubuntu

---

### Post by maryjanua on 2007-09-18
aha! o well poor m/board choice by me then! just have to live with it i spose. thanx anyway i'll keep looking :neutral:

---

### Post by Vadi on 2007-09-18
Sorry, launchpad.net, heh.

Yeah, looks like it's just your motherboard. Sorry man, hope you get a solution for this.

If what, Gutsy's coming out soon (you can even [try it out now]("http://www.ubuntu.com/testing/tribe5")), maybe they fixed it then.

---

### Post by maryjanua on 2007-09-18
wow launchpad sent me here     [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
i dont think that after 5 days of usin linux i'd b able to do all that. it looks very complicated. when does this gutsy come out? hopefully it will be fixed some folk are sayin it will be. thanx anyway but i think i'll be soundless til then i can survive. the stereo will get a bit of use at least.:) its been a while since i actually played a cd :lolflag:

---

### Post by Vadi on 2007-09-18
That page doesn't look hard, just copy/paste the instructions one by one, no tinkering required. I think you should try it.

I had a brilliant idea though - your company does offer linux drivers, why not ask their tech support to help you diangose it?

---

### Post by maryjanua on 2007-09-18
i'll maybe try that tomorrow its 3am here n time for bed

---

### Post by maryjanua on 2007-09-19
back again :( iv found the alc88 driver mentioned earlier from realtek but i cant open it keeps saing no such file/directory th iv tried doing what it says in the attached readme file. i have the tar files on my desktop but cant open them. any1 help?

---

### Post by maryjanua on 2007-09-19
heres the error message: 
billym@billym-desktop:~$ tar-/home/billym/Desktop/alsa-driver-rt20070820.tar.bz2bash: tar-/home/billym/Desktop/alsa-driver-rt20070820.tar.bz2: No such file or directory
billym@billym-desktop:~$ tar-/home/billym/Desktop/realtek-linux-audiopack-4.06b.tar.bz2
bash: tar-/home/billym/Desktop/realtek-linux-audiopack-4.06b.tar.bz2: No such file or directory
billym@billym-desktop:~$ 
 am i doing this right? to untar it

---

### Post by maryjanua on 2007-09-19
> **maryjanua said:**
> wow launchpad sent me here     [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
i dont think that after 5 days of usin linux i'd b able to do all that. it looks very complicated. when does this gutsy come out? hopefully it will be fixed some folk are sayin it will be. thanx anyway but i think i'll be soundless til then i can survive. the stereo will get a bit of use at least.:) its been a while since i actually played a cd :lolflag:

i tried doin what it says here and nothing happens when i type the 1st few lines  then it starts telling me no such file or directory when it on my desktop

---

### Post by mali2297 on 2007-09-19
> **maryjanua said:**
> heres the error message: 
billym@billym-desktop:~$ tar-/home/billym/Desktop/alsa-driver-rt20070820.tar.bz2bash: tar-/home/billym/Desktop/alsa-driver-rt20070820.tar.bz2: No such file or directory
billym@billym-desktop:~$ tar-/home/billym/Desktop/realtek-linux-audiopack-4.06b.tar.bz2
bash: tar-/home/billym/Desktop/realtek-linux-audiopack-4.06b.tar.bz2: No such file or directory
billym@billym-desktop:~$ 
 am i doing this right? to untar it

Try
```

tar -xvjf /home/billym/Desktop/alsa-driver-rt20070820.tar.bz2
tar -xvjf /home/billym/Desktop/realtek-linux-audiopack-4.06b.tar.bz2

```
Spaces are important, run *man tar* to see the meaning of *tar -xvjf*.

---

### Post by maryjanua on 2007-09-19
ok heres what it says:
alsa-lib-1.0.14/src/pcm/pcm_extplug.c
alsa-lib-1.0.14/src/pcm/pcm_dmix_generic.c
alsa-lib-1.0.14/src/pcm/pcm_symbols.c
alsa-lib-1.0.14/src/pcm/pcm_params.c
alsa-lib-1.0.14/src/pcm/pcm_softvol.c
alsa-lib-1.0.14/src/pcm/pcm_plugin.c
alsa-lib-1.0.14/src/pcm/pcm.c
alsa-lib-1.0.14/src/pcm/mask.h
alsa-lib-1.0.14/src/pcm/Makefile.in
alsa-lib-1.0.14/src/pcm/pcm_dshare.c
alsa-lib-1.0.14/src/pcm/pcm_dsnoop.c
alsa-lib-1.0.14/src/pcm/pcm_share.c
alsa-lib-1.0.14/src/pcm/interval.h
alsa-lib-1.0.14/src/pcm/interval.c
alsa-lib-1.0.14/src/pcm/mask_inline.h
alsa-lib-1.0.14/src/pcm/pcm_dmix_x86_64.h
alsa-lib-1.0.14/src/pcm/pcm_adpcm.c
alsa-lib-1.0.14/src/pcm/atomic.c
alsa-lib-1.0.14/src/pcm/pcm_ladspa.c
alsa-lib-1.0.14/src/pcm/pcm_alaw.c
alsa-lib-1.0.14/src/pcm/pcm_shm.c
alsa-lib-1.0.14/src/pcm/pcm_rate_linear.c
alsa-lib-1.0.14/src/pcm/pcm_null.c
alsa-lib-1.0.14/src/pcm/pcm_route.c
alsa-lib-1.0.14/src/pcm/interval_inline.h
alsa-lib-1.0.14/src/pcm/mask.c
alsa-lib-1.0.14/src/pcm/ladspa.h
alsa-lib-1.0.14/src/pcm/pcm_direct.h
alsa-lib-1.0.14/src/pcm/pcm_plugin.h
alsa-lib-1.0.14/src/pcm/Makefile.am
alsa-lib-1.0.14/src/pcm/pcm_iec958.c
alsa-lib-1.0.14/src/pcm/pcm_plug.c
alsa-lib-1.0.14/src/pcm/pcm_local.h
alsa-lib-1.0.14/src/pcm/pcm_file.c
alsa-lib-1.0.14/src/pcm/pcm_mulaw.c
alsa-lib-1.0.14/src/pcm/pcm_hooks.c
alsa-lib-1.0.14/src/pcm/pcm_dmix_i386.c
alsa-lib-1.0.14/src/pcm/pcm_ext_parm.h
alsa-lib-1.0.14/src/pcm/pcm_generic.h
alsa-lib-1.0.14/src/pcm/pcm_copy.c
alsa-lib-1.0.14/src/pcm/pcm_linear.c
alsa-lib-1.0.14/src/pcm/pcm_rate.c
alsa-lib-1.0.14/src/pcm/scopes/
alsa-lib-1.0.14/src/pcm/scopes/level.c
alsa-lib-1.0.14/src/pcm/scopes/Makefile.in
alsa-lib-1.0.14/src/pcm/scopes/Makefile.am
alsa-lib-1.0.14/src/pcm/pcm_dmix_x86_64.c
alsa-lib-1.0.14/src/pcm/pcm_lfloat.c
alsa-lib-1.0.14/src/async.c
alsa-lib-1.0.14/src/output.c
alsa-lib-1.0.14/src/seq/
alsa-lib-1.0.14/src/seq/seq.c
alsa-lib-1.0.14/src/seq/seq_midi_event.c
alsa-lib-1.0.14/src/seq/seqmid.c
alsa-lib-1.0.14/src/seq/Makefile.in
alsa-lib-1.0.14/src/seq/seq_local.h
alsa-lib-1.0.14/src/seq/seq_event.c
alsa-lib-1.0.14/src/seq/seq_hw.c
alsa-lib-1.0.14/src/seq/seq_symbols.c
alsa-lib-1.0.14/src/seq/Makefile.am
alsa-lib-1.0.14/src/instr/
alsa-lib-1.0.14/src/instr/simple.c
alsa-lib-1.0.14/src/instr/Makefile.in
alsa-lib-1.0.14/src/instr/iwffff.c
alsa-lib-1.0.14/src/instr/Makefile.am
alsa-lib-1.0.14/src/instr/fm.c
alsa-lib-1.0.14/src/dlmisc.c
alsa-lib-1.0.14/src/timer/
alsa-lib-1.0.14/src/timer/timer_query.c
alsa-lib-1.0.14/src/timer/timer_query_hw.c
alsa-lib-1.0.14/src/timer/Makefile.in
alsa-lib-1.0.14/src/timer/timer_hw.c
alsa-lib-1.0.14/src/timer/timer_local.h
alsa-lib-1.0.14/src/timer/Makefile.am
alsa-lib-1.0.14/src/timer/timer.c
alsa-lib-1.0.14/src/timer/timer_symbols.c
alsa-lib-1.0.14/src/Makefile.in
alsa-lib-1.0.14/src/userfile.c
alsa-lib-1.0.14/src/shmarea.c
alsa-lib-1.0.14/src/confmisc.c
alsa-lib-1.0.14/src/Versions
alsa-lib-1.0.14/src/mixer/
alsa-lib-1.0.14/src/mixer/simple.c
alsa-lib-1.0.14/src/mixer/simple_none.c
alsa-lib-1.0.14/src/mixer/Makefile.in
alsa-lib-1.0.14/src/mixer/bag.c
alsa-lib-1.0.14/src/mixer/mixer.c
alsa-lib-1.0.14/src/mixer/mixer_simple.h
alsa-lib-1.0.14/src/mixer/mixer_local.h
alsa-lib-1.0.14/src/mixer/Makefile.am
alsa-lib-1.0.14/src/mixer/simple_abst.c
alsa-lib-1.0.14/src/error.c
alsa-lib-1.0.14/src/names.c
alsa-lib-1.0.14/src/alisp/
alsa-lib-1.0.14/src/alisp/alisp.c
alsa-lib-1.0.14/src/alisp/Makefile.in
alsa-lib-1.0.14/src/alisp/alisp_snd.c
alsa-lib-1.0.14/src/alisp/alisp_local.h
alsa-lib-1.0.14/src/alisp/Makefile.am
alsa-lib-1.0.14/src/input.c
alsa-lib-1.0.14/src/hwdep/
alsa-lib-1.0.14/src/hwdep/hwdep_local.h
alsa-lib-1.0.14/src/hwdep/Makefile.in
alsa-lib-1.0.14/src/hwdep/hwdep_hw.c
alsa-lib-1.0.14/src/hwdep/hwdep_symbols.c
alsa-lib-1.0.14/src/hwdep/hwdep.c
alsa-lib-1.0.14/src/hwdep/Makefile.am
alsa-lib-1.0.14/src/socket.c
alsa-lib-1.0.14/src/control/
alsa-lib-1.0.14/src/control/control.c
alsa-lib-1.0.14/src/control/control_shm.c
alsa-lib-1.0.14/src/control/Makefile.in
alsa-lib-1.0.14/src/control/setup.c
alsa-lib-1.0.14/src/control/control_hw.c
alsa-lib-1.0.14/src/control/namehint.c
alsa-lib-1.0.14/src/control/control_ext.c
alsa-lib-1.0.14/src/control/cards.c
alsa-lib-1.0.14/src/control/Makefile.am
alsa-lib-1.0.14/src/control/control_symbols.c
alsa-lib-1.0.14/src/control/hcontrol.c
alsa-lib-1.0.14/src/control/control_local.h
alsa-lib-1.0.14/src/conf/
alsa-lib-1.0.14/src/conf/pcm/
alsa-lib-1.0.14/src/conf/pcm/surround50.conf
alsa-lib-1.0.14/src/conf/pcm/surround71.conf
alsa-lib-1.0.14/src/conf/pcm/rear.conf
alsa-lib-1.0.14/src/conf/pcm/surround41.conf
alsa-lib-1.0.14/src/conf/pcm/center_lfe.conf
alsa-lib-1.0.14/src/conf/pcm/Makefile.in
alsa-lib-1.0.14/src/conf/pcm/dpl.conf
alsa-lib-1.0.14/src/conf/pcm/dmix.conf
alsa-lib-1.0.14/src/conf/pcm/iec958.conf
alsa-lib-1.0.14/src/conf/pcm/default.conf
alsa-lib-1.0.14/src/conf/pcm/modem.conf
alsa-lib-1.0.14/src/conf/pcm/Makefile.am
alsa-lib-1.0.14/src/conf/pcm/surround40.conf
alsa-lib-1.0.14/src/conf/pcm/front.conf
alsa-lib-1.0.14/src/conf/pcm/surround51.conf
alsa-lib-1.0.14/src/conf/pcm/side.conf
alsa-lib-1.0.14/src/conf/pcm/dsnoop.conf
alsa-lib-1.0.14/src/conf/Makefile.in
alsa-lib-1.0.14/src/conf/smixer.conf
alsa-lib-1.0.14/src/conf/cards/
alsa-lib-1.0.14/src/conf/cards/CA0106.conf
alsa-lib-1.0.14/src/conf/cards/RME9652.conf
alsa-lib-1.0.14/src/conf/cards/ICH.conf
alsa-lib-1.0.14/src/conf/cards/HDA-Intel.conf
alsa-lib-1.0.14/src/conf/cards/CMI8338.conf
alsa-lib-1.0.14/src/conf/cards/Maestro3.conf
alsa-lib-1.0.14/src/conf/cards/FM801.conf
alsa-lib-1.0.14/src/conf/cards/Aureon51.conf
alsa-lib-1.0.14/src/conf/cards/ENS1371.conf
alsa-lib-1.0.14/src/conf/cards/NFORCE.conf
alsa-lib-1.0.14/src/conf/cards/YMF744.conf
alsa-lib-1.0.14/src/conf/cards/PC-Speaker.conf
alsa-lib-1.0.14/src/conf/cards/Audigy.conf
alsa-lib-1.0.14/src/conf/cards/EMU10K1X.conf
alsa-lib-1.0.14/src/conf/cards/VXPocket.conf
alsa-lib-1.0.14/src/conf/cards/AACI.conf
alsa-lib-1.0.14/src/conf/cards/PMac.conf
alsa-lib-1.0.14/src/conf/cards/Makefile.in
alsa-lib-1.0.14/src/conf/cards/CS46xx.conf
alsa-lib-1.0.14/src/conf/cards/CMI8738-MC8.conf
alsa-lib-1.0.14/src/conf/cards/AU8820.conf
alsa-lib-1.0.14/src/conf/cards/ICH4.conf
alsa-lib-1.0.14/src/conf/cards/VIA686A.conf
alsa-lib-1.0.14/src/conf/cards/SI7018.conf
alsa-lib-1.0.14/src/conf/cards/PMacToonie.conf
alsa-lib-1.0.14/src/conf/cards/AU8810.conf
alsa-lib-1.0.14/src/conf/cards/aliases.conf
alsa-lib-1.0.14/src/conf/cards/GUS.conf
alsa-lib-1.0.14/src/conf/cards/RME9636.conf
alsa-lib-1.0.14/src/conf/cards/ICE1712.conf
alsa-lib-1.0.14/src/conf/cards/CMI8338-SWIEC.conf
alsa-lib-1.0.14/src/conf/cards/VX222.conf
alsa-lib-1.0.14/src/conf/cards/ES1968.conf
alsa-lib-1.0.14/src/conf/cards/aliases.alisp
alsa-lib-1.0.14/src/conf/cards/ATIIXP-SPDMA.conf
alsa-lib-1.0.14/src/conf/cards/AU8830.conf
alsa-lib-1.0.14/src/conf/cards/VIA8237.conf
alsa-lib-1.0.14/src/conf/cards/VXPocket440.conf
alsa-lib-1.0.14/src/conf/cards/ICH-MODEM.conf
alsa-lib-1.0.14/src/conf/cards/Makefile.am
alsa-lib-1.0.14/src/conf/cards/ENS1370.conf
alsa-lib-1.0.14/src/conf/cards/ATIIXP-MODEM.conf
alsa-lib-1.0.14/src/conf/cards/Audigy2.conf
alsa-lib-1.0.14/src/conf/cards/SI7018/
alsa-lib-1.0.14/src/conf/cards/SI7018/sndop-mixer.alisp
alsa-lib-1.0.14/src/conf/cards/SI7018/sndoc-mixer.alisp
alsa-lib-1.0.14/src/conf/cards/ATIIXP.conf
alsa-lib-1.0.14/src/conf/cards/ICE1724.conf
alsa-lib-1.0.14/src/conf/cards/Aureon71.conf
alsa-lib-1.0.14/src/conf/cards/USB-Audio.conf
alsa-lib-1.0.14/src/conf/cards/TRID4DWAVENX.conf
alsa-lib-1.0.14/src/conf/cards/CMI8738-MC6.conf
alsa-lib-1.0.14/src/conf/cards/EMU10K1.conf
alsa-lib-1.0.14/src/conf/cards/VIA8233A.conf
alsa-lib-1.0.14/src/conf/cards/VIA8233.conf
alsa-lib-1.0.14/src/conf/Makefile.am
alsa-lib-1.0.14/src/conf/sndo-mixer.alisp
alsa-lib-1.0.14/src/conf/alsa.conf
alsa-lib-1.0.14/src/Makefile.am
alsa-lib-1.0.14/src/Versions.in
alsa-lib-1.0.14/src/conf.c
alsa-lib-1.0.14/src/rawmidi/
alsa-lib-1.0.14/src/rawmidi/rawmidi_hw.c
alsa-lib-1.0.14/src/rawmidi/rawmidi.c
alsa-lib-1.0.14/src/rawmidi/Makefile.in
alsa-lib-1.0.14/src/rawmidi/rawmidi_symbols.c
alsa-lib-1.0.14/src/rawmidi/Makefile.am
alsa-lib-1.0.14/src/rawmidi/rawmidi_local.h
alsa-lib-1.0.14/src/rawmidi/rawmidi_virt.c
alsa-lib-1.0.14/src/compat/
alsa-lib-1.0.14/src/compat/hsearch_r.c
alsa-lib-1.0.14/src/compat/Makefile.in
alsa-lib-1.0.14/src/compat/empty.c
alsa-lib-1.0.14/src/compat/Makefile.am
alsa-lib-1.0.14/alsalisp/
alsa-lib-1.0.14/alsalisp/Makefile.in
alsa-lib-1.0.14/alsalisp/alsalisp.c
alsa-lib-1.0.14/alsalisp/Makefile.am
alsa-lib-1.0.14/utils/
alsa-lib-1.0.14/utils/buildrpm
alsa-lib-1.0.14/utils/alsa-lib.spec.in
alsa-lib-1.0.14/utils/alsa.m4
alsa-lib-1.0.14/utils/Makefile.in
alsa-lib-1.0.14/utils/Makefile.am
alsa-lib-1.0.14/utils/alsa.pc.in
alsa-lib-1.0.14/aserver/
alsa-lib-1.0.14/aserver/Makefile.in
alsa-lib-1.0.14/aserver/Makefile.am
alsa-lib-1.0.14/aserver/COPYING
alsa-lib-1.0.14/aserver/aserver.c
alsa-lib-1.0.14/Makefile.am
alsa-lib-1.0.14/modules/
alsa-lib-1.0.14/modules/Makefile.in
alsa-lib-1.0.14/modules/mixer/
alsa-lib-1.0.14/modules/mixer/simple/
alsa-lib-1.0.14/modules/mixer/simple/hda.c
alsa-lib-1.0.14/modules/mixer/simple/sbasedl.c
alsa-lib-1.0.14/modules/mixer/simple/Makefile.in
alsa-lib-1.0.14/modules/mixer/simple/ac97.c
alsa-lib-1.0.14/modules/mixer/simple/sbase.h
alsa-lib-1.0.14/modules/mixer/simple/sbase.c
alsa-lib-1.0.14/modules/mixer/simple/Makefile.am
alsa-lib-1.0.14/modules/mixer/Makefile.in
alsa-lib-1.0.14/modules/mixer/Makefile.am
alsa-lib-1.0.14/modules/Makefile.am
alsa-lib-1.0.14/aclocal.m4
alsa-lib-1.0.14/include/
alsa-lib-1.0.14/include/pcm_old.h
alsa-lib-1.0.14/include/seqmid.h
alsa-lib-1.0.14/include/asoundef.h
alsa-lib-1.0.14/include/mixer.h
alsa-lib-1.0.14/include/hwdep.h
alsa-lib-1.0.14/include/pcm_external.h
alsa-lib-1.0.14/include/sound/
alsa-lib-1.0.14/include/sound/sb16_csp.h
alsa-lib-1.0.14/include/sound/asoundef.h
alsa-lib-1.0.14/include/sound/type_compat.h
alsa-lib-1.0.14/include/sound/hdsp.h
alsa-lib-1.0.14/include/sound/ainstr_iw.h
alsa-lib-1.0.14/include/sound/Makefile.in
alsa-lib-1.0.14/include/sound/ainstr_fm.h
alsa-lib-1.0.14/include/sound/ainstr_gf1.h
alsa-lib-1.0.14/include/sound/asound_fm.h
alsa-lib-1.0.14/include/sound/ainstr_simple.h
alsa-lib-1.0.14/include/sound/emu10k1.h
alsa-lib-1.0.14/include/sound/Makefile.am
alsa-lib-1.0.14/include/sound/sscape_ioctl.h
alsa-lib-1.0.14/include/sound/asequencer.h
alsa-lib-1.0.14/include/sound/asound.h
alsa-lib-1.0.14/include/conv.h
alsa-lib-1.0.14/include/error.h
alsa-lib-1.0.14/include/output.h
alsa-lib-1.0.14/include/pcm.h
alsa-lib-1.0.14/include/search.h
alsa-lib-1.0.14/include/asoundlib.h
alsa-lib-1.0.14/include/iatomic.h
alsa-lib-1.0.14/include/seq_midi_event.h
alsa-lib-1.0.14/include/Makefile.in
alsa-lib-1.0.14/include/seq.h
alsa-lib-1.0.14/include/rawmidi.h
alsa-lib-1.0.14/include/global.h
alsa-lib-1.0.14/include/timer.h
alsa-lib-1.0.14/include/alisp.h
alsa-lib-1.0.14/include/seq_event.h
alsa-lib-1.0.14/include/alsa-symbols.h
alsa-lib-1.0.14/include/conf.h
alsa-lib-1.0.14/include/alsa
alsa-lib-1.0.14/include/mixer_abst.h
alsa-lib-1.0.14/include/instr.h
alsa-lib-1.0.14/include/pcm_plugin.h
alsa-lib-1.0.14/include/version.h
alsa-lib-1.0.14/include/Makefile.am
alsa-lib-1.0.14/include/control.h
alsa-lib-1.0.14/include/config.h.in
alsa-lib-1.0.14/include/local.h
alsa-lib-1.0.14/include/pcm_rate.h
alsa-lib-1.0.14/include/control_external.h
alsa-lib-1.0.14/include/input.h
alsa-lib-1.0.14/include/pcm_ioplug.h
alsa-lib-1.0.14/include/aserver.h
alsa-lib-1.0.14/include/list.h
alsa-lib-1.0.14/include/sys.h
alsa-lib-1.0.14/include/pcm_extplug.h
alsa-lib-1.0.14/COPYING
alsa-lib-1.0.14/missing
alsa-lib-1.0.14/install-sh
alsa-lib-1.0.14/config.sub
billym@billym-desktop:~$ tar -xvjf /home/billym/Desktop/alsa-utils-1.0.14.tar.bz2
alsa-utils-1.0.14/
alsa-utils-1.0.14/ABOUT-NLS
alsa-utils-1.0.14/ChangeLog
alsa-utils-1.0.14/depcomp
alsa-utils-1.0.14/speaker-test/
alsa-utils-1.0.14/speaker-test/readme.txt
alsa-utils-1.0.14/speaker-test/Makefile.in
alsa-utils-1.0.14/speaker-test/speaker-test.1
alsa-utils-1.0.14/speaker-test/Makefile.am
alsa-utils-1.0.14/speaker-test/pink.c
alsa-utils-1.0.14/speaker-test/speaker-test.c
alsa-utils-1.0.14/speaker-test/samples/
alsa-utils-1.0.14/speaker-test/samples/sample_map.csv
alsa-utils-1.0.14/speaker-test/samples/Makefile.in
alsa-utils-1.0.14/speaker-test/samples/Noise.wav
alsa-utils-1.0.14/speaker-test/samples/Side_Right.wav
alsa-utils-1.0.14/speaker-test/samples/Front_Left.wav
alsa-utils-1.0.14/speaker-test/samples/Front_Center.wav
alsa-utils-1.0.14/speaker-test/samples/Front_Right.wav
alsa-utils-1.0.14/speaker-test/samples/Rear_Center.wav
alsa-utils-1.0.14/speaker-test/samples/Rear_Left.wav
alsa-utils-1.0.14/speaker-test/samples/Side_Left.wav
alsa-utils-1.0.14/speaker-test/samples/Makefile.am
alsa-utils-1.0.14/speaker-test/samples/Rear_Right.wav
alsa-utils-1.0.14/speaker-test/pink.h
alsa-utils-1.0.14/alsaconf/
alsa-utils-1.0.14/alsaconf/alsaconf.in
alsa-utils-1.0.14/alsaconf/Makefile.in
alsa-utils-1.0.14/alsaconf/alsaconf.8
alsa-utils-1.0.14/alsaconf/po/
alsa-utils-1.0.14/alsaconf/po/Makefile.in
alsa-utils-1.0.14/alsaconf/po/ja.po
alsa-utils-1.0.14/alsaconf/po/ru.po
alsa-utils-1.0.14/alsaconf/Makefile.am
alsa-utils-1.0.14/alsaconf/alsaconf.fr.8
alsa-utils-1.0.14/mkinstalldirs
alsa-utils-1.0.14/TODO
alsa-utils-1.0.14/acinclude.m4
alsa-utils-1.0.14/configure.in
alsa-utils-1.0.14/seq/
alsa-utils-1.0.14/seq/aseqnet/
alsa-utils-1.0.14/seq/aseqnet/aseqnet.c
alsa-utils-1.0.14/seq/aseqnet/Makefile.in
alsa-utils-1.0.14/seq/aseqnet/aseqnet.1
alsa-utils-1.0.14/seq/aseqnet/Makefile.am
alsa-utils-1.0.14/seq/aseqnet/README.aseqnet
alsa-utils-1.0.14/seq/aplaymidi/
alsa-utils-1.0.14/seq/aplaymidi/aplaymidi.c
alsa-utils-1.0.14/seq/aplaymidi/Makefile.in
alsa-utils-1.0.14/seq/aplaymidi/arecordmidi.1
alsa-utils-1.0.14/seq/aplaymidi/Makefile.am
alsa-utils-1.0.14/seq/aplaymidi/arecordmidi.c
alsa-utils-1.0.14/seq/aplaymidi/aplaymidi.1
alsa-utils-1.0.14/seq/aconnect/
alsa-utils-1.0.14/seq/aconnect/aconnect.1
alsa-utils-1.0.14/seq/aconnect/Makefile.in
alsa-utils-1.0.14/seq/aconnect/README.aconnect
alsa-utils-1.0.14/seq/aconnect/Makefile.am
alsa-utils-1.0.14/seq/aconnect/aconnect.c
alsa-utils-1.0.14/seq/Makefile.in
alsa-utils-1.0.14/seq/aseqdump/
alsa-utils-1.0.14/seq/aseqdump/aseqdump.1
alsa-utils-1.0.14/seq/aseqdump/Makefile.in
alsa-utils-1.0.14/seq/aseqdump/Makefile.am
alsa-utils-1.0.14/seq/aseqdump/aseqdump.c
alsa-utils-1.0.14/seq/Makefile.am
alsa-utils-1.0.14/hgcompile
alsa-utils-1.0.14/INSTALL
alsa-utils-1.0.14/configure
alsa-utils-1.0.14/Makefile.in
alsa-utils-1.0.14/amixer/
alsa-utils-1.0.14/amixer/amixer.h
alsa-utils-1.0.14/amixer/amixer.c
alsa-utils-1.0.14/amixer/Makefile.in
alsa-utils-1.0.14/amixer/amixer.1
alsa-utils-1.0.14/amixer/Makefile.am
alsa-utils-1.0.14/amidi/
alsa-utils-1.0.14/amidi/amidi.c
alsa-utils-1.0.14/amidi/amidi.1
alsa-utils-1.0.14/amidi/Makefile.in
alsa-utils-1.0.14/amidi/Makefile.am
alsa-utils-1.0.14/config.guess
alsa-utils-1.0.14/m4/
alsa-utils-1.0.14/m4/gettext.m4
alsa-utils-1.0.14/m4/ulonglong.m4
alsa-utils-1.0.14/m4/xsize.m4
alsa-utils-1.0.14/m4/longdouble.m4
alsa-utils-1.0.14/m4/inttypes_h.m4
alsa-utils-1.0.14/m4/Makefile.in
alsa-utils-1.0.14/m4/lcmessage.m4
alsa-utils-1.0.14/m4/lib-link.m4
alsa-utils-1.0.14/m4/progtest.m4
alsa-utils-1.0.14/m4/inttypes-h.m4
alsa-utils-1.0.14/m4/signed.m4
alsa-utils-1.0.14/m4/lib-prefix.m4
alsa-utils-1.0.14/m4/glibc2.m4
alsa-utils-1.0.14/m4/longlong.m4
alsa-utils-1.0.14/m4/inttypes-pri.m4
alsa-utils-1.0.14/m4/stdint_h.m4
alsa-utils-1.0.14/m4/intdiv0.m4
alsa-utils-1.0.14/m4/wint_t.m4
alsa-utils-1.0.14/m4/uintmax_t.m4
alsa-utils-1.0.14/m4/glibc21.m4
alsa-utils-1.0.14/m4/lock.m4
alsa-utils-1.0.14/m4/wchar_t.m4
alsa-utils-1.0.14/m4/printf-posix.m4
alsa-utils-1.0.14/m4/lib-ld.m4
alsa-utils-1.0.14/m4/iconv.m4
alsa-utils-1.0.14/m4/Makefile.am
alsa-utils-1.0.14/m4/intmax.m4
alsa-utils-1.0.14/m4/po.m4
alsa-utils-1.0.14/m4/codeset.m4
alsa-utils-1.0.14/m4/nls.m4
alsa-utils-1.0.14/m4/size_max.m4
alsa-utils-1.0.14/m4/visibility.m4
alsa-utils-1.0.14/README
alsa-utils-1.0.14/config.rpath
alsa-utils-1.0.14/utils/
alsa-utils-1.0.14/utils/buildrpm
alsa-utils-1.0.14/utils/Makefile.in
alsa-utils-1.0.14/utils/alsa-utils.spec.in
alsa-utils-1.0.14/utils/Makefile.am
alsa-utils-1.0.14/po/
alsa-utils-1.0.14/po/en@quot.header
alsa-utils-1.0.14/po/alsa-utils.pot
alsa-utils-1.0.14/po/stamp-po
alsa-utils-1.0.14/po/boldquot.sed
alsa-utils-1.0.14/po/remove-potcdate.sin
alsa-utils-1.0.14/po/Makefile.in.in
alsa-utils-1.0.14/po/POTFILES.in
alsa-utils-1.0.14/po/ja.po
alsa-utils-1.0.14/po/Rules-quot
alsa-utils-1.0.14/po/quot.sed
alsa-utils-1.0.14/po/insert-header.sin
alsa-utils-1.0.14/po/en@boldquot.header
alsa-utils-1.0.14/po/Makevars
alsa-utils-1.0.14/po/LINGUAS
alsa-utils-1.0.14/po/ja.gmo
alsa-utils-1.0.14/aplay/
alsa-utils-1.0.14/aplay/arecord.1
alsa-utils-1.0.14/aplay/Makefile.in
alsa-utils-1.0.14/aplay/Makefile.am
alsa-utils-1.0.14/aplay/aplay.c
alsa-utils-1.0.14/aplay/aplay.1
alsa-utils-1.0.14/aplay/formats.h
alsa-utils-1.0.14/iecset/
alsa-utils-1.0.14/iecset/iecset.1
alsa-utils-1.0.14/iecset/Makefile.in
alsa-utils-1.0.14/iecset/Makefile.am
alsa-utils-1.0.14/iecset/iecset.c
alsa-utils-1.0.14/iecset/iecbits.c
alsa-utils-1.0.14/Makefile.am
alsa-utils-1.0.14/aclocal.m4
alsa-utils-1.0.14/include/
alsa-utils-1.0.14/include/Makefile.in
alsa-utils-1.0.14/include/gettext.h
alsa-utils-1.0.14/include/aconfig.h.in
alsa-utils-1.0.14/include/version.h
alsa-utils-1.0.14/include/Makefile.am
alsa-utils-1.0.14/COPYING
alsa-utils-1.0.14/alsactl/
alsa-utils-1.0.14/alsactl/alsactl.1
alsa-utils-1.0.14/alsactl/alsactl.c
alsa-utils-1.0.14/alsactl/Makefile.in
alsa-utils-1.0.14/alsactl/names.c
alsa-utils-1.0.14/alsactl/Makefile.am
alsa-utils-1.0.14/alsactl/state.c
alsa-utils-1.0.14/alsactl/alsactl.h
alsa-utils-1.0.14/alsamixer/
alsa-utils-1.0.14/alsamixer/alsamixer.1
alsa-utils-1.0.14/alsamixer/Makefile.in
alsa-utils-1.0.14/alsamixer/alsamixer.c
alsa-utils-1.0.14/alsamixer/README
alsa-utils-1.0.14/alsamixer/Makefile.am
alsa-utils-1.0.14/missing
alsa-utils-1.0.14/install-sh
alsa-utils-1.0.14/config.sub
billym@billym-desktop:~$ tar -xvjf /home/billym/Desktop/realtek-linux-audiopack-4.06b.tar.bz2
./realtek-linux-audiopack-4.06b/
./realtek-linux-audiopack-4.06b/Readme.txt
./realtek-linux-audiopack-4.06b/alsa-driver-rt20070820.tar.bz2
./realtek-linux-audiopack-4.06b/version
./realtek-linux-audiopack-4.06b/alsa-lib-1.0.14.tar.bz2
./realtek-linux-audiopack-4.06b/install
./realtek-linux-audiopack-4.06b/alsa-utils-1.0.14.tar.bz2
./realtek-linux-audiopack-4.06b/test.wav.bz2
billym@billym-desktop:~$ 

what nxt? still no sound

---

### Post by mali2297 on 2007-09-19
Alright, try to run the lines below in the terminal. This time, stop if you get an error and post the message.

```

sudo apt-get install build-essential ncurses-dev gettext
sudo apt-get install libncurses5-dev
sudo apt-get install linux-headers-'uname -r'
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp /home/billym/realtek-linux-audiopack-4.06b/alsa* .
sudo tar -xvjf alsa-driver-rt20070820.tar.bz2
sudo tar -xvjf alsa-lib-1.0.14.tar.bz2
sudo tar -xvjf alsa-utils-1.0.14.tar.bz2
cd alsa-driver*
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

```

If you manage to get through all of the above without any errors, **reboot**, and then post the output of this:
```

cat /proc/asound/card0/codec#* | grep Codec

```

---

### Post by maryjanua on 2007-09-19
heres everything it said didnt look like any errors (couple of warnings)
make[2]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14/aserver'
make[1]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14/aserver'
Making install in alsalisp
make[1]: Entering directory `/usr/src/alsa/alsa-lib-1.0.14/alsalisp'
make[2]: Entering directory `/usr/src/alsa/alsa-lib-1.0.14/alsalisp'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14/alsalisp'
make[1]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14/alsalisp'
Making install in test
make[1]: Entering directory `/usr/src/alsa/alsa-lib-1.0.14/test'
make[2]: Entering directory `/usr/src/alsa/alsa-lib-1.0.14/test'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14/test'
make[1]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14/test'
Making install in utils
make[1]: Entering directory `/usr/src/alsa/alsa-lib-1.0.14/utils'
make[2]: Entering directory `/usr/src/alsa/alsa-lib-1.0.14/utils'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/aclocal" || mkdir -p -- "/usr/share/aclocal"
 /usr/bin/install -c -m 644 'alsa.m4' '/usr/share/aclocal/alsa.m4'
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'alsa.pc' '/usr/lib/pkgconfig/alsa.pc'
make[2]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14/utils'
make[1]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14/utils'
make[1]: Entering directory `/usr/src/alsa/alsa-lib-1.0.14'
make[2]: Entering directory `/usr/src/alsa/alsa-lib-1.0.14'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14'
make[1]: Leaving directory `/usr/src/alsa/alsa-lib-1.0.14'
billym@billym-desktop:/usr/src/alsa/alsa-lib-1.0.14$ cd ../alsa-utils*
billym@billym-desktop:/usr/src/alsa/alsa-utils-1.0.14$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating alsactl/Makefile
config.status: creating alsamixer/Makefile
config.status: creating amidi/Makefile
config.status: creating amixer/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating alsaconf/alsaconf
config.status: creating alsaconf/Makefile
config.status: creating alsaconf/po/Makefile
config.status: WARNING:  alsaconf/po/Makefile.in seems to ignore the --datarootdir setting
config.status: creating aplay/Makefile
config.status: creating include/Makefile
config.status: creating iecset/Makefile
config.status: creating utils/Makefile
config.status: creating utils/alsa-utils.spec
config.status: creating seq/Makefile
config.status: creating seq/aconnect/Makefile
config.status: creating seq/aplaymidi/Makefile
config.status: creating seq/aseqdump/Makefile
config.status: creating seq/aseqnet/Makefile
config.status: creating speaker-test/Makefile
config.status: creating speaker-test/samples/Makefile
config.status: creating include/aconfig.h
config.status: executing po-directories commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
config.status: executing depfiles commands
billym@billym-desktop:/usr/src/alsa/alsa-utils-1.0.14$ sudo make
Making all in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/include'
make  all-am
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/include'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/include'
Making all in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
        then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
        then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT names.o -MD -MP -MF ".deps/names.Tpo" -c -o names.o names.c; \
        then mv -f ".deps/names.Tpo" ".deps/names.Po"; else rm -f ".deps/names.Tpo"; exit 1; fi
gcc  -g -O2   -o alsactl  alsactl.o state.o names.o  -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
Making all in alsaconf
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
Making all in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf/po'
35 translated messages, 1 untranslated message.
34 translated messages, 1 fuzzy translation, 1 untranslated message.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf/po'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
Making all in alsamixer
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsamixer.o -MD -MP -MF ".deps/alsamixer.Tpo" -c -o alsamixer.o alsamixer.c; \
        then mv -f ".deps/alsamixer.Tpo" ".deps/alsamixer.Po"; else rm -f ".deps/alsamixer.Tpo"; exit 1; fi
gcc  -g -O2   -o alsamixer  alsamixer.o -lncurses -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
Making all in amidi
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/amidi'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amidi.o -MD -MP -MF ".deps/amidi.Tpo" -c -o amidi.o amidi.c; \
        then mv -f ".deps/amidi.Tpo" ".deps/amidi.Po"; else rm -f ".deps/amidi.Tpo"; exit 1; fi
gcc  -g -O2   -o amidi  amidi.o  -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/amidi'
Making all in amixer
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/amixer'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT amixer.o -MD -MP -MF ".deps/amixer.Tpo" -c -o amixer.o amixer.c; \
        then mv -f ".deps/amixer.Tpo" ".deps/amixer.Po"; else rm -f ".deps/amixer.Tpo"; exit 1; fi
gcc  -g -O2   -o amixer  amixer.o -lm -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/amixer'
Making all in aplay
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT aplay.o -MD -MP -MF ".deps/aplay.Tpo" -c -o aplay.o aplay.c; \
        then mv -f ".deps/aplay.Tpo" ".deps/aplay.Po"; else rm -f ".deps/aplay.Tpo"; exit 1; fi
gcc  -g -O2   -o aplay  aplay.o -lasound  -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
Making all in iecset
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/iecset'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecset.o -MD -MP -MF ".deps/iecset.Tpo" -c -o iecset.o iecset.c; \
        then mv -f ".deps/iecset.Tpo" ".deps/iecset.Po"; else rm -f ".deps/iecset.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT iecbits.o -MD -MP -MF ".deps/iecbits.Tpo" -c -o iecbits.o iecbits.c; \
        then mv -f ".deps/iecbits.Tpo" ".deps/iecbits.Po"; else rm -f ".deps/iecbits.Tpo"; exit 1; fi
gcc  -g -O2   -o iecset  iecset.o iecbits.o -lm -lasound -lm -ldl -lpthread
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/iecset'
Making all in seq
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
Making all in aconnect
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aconnect.o -MD -MP -MF ".deps/aconnect.Tpo" -c -o aconnect.o aconnect.c; \
        then mv -f ".deps/aconnect.Tpo" ".deps/aconnect.Po"; else rm -f ".deps/aconnect.Tpo"; exit 1; fi
gcc  -g -O2   -o aconnect  aconnect.o  -lasound -lm -ldl -lpthread
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
Making all in aplaymidi
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aplaymidi.o -MD -MP -MF ".deps/aplaymidi.Tpo" -c -o aplaymidi.o aplaymidi.c; \
        then mv -f ".deps/aplaymidi.Tpo" ".deps/aplaymidi.Po"; else rm -f ".deps/aplaymidi.Tpo"; exit 1; fi
gcc  -g -O2   -o aplaymidi  aplaymidi.o  -lasound -lm -ldl -lpthread
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT arecordmidi.o -MD -MP -MF ".deps/arecordmidi.Tpo" -c -o arecordmidi.o arecordmidi.c; \
        then mv -f ".deps/arecordmidi.Tpo" ".deps/arecordmidi.Po"; else rm -f ".deps/arecordmidi.Tpo"; exit 1; fi
gcc  -g -O2   -o arecordmidi  arecordmidi.o  -lasound -lm -ldl -lpthread
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
Making all in aseqdump
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqdump.o -MD -MP -MF ".deps/aseqdump.Tpo" -c -o aseqdump.o aseqdump.c; \
        then mv -f ".deps/aseqdump.Tpo" ".deps/aseqdump.Po"; else rm -f ".deps/aseqdump.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqdump  aseqdump.o  -lasound -lm -ldl -lpthread
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
Making all in aseqnet
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT aseqnet.o -MD -MP -MF ".deps/aseqnet.Tpo" -c -o aseqnet.o aseqnet.c; \
        then mv -f ".deps/aseqnet.Tpo" ".deps/aseqnet.Po"; else rm -f ".deps/aseqnet.Tpo"; exit 1; fi
gcc  -g -O2   -o aseqnet  aseqnet.o  -lasound -lm -ldl -lpthread
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
Making all in speaker-test
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
Making all in samples
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT speaker-test.o -MD -MP -MF ".deps/speaker-test.Tpo" -c -o speaker-test.o speaker-test.c; \
        then mv -f ".deps/speaker-test.Tpo" ".deps/speaker-test.Po"; else rm -f ".deps/speaker-test.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT pink.o -MD -MP -MF ".deps/pink.Tpo" -c -o pink.o pink.c; \
        then mv -f ".deps/pink.Tpo" ".deps/pink.Po"; else rm -f ".deps/pink.Tpo"; exit 1; fi
gcc  -g -O2   -o speaker-test  speaker-test.o pink.o  -lasound -lm -ldl -lpthread
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
Making all in utils
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/utils'
Making all in m4
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/m4'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/m4'
Making all in po
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/po'
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14'
billym@billym-desktop:/usr/src/alsa/alsa-utils-1.0.14$ sudo make install
Making install in include
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/include'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/include'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/include'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/include'
Making install in alsactl
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
  /usr/bin/install -c 'alsactl' '/usr/sbin/alsactl'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsactl.1' '/usr/share/man/man1/alsactl.1'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsactl'
Making install in alsaconf
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
Making install in po
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf/po'
mkdir -p -- /usr/share
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf/po'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
test -z "/usr/sbin" || mkdir -p -- "/usr/sbin"
 /usr/bin/install -c 'alsaconf' '/usr/sbin/alsaconf'
 /usr/bin/install -c -m 644 alsaconf.8 /usr/share/man/man8/alsaconf.8
 /usr/bin/install -c -m 644 alsaconf.fr.8 /usr/share/man/fr/man8/alsaconf.8
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsaconf'
Making install in alsamixer
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'alsamixer' '/usr/bin/alsamixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './alsamixer.1' '/usr/share/man/man1/alsamixer.1'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/alsamixer'
Making install in amidi
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/amidi'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/amidi'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amidi' '/usr/bin/amidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amidi.1' '/usr/share/man/man1/amidi.1'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/amidi'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/amidi'
Making install in amixer
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/amixer'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/amixer'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'amixer' '/usr/bin/amixer'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './amixer.1' '/usr/share/man/man1/amixer.1'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/amixer'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/amixer'
Making install in aplay
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplay' '/usr/bin/aplay'
make  install-exec-hook
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
rm -f arecord
ln -s aplay arecord
rm -f /usr/bin/arecord
(cd /usr/bin && ln -s aplay arecord)
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplay.1' '/usr/share/man/man1/aplay.1'
 /usr/bin/install -c -m 644 './arecord.1' '/usr/share/man/man1/arecord.1'
make  install-data-hook
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
rm -f /usr/share/man/man1/arecord.1
(cd /usr/share/man/man1 && ln -s aplay.1 arecord.1)
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/aplay'
Making install in iecset
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/iecset'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/iecset'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'iecset' '/usr/bin/iecset'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './iecset.1' '/usr/share/man/man1/iecset.1'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/iecset'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/iecset'
Making install in seq
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
Making install in aconnect
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aconnect' '/usr/bin/aconnect'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aconnect.1' '/usr/share/man/man1/aconnect.1'
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aconnect'
Making install in aplaymidi
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aplaymidi' '/usr/bin/aplaymidi'
  /usr/bin/install -c 'arecordmidi' '/usr/bin/arecordmidi'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aplaymidi.1' '/usr/share/man/man1/aplaymidi.1'
 /usr/bin/install -c -m 644 './arecordmidi.1' '/usr/share/man/man1/arecordmidi.1'
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aplaymidi'
Making install in aseqdump
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqdump' '/usr/bin/aseqdump'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqdump.1' '/usr/share/man/man1/aseqdump.1'
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqdump'
Making install in aseqnet
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'aseqnet' '/usr/bin/aseqnet'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './aseqnet.1' '/usr/share/man/man1/aseqnet.1'
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq/aseqnet'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/seq'
Making install in speaker-test
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
Making install in samples
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/share/alsa/speaker-test" || mkdir -p -- "/usr/share/alsa/speaker-test"
 /usr/bin/install -c -m 644 'sample_map.csv' '/usr/share/alsa/speaker-test/sample_map.csv'
test -z "/usr/share/sounds/alsa" || mkdir -p -- "/usr/share/sounds/alsa"
 /usr/bin/install -c -m 644 'Front_Left.wav' '/usr/share/sounds/alsa/Front_Left.wav'
 /usr/bin/install -c -m 644 'Rear_Center.wav' '/usr/share/sounds/alsa/Rear_Center.wav'
 /usr/bin/install -c -m 644 'Rear_Right.wav' '/usr/share/sounds/alsa/Rear_Right.wav'
 /usr/bin/install -c -m 644 'Side_Right.wav' '/usr/share/sounds/alsa/Side_Right.wav'
 /usr/bin/install -c -m 644 'Front_Center.wav' '/usr/share/sounds/alsa/Front_Center.wav'
 /usr/bin/install -c -m 644 'Front_Right.wav' '/usr/share/sounds/alsa/Front_Right.wav'
 /usr/bin/install -c -m 644 'Noise.wav' '/usr/share/sounds/alsa/Noise.wav'
 /usr/bin/install -c -m 644 'Rear_Left.wav' '/usr/share/sounds/alsa/Rear_Left.wav'
 /usr/bin/install -c -m 644 'Side_Left.wav' '/usr/share/sounds/alsa/Side_Left.wav'
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test/samples'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
make[3]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /usr/bin/install -c 'speaker-test' '/usr/bin/speaker-test'
test -z "/usr/share/man/man1" || mkdir -p -- "/usr/share/man/man1"
 /usr/bin/install -c -m 644 './speaker-test.1' '/usr/share/man/man1/speaker-test.1'
make[3]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/speaker-test'
Making install in utils
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/utils'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/utils'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/utils'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/utils'
Making install in m4
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/m4'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/m4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/m4'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/m4'
Making install in po
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14/po'
mkdir -p -- /usr/share
installing ja.gmo as /usr/share/locale/ja/LC_MESSAGES/alsa-utils.mo
if test "alsa-utils" = "gettext-tools"; then \
          mkdir -p -- /usr/share/gettext/po; \
          for file in Makefile.in.in remove-potcdate.sin quot.sed boldquot.sed [email]en@quot.head[/email]er [email]en@boldquot.head[/email]er insert-header.sin Rules-quot   Makevars.template; do \
            /usr/bin/install -c -m 644 ./$file \
                            /usr/share/gettext/po/$file; \
          done; \
          for file in Makevars; do \
            rm -f /usr/share/gettext/po/$file; \
          done; \
        else \
          : ; \
        fi
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14/po'
make[1]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14'
make[2]: Entering directory `/usr/src/alsa/alsa-utils-1.0.14'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14'
make[1]: Leaving directory `/usr/src/alsa/alsa-utils-1.0.14'
billym@billym-desktop:/usr/src/alsa/alsa-utils-1.0.14$ 

rebooting now

---

### Post by maryjanua on 2007-09-19
i have sound again :guitar: :) thank you very much mali.
=D>=D>=D>=D

did that last command and tada! theres my sound driver
billym@billym-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
billym@billym-desktop:~$ 

u are the man \\:D/

---

### Post by Vadi on 2007-09-19
=D>=D>=D>

Nice!!

Now maybe you can go help all other people who had problems with the card?

By the way, you just compiled your own drivers, heh.

---

### Post by mali2297 on 2007-09-19
> **maryjanua said:**
> i have sound again :guitar: :) thank you very much mali.
=D>=D>=D>=D

did that last command and tada! theres my sound driver
billym@billym-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
billym@billym-desktop:~$ 

u are the man \\:D/

OK, but I wasn't finished... :-(
I was planning to lead you through *Manually Specify Module Parameters* in the Howto.

Oh, well. If it's working, let us leave it with that and hope it will last this time. I guess I have to find something else to do. :-k

---

### Post by maryjanua on 2007-09-19
compiled my own drivers? as in write my own software?
wow im amazed.
 iv put a link onto this thread for other folk to see in the launchpad bugs section

your help has been invaluable too vadi thanks very much:KS:)
i think i'll go and look at the linux commands site for a while and actually learn about what i'm doing
itl be byebye windos soon now linux is all up and runnin

---

### Post by maryjanua on 2007-09-19
no mali by all means teach me more!! lol
iv rebooted a few times to make sure it works and it all seems fine

---

### Post by maryjanua on 2007-09-20
aha

---

### Post by berrydfu on 2008-04-24
I have a MSI P6NGM motherboard which has a Realtek ALC888 integrated sound which I cannot get to work. I have installed Ubuntu 7.10 and I tried mali2297's solution however when I get to this step this is the error I receive. Has ncurses-dev been replaced by another program? What do I need to do in order to get sound. Need some help I have just started experimenting with Linux.


kyle@Ubuntu:~$ sudo apt-get install build-essential ncurses-dev gettext
[sudo] password for kyle:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ncurses-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ncurses-dev has no installation candidate

---

### Post by Vadi on 2008-04-24
Hm. Try "libncurses5-dev" instead.

---

### Post by mali2297 on 2008-04-24
> **berrydfu said:**
> I have a MSI P6NGM motherboard which has a Realtek ALC888 integrated sound which I cannot get to work. I have installed Ubuntu 7.10 and I tried mali2297's solution however when I get to this step this is the error I receive. Has ncurses-dev been replaced by another program? What do I need to do in order to get sound. Need some help I have just started experimenting with Linux.


Since Ubuntu 8.04 now is available, my first suggestion is to upgrade to this latest version.

If I remember correctly, maryjanua's sound card worked out of the box when s/he upgraded from 7.04 to 7.10.

---

### Post by berrydfu on 2008-04-24
After trying libnurses5-dev as instructed by Vadi I receive this result. I am now going to install Ubuntu 8.04 Hardy Heron hopefully it will give me sound.


kyle@Ubuntu:~$ sudo apt-get install build-essential libncurses5-dev gettext[sudo] password for kyle:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libncurses5-dev
kyle@Ubuntu:~$

---

### Post by mali2297 on 2008-04-25
If you reencounter the problem with missing packages, open Synaptic, enable all repositories (via Settings -> Repositories) and use the search function.

---

### Post by berrydfu on 2008-04-26
I installed 8.04 and when I booted it up my sound worked perfectly. Thanks a lot for the help. However, now I can't set my screen resolution to anything but 800x600 or 640x480. I have a 1920x1200 monitor and would really like to have that resolution.  I downloaded Envyng and tried to have it automatically set up my video card but it didn't work. It gave an error stating it couldn't recognize my video card. What do I need to do in order to fix my resolution. I didn't have this problem with 7.10. Any help would be greatly appreciated.

---

### Post by berrydfu on 2008-04-27
> **berrydfu said:**
> I installed 8.04 and when I booted it up my sound worked perfectly. Thanks a lot for the help. However, now I can't set my screen resolution to anything but 800x600 or 640x480. I have a 1920x1200 monitor and would really like to have that resolution.  I downloaded Envyng and tried to have it automatically set up my video card but it didn't work. It gave an error stating it couldn't recognize my video card. What do I need to do in order to fix my resolution. I didn't have this problem with 7.10. Any help would be greatly appreciated.

Well I got it fixed on my own. I just needed to go to system -> administration -> hardware drivers and it downloaded the correct driver for me.

---

