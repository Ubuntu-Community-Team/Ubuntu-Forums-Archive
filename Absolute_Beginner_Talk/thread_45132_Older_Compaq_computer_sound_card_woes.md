---
title: "Older Compaq computer sound card woes"
date: 2005-06-28
forum: Absolute Beginner Talk
---

### Post by midwest on 2005-06-28
I have just taken the leap into the linux world w/ubuntu.  Love the interface, the flexibility, & the (steep) new learning curve...  I've read post & thread & web page & indexes, but I can't seem to find the answer.  I have an older Compaq computer w/an on board ESS 1869F ISA (I think) sound card/chipset.  It doesn't appear that it has been recognized by the OS (looking at the system/devices list).

There's probably a simple fix that I haven't been able to decipher.  Looking for newbie help here; trying to kick the Big Brother Bill (BBB) Windows habit (3 other existing BBB computers in the house) starting with this older piece of hardware.

Any help would be greatly appreciated.

---

### Post by skoal on 2005-06-28
From a terminal, what does 'lspci | grep audio' return?
Also from a terminal, what does 'lsmod | grep snd' return?

I think you need the module 'snd-es18xx' for your particular ISA soundcard.  So, you could type in 'modprobe snd-es18xx' and then try 'alsamixer' and see if you can get any sound while playing an mp3 or something like that...

\\//_

---

