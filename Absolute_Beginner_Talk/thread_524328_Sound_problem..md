---
title: "Sound problem."
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by demonicdude on 2007-08-13
Hello all, i recently installed Ubuntu 7.04 (actually just today =D). A Dual-boot of Windows Xp and Ubuntu Now i am trying to fix my sound. Nothing at all comes through when i log on or log off (which I've done a lot today trying to fix my internet as well ).  I looked at the volume control, everything is not muted, i tried all the switches. I've also been tryin got research the problem on the forums, but alas i cannot find anything that will help.. (maybe i don't know what to search for -.-...). 

     Anyways, as i was researching, i saw that often you guys would ask for two pieces of information: lscpi and lsmod | grep snd  and both those two relate to audio... well here they are.. =D

lscpi:
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)

and lsmod | grep snd:
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
        Flags: bus master, slow devsel, latency 32, IRQ 3
        I/O ports at df00 [size=64]
        Capabilities: <access denied>

I don't if any of that will help, but its worth a shot. 
Oh and also, i installed ubuntu version 6.*something* some time while back, and my sound worked perfectly with me not having to do anything. 

and also also, i got my internet working YAY!

---

### Post by carloslosgrande on 2007-08-13
Hi, have you tried double clicking on the sound icon in your top panel? this will give you a gui to play around with your volumes.
Alternatively, in 'termina'l type 'alsamixer'
Both of these may show your mute on.

---

### Post by demonicdude on 2007-08-13
hmm.. tried both of them, unmuted everything, nothing seemed to change =(. Sound still does not work...

Oh on a side note if anyone could answer this for me too: When i install Opera where does it install the files to?!?!? o.o.

---

### Post by Arthur Archnix on 2007-08-13
I presume sound works fine in XP?

Reboot the computer, go into bios, and reset to defaults. Reboot into ubuntu. Sound?

If not, start at this thread [here]("http://ubuntuforums.org/showthread.php?t=205449").

---

### Post by carloslosgrande on 2007-08-13
One more thing, have you checked in >system>preferences>sound to make sure its on 'autodetect'?
You can test in there as well

oh, and your opera files are in your home directory, mine looks like this   home/ozymandias/.opera
if you do 'ctrl h' you'll see all the hidden system files.

---

### Post by demonicdude on 2007-08-13
yup sounds works fine in Windows Xp

will reseting the bios do anything else to my computer? Or shoud it not really affect it or have any real side effects..? Plus.. getting into bios.. damn i havent done that in a long time.. I think i have to press f8 repeatdly.. or f1... -.-.. One leads me to options like safe mode in win xp, other is bios.. Bah i'll try both.

Edit: Updating stuff, so its going to take me around 5-10 minutes to do that >.<....

edit # 2: uggh the updates are taking forever....

I didnt see your last post carlos =D. To answer that: i've tried that stuff too with no luck either =(
thank you for the opera thing though! Didn't think they would hide it lol.

---

### Post by Arthur Archnix on 2007-08-13
No, resetting will have no adverse effects on your system. Truthfully, there's no reason to believe it will have ANY effect, all I know is that this is how I got my sound working after installing XP and Vista prior to Ubuntu.

---

### Post by demonicdude on 2007-08-13
no luck =(. i looked at that guide before, but it all looked so complicated =[. Any other helpfult resources? =D? (i'm going to try to follow that guide, but probably in the morning cause its getting kind of late =) )

---

### Post by Arthur Archnix on 2007-08-13
No, it really is the best general troubleshooter I've come across. It helps you narrow down your problem so that you can do better searches on the forums, internet, and ask better questions if you don't find your answers. 

And really, it's pretty simple if you follow it step-by-step. For instance, does this return anything?
```
aplay -l
```
If something shows up it means ubuntu has detected and installed the drivers for your sound, there's just something minor to tweak, like volume levels, muting, etc. If nothing shows up it could mean the correct driver hasn't been installed.

Here's another simple suggestion from the guide:
```
grep 'audio' /etc/group
```
You should see your name there. Like below. If you don't, well, check the guide for how to fix.
```
arthur@archnix:~$ grep 'audio' /etc/group
audio:x:29:arthur
```

The guide goes into more detail, just try one thing at a time. And don't try any compiling or such until you've tackled all the simple stuff first.

Best,

---

### Post by demonicdude on 2007-08-13
well, just tried the guide. No luck again =(.  it looks like the card is installed and everything, but probably some hidden switch is ticked or something like that. I was having problems with these speakers before on my Windows Xp, turns out i had to turn it from analog output to digtial? Anyone know how i could do that or if its preset like that?, i'm going to test out another set of speakers i have (which are analog). 

Alright! so with my other speakers, sound works, (these are really old compaq speakers though and very annoying lol). So i think right now the problem is what i stated in the first paragraph. I couldn't do it through windows xp, magically it happened >.<. Hopefully there's an easy way to do that in here?

Edit: Another quick question, is there anyway of keeping my windows partition mounted on boot? Like through the /etc/modules/ thing? I have all my music there, and i do not feel like wasting 2 gigs of space on ubuntu =D. Thanks for all the help you guys are giving =)

---

### Post by demonicdude on 2007-08-13
*bump~~~*

---

### Post by demonicdude on 2007-08-13
el bump dos.

I think all i have to do is switch the sound from an analog output to a digital one, but i still can't figure it out.

Edit: this is what i need to do in linux,  but these instructions are for  windows xD 
[http://support.microsoft.com/kb/302710](http://support.microsoft.com/kb/302710)

---

### Post by kingofkings on 2007-08-13
I'm having the same problem. I tried everything. It's no the sound card. I have no idea what to do. Please help.

---

### Post by Arthur Archnix on 2007-08-13
I'm glad you found your sound working. In your sound preferences you'll find different settings. One of them (in mine at least) let's me choose between analogy and digital. Try flipping those around a bit and see if that works. Restore to autodetect if not.

You might also contact [this]("http://ubuntuforums.org/showthread.php?t=199408") guy, and see if he got them working, and if so maybe he could post the solution on his thread.

This site [here]("http://cybernightlife.50webs.com/ba735.html") has more.

It looks like Alsa defaults to analog, but can be switched to digital.

---

### Post by demonicdude on 2007-08-13
mhmm thats the problem, alsa doesn't have an analog/digital switch =(. And i saw that website before =D, where would i get emu10k? 

I'll be also on the lookout of that guy's thread just to see if he gets any solution to that too =)

---

### Post by Arthur Archnix on 2007-08-13
There are some suggestions [here]("http://gentoo-wiki.com/HOWTO_Dolby_Digital_Out_(AC3,_SPDIF)") on how to make alsa use digital only.

---

### Post by demonicdude on 2007-08-13
Wait, maybe  i haven't downloaded everything that i could from alsa? Maybe i'm like missing a file that allows me to do that?

---

### Post by Arthur Archnix on 2007-08-13
> **demonicdude said:**
> Wait, maybe  i haven't downloaded everything that i could from alsa? Maybe i'm like missing a file that allows me to do that?

Not too sure demonicdue. I stick to answering questions in the beginning forums for a reason. :)

I think you should post a new thread to the multimedia and video forum. Put as much detail in there as you can. For instance, the output of aplay -l, the audio card found on lspci, the output of lsmod, what kind of speakers you have, and then why it works in windows but not linux. And mention that sound works if you plug other cheapy speakers in.

I'll be watching it with interest, hoping you find your answer [-o<

Best,

---

### Post by demonicdude on 2007-08-13
Alright, thanks for all the help you gave =D. I'll do what you said now =X *hopes for the best*

---

### Post by Arthur Archnix on 2007-08-13
For any who follow in the path of demonicdude, the thread continues [here]("http://ubuntuforums.org/showthread.php?t=524969").

---

### Post by bjarneh on 2007-08-13
it usually mounts at startup (the windows partition i mean), but if not, you can set it up in /etc/fstab ie. adding a line somewhat similar to this one....
 

/dev/sda1      /media/sda1   ntfs    defaults      0     1


(if your Windows partition is sda1 and you want to mount it on /media/sda1 and so on....
and i understood your question right)

---

