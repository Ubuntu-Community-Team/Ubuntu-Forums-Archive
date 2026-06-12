---
title: "&quot;Crackly&quot; Sound... going nuts"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Spektyr on 2007-08-17
I recently put together (for the zillionth time) my wife's computer and loaded Ubuntu Feisty onto it.

Everything's been going pretty well except for the sound.  (I was having a bunch of hardware problems with that machine that I've cleared up by putting in a new mobo/cpu combo.)


It's running on the onboard sound of the motherboard, which is a K8M800 (the box says K8M800-COMBO-43-R).  All sound played, regardless of player, sound file type, or any other discernible variable is "crackly".  It has very small static "pops" that similar to electronic pins dropping.  Rapidly.  Basically it makes my aural nerves itch.

Also, it seems like the output is very weak - I have the volume settings in Ubuntu cranked up and the speakers themselves cranked up and it's just a mild listening volume (I usually have the TV turned up louder than this.)


I can't figure out what's wrong, let alone where to start.  Do I have a BIOS setting wrong?  Something messed up in Ubuntu?

Help!

---

### Post by heimo on 2007-08-18
Could you run and tell us output of command:

```
 lspci | grep -i audio
```

I'm uncertain which audio chip your system uses, but if it's Intel, you could try this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by bobpur on 2007-08-18
Is your plug in the right jack? On most (not all) 2.1 systems the speaker wire has a light green plug that plugs into the jack on your soundcard  that is a like color. Other jacks may work but give distorted sound. I don't know what your motherboard looks like but most have a jack for 2.1 (Two speakers and a sub-woofer) sound systems and additional jacks of different colors for 4.1,5.1 or 7.1 systems.
Also, try a different driver. ALSA is not your only choice. It's just the most common.

---

### Post by heimo on 2007-08-18
> **bobpur said:**
> Is your plug in the right jack?

Ah! Bobpur, you added what I forgot to suggest. Very low volume could mean that speakers are connected to headphone output. That was my initial thought, but it seemed too obvious. Also I didn't say that Spektyr should try checking his channels with alsamixer.

---

### Post by Spektyr on 2007-08-18
> **heimo said:**
> Could you run and tell us output of command:

```
 lspci | grep -i audio
```

I'm uncertain which audio chip your system uses, but if it's Intel, you could try this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

The output was:

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)


There are three jacks on the back of the computer, I've tried the plug in all three and the only way to get any sound at all is by plugging it into the green one (where it's been all along).

I have no clue what to do with the suggestions of trying another driver or checking things with alsamixer.

I am an "Absolute Beginner" in most regards, so I came here.

---

### Post by heimo on 2007-08-18
Yeah. The link about Intel isn't for you. :-( The good news is, that should be very well supported chip, I've used it on at least two systems with good results.

Open a terminal window (Applications->Accessories->Terminal) and type alsamixer [and hit enter]. You can navigate it with arrow keys, use m key to mute / unmute channels, tabulator to see more channels, and up/down arrow to change channel volume. Keep some music / audio playing while you do this.

---

### Post by HermanAB on 2007-08-18
Hmm, try booting another distribution off a CD, for example Knoppix.  If the sound is still bad, then you likely have a hardware problem.

---

### Post by Arthur Archnix on 2007-08-18
Wait, booting another distro live cd is a good idea, but it would be simpler to eliminate the speakers first. Plug in some headphones first to the speaker out, do you still hear the crackling sounds?

---

### Post by Spektyr on 2007-08-18
> **heimo said:**
> Yeah. The link about Intel isn't for you. :-( The good news is, that should be very well supported chip, I've used it on at least two systems with good results.

Open a terminal window (Applications->Accessories->Terminal) and type alsamixer [and hit enter]. You can navigate it with arrow keys, use m key to mute / unmute channels, tabulator to see more channels, and up/down arrow to change channel volume. Keep some music / audio playing while you do this.

Any time I changed the volume on something I had a 90% chance of the sound quitting entirely.  Twice I was able to get it back by adjusting the volume down and then back up on the Master volume, but it quickly just cut out entirely and wouldn't come back.  I then discovered that the main volume control had been set at 50%, which is too quiet to be heard.

I have no idea what I'm looking for in this program anyway, so I'm not sure how I'm supposed to fix anything except by trial and error, and I generally shy away from the "monkey pushing random buttons" repair method.  If you've got some suggestions as to what I should try I'd be very interested.

