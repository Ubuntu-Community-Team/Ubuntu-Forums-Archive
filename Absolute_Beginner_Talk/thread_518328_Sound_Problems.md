---
title: "Sound Problems"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by eamonn on 2007-08-05
I've been having this problem for a while now and I still can't figure it out. The sound on my laptop won't work. When I type in "lpsci" I get this in response

> 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
Subsystem: Rioworks Unknown device 203a
Flags: bus master, medium devsel, latency 0, IRQ 10
I/O ports at 1c00 [size=256]
I/O ports at 18c0 [size=64]
Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
Memory at e0100800 (32-bit, non-prefetchable) [size=256]
Capabilities: <access denied>


So it recognizes my sound card.

But, when I type in "alsamixer" and "amixer" in the terminal I get the following responses:

> alsamixer: function snd_ctl_open failed for default: No such device > amixer: Mixer attach default error: No such deviced

This is weird because if I go to the Gnome Alsamixer I can work everything around, I just don't get any sound. But if I go to CLI alsamixer, it still doesn't work, and I still don't get sound.

Somebody else told me "how unusual - Gnome alsamixer works, but the CLI alsamixer doesn't" and that "there are other sound drivers (OSS), but if you were using that, then I don't think the Gnome alsamixer should work either." So, if somebody could help me figure this out I'd really appreciate it.

---

### Post by moore.bryan on 2007-08-05
*got mine working by following [this guide]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and making sure to set my kernel variable in every command (e.g. ./configure kernelpath=/usr/src/linux-headers-2.6.20-16-server).*

---

### Post by eamonn on 2007-08-05
Thanks, I went to that guide and typed in the following command:

> sudo apt-get install build-essential ncurses-dev gettext

and I got the following response:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package ncurses-dev is a virtual package provided by:
  libncurses5-dev 5.5-2ubuntu1
You should explicitly select one to install.
E: Package ncurses-dev has no installation candidate


So, I explicitly select one (of what) to install? What do I do here?
And how do I give "ncurses-dev" an installation candidate?

---

### Post by moore.bryan on 2007-08-05
*install libncurses5-dev*

---

### Post by eamonn on 2007-08-05
Sorry for my naivitee, do I put "libncurses5-dev" in place of "ncurses-dev" on the command "sudo apt-get install build-essential ncurses-dev gettext"?

---

### Post by eamonn on 2007-08-05
Well, I tried doing that, and it worked. Then I went to step two and that worked as well. When I got to step 3, where I entered the command: 

> sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver-1.0.14.tar.bz2
sudo tar xjf alsa-lib-1.0.14a.tar.bz2
sudo tar xjf alsa-utils-1.0.14.tar.bz2


I got the following response:

> eamonn@ubuntu:~$ sudo mkdir -p /usr/src/alsa
eamonn@ubuntu:~$ cd /usr/src/alsa
eamonn@ubuntu:/usr/src/alsa$ sudo cp ~/downloads/alsa* .
cp: cannot stat `/home/eamonn/downloads/alsa*': No such file or directory
eamonn@ubuntu:/usr/src/alsa$ sudo tar xjf alsa-driver-1.0.14.tar.bz2
tar: alsa-driver-1.0.14.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
eamonn@ubuntu:/usr/src/alsa$ sudo tar xjf alsa-lib-1.0.14a.tar.bz2
tar: alsa-lib-1.0.14a.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
eamonn@ubuntu:/usr/src/alsa$ sudo tar xjf alsa-utils-1.0.14.tar.bz2
tar: alsa-utils-1.0.14.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


What gives? Did I do something wrong?

---

### Post by eamonn on 2007-08-05
Anybody?

---

### Post by stil on 2007-08-05
Hou need to find where you saved those .tar files. It seems they're not in the right place for the instrucitons to work. The rest of the commands become redundant after line four.

---

### Post by eamonn on 2007-08-05
Thanks, I see what I missed. Sorry, but on the HowTo it says "Download the latest version of alsa from [WWW] Alsa project (driver, library, and utils) to a directory..." and I click on the "alsa-driver" or libs, or utils link I see a huge list of things for download. Do I download every single one or specific ones? I'm so sorry for all the work this is. Thanks for your help brian and still.

---

### Post by ayenack on 2007-08-05
Try this.

**gksudo gedit /etc/modprobe.d/alsa-base**

Add this line at the end of file.

**options snd-hda-intel model='your_card'**

Where your_card = the model of your intel sound chip.

---

### Post by eamonn on 2007-08-05
I'm sorry, from this: 

> Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

Where do I get the name of my sound card?

---

### Post by eamonn on 2007-08-05
Or is it "snd-intel8x0" ?

---

### Post by eamonn on 2007-08-05
> **ayenack said:**
> Try this.

**gksudo gedit /etc/modprobe.d/alsa-base**

Add this line at the end of file.

**options snd-hda-intel model='your_card'**

Where your_card = the model of your intel sound chip.

I tried that using "intel8x0" and I still don't have sound.
How do I update, or download for the first time, the Alsa drivers, libraries, and utilities?

---

### Post by ayenack on 2007-08-05
Good question. I think but am not sure that it'll be one of these ICH4/ICH4-L/ICH4-M.

I'll try to find out and post back when I find something.

---

### Post by eamonn on 2007-08-05
Okay great. Thank you for the help.

---

### Post by eamonn on 2007-08-06
This is from [URL="https://help.ubuntu.com/community/HdaIntelSoundHowto"]HdaIntelSoundHowto
[/URL]
> #

Download the latest version of alsa from [WWW] Alsa project (driver, library, and utils) to a directory (eg. ~/downloads). In the following we assume that the latest version is 1.0.14. Please change this in accordance with the one you downloaded from the Alsa project site.

    *

      [WWW] alsa-driver
    *

      [WWW] alsa-lib
    *

      [WWW] alsa-utils



I don't know how to download those files and get them ready for the next step in the walkthrough. Could somebody help me with this?

---

### Post by anewguy on 2007-08-06
Try  a silly little step for me, if you can.  If you have the speaker showing on your top bar for the volume control, double-click it.  If the window that opens doesn't say Volume Control (Alsa Mixer), then click on "File" and "Change Device" and select the "Alsa Mixer".  Now back on the main volume control window, click on "Edit" and then "Preferences".  Scroll through the list - if you see "External Amplifier", click on the leading box so there is a check mark in it, then close the Preferences window.  Now back on the main volume control windows, click on "Switches" and then uncheck external amplifier there.  It sounds counter intuitive to enable it in the preferences and then turn it off in the settings, but that made the sound on my laptop work - maybe it will work for you.:)

---

### Post by ayenack on 2007-08-06
I can't work out what your actual card is called.

Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03) 

My best bet for your card is that 82801DB is what you should put for the name of the sound device. If this does not work try adding /DBL/DBM to the end of the name or variations on this i.e. 82801DBL and so forth.

I'm sorry I could not be of more help on this. I'll keep trying to work this one out.

---

