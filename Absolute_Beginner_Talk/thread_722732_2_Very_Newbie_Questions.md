---
title: "2 Very Newbie Questions"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Literati on 2008-03-12
First off, I'm trying to install Firefox 3 Beta 4 onto Gutsy. Now, being as this is my first foray into Ubuntu, I can't seem to figure out how to install it! :D

I've downloaded the .tar.bz2 file onto my desktop, and even extracted it onto my desktop. Then, I opened Synaptic Package Manager, and went to Firefox, but it won't bring me anywhere where I can tell it "Install This" sort of thing. Help?

Secondly, I don't have any sound! :D I use Altec Lansing speakers (5 of them) and I can't seem to get any sound out of the damn things.

Thanks in advance. :)

---

### Post by Joeb454 on 2008-03-12
You just need to run Firefox 3 Beta 4 straight from the extracted folder on your desktop :)

---

### Post by Nepherte on 2008-03-12
After extracting the tar.bz2 file, simply launch the firefox file.

Using synaptic manager is a whole different way to install software. When using synaptic, just choose the packages you want to install. Synaptic will download them for you and install them.

---

### Post by PeterJS on 2008-03-12
On the firefox front the reason you can't find an option in synaptic for install this random thing, is that that's not how synaptic works. Synaptic installs things from the package repository, if you're looking to install stand alone packages from all over the internet you want to get them in .deb package format. 

As for installing FF3B4, you're best bet is putting it someplace out of the way, sticking it in your home directory is easy, but not necessariliy out of the way, or you could put in in /opt/ which is out of the way but then you have to deal with privilage escalation as /opt/ is owned by root. The way I have FF3B4 set up is I extracted the tarball in to my home directory, renamed the firefox folder to firefox3b4 (so I could tell it a part from beta3 and beta2 before that). Once you have chosen where you want to put the beta, you'll want to create a symlink between where you unpacked it and a standard location the system will know to look for it.
```

sudo ln -s /home/USERNAME/firefox-3.0b4/firefox /usr/local/bin/firefox-3.0

```
or
```

sudo ln -s /opt/firefox-3.0b4/firefox /usr/local/bin/firefox-3.0

```
Depending on where you un packed the beta to.

---

### Post by Literati on 2008-03-12
Okay, thank you all for the help on "installing" Firefox
This is all very foreign to me, but I'm eager to learn. And it just seemed...odd, to not have an EXE that I need to play with in order to install something! :D It's just...working :D

Can anyone help me with my sound issue?

Also, I have a third question, I'm using a Microsoft Wireless Laser Mouse 5000, and it has 5 buttons

On windows, it worked like this:

Very Left Button: Back (On Browsers)
Left Click: Select (Regular left click)
Scroll Button: New Tab (Firefox)
Right Click: Menu (Regular Right Click)
Very Right Button: Double Click

Now, Left Click, Scroll Click, and Right click are doing as they should. But my Very Left Click is posting URLs... and my very right click is acting like a regular right click.

How do I tell the mouse and computer that I want the very left click to be a "BACK" button (I don't much care for the double click, but it'd be nice too)

---

### Post by handydan918 on 2008-03-12
Re: Sound
Gonna need some system info. open a terminal and do ```
lspci
``` and ```
lsmod | grep snd
```
Then copy and paste the output back here.

---

### Post by Literati on 2008-03-12
matt@Matt:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
02:0b.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
02:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
02:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
matt@Matt:~$ lsmod | grep snd
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           137248  2 snd_emu10k1_synth
snd_intel8x0           34972  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_ac97_codec        100644  2 snd_emu10k1,snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_midi            9600  0 
snd_pcm                80388  4 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  16 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_seq_oss,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  3 snd_emu10k1,snd_intel8x0,snd_pcm

---
I know you're looking for sound and mouse, but if you can see anything in there that looks like it need UPGRADING, then I'm sort of upgrading my computer piece by piece, and if you could point something out, I'd appreciate it :) 

Ooh, and since my Video Card is listed there (Radeon 9600) why do I get "The Composite extension is not available" error when trying to enable ANY visual effects? I can't even put Normal ones.

Thanks again for all the help :)

EDIT: I remember hearing of a great media player back when I was thinking of switching to Ubuntu, it started with an A, something like Amarok or something. I'll search around, and might find it in the meantime, but if someone could just tell me the name, it'd be appreciated :)

---