> **Arthur Archnix said:**
> Wait, booting another distro live cd is a good idea, but it would be simpler to eliminate the speakers first. Plug in some headphones first to the speaker out, do you still hear the crackling sounds?

I'm a newbie to Ubuntu, not troubleshooting.  I've tried a different set of speakers with the same results.  The problem definitely exists within the box somewhere, either hardware or software.

When I boot to the Feisty Live CD I have no sound whatsoever, but I have no clue what that means.

---

### Post by expatCM on 2007-08-18
Not sure that I understand this one at all but let me try and understand something.

You say that you needed to replace the motherboard.  Before you replaced the motherboard did you have this problem with sound or was the sound working perfectly?

---

### Post by Spektyr on 2007-08-18
The sound was working before, but that was a different computer.  (The only thing in common between this machine and the previous incarnation is the video card, memory, and the case.  Everything else - including the installation of Ubuntu - is new.)

---

### Post by Arthur Archnix on 2007-08-18
I wasn't able to find anyone complaining of similar problems with your card. I'm thinking as this is a brand new mobo, it should be under warranty. 

Before doing that though, I'd try booting a different distro's live cd, maybe knoppix? I'd also disable sound in the bios, reboot to confirm no sound at all, then reset bios to default and reboot. At that point I'd probably set up windows, install the drivers from the manufacturer, and confirm that the problem persists.

But give the forums a few more days... it's possible a solution will be found.

Have you switched to OSS output with the same result?

Can you do a lsmod and post the output. Wrap the output in quotes or code or something, because it will be long.

---

### Post by Spektyr on 2007-08-18
> **Arthur Archnix said:**
> I wasn't able to find anyone complaining of similar problems with your card. I'm thinking as this is a brand new mobo, it should be under warranty.

I'd rather try poking a badger with a sharp stick than RMA this thing.  I made the mistake of buying it from geeks.com and the geniuses there decided to remove one of the heatsink bracket screws from the motherboard before they shipped it, so it was completely useless when it arrived.  When I filed an incident to get a replacement screw sent I had to spend a good hour on the phone explaining to half a dozen people what the heck was wrong (after getting disconnected every time they transferred me somewhere else).

I explained that this was something I wanted solved rapidly, so it only took them a week to get around to sending me an email claiming that they'd shipped the replacement.  Apparently they don't understand the concept of a Tracking Number because they were stupid enough to include it in this email.  When checked it very clearly stated that the package information had been sent, but the package had not actually been given to FedEx.

A week later I call again (same issues with their phones) to complain about them only transmitting information to FedEx, they again claim the package was actually shipped.  A guy promises he'll call FedEx and find out what's going on, then call me.  He never calls.  Later that afternoon FedEx actually gets the package.  Two days later I finally get it.


So anything that involves me never having contact with geeks.com ever again is preferable.

> **Arthur Archnix said:**
> Before doing that though, I'd try booting a different distro's live cd, maybe knoppix? I'd also disable sound in the bios, reboot to confirm no sound at all, then reset bios to default and reboot. At that point I'd probably set up windows, install the drivers from the manufacturer, and confirm that the problem persists.

I'll try the BIOS stuff, but I'd rather not download and burn a CD with an OS I don't really want or need.  And I'd certainly not want to buy Windows.

> **Arthur Archnix said:**
> Have you switched to OSS output with the same result?

Can you do a lsmod and post the output. Wrap the output in quotes or code or something, because it will be long.

Who to what?  Remember, I'm in Absolute Beginner Talk.  I don't have the first clue how to do any of that, unless the second one involves simply typing "lsmod" into the terminal.

I've got a decent working knowledge of most things computer, just not so great on Linux yet.

---

### Post by sevix on 2007-08-18
Completely non-technical approach, but I had similar problem as you, very crackly sounds, when before I never had the problem..
I solved it by turning the master volume down to 3/4 and just turning my speakers up louder, clean sound from that point on for me. Its worth trying this BEFORE you go through a bunch of hoops.

---

### Post by Arthur Archnix on 2007-08-18
> **Spektyr said:**
>  I don't have the first clue how to do any of that, unless the second one involves simply typing "lsmod" into the terminal.

Exactly.

---

