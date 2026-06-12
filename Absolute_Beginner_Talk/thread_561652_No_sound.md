---
title: "No sound"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by Mynuet on 2007-09-27
I keep finding threads to deal with sound issues, but I've come to a block - none of the solutions seem to work anymore, and I'm desperately afraid to screw things up.  This leaning curve is a bit intimidating!  I don't even remember what I did anymore, but first the sound didn't work, and neither did flash.  Then flash worked, just with no sound for it - but the sound was there for other apps.  Then one day there was a random error message and no sound whatsoever.

Since I've managed to pick up this much, the lspci and lsmod | grep snd results are below.  The sound is the onboard audio of the  [BIOSTAR NF520-A2 motherboard]("http://www.newegg.com/product/product.asp?item=N82E16813138077"), it's an AMD 64 X2 processor, 2 gigs of ram, and the installation is Feisty Fawn (Bambi's revenge?) 7.04...  If I need to include any more information, please just let me know.  Any and all help would be vastly appreciated.  I don't want to go back to Windows!

---------

lspci

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)

00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)

00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)

00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)

00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)

00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)

00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)

00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)

00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)

00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)

00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)

00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

01:08.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)


---------

lsmod | grep snd
snd_pcm_oss            47488  0 

snd_mixer_oss          20096  1 snd_pcm_oss

snd_pcm                93960  1 snd_pcm_oss

snd_seq_oss            39296  0 

snd_seq_midi_event     10240  1 snd_seq_oss

snd_seq                63776  4 snd_seq_oss,snd_seq_midi_event

snd_timer              27656  2 snd_pcm,snd_seq

snd_seq_device         10900  2 snd_seq_oss,snd_seq

snd                    72360  7 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device

soundcore              10272  1 snd

snd_page_alloc         12944  1 snd_pcm

---

### Post by gwoodard on 2007-09-27
Just a question did u check volume control or default device?

---

### Post by Mynuet on 2007-09-27
I checked that the speakers are hooked up, and that the volume is turned up.  

Going to system -> sound preferences -> sound playback, it offers three options besides the autodetect, ALSA, ESD, and OSS.  I get this message: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

---

### Post by nowshining on 2007-09-28
"Could not open resource for writing" 

might be ur clue - I think that it's a permission problem..

---

### Post by Mynuet on 2007-09-28
What does that mean, and how do I fix it?

---

### Post by nowshining on 2007-09-28
[https://answers.launchpad.net/ubuntu/+source/hal/+question/2437](https://answers.launchpad.net/ubuntu/+source/hal/+question/2437)

some suggestions there. edit: even tho the thread/question is old - it might work in the current version of ubuntu.

---

### Post by Mynuet on 2007-09-28
So when they say "reinstall Ubuntu CD" as the solution, does that mean I lose all the stuff currently on my hard drive?  Why would the sound work on a reinstall when it didn't work after the first install?

Another search turned up the command to do this:

$ aplay --list-devices
aplay: device_list:204: no soundcards found...

So it doesn't even acknowledge that the onboard audio exists.  *tears hair out*


$ sudo lshw -class sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
       resources: iomemory:fe028000-fe02bfff irq:5

---

### Post by Mynuet on 2007-10-08
I sucked it up and reinstalled Ubuntu and still no sound.  I followed the directions [here]("http://ubuntuforums.org/showthread.php?t=205449") and [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

Does anyone have any suggestions for what else I can possibly try?  Other than just fleeing back to Windows?

---

### Post by nowshining on 2007-10-09
sorry i have no other suggestions right now. :(

---

### Post by anaconda on 2007-10-09
do you belong to audio group? I just solved my problem and found out thet the sound didn't work because I wasn't in audio group!

You can check which groups you belong by typing in terminal:
```
groups
```

---

### Post by Mynuet on 2007-10-09
groups:
sharlene adm dialout cdrom floppy dip video plugdev scanner netdev lpadmin powerdev admin


How would I add an audio one?

---

### Post by anaconda on 2007-10-10
groups command will show which groups you belong to. not which groups exists, so
there probably is an audio group, but it seems you aren't a member of it!

Type in terminal:
sudo gedit /etc/group

and find a line like this:
audio: x:29:rob,anaconda

and add your username to that line. Save the file and reboot. and check which groups you belong with "groups"

another (easier?) way to add your user to the audio group would be:
sudo adduser yourusername audio

If there isnt an audio group then I cant help you. I dont think adding the group would help?

---

### Post by Mynuet on 2007-10-10
I have sound!  Not on flash, but for everything else - sound!  Woohoo!  \\:D/

Thank you very much for your help!

---

### Post by phr0ze on 2007-10-10
Was the solution adding yourself to the audio group? Thanks.

---

### Post by Mynuet on 2007-10-13
Yeah, that was what did it.  Sorry for not specifying.

---

