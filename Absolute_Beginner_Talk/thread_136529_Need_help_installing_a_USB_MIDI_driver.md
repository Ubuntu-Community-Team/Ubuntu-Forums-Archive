---
title: "Need help installing a USB MIDI driver"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by hovmod on 2006-02-26
Hi again - 

I have successfully followed a lot of detailed instructions and have managed to set up my system pretty well, I think.

The missing ingredient now is my MIDI keyboard, which is connected to a MIDISport 2x2 device.

This page: 
[http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html](http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html) 
has a driver, but I'm too much of a newb to dare install it. I think I've downloaded the tar file, but can't tell... :)

Please, someone, help me with *detailed* instructions, install the USBMidi driver...

Thanks.

---

### Post by Pragmatist on 2006-02-28
First, is your device one of the supported devices listed on the website you sent us??

If it is, then you download the tar.gz file.  If you don't know if you downloaded it or not, check your home directory.  If it isn't there you could try this: ```
sudo updatedb
``` then ```
locate usbmidi-20040829.tar.gz
```  If no file is found, you didn't download it.  Download it again and make a note of where your saving the file.  Then, go into the directory where the file is saved and type: ```
tar xvzf usbmidi-20040829.tar.gz
```  The tar.gz file is like a zip file.  It is just compressed.  The above command decompresses it.  Now there should be a directory named usbmidi or something similar.  It will be a subdirectory to the directory you typed the above commands. change to this new directory using the ```
cd
``` command and the name of the new directory: ```
cd <name directory>
```  Now there should be files named README and INSTALL.  Read them and follow the directions.  Usually, you do the following:

1. ./configure
2. make
3. sudo make install

But read the instructions first.  After you do that, if you need more help we'll take it from there.

---

### Post by hovmod on 2006-03-01
Thank you. I already tried that, and got several errors. The README says 'if you meet any errors, fix it' - which isn't all that helpful at my level... :)

---

### Post by Pragmatist on 2006-03-01
At which stage do the errors happen: during** ./configure**, during **make **or during **make install** ??

Finally, send us the errors (just cut the contents of your terminal screen and paste them here)

Often the errors look scary and complicated even when they are simple and easy.  Frequently there is just a library or other dependency required and all that is necessary is to install it.  However, we can't help unless we know what the error(s) are.

---

### Post by hovmod on 2006-03-02
OK, thank you. 

I have "moved on" from one USB to MIDI driver to another - the PODxt can thruput MIDI, so if I install the POD I can use that instead of putting unsupported firmware in my Midiman unit.

Of course, I didn't get the POD driver to work either. :)

The driver and info is here: [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)

and this is what flashes by in the terminal window when I try to make install: 

> tormod@tormodc:~/Download/Line6/line6usb-0.6.1$ sudo make install
make -C /lib/modules/2.6.12-50preempt/build SUBDIRS=/home/tormod/Download/Line6/line6usb-0.6.1 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.12'
Building modules, stage 2.
MODPOST
*** Warning: "__mulsf3" [/home/tormod/Download/Line6/line6usb-0.6.1/line6usb.ko] undefined!
*** Warning: "__ltsf2" [/home/tormod/Download/Line6/line6usb-0.6.1/line6usb.ko] undefined!
*** Warning: "__floatsisf" [/home/tormod/Download/Line6/line6usb-0.6.1/line6usb.ko] undefined!
*** Warning: "__fixdfsi" [/home/tormod/Download/Line6/line6usb-0.6.1/line6usb.ko] undefined!
*** Warning: "__adddf3" [/home/tormod/Download/Line6/line6usb-0.6.1/line6usb.ko] undefined!
*** Warning: "__extendsfdf2" [/home/tormod/Download/Line6/line6usb-0.6.1/line6usb.ko] undefined!
*** Warning: "__subsf3" [/home/tormod/Download/Line6/line6usb-0.6.1/line6usb.ko] undefined!
*** Warning: "__fixsfsi" [/home/tormod/Download/Line6/line6usb-0.6.1/line6usb.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
mkdir -p /lib/modules/2.6.12-50preempt/kernel/sound/usb
cp line6usb.ko /lib/modules/2.6.12-50preempt/kernel/sound/usb
mkdir -p /usr/bin/bin
cp *.sh *.pl /usr/bin
depmod -a
modprobe line6usb
FATAL: Error inserting line6usb (/lib/modules/2.6.12-50preempt/kernel/sound/usb/line6usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1


As you can see, it stops at the line6usb.ko file, but the file is there. I read the DMESG file, and there was a whole bunch of lines about the line6usb thing, but I couldn't make much sense of it. I'm sure you can, but I'd have to get home (I'm at work right now) to copy that for you.

Can you see what I'm doing wrong? Should I move something, install something? 

I appreciate your time and effort helping me. :)

---

### Post by Pragmatist on 2006-03-02
Yeah, definitely send the dmesg output lines relating to line6usb
Also, give output of: **uname -r**

Incidentally, it probably doesn't matter for this problem, but typically one doesn't make subdirectories to root (like /Download)  You would usually either make that directory under your home directory (like /home/username/Download) or, the most standard thing is to install "userland" programs at /usr/local  Everything else being equal it is better to do things this way, since many of the scripts, especially install scripts, assume these locations by default.  You could easily edit the scripts and type in different locations.  In fact, sometimes this kind of editing is necessary when you compile your own software (which is why reading the README and INSTALL files is so important).  But I'm lazy and I would just prefer things to work most of the time without my having to do anything special.
You can read more about these filesystem standards at: 

[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html)

---

### Post by hovmod on 2006-03-02
uname -r gives 2.6.12-50preempt 
(because I've done a few things recommended in a 'how to set up linux for music' document)

the dmesg file doesn't have entries on line6usb today, even after I try 'make install' or 'modprobe line6usb'.

Hmm... Maybe I should install a distro where this stuff is known to work...?

---

### Post by Pragmatist on 2006-03-02
Using an RPM-based distro will be easier since this particular software has RPMs  Of course, using a music distro could be even easier. I know when I was doing music I used CCRMA from Stanford U.  and I tried ReMudi and DeMudi  

That is not to say that you can't do it with a debian distro.  It just will take some more time.  In fact, if your not in a hurry, you'll gain from the experience as you will probably have to install some software from source at some point in the future on any distro that you use.

Try:
```
cat /var/log/dmesg* | grep line6usb
```

---

### Post by hovmod on 2006-03-02
Grep couldn't find more instances of "line6usb" than I could with my own eyes... :)

I appreciate your thoughts. I tried running the RPM, and it seemed to do *something* (lots of stuff in the terminal window), except it obviously didn't install the driver :)

I was half joking when I said I should switch to another distro... Like you say, anything I do is another thing learned. I was just hoping I could intersperse those bouts of OS-tweaks and learning with some actual music-making, and the only thing between me and that is this driver! :x
I am not afraid of the command line, and I can read, I just haven't reached that "critical mass" yet, where it snaps and I really start getting it.

btw, my Download directory isn't on the root, it is under /home/tormod/ as you can see in the text I pasted above. I don't know why the prompt seems to disagree, but I'm actually in the /home/tormod/Download directory when I try to make install. :shrug:

EDIT - maybe that's it! All those lines say that it's undefined... Does that mean it's undefined for a file with that path? Maybe there are "hardcoded" paths in the source files? Which one(s) should I look in first? (time to break out those C-books...)

I've posted a couple of times in a thread over at the Line6 forum where the guy who wrote the driver hangs out, but I don't think he's in the teaching newbies busniess. So thanks again, Pragmatist - much appreciated.

Now let's see - what next?

---

### Post by Pragmatist on 2006-03-02
Whoops! Don't know how I missed all those lines with /home/tormod/Download
> [ I don't know why the prompt seems to disagree  Actually there is no problem with your prompt (I missed this too :)  
>  tormod@tormodc:~/Download/Line6/line6usb-0.6.1$
the ~ before /Download is an alias for your home directory.  You can use the ~ always in place of /home/tormod

How about the output of ```
lsmod
```

Also, send me a link to those instructions you used to set up your computer for music.  The kernel you are using: > 2.6.12-50preempt  seems very unusual. I didn't even get one hit when I punched that into linux google.  So, I'm guessing you got that kernel when you were following those other instructions.  You might be better off just making a "vanilla kernel".  
When you boot, is there a list of kernels to choose from??

---

### Post by hovmod on 2006-03-02
The preemptible kernel instructions were from the ubuntu studio wiki, in the 'studio preparation' section: [http://ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation](http://ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation)
Scroll down to 'low-latency kernel'. I *think* I followed the instructions to the letter, and I did apparently get good results, although without midi input it's hard to tell...

Let's see; lsmod: 

```