### Post by handydan918 on 2008-03-12
looks like you have a soundblaster and an intel audio chip. You may need to go into the BIOS and disable the on-board sound. If the sound doesn't just work on reboot, try ```
sudo alsaconf
```

---

### Post by Tatty on 2008-03-12
> **Literati said:**
> 
Ooh, and since my Video Card is listed there (Radeon 9600) why do I get "The Composite extension is not available" error when trying to enable ANY visual effects? I can't even put Normal ones.

Have you got the proprietry drivers enabled?  Go to System->Administration->Restricted Drivers Manager and enable any drivers which it suggests.

---

### Post by Literati on 2008-03-12
> **Tatty said:**
> Have you got the proprietry drivers enabled?  Go to System->Administration->Restricted Drivers Manager and enable any drivers which it suggests.

I do. That was the first thing I did...
Any suggestions?

And HandyDan, I'm going to do that right this second. Give me a moment :)

---

### Post by Tatty on 2008-03-12
> **Literati said:**
> I do. That was the first thing I did...
Any suggestions?


ok, in that case make sure you have the following lines in your xorg.conf file

```
Section "Extensions"
        Option  "Composite" "enable"
EndSection

```

**EDIT:** i put disable by mistake at first, so make sure you get it right ;)

---

### Post by Literati on 2008-03-12
> **handydan918 said:**
> looks like you have a soundblaster and an intel audio chip. You may need to go into the BIOS and disable the on-board sound. If the sound doesn't just work on reboot, try ```
sudo alsaconf
```

So, I went into the BIOS, and I couldn't find anything talking about Audio Controllers, or anything with that model number... :|

So I tried your other suggestion and got this:

matt@Matt:~$ sudo alsaconf
[sudo] password for matt:
sudo: alsaconf: command not found

:(

---

### Post by Literati on 2008-03-12
> **Tatty said:**
> ok, in that case make sure you have the following lines in your xorg.conf file

```
Section "Extensions"
        Option  "Composite" "enable"
EndSection

```

**EDIT:** i put disable by mistake at first, so make sure you get it right ;)

Okay, it was set as

Section "Extensions"
            Option "Composite" O
EndSection

So I enabled it, and saved it, I'll go try the effects again :) Hope it works!

EDIT: No dice. :(
EDIT2: I just came back from a reset, and tried agian. This time, instead of giving me a composite error, it said simply: 

Desktop Effects Could Not Be Enabled.

---

### Post by Literati on 2008-03-12
Sorry, but I have another 2 questions (along with the ones I've already asked)

You guys might slap me, for being so dumb. 
But I'm trying to open a BitTorrent application, Transmission.
Now, it's asking me whee I've saved it, but I can't remember. And I see no where that tells me exactly where it is saved. How do I find the thing? :(

---

### Post by handydan918 on 2008-03-12
> **Literati said:**
> So, I went into the BIOS, and I couldn't find anything talking about Audio Controllers, or anything with that model number... :|
Hmmpph. OK.> 
So I tried your other suggestion and got this:

matt@Matt:~$ sudo alsaconf
[sudo] password for matt:
sudo: alsaconf: command not found

:(
```
sudo apt-get install alsaconf
```
Unless there is a better way to configure sound cards in gnome. I'm mostly a KDE guy...

---

### Post by Literati on 2008-03-13
> **handydan918 said:**
> Hmmpph. OK.
```
sudo apt-get install alsaconf
```
Unless there is a better way to configure sound cards in gnome. I'm mostly a KDE guy...

matt@Matt:~$ sudo apt-get install alsaconf
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsaconf

Wow. I must be doing something wrong. 
:(

---

### Post by scragar on 2008-03-13
w0w, I've had no sound for so long, just tried:
```
sudo apt-get install asoundconf-gtk && asoundconf-gtk
``` then picked my sound card in the box and suddenly it all works, go figure.

---

### Post by Literati on 2008-03-13
> **scragar said:**
> w0w, I've had no sound for so long, just tried:
```
sudo apt-get install asoundconf-gtk && asoundconf-gtk
``` then picked my sound card in the box and suddenly it all works, go figure.

I'm floored. 
That worked! :D
Thank you both! :)

Now, would anyone be able to still help with my other two questions?

Where do I find Transmission? Or, how do I search for it? Is there a default "install" directory of sorts?

And as for my Visual Effects, any ideas?

---

### Post by PeterJS on 2008-03-13
For the desktop effects try this:
[https://help.ubuntu.com/community/CompositeManager/Xgl/simple](https://help.ubuntu.com/community/CompositeManager/Xgl/simple)

And to install transmission, open up synaptic package manager (System > Administration > Synaptic Package Manager), and search for transmission, if you find it right click on it in the right pane and select mark for installation, and then apply. For good measure, THE guide to installing stuff:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

As to where things are installed, that depends on what they are. Unlike in windows where files are organized according to what program they belong to, under linux they are organized according to function, all of the essential (for booting) programs are in bin, the vast majority of programs are in /usr/bin, shared libraries are in /usr/lib/, art, icons, themes, documentation, and other non-executable stuff is in /usr/share. Here's the full description of what's where and why:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by Literati on 2008-03-13
Thank you VERY much for all the help Peter :) 
That worked perfectly (And the effects are very nice :P) 
I'll keep in mind that most programs are installed into /usr/bin That helps me a lot :) 
Also, thanks for the guide! I've bookmarked it!

Thank you all for your help, you've been very understanding and helpful! :)

---