### Post by heltinde on 2005-06-29
You might wanna look at this: [https://bugzilla.ubuntu.com/show_bug.cgi?id=8852](https://bugzilla.ubuntu.com/show_bug.cgi?id=8852)

To be honest, I haven't got mine to work properly yet. Well sometimes if I write esd in the terminal I can play cd's.

If you get yours to work with ALSA, then please tell me how.

---

### Post by az on 2005-06-29
[QUOTE=midwest]I have just taken the leap into the linux world w/ubuntu.  Love the interface, the flexibility, & the (steep) new learning curve...  I've read post & thread & web page & indexes, but I can't seem to find the answer.  I have an older Compaq computer w/an on board ESS 1869F ISA (I think) sound card/chipset.  It doesn't appear that it has been recognized by the OS (looking at the system/devices list).

There's probably a simple fix that I haven't been able to decipher.  Looking for newbie help here; trying to kick the Big Brother Bill (BBB) Windows habit (3 other existing BBB computers in the house) starting with this older piece of hardware.

Any help would be greatly appreciated.[/QUOTE]

[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

---

### Post by midwest on 2005-06-29
[QUOTE=heltinde]You might wanna look at this: [https://bugzilla.ubuntu.com/show_bug.cgi?id=8852](https://bugzilla.ubuntu.com/show_bug.cgi?id=8852)

To be honest, I haven't got mine to work properly yet. Well sometimes if I write esd in the terminal I can play cd's.

If you get yours to work with ALSA, then please tell me how.[/QUOTE]


Tried the fix described on bugzilla.  I get an error when I then run modprobe snd-es18xx that looks like this:

WARNING: /etc/modprobe.d/soundcard.conf line 4: ignoring bad line starting with 'irq=5'

I did the Copy-n-paste, so it's not my typing...  Maybe this line should have been part of the previous line?  If so, how do I go about editing the file?

---

### Post by midwest on 2005-06-29
[QUOTE=skoal]From a terminal, what does 'lspci | grep audio' return?
Also from a terminal, what does 'lsmod | grep snd' return?

I think you need the module 'snd-es18xx' for your particular ISA soundcard.  So, you could type in 'modprobe snd-es18xx' and then try 'alsamixer' and see if you can get any sound while playing an mp3 or something like that...

\\//_[/QUOTE]

Tried both the lspci & lsmod & returned nothing (although the 1st time I tried, the lsmod returned values).  I now don't get anything to return from root or user terminal.

I tried the fix shown on [https://bugzilla.ubuntu.com/show_bug.cgi?id=8852](https://bugzilla.ubuntu.com/show_bug.cgi?id=8852) as I've replied.  It seems like this is the right direction, but haven't gotten there yet.  On re-boot, the error listed (WARNING: /etc/modprobe.d/soundcard.conf line 4: ignoring bad line starting with 'irq=5') now shows up many times in the information listing.

Ideas??

---

### Post by andlinux21 on 2005-06-29
here try this and see if it helps you at all it worked for me in gnome

[http://www.ubuntuforums.org/showthread.php?t=44831&highlight=sound+problems](http://www.ubuntuforums.org/showthread.php?t=44831&highlight=sound+problems)

---

### Post by skoal on 2005-06-29
Ooops! silly me.  I said use 'lspci' thinking it was an integrated sound chip, and I'm still not quite sure if you have an ISA card or some ESS integrated sound chip (on a laptop for example).  Anyways, since 'lspci' returned nothing, I'll assume it's an ISA card.

[list]
[*]Did you follow the link azz posted?
[*]Check your BIOS from a cold/warm {re}boot and record any settings noted in the sound config menu (if any).  Post back with those if possible.
[*]From a terminal, what does 'ls -d /proc/bus/p*' return? Do you see '/proc/bus/pnp'?
[*]Can you post back (*with an attachment* to your post) the following file, 'dmesg.txt'? Create it by doing the following from a terminal: 

dmesg > /tmp/dmesg.txt

That should tell me if the kernel found your ESS device, hidden away in there somewhere I'm sure.
[*]If still no luck, try and download the "isapnptools" package from our repos.  I do not think it's in a standard repo so you may have to add others in your /etc/apt/sources.list file first.  Anyways, install that package and issue the following from a terminal:

sudo pnpdump

report back what that says, by file attachment or wrapping it in *quotes* back here in your response.

* 'pnpdump' is an old tool for 2.4 kernels, and I haven't heard of any cases for a 2.6 kernel not configuring an ISA PnP card yet on it's own.  But I use all PCI, so I could be wrong here and maybe some cards still ned it. I haven't used 'isapnp' tools since 97(?) trying to get my SoundBlaster Modem working.  It's a hairy beast.  Very ugly method.  It's the tammy faye baker of all configs.
[/list]

/edit Oops! see post above mine first...

\\//_

---

### Post by wvslkr on 2005-06-30
I use this sound chipset in an old Compaq Deskpro.  Old Enron box off of ebay.  The only thing I have had to do is add a line to /etc/modules > snd-es18xx isapnp=0.  This works under Ubuntu and Mepis on this box,P233.  It works also under Kanotix poor mans install on this same machine,but if I recall correctly Kanotix picked it up in the install.

When It boots alsa throws am error message that pnp settings are invalid on both Mepis and Ubuntu.  It then says it is going to autoconfig and proceeds to set the card-chip up and it works.  I can only suggest that entering the irq values are confusing something in alsa or the kernel.  Try removing any irq and or dma settings that have been made in other places and try the line in /etc/modules as stated above.

Note that the isapnp=0 is needed, won't work without.  I have also used other Compaqs with this chipset without problems, deb based and slack based.  

Also it will have to be twiddled to work with esd or alsa or arts, whichever you are using. 

My 2 cents:  Hope it helps. :)

---

### Post by midwest on 2005-07-01
[QUOTE=skoal]Ooops! silly me.  I said use 'lspci' thinking it was an integrated sound chip, and I'm still not quite sure if you have an ISA card or some ESS integrated sound chip (on a laptop for example).  Anyways, since 'lspci' returned nothing, I'll assume it's an ISA card.

[list]
[*]Did you follow the link azz posted?
[*]Check your BIOS from a cold/warm {re}boot and record any settings noted in the sound config menu (if any).  Post back with those if possible.
[*]From a terminal, what does 'ls -d /proc/bus/p*' return? Do you see '/proc/bus/pnp'?
[*]Can you post back (*with an attachment* to your post) the following file, 'dmesg.txt'? Create it by doing the following from a terminal: 

dmesg > /tmp/dmesg.txt

That should tell me if the kernel found your ESS device, hidden away in there somewhere I'm sure.
[*]If still no luck, try and download the "isapnptools" package from our repos.  I do not think it's in a standard repo so you may have to add others in your /etc/apt/sources.list file first.  Anyways, install that package and issue the following from a terminal:

sudo pnpdump

report back what that says, by file attachment or wrapping it in *quotes* back here in your response.

* 'pnpdump' is an old tool for 2.4 kernels, and I haven't heard of any cases for a 2.6 kernel not configuring an ISA PnP card yet on it's own.  But I use all PCI, so I could be wrong here and maybe some cards still ned it. I haven't used 'isapnp' tools since 97(?) trying to get my SoundBlaster Modem working.  It's a hairy beast.  Very ugly method.  It's the tammy faye baker of all configs.
[/list]

/edit Oops! see post above mine first...

\\//_[/QUOTE]


I need to probably update where I've been.  First of all, my system is also a 2nd had desktop.  Compaq Presario 5190.  400 MHZ P2 (I think), no sound card - on board ESS chipset.  I've not done much research into the nuts & bolts; pieced info together from what I saw w/the previous W98 install & my XP install that I've since removed.  I may have to do some more digging to get the actual information on the pieces & parts in the box.

After my last ordeal, I logged off & (for no reason) logged back on as another user.  I was floored... sound filled the room!  Not sure what changed.  If there's anything worse than having a tough problem to solve, it's solving it w/out knowing what you did.  Anyway, I logged back into my account & had sound there too.  The one thing that caught my eye was the CD player had something about OSS on it (not ALSA that I've been struggling with).  Not sure if that is significant or not.

I figured out how to edit my soundcard.conf file (a tip from another post).  Got everything on one line for line 3.  Now when I boot, I don't get the IRQ errors.  Subtle mistake that I made.  The file soundcard.conf is stored in modprobe.d and is as follows:

alias sound-slot-0 snd-card-0
alias snd-card-0 snd-es18xx
options snd-es18xx enable=1 isapnp=0 port=0x220 mpu_port=0x388 fm_port=0x330 irq=5 dma1=1 dma2=0

When I  read the post that described how to create this file, the listing showed 4 lines with the 4th having irq=5 dma... etc.  This posting shows 3 lines which is correct, I believe.

I attached my bios screenshot taken right after re-boot.  Not sure if that was what you were looking for.  If I'm reading the screen right, it also does not look like a sound device was detected.  

Still fighting.  Still learning.  Still wanting sound.  Appreciate the time.

---

### Post by midwest on 2005-07-01
[QUOTE=andlinux21]here try this and see if it helps you at all it worked for me in gnome

[http://www.ubuntuforums.org/showthread.php?t=44831&highlight=sound+problems](http://www.ubuntuforums.org/showthread.php?t=44831&highlight=sound+problems)[/QUOTE]

SUCCESS!!!

I added the line: 'sb io=0x220 dma=1 mpu_io=0x330 irq=5' to the end of my etc/modules file and voila'!  sound.  I haven't tried mp3's, but the cd player and the Gnome event sounds seem to work just fine.

Thanx to all who led me to the answer.   I feel muuuuch better now.  Any ideas on what that line actually is telling the OS?..  soundboard, memory, dma.. mpu.. interrupt request.. ???

Rock on! =D> 

EVEN THOUGH I DON'T KNOW WHAT I'M DOING, IT DOESN'T MEAN I'M WRONG!

---

### Post by meraya on 2005-09-04
Guys

i have almost the same issue in my old compaq presario 18xl381 with an ESS-SOLO1 sound card ESS1938. 

modprob es1938 gives this.
FATAL: Module es1938 not found.

lsmod | grep snd gives this:
snd_es1938             20388  1
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  2 snd_es1938,snd_pcm_oss
snd_page_alloc          9604  1 snd_pcm
snd_opl3_lib           10112  1 snd_es1938
snd_timer              23300  2 snd_pcm,snd_opl3_lib
snd_hwdep               9220  1 snd_opl3_lib
gameport                4608  1 snd_es1938
snd_mpu401_uart         7168  1 snd_es1938
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  2 snd_opl3_lib,snd_rawmidi
snd                    50276  12 snd_es1938,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device


i checked all the posts on the subjuct "microphone" (123 posts) and i could not figure out what the fcuk is wrong with it

Here is what i get from the Control Centre - Sound System:

"Sound server informational message
Error while initialising the sound driver
device: default can't be open for capture (device or resource busy).
The sound server will continue, using the null output device."

I tried checking the mic on gnome meeting and this is what i get:

"impossible to open the selected audio device (ESS ES1938 (Solo-1) for recording. Please check your audio setup, the permissions and that the device is not busy).

I tried all possible checking and unchecking of microphones lines in and all the other stuff suggested in the posts.
My microphone was working perfectly with SUSE 9.1 and i'm reaching the top of the frustration and on monday i have to start working with Skype and Gnome meeting!

Please help
Cheers

---