Module                  Size  Used by
rfcomm                 35612  0
l2cap                  24068  5 rfcomm
bluetooth              44420  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5380  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
realtime                6032  0
commoncap               6784  1 realtime
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11264  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5632  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  223424  8
af_packet              20872  2
floppy                 53204  0
rtc                    12600  0
pcspkr                  3780  0
joydev                  9280  0
tsdev                   7616  0
wacom                  13056  0
ohci1394               31156  0
snd_emu10k1_synth       6784  0
snd_emux_synth         33536  1 snd_emu10k1_synth
snd_seq_virmidi         7296  1 snd_emux_synth
snd_seq_midi_emul       6400  1 snd_emux_synth
snd_emu10k1           101412  3 snd_emu10k1_synth
snd_ac97_codec         82464  1 snd_emu10k1
snd_pcm_oss            47008  0
snd_mixer_oss          16512  1 snd_pcm_oss
snd_pcm                80520  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_ac97_bus            2304  1 snd_ac97_codec
snd_page_alloc         10248  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  2 snd_emux_synth,snd_emu10k1
snd_hwdep               8992  2 snd_emux_synth,snd_emu10k1
bt878                   9912  0
bttv                  141840  1 bt878
video_buf              20100  1 bttv
firmware_class          9728  1 bttv
i2c_algo_bit            8584  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4872  1 bttv
tveeprom               12568  1 bttv
i2c_core               20112  4 i2c_acpi_ec,bttv,i2c_algo_bit,tveeprom
videodev                9600  1 bttv
tpm_atmel               5504  0
tpm_nsc                 6528  0
tpm                     9760  2 tpm_atmel,tpm_nsc
hw_random               5396  0
pci_hotplug            25652  0
intel_agp              21148  1
agpgart                32456  1 intel_agp
nls_utf8                2176  3
ntfs                   91888  3
dm_mod                 50876  1
snd_seq_dummy           3972  0
snd_seq_oss            31744  0
snd_seq_midi            8736  0
snd_rawmidi            23712  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
evdev                   9088  0
snd_seq_midi_event      6912  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                46864  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22788  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          8332  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    52068  20 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_util_mem,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore               9568  1 snd
sr_mod                 15652  0
sbp2                   21384  0
ieee1394               91704  2 ohci1394,sbp2
psmouse                26116  0
mousedev               11040  1
parport_pc             32068  1
lp                     11460  0
parport                32840  2 parport_pc,lp
md                     41680  0
ext3                  116872  1
jbd                    52248  1 ext3
thermal                13192  0
processor              23228  1 thermal
fan                     4740  0
usbhid                 30816  0
e100                   34048  0
mii                     5120  1 e100
ehci_hcd               30344  0
uhci_hcd               28688  0
usbcore               106236  5 wacom,usbhid,ehci_hcd,uhci_hcd
sd_mod                 17424  7
ide_cd                 37124  0
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0
ata_piix                9476  11
libata                 47620  1 ata_piix
scsi_mod              126408  4 sr_mod,sbp2,sd_mod,libata
piix                    9604  1
ide_core              126164  3 ide_cd,ide_generic,piix
unix                   25904  698
vga16fb                11848  1
vgastate                8192  1 vga16fb
softcursor              2432  1 vga16fb
cfbimgblt               3072  1 vga16fb
cfbfillrect             3840  1 vga16fb
cfbcopyarea             4480  1 vga16fb
fbcon                  34432  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5120  1 fbcon

