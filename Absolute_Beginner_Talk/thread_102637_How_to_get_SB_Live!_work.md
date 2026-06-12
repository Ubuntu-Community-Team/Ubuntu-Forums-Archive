---
title: "How to get SB Live! work?"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by carlossaatana on 2005-12-12
These Linux things are really confusing me. Everything seems to be more and more complicated. Ok, I have got problem with my soundcard: Sound Blaster Live!. I think that Ubuntu does not even recognize my soundcard. I can not even find it on device manager, allthough everyting else is there as supposed. Is there somekind of driver I should get or do I have to install something from Synaptic Package Manager?

---

### Post by Estariel on 2005-12-12
The driver should come with the kernel, so there is no need to install it manually.
My SBLive! just works, so maybe yours is just muted...?

I don't know the name of the mixer application in GNOME (I use KDE), but you can use a non graphical application: Open a terminal and do the following
```
alsamixer
```

A mixer should appear. If it says "MM" below a channel, the channel is muted. Unmute all channels, adjust the volumes, and try to play a music file.

---

### Post by carlossaatana on 2005-12-12
I solved my problem by taking out SB Live! and started using on-board soundcard. Now everything works out just fine.

---

### Post by PatrickMay16 on 2005-12-12
Very odd. My Sound Blaster Live! worked straight away with no problems.
I've even been able to get hardware midi working with it.

---

### Post by carlossaatana on 2005-12-12
My SB Live! stopped working even in Windows Xp few days ago.  Maybe whole soundcard is totally fucked up.

---

### Post by NotJustANewbie on 2005-12-12
lol, my SB Live! "just worked" on install too.

---

### Post by carlossaatana on 2005-12-12
I going to struggle with my SB Live! someday, but now I am so busy. Gotta read for exam.

---

### Post by Micro Rotors on 2005-12-12
My SB Live is not working either and when I put 
```
alsamixer
```
 it says I am using the onboard Nvidia that I dont want to use.

Any hints here?

---

### Post by pianomany2k on 2005-12-12
[QUOTE=PatrickMay16]Very odd. My Sound Blaster Live! worked straight away with no problems.
I've even been able to get hardware midi working with it.[/QUOTE]

Patrick:

How did you get the MIDI working?? The only thing that doesn't work on my SB Live! is the MIDI.

---Pianomany2k

---

### Post by Delkster on 2005-12-12
[QUOTE=pianomany2k]How did you get the MIDI working?? The only thing that doesn't work on my SB Live! is the MIDI.[/QUOTE]

EDIT:
I'm assuming that you mean hardware midi playback. I don't know about connecting midi devices to the sound card.


You'll need to load the appropriate driver module (snd_emu10k1_synth, I think) and load a soundfont onto the SB Live! card.

The module comes with the kernel but I don't think it's automatically loaded by Ubuntu so you may need to load it manually. You can add the line "snd-emu10k1-synth" without the quotation marks to /etc/modules to ensure that the module is loaded every time the system starts. You can open it up in a text editor by entering the following command in the terminal:

```
sudo gedit /etc/modules
```

Just add the new line at the end of the file.

You can find a soundfont on the original SB Live! Windows driver CD. There are also free soundfonts available on the internet but I haven't tried them. If you want to try the soundfont supplied on the Creative driver CD, according to some websites you could look for them in /media/cdrom/AUDIO/Common/SFBANK (I guess I also found them at that location but I don't remember it exactly anymore and I don't have the CD at hand). I'm using 8MBGMSFX.SF2. Copy the file somewhere on the hard disk (I put it in /usr/local/share/soundfont/ but I'm not sure what would be the most correct location for it). You can then load the soundfont with the asfxload utility (probably needs to be run with root privileges, i.e. with sudo):

```

sudo asfxload [the_path_and_filename_of_the_soundfont]

```

You can find the asfxload utility in the awesfx package which is available in the universe repository.

The soundfont will only remain loaded until the next system reboot or shutdown. I've put "asfxload /usr/local/share/soundfont/8MBGMSFX.SF2" in a startup script so it gets run on every system start. If you don't want to start messing with that, another option is to just run the command every time you need midi playback.

There may also be some other magic to it but I don't remember anything else I'd have needed to do to get it working. If you can't get it working, ask here or try to find more information on the web. There are some howtos on the web, although some of them may be a bit outdated and the information may not be very easy to find. I remember it took a while for me to get it working.

Someone else may be able to recommend a better soundfont. Like I said, I haven't tried any others yet.

---

### Post by carlossaatana on 2005-12-13
[QUOTE=Micro Rotors]My SB Live is not working either and when I put 
```
alsamixer
```
 it says I am using the onboard Nvidia that I dont want to use.

Any hints here?[/QUOTE]

Disable onboard Nvidia via BIOS.

---

### Post by christhemonkey on 2006-01-17
I use Ultimate.SF2 from [www.hammersound.net](www.hammersound.net)
[http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=72;SoundFont_Location_Selected=Download%20UK;SoundFont_Filename_Selected=Ultimate.zip]("http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=72;SoundFont_Location_Selected=Download%20UK;SoundFont_Filename_Selected=Ultimate.zip")

---