### Post by Arthur Archnix on 2007-08-18
> **sevix said:**
> Completely non-technical approach, but I had similar problem as you, very crackly sounds, when before I never had the problem..
I solved it by turning the master volume down to 3/4 and just turning my speakers up louder, clean sound from that point on for me. Its worth trying this BEFORE you go through a bunch of hoops.

This is true also. From what I've read the sound card is a real cheapy. Maxing out the volume controls, which you've done because of the low sound volume output, may help with the crackling sound. This can be done in alsamixer (type that in a terminal) then when you're done lowering the voumes and are back in the terminal type
```
sudo aslactl store
```

---

### Post by Spektyr on 2007-08-18
> **sevix said:**
> Completely non-technical approach, but I had similar problem as you, very crackly sounds, when before I never had the problem..
I solved it by turning the master volume down to 3/4 and just turning my speakers up louder, clean sound from that point on for me. Its worth trying this BEFORE you go through a bunch of hoops.

If I reduce the master volume at all I don't have enough output signal for the amplified speakers to produce anything but faint, unintelligible noises.  I've got the master volume at 100% and the speakers on 90% just to have something rather quiet to listen to.

lsmod:
> Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
powernow_k8            16064  0 
cpufreq_ondemand        9228  1 
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
tc1100_wmi              8068  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
container               5248  0 
asus_acpi              17308  0 
button                  8720  0 
dock                   10268  0 
video                  16388  0 
battery                10756  0 
backlight               7040  1 asus_acpi
ipv6                  268960  10 
lp                     12452  0 
fuse                   46612  0 
analog                 12832  0 
snd_via82xx            29208  1 
gameport               16520  2 analog,snd_via82xx
snd_ac97_codec         98464  1 snd_via82xx
snd_mpu401              9256  0 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_via82xx,snd_pcm
snd_mpu401_uart         9472  2 snd_via82xx,snd_mpu401
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  14 snd_via82xx,snd_ac97_codec,snd_mpu401,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usblp                  14848  0 
i2c_viapro             10132  0 
k8temp                  6656  0 
i2c_core               22656  2 i2c_ec,i2c_viapro
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
soundcore               8672  1 snd
amd64_agp              13700  1 
agpgart                35400  1 amd64_agp
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  4 
usbhid                 26592  0 
hid                    27392  1 usbhid
via82cxxx              10372  0 [permanent]
generic                 5124  0 [permanent]
floppy                 59524  0 
via_rhine              25608  0 
mii                     6528  1 via_rhine
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  5 usblp,usbhid,ehci_hcd,uhci_hcd
ata_generic             9092  0 
sata_via               12548  0 
libata                125720  2 ata_generic,sata_via
scsi_mod              142348  1 libata
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


---

### Post by Arthur Archnix on 2007-08-18
Yes but low sound output is a different problem from crackly sound output. Maybe we're trying to fix the wrong problem here. Use headphones and alsamixer to drop the volume below max and see if the crackling sound persists.

---

### Post by the.phantom on 2007-08-18
i had bad sounds on my system too and i went and right clicked the speaker icon

clicked
open volume controls

clicked ( to red x) the features i didn't need 

went and clicked "the switches tab"
and unchecked the box and now sounds are good !

but that is just me on my system !!!
but easy to do, and undo if it didn't work for you !

---

### Post by expatCM on 2007-08-18
What do I know .......  but if you could use sound without the crackles by booting to a live CD then the problem is with Ubuntu.  However, if you cannot loose the crackles at all then the main candidate is a defective mother board.

Do crackles normally not reflect a bad soldered joint or a loose soldered socket?   Is there any other cause?

If it were me I think I would probably return the motherboard ....

---

### Post by fredj on 2007-08-19
There are lots of causes for crackly sound in Ubuntu, it doesn't necessarily mean you have a
defective motherboard. This is the least likely cause. 
Open the alsa mixer (double click on the speaker icon in the system tray). Check the File->
Change Device menu to make sure that the correct audio device is selected.
Use the Edit->Preferences menu to add all the possible volume controls and switches for both
playback and record. Ensure that suitable volume levels are set and that all the controls are 
unmuted.

---

