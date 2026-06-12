---
title: "Help! Error with CD burner.  (Screenshot included)"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Indy452 on 2008-02-17
I've tried I really have to figure this issue out but I keep hitting a brick wall in my efforts.

I've had alot of fun getting to know Ubuntu but this one little problem is keeping me from reaping all the benifits I had with xp.  If we can get this CD burner to work I'll be one happy camper.

All I can say is, there is a blank 700 mb cd in the drive but I just keep getting the error message it needs a blank cd inserted. I've clicked that o.k. button a thousand times and I've tried two different cd burning applications and it just simply is not working for me.  Its an external oldie, a HP 8200 series cd writer. I like it because its slow by nature and good for burning ISO's like the Kubuntu I would like to burn here in Ubuntu.

Please offer me some help as I have no more resources left to turn to.
[IMG]http://i187.photobucket.com/albums/x152/Indy452/computer%20stuff/Screenshot-1-1.png[/IMG]
Neal

---

### Post by spiderbatdad on 2008-02-17
try running ```
depmod -a
```

and post output of ```
lsmod
```

---

### Post by Indy452 on 2008-02-17
> **spiderbatdad said:**
> try running ```
depmod -a
```

and post output of ```
lsmod
```



l-desktop:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.22-14-generic/modules.dep.temp for writing: Permission denied
 
This is what I get in my terminal after hitting enter.

As for lsmod ???????

---

### Post by spiderbatdad on 2008-02-17
sorry sudo depmod -a

also sudo modprobe st

then lsmod

---

### Post by Indy452 on 2008-02-17
neal@neal-desktop:~$ sudo depmod -a
[sudo] password for neal:
sudo modprobe st
neal@neal-desktop:~$ sudo modprobe st
neal@neal-desktop:~$ lsmod
Module                  Size  Used by
st                     40348  0 
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14080  0 
fat                    54300  1 vfat
ipv6                  273892  8 
af_packet              24840  2 
r128                   41088  2 
drm                    83348  3 r128
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
apm                    22616  2 
lp                     12580  0 
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         8064  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           137248  2 snd_emu10k1_synth
snd_ac97_codec        100644  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10244  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
snd_seq_midi            9600  0 
snd_rawmidi            25728  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                53232  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcspkr                  4224  0 
intel_agp              25620  1 
agpgart                35016  2 drm,intel_agp
emu10k1_gp              4736  0 
gameport               16776  2 emu10k1_gp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
serio_raw               8068  0 
snd_timer              24324  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9228  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                39952  0 
soundcore               8800  1 snd
i2c_piix4               9740  0 
i2c_core               26112  1 i2c_piix4
evdev                  11136  1 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usb_storage            73024  0 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
floppy                 60004  0 
8139too                27776  0 
mii                     6528  1 8139too
uhci_hcd               26640  0 
usbcore               138632  4 usb_storage,libusual,uhci_hcd
ata_piix               17540  2 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 st,usb_storage,sg,sr_mod,sd_mod,libata
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
neal@neal-desktop:~$ 




Have I done that right?  What are we looking for?  Should I shut up and try it?

Neal

---

### Post by spiderbatdad on 2008-02-17
looks like the module is loaded. it should work if the cd is blank

---

### Post by kaginken on 2008-02-17
Does the cd-rom 'read' a cd okay if you put one in?  Just trying to see if it is working at all...

If so, and it's just the burn issue, try brasero, or another burning app...

Also, it may just be that you attempted to burn to your blank dvd, and in the process it burned enuf to actually make it no longer blank.  So, try a blank cd, a fresh one that you KNOW is blank.  

Hope that helps!  Hang in there - ubuntu can definitely burn a cd for you, this is part of the 'fun'!  :D

---

### Post by Indy452 on 2008-02-18
> **spiderbatdad said:**
> looks like the module is loaded. it should work if the cd is blank

Does the cd writer ned to be mounted? In properties of the writer you can set the target or something. I'm not yet skilled in that dept, thats why I ask so many Questions..

Thats a real bummer. I will need to use a cd burner once and awhile. 

Thanks for the help spiderbatdad. I appreciate it. 

Neal

---

### Post by spiderbatdad on 2008-02-18
I'm looking for bug reports...I only now noticed you are using xubuntu. Maybe someone else will chime in. You might also look for another cd burning app in your package manager...like brassero.
Also run an update.```
sudo apt-get update
```

---

### Post by Indy452 on 2008-02-18
> **kaginken said:**
> Does the cd-rom 'read' a cd okay if you put one in?  Just trying to see if it is working at all...

If so, and it's just the burn issue, try brasero, or another burning app...

Also, it may just be that you attempted to burn to your blank dvd, and in the process it burned enuf to actually make it no longer blank.  So, try a blank cd, a fresh one that you KNOW is blank.  

Hope that helps!  Hang in there - ubuntu can definitely burn a cd for you, this is part of the 'fun'!  :D

This thing works, I'm listening to Johnny Cash right now!