```

Whoa.
I'm posting this for your entertainment, and I'll try to make sense of it as well.
If you see something that makes you go hmmm let me know, yeah?

:)

See how neither EZUSB or line6usb are there? Hmmm...

---

### Post by hovmod on 2006-03-02
Ah - tried 'modprobe line6usb' and here's the result in the dmesg file after that: 

```

[4294698.200000] line6usb: disagrees about version of symbol snd_rawmidi_receive
[4294698.200000] line6usb: Unknown symbol snd_rawmidi_receive
[4294698.200000] line6usb: disagrees about version of symbol snd_ctl_add
[4294698.200000] line6usb: Unknown symbol snd_ctl_add
[4294698.200000] line6usb: disagrees about version of symbol snd_pcm_new
[4294698.201000] line6usb: Unknown symbol snd_pcm_new
[4294698.201000] line6usb: Unknown symbol __fixsfsi
[4294698.201000] line6usb: disagrees about version of symbol snd_card_register
[4294698.201000] line6usb: Unknown symbol snd_card_register
[4294698.201000] line6usb: disagrees about version of symbol snd_card_free
[4294698.201000] line6usb: Unknown symbol snd_card_free
[4294698.201000] line6usb: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[4294698.201000] line6usb: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[4294698.201000] line6usb: Unknown symbol __subsf3
[4294698.201000] line6usb: Unknown symbol __extendsfdf2
[4294698.201000] line6usb: Unknown symbol __adddf3
[4294698.201000] line6usb: disagrees about version of symbol snd_ctl_new1
[4294698.201000] line6usb: Unknown symbol snd_ctl_new1
[4294698.201000] line6usb: disagrees about version of symbol snd_rawmidi_transmit_ack
[4294698.201000] line6usb: Unknown symbol snd_rawmidi_transmit_ack
[4294698.201000] line6usb: Unknown symbol __fixdfsi
[4294698.201000] line6usb: disagrees about version of symbol snd_card_new
[4294698.201000] line6usb: Unknown symbol snd_card_new
[4294698.201000] line6usb: disagrees about version of symbol snd_pcm_lib_malloc_pages
[4294698.201000] line6usb: Unknown symbol snd_pcm_lib_malloc_pages
[4294698.201000] line6usb: disagrees about version of symbol snd_pcm_lib_ioctl
[4294698.201000] line6usb: Unknown symbol snd_pcm_lib_ioctl
[4294698.201000] line6usb: disagrees about version of symbol snd_pcm_lib_free_pages
[4294698.201000] line6usb: Unknown symbol snd_pcm_lib_free_pages
[4294698.201000] line6usb: disagrees about version of symbol snd_rawmidi_transmit_peek
[4294698.201000] line6usb: Unknown symbol snd_rawmidi_transmit_peek
[4294698.201000] line6usb: Unknown symbol __floatsisf
[4294698.201000] line6usb: disagrees about version of symbol snd_pcm_set_ops
[4294698.201000] line6usb: Unknown symbol snd_pcm_set_ops
[4294698.201000] line6usb: disagrees about version of symbol snd_device_new
[4294698.201000] line6usb: Unknown symbol snd_device_new
[4294698.201000] line6usb: Unknown symbol __ltsf2
[4294698.201000] line6usb: Unknown symbol __mulsf3
[4294698.201000] line6usb: disagrees about version of symbol snd_rawmidi_new
[4294698.201000] line6usb: Unknown symbol snd_rawmidi_new
[4294698.201000] line6usb: disagrees about version of symbol snd_card_disconnect
[4294698.201000] line6usb: Unknown symbol snd_card_disconnect
[4294698.202000] line6usb: disagrees about version of symbol snd_rawmidi_set_ops
[4294698.202000] line6usb: Unknown symbol snd_rawmidi_set_ops
[4294698.202000] line6usb: disagrees about version of symbol snd_pcm_period_elapsed
[4294698.202000] line6usb: Unknown symbol snd_pcm_period_elapsed
[4294698.302000] spca5xx: version magic '2.6.12-50preempt preempt 386 gcc-4.0' should be '2.6.12-50preempt preempt 386 gcc-3.4'