### Post by Spektyr on 2007-08-19
> **fredj said:**
> There are lots of causes for crackly sound in Ubuntu, it doesn't necessarily mean you have a
defective motherboard. This is the least likely cause. 
Open the alsa mixer (double click on the speaker icon in the system tray). Check the File->
Change Device menu to make sure that the correct audio device is selected.
Use the Edit->Preferences menu to add all the possible volume controls and switches for both
playback and record. Ensure that suitable volume levels are set and that all the controls are 
unmuted.

"Make sure that the correct audio device is selected" presumes I first know what the correct audio device is.  I have two options: VIA 8237 (Alsa mixer) and Realtek ALC655 rev 0 (OSS Mixer).  I'm assuming the first one is the correct one, mainly because I get no sound whatsoever off the second one.

I turned all the volume controls in the alsamixer all the way up and got no sound at all.  However, upon reboot I was nearly deafened by the startup sound, so something in there seems to have finally given me a decent output level.

Unfortunately... as soon as I tried reducing the Master volume control the sound cut out entirely and wouldn't come back.  Let me rephrase that just to be clear: the computer stops playing all sound of any kind after adjusting the main volume downward past roughly 60%.

Through all this the sound was still full of static, until of course it quit entirely.  When rebooted the sound came back, and when I tried adjusting the Master volume control it did not cut out, but the slider seemed to "resist" being moved.  Moving it down to 50% did not reduce the static, so I tried the other controls as well.  When moving the Center channel control (these are 2.1 speakers, so no center speaker is present) the sound cut off again.  It did it again on the next reboot when adjusting the Phone volume.

I'm baffled.

---

### Post by kleo skywalker on 2007-08-20
> **Spektyr said:**
> "Make sure that the correct audio device is selected" presumes I first know what the correct audio device is.  I have two options: VIA 8237 (Alsa mixer) and Realtek ALC655 rev 0 (OSS Mixer).  I'm assuming the first one is the correct one, mainly because I get no sound whatsoever off the second one.

I turned all the volume controls in the alsamixer all the way up and got no sound at all.  However, upon reboot I was nearly deafened by the startup sound, so something in there seems to have finally given me a decent output level.

Unfortunately... as soon as I tried reducing the Master volume control the sound cut out entirely and wouldn't come back.  Let me rephrase that just to be clear: the computer stops playing all sound of any kind after adjusting the main volume downward past roughly 60%.

Through all this the sound was still full of static, until of course it quit entirely.  When rebooted the sound came back, and when I tried adjusting the Master volume control it did not cut out, but the slider seemed to "resist" being moved.  Moving it down to 50% did not reduce the static, so I tried the other controls as well.  When moving the Center channel control (these are 2.1 speakers, so no center speaker is present) the sound cut off again.  It did it again on the next reboot when adjusting the Phone volume.

I'm baffled.

I have major sound problems with Feisty too. Haven't been able to fix cracking at high pitches, but I did get rid of the static - I installed the graphical tool for ALSA Mixer (can't remember if it was from add/remove or synaptic) and moved the Mic slider down. In case you haven't already tried this, give it a shot and see if it works.

---

### Post by TeaSwigger on 2007-08-20
> I'm a newbie to Ubuntu, not troubleshooting. I've tried a different set of speakers with the same results. The problem definitely exists within the box somewhere, either hardware or software.

Of course after checking that the card's plugs and connections are perfectly clean in and out and with an entirely different connector and wiring and preamp and so forth all the way down the line as well, correct? Because it sounds like a bad connection causing resistance issues. If the answer is no, you'll find me hiding under the table.

---

### Post by heimo on 2007-08-20
> **TeaSwigger said:**
> Of course after checking that the card's plugs and connections are perfectly clean in and out and with an entirely different connector and wiring and preamp and so forth all the way down the line as well, correct? Because it sounds like a bad connection causing resistance issues. If the answer is no, you'll find me hiding under the table.

There has been posts and bug about crackling sound in VLC when using Alsa, which could easily be diagnosed as hardware problem, but isn't. I'm not saying this (Spektyrs) isn't hardware problem, just that it may very well be some kind of weird software problem.

---

### Post by Spektyr on 2007-08-20
I think the key to solving this is the problem with the sound cutting out entirely.  Has anyone considered that?


"Bad connections" does not explain why adjusting the volume down would cause the sound to die even when the volume is turned back up.


I have no idea what's going on or even how the software side of things (drivers) really works in any operating system, but my years of computer geekery tells me that this problem is at least influenced by software (since software can "break" it more than it already is).