I'll try more blanks, but I got that one right out of a new pack.     wait the CD writer just ejected itself! WTF?  Maybe my old junk is really junk now. The stuff is in good shape but older thats all.  Now why did my cd eject on its own??  I noticed the sound jucer was playing the cd is that normal to be a default?

---

### Post by Indy452 on 2008-02-18
> **spiderbatdad said:**
> I'm looking for bug reports...I only now noticed you are using xubuntu. Maybe someone else will chime in. You might also look for another cd burning app in your package manager...like brassero.
Also run an update.```
sudo apt-get update
```

  NO,  NO . I'm using Ubuntu 7.1 on a different computer.  I have X on another one here.

I need to change my profile I guess to all the above.  Actually the Ubuntu has given me the most success with all the stuff I use.  Except this I guess,  but I'll hound the forum till I get her done.

N

---

### Post by kaginken on 2008-02-18
HMMMM....

Try this:  

Take any cd's out, unplug any unnecessary usb anythings, and Reboot.

When it comes back up, log in, stick in a blank cd (that you KNOW is fresh and clean).  Brasero should start automatically and ask what you want to do with the CD.  If not, start brasero (which I can see from your screenshot that this is what you are trying to use).  Brasero is DEFINIITELY the boss burner, so stick with that.

Keep your music player and any other unnecessary variables out of the picture until we can get this working and then you can add things back, one at a time, thus determining which one may be the culprit.

Hope this helps!

---

### Post by spiderbatdad on 2008-02-18
could you post the brand of cd/dvd burner?

---

### Post by spiderbatdad on 2008-02-18
This is most likely a problem with the cdrom itself. Is it dirty? maybe try some canned air to clean it out. I know this sounds lame, but it is not an uncommon fix. I suspect this is not software related.

---

### Post by Indy452 on 2008-02-18
> **spiderbatdad said:**
> could you post the brand of cd/dvd burner?

Its a HP external 8200 series.  In properties it says cd writer+ 8290  It is connected through a usb port.

I blew it out with air also and I re-booted like I have b4 with no change.  Maybe it is time for a new one but it worked fine for me in xp a couple of weeks ago, Thats how I got here now you know. I burned xubuntu and ubuntu on it and here I am.  I thought I'd give kubuntu a shot but I was gonna have to get it through Ubuntu.

N

---

