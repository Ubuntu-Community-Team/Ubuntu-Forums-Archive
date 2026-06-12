---
title: "[SOLVED] Installation path of w32codecs?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by perixx on 2007-10-12
I've just installed the w32codecs via Synaptic...

but I still need to provide Gxine with the installation path. Can someone tell me where they are, pls?

perixx

---

### Post by por100pre1 on 2007-10-12
They should be in /usr/lib/codecs .

---

### Post by FuturePilot on 2007-10-12
They're also in /usr/lib/win32 in addition to /usr/lib/codecs

---

### Post by perixx on 2007-10-12
ehh... I can't find them in either directory :-?

---

### Post by rsambuca on 2007-10-12
You can find all the files and directories they are in if you use the Synaptic Package  Manager.  Right-click a package that you have installed, and select "Properties".  There is a tab labeled "installed Files" which shows all directories and files.

---

### Post by perixx on 2007-10-13
Hi rsambuca!

Seems, like it went wrong in the first place... I cannot install w32codecs via Synaptic. I have to manually search it and when I want to install, there's no "install candidate"  and repositories aren't configures properly. I need to do some further investigation.

Thank you.

perixx

---

### Post by rsambuca on 2007-10-13
If you add the medibuntu repositories, you can get the codecs.  [Here is a link]("http://medibuntu.sos-sts.com/repository.php").  Just run the two terminal commands for your version of Ubuntu.

---

### Post by perixx on 2007-10-13
Oh great! Thanks for this link..! 
It's always a little depressing to read 'look for this repository' or 'adjust the repositories to your need' and stuff like that. Something concrete is always making me happy :guitar:
 
Is there a way to copy and paste those links into the terminal somehow? I don't know how to produce those special characters like the vertical aligned slash, since I have a German keyboard layout... or perhaps you know how to type in the appropriate ascii-code?

perixx

---

### Post by rsambuca on 2007-10-13
> **perixx said:**
> Oh great! Thanks for this link..! 
It's always a little depressing to read 'look for this repository' or 'adjust the repositories to your need' and stuff like that. Something concrete is always making me happy :guitar:
 
Is there a way to copy and paste those links into the terminal somehow? I don't know how to produce those special characters like the vertical aligned slash, since I have a German keyboard layout... or perhaps you know how to type in the appropriate ascii-code?

perixx
Just highlight the commands using your mouse, then press the middle mouse button on the terminal and it will paste it.

Alternatively you can highlight the commands, right-click and select copy.  Then move to the terminal, and press Control-V to paste.

---

### Post by perixx on 2007-10-13
OK, I found out the second solution in the meantime and installed the codecs...
Thanks a lot! :]
Can you despite tell me about the ascii-code ?

perixx

---

### Post by rsambuca on 2007-10-13
Sorry, no idea about the asci code. Maybe check under "System - Preferences - Keyboard".

---

### Post by perixx on 2007-10-13
Hi again, rsambuca..!

I successfully installed the w32codecs now, alas, I'm not fully sure what it was good for... :-]

The only improvement is, that I can play .avi files with Gxine now - at least without sound (don't know, if my testfile has sound!), mp3's (definitely without sound).
Wav's - still no go; that's why I installed it in the first place...

perixx

---

### Post by rsambuca on 2007-10-13
OK, let's start over here.  You never really said in this thread what you were trying to accomplish.  I take it from your last post that you are having a bunch of multimedia issues regarding playback.  Is this correct?  Maybe if you listed out what works, what doesn't, and what you have tried, then perhaps we can figure something else out.

---

### Post by perixx on 2007-10-14
Very true! Here's my sad Gxine-story....

Currently I can play:

with Gxine

- .ogg files (produced 'segmentation fault once, though)
- .wmv files (video + sound)
- .avi files (don't know if with or without sound, have only mute testfile)


with Aplay

- .wav files


tried playback with Gxine:

- Audio-CD's -> Gxine autoplays it, with secondwise and periodically disrupted sound output (app. every 5 seconds one second playing) 
- .wav -> freezes Gxine - have to kill it with Process manager 
- .mp3 -> 'playing back' without sound output
- .m4a -> 'playing back' without sound output
- .mid -> error 'no demultiplexer found'
- .mpg/.mpeg -> error 'no demultiplexer found' 
- .mov -> Gxine freezing and grey error window popping up; Tasks: 6884/Z & 7009/S
- .vob (DVD-Video), sometimes shown as 'unknonwn', sometimes as 'DVD_VIDEO' in Thunar -> error 'no demultiplexer found' / one particular DVD, shown WITH name in Thunar, (autoplay): error 'No Plugin found. File either doesn't exist, has wrong file permissions or the URL is faulty' + 'read error from /dev/dvd' (these is are translations); when I close Gxine and re-open a file from that DVD again, the same error as with other DVD's occurs. 

Besides, if Thunar is open during such eject/inserting orgies, it's gonna hang-up to about 90%
  
Well, I guess that's all...

What do you think about this mess?

perixx

---

### Post by perixx on 2007-10-14
Ok, after finally really installing it: 

I had to find the medibuntu's repository-link first, add it to the '3rd party repositories' and then 'update' Synaptic. After that, I could install the w32codecs via Synaptic. The terminal-commands are: 

1. sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

2. wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update.

3. sudo apt-get install w32codecs.


Now I can confirm the 2 locations:

Symlink /usr/lib/win32 to 
/usr/lib/codecs

Mission accomplished!
Thanks for help... :)

perixx

---