I believe that if we can answer the question of why the sound cuts completely out after "fiddling" with the various - wholly unrelated - volume controls we'll either discover the true problem or be one step closer to this discovery.

---

### Post by TeaSwigger on 2007-08-20
> **Spektyr said:**
> I think the key to solving this is the problem with the sound cutting out entirely.  Has anyone considered that?


"Bad connections" does not explain why adjusting the volume down would cause the sound to die even when the volume is turned back up.

Well, yes it can. Connection problems, sometimes a bad wire for example, can indeed cause sound to cut out entirely and take a lot more current to reestablish than there was at the point it cut out, resulting in problems that could fit his descriptions. He only specified changing speakers, which still leaves the rest. By no means am I saying that this is the problem, only that it could be and it'd be nice to rule it out. :)

---

### Post by Spektyr on 2007-08-20
> **TeaSwigger said:**
> Well, yes it can. Connection problems, sometimes a bad wire for example, can indeed cause sound to cut out entirely and take a lot more current to reestablish than there was at the point it cut out, resulting in problems that could fit his descriptions. He only specified changing speakers, which still leaves the rest. By no means am I saying that this is the problem, only that it could be and it'd be nice to rule it out. :)

So you're saying that you believe it's possible that a connection that is established at X watts of power can be completely severed by reducing power to X - Y watts, but not re-established by increasing back to X watts?  Then how could it possibly be re-established by a reboot, which would by definition only be able to output the previous maximum of X watts?

Or are you suggesting that somehow the boot-up process causes the connection to be established by over-volting somehow?


I'm sorry, I was trained to troubleshoot based upon a logical process of eliminating potential problems based upon likelihood.  If my car fails to start I don't begin by checking tire pressure simply because it's theoretically possible that having too great a right-to-left slant might somehow be causing a fuel flow problem in the carburetor.  I'm going to start by checking if I'm missing fuel or spark.


The speakers cut out permanently until reboot while adjusting both "mic" and "phone" sliders.  Neither of these should have any effect whatsoever on the output going through the speaker port electronically.  The only explanation that makes any sense in terms of sheer percentages of likelihood is that there is some kind of software problem.

If I adjust the sensitivity of my mouse and the printer spits out a test page, I don't assume the connections are loose.  The simplest assumption is that the computer has a software glitch that has the two confused.


And just so that we can stop talking about whether or not there's theoretical "dirt" in the connectors, there isn't.  Okay?  They're clean.

---

### Post by err_ok on 2007-08-20
i experienced crackly sound at one point aswell, it was because i had PCM turned up to full.

If you keep it at 80% and then have master at 100% you don't get it anymore... Not sure about the volume issue though.

---

### Post by pdlethbridge on 2007-08-20
Have you tried the speakers on another computer?

---

### Post by Spektyr on 2007-08-21
> **err_ok said:**
> i experienced crackly sound at one point aswell, it was because i had PCM turned up to full.

If you keep it at 80% and then have master at 100% you don't get it anymore... Not sure about the volume issue though.

That's what my settings are currently at, but I've still got crackling.

> **pdlethbridge said:**
> Have you tried the speakers on another computer?

It.  Is.  Not.  The.  Speakers.

If you observe the problem with one set of equipment, trade in a known-good part, and still observe the same problem you can rule out the original part as the source of the problem.

Since I've already said repeatedly that I've tried a different set of speakers with the same result the only logical conclusion that can be drawn is that neither set of speakers is the source of the problem.  This would render testing the speakers on another computer pointless.


I understand hardware.  I need help troubleshooting the software.

---