### Post by spiderbatdad on 2008-02-18
oh! usb connected. ack. probably a problem with HAL.  Not sure how to fix this. you could try cold plugging...unplug and plug in again on a running system. You can probably burn from the command line. There is a guide here you can try until the problem is fixed. [https://help.ubuntu.com/community/CdDvdBurning](https://help.ubuntu.com/community/CdDvdBurning)

scroll down to: Burning a cd on the command line with cdrecord.

Regards

---

### Post by spiderbatdad on 2008-02-18
This might serve you also: [http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Smart-DVDCD-Burner.shtml](http://www.softpedia.com/get/CD-DVD-Tools/Data-CD-DVD-Burning/Smart-DVDCD-Burner.shtml)

---

### Post by spiderbatdad on 2008-02-18
It may be possible to set a mount point for the device manually in Places>>Computer...Right click cdrw drive...select properties. Go to "drive" tab and click the settings arrow.  mount point.../dev/scd0... file system...ext3...options -t

I'm guessing at the values. I've never tired this. perhaps some research, or someone who knows how to do this could contribute.

---

### Post by Indy452 on 2008-02-18
> **spiderbatdad said:**
> It may be possible to set a mount point for the device manually in Places>>Computer...Right click cdrw drive...select properties. Go to "drive" tab and click the settings arrow.  mount point.../dev/scd0... file system...ext3...options -t

I'm guessing at the values. I've never tired this. perhaps some research, or someone who knows how to do this could contribute.

Yes Yes,  Can someone confirm this. Because in my settings tab there is nothing there for mount point. Anyone confirm that something should be there?

N

---

### Post by kaginken on 2008-02-18
We haven't attempted it commando style yet?  Ok then:

sudo mkdir /mnt/cdrom
mount -t vfat /dev/hdc /mnt/cdrom [where /dev/hdc is your CD drive]

That's a risk free method to try, who knows, it may even return some useful error(s) if it still fails.

---

### Post by spiderbatdad on 2008-02-18
OK. I just dug an external CD-R/RW burner out of the closet. Sony 2100U. Plugged it into the usb port while the computer was already up and running, and I was logged into my linux user account.
I navigated to Places>>Computer, and there were the two cd devices...internal and external. I took some screenshots.  Popped a cd into the thing, and bingo was asked what type of disk I wanted to make. I closed that dialogue window, went to a music folder, selected some songs, opened the cd by clicking on the desktop image, and pasted my slection into the window...chose write disk and viola...burned a cd....simple. 

Now some devices may only recognize discs made by certain manufacturers.

---

### Post by Indy452 on 2008-02-18
> **kaginken said:**
> We haven't attempted it commando style yet?  Ok then:

sudo mkdir /mnt/cdrom
mount -t vfat /dev/hdc /mnt/cdrom [where /dev/hdc is your CD drive]

That's a risk free method to try, who knows, it may even return some useful error(s) if it still fails.

Well, I tried this code in terminal with terminal saying.................. neal@neal-desktop:~$ sudo mkdir /mnt/cdrom
mkdir: cannot create directory `/mnt/cdrom': File exists
neal@neal-desktop:~$ mount -t vfat /dev/hdc /mnt/cdrom [where /dev/hdc is your CD drive]
mount: only root can do that
neal@neal-desktop:~$ 

Maybe I'm not doing it right?  I've not been real comfy with the code thing yet I guess as they are "unknown territory" for me at this point still.

What now?

Neal

---

### Post by spiderbatdad on 2008-02-18
So does the device show up as an external drive the way mine does?  Does ```
lsusb
```show it?

---

### Post by Indy452 on 2008-02-18
> **spiderbatdad said:**
> So does the device show up as an external drive the way mine does?  Does ```
lsusb
```show it?


You mean like this?  Sorry I don't know how to do thumbnails yet.

[IMG]http://i187.photobucket.com/albums/x152/Indy452/computer%20stuff/Screenshot.png[/IMG]

---

### Post by spiderbatdad on 2008-02-18
ok that is disgusting! by all rights this device should be working fine.  To do thumbnails just scroll down a bit till you see "manage attachments" after you selected "Post Reply"  click on that and browse to the location of your pictures...then upload them.

Maybe try a different method of starting the writing...like I did above. Close any dialogues that open when you insert a cd. Open the cd directory by clicking on the cd image on your desktop, then drag any files you want to burn into that window. I opened my music folder...chose the edit menu...chose select all...edit menu again..chose copy. Then went to the cd window...right clicked in the open space...chose paste...clicked the write to disk button.

I'm starting to think the machine doesn't like your disks. Nice desktop wallpaper, btw.

---

### Post by Indy452 on 2008-02-18
Notice on this one I'm ready to burn the ISO but on the device window is says "type" well it also says "no disc" next to it. This sucker is loaded and ready to go but as soon as I hit the burn button thats when the error pops up saying no disc in drive then the door on the burner opens  automatically causing great frustration and obsession.

I've checked for integrity of file and all is good also in case someone wondered.

[IMG]http://i187.photobucket.com/albums/x152/Indy452/computer%20stuff/Dataprojectfailure.png[/IMG]

---

### Post by kaginken on 2008-02-18
hey, that command line version should work.  The reason the first one (mkdir /mnt/cdrom) failed is because you already have a /mnt/cdrom directory which is good.

The second (mount) command, you need to use sudo, aka sudo mount...blah blah

my bad.

What's that do ?

---

### Post by spiderbatdad on 2008-02-18
I believe the frustration is in not being able to use the gui. The command line is definitely a step in the wrong direction for applications of this type. It's like going back to a crank on the front of the car to turn the engine over.

I think your hp burner doesn't like those disks. Are they re-writable? Those can be troublesome.

---

### Post by kaginken on 2008-02-18
I agree with the command line sucking for cd burning - but priceless in the feedback it gives whilst troubleshooting...grasshopper.  :)

---

### Post by spiderbatdad on 2008-02-18
edited

---

### Post by kaginken on 2008-02-18
Hmmmm...that last post was completely irrelevant, illogical and out of context, so I will not comment.

I'm trying to confirm this cdrom is even mounted - what's the output from that mount command?  I'm trying oh so hard to get my third thanks!!  -_-

---

### Post by spiderbatdad on 2008-02-18
It is indeed mounted, as evidenced by his screenshots...external crdom device displayed in the computer places directory, and the cd disk mounted on the desktop...really, I believe it should be labeled "blank disk."  I'm sticking to my story: his device doesn't like his disks.  Hope to see resolution to this problem.

---

### Post by Indy452 on 2008-02-18
Well unfortunatelly I don't have any cd roms other than these cheap HP cd-r 52x 700mb discs. I have two re-writables but the burner spit them out also. 

I guess its possible it does'nt like these cheap discs. It is a new stack but I burned xubuntu on one when I used to use windowsxp.  I do remember it was kinda fussy then too but nothing like this.

This thing wants to take off but this one little issue is keeping it from having supreme success. When I insert a disc you can hear it start up, make a little sound or so and then I see the progress bar on the brasero application start to move and BAM! Done and it ejects on its own. Damn! 

I have to work tommorow but I'll check this site periodically for updates and I'll get some better cd's to try also. Any suggestion on brands and types? I usually just get whatever works and the price is right.

Thanks guys.

Neal

---

### Post by kaginken on 2008-02-19
I suggest buying the smallest amout of the most expensive blank cd-r your local store sells!  :D

If that solves your problem - then use trial and error to find an affordable solution that works in your picky cdrom drive.

If that doesn't work - I got a few used cd-rw's I'll sell REAL cheap!  :D

---

