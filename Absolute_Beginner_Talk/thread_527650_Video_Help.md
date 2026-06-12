---
title: "Video Help"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by .Panic on 2007-08-16
Hello,

I want to watch some videos with firefox in browser. I asked my friend first and he gave me these steps:

```
gksudo gedit /etc/apt/sources.list
enter these two lines and save your file
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
sudo apt-get update
sudo apt-get install mplayer
sudo apt-get install mozilla-mplayer
```

I have done all that and when I try to watch it it says:

Click here to download plugin.
I click where it says click.
Unknown Plugin (application/x-mplayer2) Manual Install

Any help would be appreciated. :)

Thanks,

.Panic

Edit: I can stream stuff from youtube if that helps.

---

### Post by diatribe on 2007-08-16
have you restarted firefox?

---

### Post by wolfen69 on 2007-08-16
good luck. ive been trying for months to get streaming video to work. ive tried everything humanly possible. no go. strangely, in ubuntu ultimate, streaming video works fine in firefox.

---

### Post by .Panic on 2007-08-16
> **diatribe said:**
> have you restarted firefox?

Yes I have restarted firefox.

---

### Post by phenest on 2007-08-16
You need codecs installed.

Here's a tip:

When the video window in the browser appears (no video though), right click and choose "Open with Movie Player". Movie Player can't player it either, but with Feisty, it will suggest you download a suitable codec. Once downloaded, Movie Player will play the video. If not, refresh the web page and try again. Some codecs require 2 or 3 attempts downloading different packages each time.

Worked for me.

---

### Post by .Panic on 2007-08-16
To clear things up this is what I'm looking at,
[http://i18.tinypic.com/5y7mbfl.png](http://i18.tinypic.com/5y7mbfl.png)

[IMG]http://i18.tinypic.com/5y7mbfl.png[/IMG]

---

### Post by phenest on 2007-08-16
You're running the 64 bit version of Ubuntu. The plugin needed is Flash. This doesn't exist for 64 bit.

Here is the solution (worked for me):
[http://ubuntuforums.org/showthread.php?t=341727]("http://ubuntuforums.org/showthread.php?t=341727")

---

### Post by phenest on 2007-08-16
D'oh! I really got to start wearing my glasses. Not Flash. But the problem is the same. You need 64 bit codecs for this to work.

Hold on, I'll be back ...

---

### Post by .Panic on 2007-08-16
> **phenest said:**
> D'oh! I really got to start wearing my glasses. Not Flash. But the problem is the same. You need 64 bit codecs for this to work.

Hold on, I'll be back ...

Thanks. I'm waiting for you answer.

---

### Post by phenest on 2007-08-16
Follow this guide and install w64codecs:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by RomeReactor on 2007-08-16
Hi. You'll need to install w32codecs to play wmv videos. There are some patent/copyright issues with some codecs, w32coedcs included. Read the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") page for some information regarding this issue.

If you still want the codecs, then open a terminal and enter:
```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```
this will add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories to your sources.list; then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
to get the gpg key and update the repository information on your package managers; and lastly:
```
sudo apt-get install w32codecs
```

**EDIT**: **.Panic**, I didn't find any indication that you're running Dapper 64 bit; are you?

---

### Post by .Panic on 2007-08-16
> **phenest said:**
> Follow this guide and install w64codecs:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Okay. I dl it to the desktop. I right click on it and the click GDebi Package Installer. A little bit later it says,

The package might be corrupted or you are not allowed to open the file. Check the permissions on th file. 

What do I do know??

@ RomeReactor
You will have to excuse me. I don't know if I am.

---

### Post by RomeReactor on 2007-08-16
Try downloading it again; it's possible the download is corrupted.

If you **are** using 64 bit, you can get the w64codecs package from [here]("http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu1_amd64.deb"). If you're using 32 bit, then get the w32codecs from [here]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1_i386.deb"). If you don't know or don't remember which architecture you're running, enter this in the terminal:
```
uname -m
```
If it says **386** or **686**, then you're running 32 bit Ubuntu; if it reads **x86_64**, then it's 64 bit.

---

### Post by .Panic on 2007-08-16
> **RomeReactor said:**
> Try downloading it again; it's possible the download is corrupted.

If you **are** using 64 bit, you can get the w64codecs package from [here]("http://packages.medibuntu.org/pool/non-free/w/w64codecs/w64codecs_20061203-0medibuntu1_amd64.deb"). If you're using 32 bit, then get the w32codecs from [here]("http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20061022-0medibuntu1_i386.deb"). If you don't know or don't remember which architecture you're running, enter this in the terminal:
```
uname -m
```
If it says **386** or **686**, then you're running 32 bit Ubuntu; if it reads **x86_64**, then it's 64 bit.

I have 32 bit. I'm also re-downloading atm.

Edit: So I should dl the 32 bit one???

---

### Post by .Panic on 2007-08-16
What am I doing wrong? I'm still at the same result as post nubmer 6. Maybes restart the computer???

---

### Post by RomeReactor on 2007-08-16
Yes the 32 bit version is the one you need. If you already restarted Firefox and the problem persists, try rebooting the machine. If it still doesn't work after that, you want to remove the Totem plugin for Firefox (**totem-mozilla**) and install instead the mplayer plugin (**mozilla-mplayer**).

---