### Post by heimo on 2007-08-21
Did you try disabling esd in Sound Preferences? (System->Preferences->Sound) Any difference? After disabling it, run "killall esd" on terminal to make sure it's not running.  You could also try installing command line mp3 player (mpg123 is one*), shutdown graphical user interface ```
sudo /etc/init.d/gdm stop
```, play a music file on command line (mpg123 file.mp3) and see if there's any difference. To start X again, type ```
sudo /etc/init.d/gdm start
```*) mpg123 is available from [multiverse]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

---

### Post by Spektyr on 2007-08-21
I tried the disabling ESD and had the same results (crackling).

While there I tried the Test sound in each of the Devices available in Sound Preferences and had crackling in all of them.

I couldn't get anything to happen after I shut down the GUI and had to reboot.

---

### Post by Arthur Archnix on 2007-08-22
Have you tried upgrading to the latest ALSA drivers yet?

There's a comprehensiive sound solutions guide by Lord Raiden on here somewhere, but I can't get  the link to work right now. It's got instructions for upgrading to the latest version of ALSA.

---

### Post by Spektyr on 2007-08-22
> **Arthur Archnix said:**
> Have you tried upgrading to the latest ALSA drivers yet?

There's a comprehensiive sound solutions guide by Lord Raiden on here somewhere, but I can't get  the link to work right now. It's got instructions for upgrading to the latest version of ALSA.

That sounds like a great idea... how do I do that?

---

### Post by heimo on 2007-08-22
> **Spektyr said:**
> That sounds like a great idea... how do I do that?

I'd guess it involves reading a comprehensive sound solutions guide by Lord Raiden:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Spektyr on 2007-08-22
> **heimo said:**
> I'd guess it involves reading a comprehensive sound solutions guide by Lord Raiden:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Well... that certainly is a whole lot of information.  Which part is the part that says how to do that?  Am I supposed to do it all?  I read something in there about one of the commands disabling the GUI or something?  I'm not exactly comfortable with that since every time I've done that in the past the computer has done absolutely nothing at blazing speed and had to be rebooted.

---

### Post by Arthur Archnix on 2007-08-22
That's the old guide. The link to the new one is down. I've pm'd Lord Raiden asking for a current link. 

To Spec, you have my respect. Your persistence and determination is admirable. I gave up on Edgy altogether because i had no luck getting good sound. It just worked in Feisty. Anyway, I'll be keeping an eye on this as long as your here and wishing you well.

Best,

---

### Post by Spektyr on 2007-08-22
Heh, well it's nice to be complimented on my persistence, but from my perspective it's not that remarkable.

My wife has to have a computer or my life is unpleasant.

My wife is not an audiophile to the same degree that I am, and thus doesn't mind the crackling as much as I do.

Thus my wife will play music on her computer in spite of this problem, which drives me up the wall.


Therefore the problem absolutely must be resolved.  As a possible back-up solution I'm considering buying a soundcard and installing that.

---

### Post by TeaSwigger on 2007-08-22
> **Spektyr said:**
> So you're saying that you believe it's possible that a connection that is established at X watts of power can be completely severed by reducing power to X - Y watts, but not re-established by increasing back to X watts?  Then how could it possibly be re-established by a reboot, which would by definition only be able to output the previous maximum of X watts?

Not being there, we're down to the clarity and effectiveness of your descriptions. In the terms of that analogy what I said was that I've heard sound established at X watts, lost at X - Y watts and only re-established at a value higher than any of the previous, do to a fault in a wire. It's no theory, it's happened many times; I've been around a lot of audio equipment. Of course one reason is that there's more to an analog audio electrical signal than "watts." So never minding speakers, is the rest of the electrical path fine or not?

> Or are you suggesting that somehow the boot-up process causes the connection to be established by over-volting somehow?

You've never known failing audio equipment to play when turned off and back on, then promptly fail again? Well that actually happens too, and again nobody's talking about speakers or watts.

> I'm sorry, I was trained to troubleshoot based upon a logical process of eliminating potential problems based upon likelihood.  If my car fails to start I don't begin by checking tire pressure simply because it's theoretically possible that having too great a right-to-left slant might somehow be causing a fuel flow problem in the carburetor.  I'm going to start by checking if I'm missing fuel or spark.

That's nice to know.

> The speakers cut out permanently until reboot while adjusting both "mic" and "phone" sliders.  Neither of these should have any effect whatsoever on the output going through the speaker port electronically.  The only explanation that makes any sense in terms of sheer percentages of likelihood is that there is some kind of software problem.

Agree. But then this is the first time you've put it quite that way. Have you confirmed the card is supported by the software and that the card is not defective? The first no one's going to research for you and the second no one can help you with from here.

> If I adjust the sensitivity of my mouse and the printer spits out a test page, I don't assume the connections are loose.  The simplest assumption is that the computer has a software glitch that has the two confused.

That's also nice to know.

> And just so that we can stop talking about whether or not there's theoretical "dirt" in the connectors, there isn't.  Okay?  They're clean.

That's even nicer to know.

> **Arthur Archnix said:**
> To Spec, you have my respect. Your persistence and determination is admirable. I gave up on Edgy altogether because i had no luck getting good sound. It just worked in Feisty. Anyway, I'll be keeping an eye on this as long as your here and wishing you well.

At this point I'm more impressed with heimo's, but it's nice to see there's lots of persistence around these days. 

> **Spektyr said:**
> Well... that certainly is a whole lot of information.  Which part is the part that says how to do that?  Am I supposed to do it all?  I read something in there about one of the commands disabling the GUI or something?  I'm not exactly comfortable with that since every time I've done that in the past the computer has done absolutely nothing at blazing speed and had to be rebooted.

And it was most kind of heimo to point you to it. Once you've taken the next logical troubleshooting step and updated ALSA and/or to a current build, do post back and someone else will hopefully reply.

---

### Post by Spektyr on 2007-08-23
> **TeaSwigger said:**
> And it was most kind of heimo to point you to it. Once you've taken the next logical troubleshooting step and updated ALSA and/or to a current build, do post back and someone else will hopefully reply.

You mean once I've done the thing described on a newer thread that is currently not available, and assuming of course that I even understand what's written on that thread once it is available - *then* I should ask for help?

If you're simply going to be dismissive you can do that without posting.  And unless someone can explain to me a reason why I shouldn't continue posting I think I'll do that until the new thread is located and the next logical troubleshooting step can be taken.

---

### Post by heimo on 2007-08-23
> **Spektyr said:**
> And unless someone can explain to me a reason why I shouldn't continue posting I think I'll do that until the new thread is located and the next logical troubleshooting step can be taken.

Dear Dr Spock,

We appreciate your infallible logic, but need to remind that most of us have only human blood running in our veins.

Now, Scott beam me up. I mean, ubsubscribe me from this thread.

Sincerely,
heimo

PS. I truly wish you can get this solved somehow. If nothing else works, you might try another brand sound card / audio interface, those are quite inexpensive.

---

### Post by Dr_Deadmeat on 2007-09-01
Might be a bit late to revive this thread, but it is only a week old...
I get the same trouble with mine sound card (A "Creative Labs SB Live!"), and I do have windows, and the trouble is not in windows, but it is in Ubuntu. My pcm is set to 75% and my master is at 75% which is what I use on my laptop too, and it works perfectly well with that.

Does anyone know anything to help me? The problem only occurs when the computer is working. I believe it is when the processor works, but it might be when the harddrive is working too.

In advance thanks for any help.

---

### Post by ajmstilt on 2007-09-02
To add, I had very similar problems with my onboard sound card giving my crackling and static.  (it was most evident on low bitrate mp3s, less so on high bitrate files, but still there)  I also noticed that the longer i let rythmbox or amarok go, the worse the static got.  

The only thing I've been able to do is use OSS (system -> prefrences -> sound) and and every couple of hours kill all sound, switch to Alsa, then back to OSS and it's tolorable again for a few hours.

I'm very new to ubuntu, so if I'm missing an easy step, I'm keeping an eye on this thread.

then again it might just be because i'm on _64 and maybe drivers don't play right?

---

### Post by dshep369 on 2007-09-02
I'm new here and just installed linux myself and am really clueless about much of the terminology BUT i had the same problem on Windows with SB Live! after reinstall and had to turn off digital setting. I just did this on my newly installed linux by double clicking on sound/mixer icon and clicking on the switches tab and UNchecking the digital setting. Not sure if this problem has been resolved yet [new here] but if not you might try it...

---

### Post by Dr_Deadmeat on 2007-09-02
> **ajmstilt said:**
> To add, I had very similar problems with my onboard sound card giving my crackling and static.  (it was most evident on low bitrate mp3s, less so on high bitrate files, but still there)  I also noticed that the longer i let rythmbox or amarok go, the worse the static got.  

The only thing I've been able to do is use OSS (system -> prefrences -> sound) and and every couple of hours kill all sound, switch to Alsa, then back to OSS and it's tolorable again for a few hours.

I'm very new to ubuntu, so if I'm missing an easy step, I'm keeping an eye on this thread.

then again it might just be because i'm on _64 and maybe drivers don't play right?

I am using the 32 bit install on a 32 bit cpu, and i have the oame problems. I dont believe it is the architechture of your cpu. But it might be.

---