```

Hopefully we're pretty close to the solution now. I can almost taste the success.... :D

---

### Post by hovmod on 2006-03-02
[quote="The author, Markus Grabner]
Looks weird indeed. Just a few thoughts:
*) Does your installed kernel binaries version match the kernel source version?
*) I've never tried with a kernel source tree *not* under "/usr/src/linux", so you could try to symlink your source tree:
ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
*) Could you please exactly specify your system (Linux distribution, compiler version, ...)

Kind regards,
Markus 
[/quote]

That was nice of him. I really want to answer those questions, so could you help me with the following so I don't have to bother him with the super simple stuff: 

*) Does your installed kernel binaries version match the kernel source version?

How can I tell?

*) Could you please exactly specify your system (Linux distribution, compiler version, ...)

Is there a nice little command I can use to answer that?

Thanks a lot.

Tormod

---

### Post by Pragmatist on 2006-03-02
> If something goes wrong, just choose the original kernel from the Grub menu during bootup

I got that from the **enabling Preemption** PAGE.

You can get some good info with ```
uname -a
```  I'm not sure exactly what he means by the source versus the binary.  The kernel that is run when starting up can be found in**/boot**  I think what he is getting at is that you might have mismatched source and binary.  So, for example, the machine is starting kernel 2.6.12-50preempt but the source for that is in the wrong place so that the system can't find the corresponding resources for this new, preempt, kernel.

What I would do is take a look in **/boot** my guess is that you have multiple kernels.  Then you can edit **/boot/grub/menu.lst**  if you don't know how to do that, send the contents of the file here.

---

### Post by hovmod on 2006-03-02
I do indeed have multiple kernels, and my grub menu has six different options plus Windows... But I don't really think something went all that wrong. I get very acceptable latency when I try to run audio through the system.

It's just these USB-MIDI drivers that aren't seeing what they expect...

I assume that if I select a different kernel during startup I lose the preemtible, low latency jobby and proobably all my installed programs and settings and stuff? 

I'll give it a try just for the sake of learning something, but I don't want to compromise: I want BOTH midi in AND low latency... :D

---

### Post by Pragmatist on 2006-03-02
Yeah, I would try a basic kernel, just to troubleshoot the problem.  If it works with the basic kernel, then you know that you need to make some, probably small, modification to the preempt one.

Quick update: I just typed: **Unknown symbol __fixdfsi** as a keyword in [www.google.com/linux](www.google.com/linux)  After looking at a bunch of posts of other problems that had this message in dmesg, they all seem to be about kernel configuration.  This would make sense if the preempt kernel was setup streamlined for the various audio packages it anticipated.  When performance is critical, you try and have an "unbloated" kernel and don't include options if you don't have too.  This driver you need probably requires some options in your kernel that you don't have.  If the experiment with the basic kernel works, you will just recompile the preempt kernel but add the additional options you need.  This is not an uncommon procedure in Linux.

Just for fun, take a look at the kernel config files under **/boot**  they look like this: **config-2.6.12-10-386**  This will give you some idea of what a kernel configuration looks like.

This shouldn't screw up anything else you installed, as the kernel is just a program.

---

### Post by hovmod on 2006-03-02
OK, I did the first experiment - I booted up in the previous kernel in the grub menu, and it didn't work there either. A bit different error message that time, but nope. 
And when I booted up in the latest one, all my firefox bookmarks and cookies and stuff was gone. :(
Anyway, it's late here and I need to sleep.

Thank you very much!

---

### Post by dolson on 2006-03-11
FWIW, the podxtpro driver is included in Dapper's kernel as a module... So all you have to do is sudo modprobe podxtpro and it's there.

---

### Post by patrixl on 2006-03-13
I believe those drivers are out of date. I followed the instructions on

[http://ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation#ALSA_Sequencer](http://ubuntustudio.com/wiki/index.php/Breezy:Studio_Preparation#ALSA_Sequencer)

I am now successfully using my MidiSport uno usb interface! Haven't tried my keyb yet, buit the output works great.

usb midi drivers are included with ALSA for a long time now, you shouldn't need these usb-midi drivers from 2004 ;)

---

