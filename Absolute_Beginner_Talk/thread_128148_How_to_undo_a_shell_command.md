---
title: "How to undo a shell command?"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by Mike_SMD on 2006-02-10
Hi,
I've been having problems getting sound to run on the game Chromium and I tried to use a fix that came from another thread. I typed the following command at the terminal;

$ sudo usermod -G audio [username]

(substituting the username bit for my actual username)

Now *none* of the games seem to work (chromium, planet penguin racer, neverball). They all crash almost instantly at startup and I get the following error;

mike@ubuntu:~$ chromium
randomizing.
SDL initialized.
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
mike@ubuntu:~$

My question is this... how do I undo the command that I issued? Things worked before except for the sound in Chromium... I'd like to get back to that state. I've already looked up the usermod command online but I see no way to remove my user from that group. If that's what needs to be done. 

Here's what I have;

mike@ubuntu:~$ groups
mike audio
mike@ubuntu:~$

Any help would be greatly appreciated as at this point I'm basically kind of stuck.

Thanks very much...


Mike_SMD.

---

### Post by chronusdark on 2006-02-10
try doing the same thing but with +G rather than -G

---

### Post by chronusdark on 2006-02-10
also if you want goto System -> admistration -> users and groups and add yourself to the games group

[Edit] my bad that doesnt work

---

### Post by Mike_SMD on 2006-02-10
Ok.
I did that (the + advice) and now the games aren't crashing but I'm on to something new again. At this point, both Chromium and Planet Penguin Racer will begin without sound, but Neverball crashes immediately and gives me this response;

mike@ubuntu:~$ /usr/games/neverball
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x75
  Serial number of failed request:  107
  Current serial number in output stream:  109
mike@ubuntu:~$

Hmmm... that's actually different from what I got the first time. The first time it also included a line about sound not being installed. Do you think it would make any difference if I tried to reinstall the sound drivers (I think that means ESD, ALSA and OSS) and then reconfigured my X server? I only bring up the X server as my available list of possible resolutions and refresh rates seems to have changed as well...

All very odd.
Thanks for the quick response and any more advice would be great,


Mike_SMD.

---

### Post by chronusdark on 2006-02-10
did you install these games with a package manager (synaptic/apt-get)?

if so try removing them and readding them 

in the mean time also goto -> system -->administration --> users and groups 

then double click on your name 

then click on the user permissions and check that you are allowed to use the audio and video devices

your issues sounds to me like a permissions issue but i may be wrong

---

### Post by chronusdark on 2006-02-10
yea try to reconfig x if what i told you doesnt work i cant remember the command but perhaps someone will jump in here in a bit and help us out

---

### Post by Mike_SMD on 2006-02-10
Ha ha...
Nothing is ever easy.

I just tried to reconfigure X using the following command;

sudo dpkg-reconfigure xserver-xorg

As usual it asked for my password and then nothing. Returned me to the command prompt without anything obvious happening at all. I also just tried to use synaptic to remove the games for a reinstall but it doesn't start up either, neither does using the menu to navigate to: 

system -->administration --> users and groups

Which shows a tab at the bottom of the screen for a few seconds and then just disappears with nothing further happening as well. It might be a permissions thing... do you know of a command that I can use to check my permissions from the shell? Or, uhhh... you know... anything else that I could try?

Thanks,

Mike_SMD.

---

### Post by Mike_SMD on 2006-02-10
Ok.
I follwed anoth thread's advice and edited my sudoers file, adding myself onto the list at the bottom. Now synaptic works and I was able to check on the permissions of my user. I added all the permissions. I reconfigured X server but it isn't quite working as expected as I still can't seem to get the options set for resolution and refresh rate... though I did just reselect them in the list. I only logged out and then back in though... perhaps I'll try a full reboot and then see what happens.

Anyways, I'll do that... and then get back to this for one last quick update before I have to run and pick up my special lady friend...

Thanks for everything so far,

Mike_SMD.

---

### Post by Mike_SMD on 2006-02-10
Ok... the reboot did it and I've now got access to the full whomp of resolutions. Now I'm off but I'll check back later on for any other wisdom that might be offered. Thanks for the help and have a nice day!


Mike_SMD.

---

### Post by cwaldbieser on 2006-02-10
> **Mike_SMD]Hi,
I've been having problems getting sound to run on the game Chromium and I tried to use a fix that came from another thread. I typed the following command at the terminal said:**
> 

(substituting the username bit for my actual username)

Now *none* of the games seem to work (chromium, planet penguin racer, neverball). They all crash almost instantly at startup and I get the following error;

mike@ubuntu:~$ chromium
randomizing.
SDL initialized.
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
mike@ubuntu:~$

My question is this... how do I undo the command that I issued? Things worked before except for the sound in Chromium... I'd like to get back to that state. I've already looked up the usermod command online but I see no way to remove my user from that group. If that's what needs to be done. 

Here's what I have;

mike@ubuntu:~$ groups
mike audio
mike@ubuntu:~$

Any help would be greatly appreciated as at this point I'm basically kind of stuck.

Thanks very much...


Mike_SMD.

In your home directory, create a file called ".openalrc".  Paste the following in it:
```

# Contains user settings for OpenAL
# Goes in ~/.openalrc

# Use ALSA (Advanced Linux Sound Architecture) (also valid: sdl, native)
;;(define devices '(alsa))

# Four speaker surround with ALSA
;;(define speaker-num 4)
;;(define alsa-out-device "surround40:0,0")

#Use ESD (esound => Enlightend Sound Daemon)
;;(define devices '(esd native))
(define devices '(esd sdl native))

# Use SDL (Simple Direct Media Layer) backend.
;;(define devices '(sdl native))

```
All the lines with ";;" in front are commented out.  I use esd (enlightened sound daemon) through SDL (simple direct media layer), so that one is uncommented.  If that doesn't work for you, try commenting and uncommenting various options to match the settings you use.

---

### Post by Mike_SMD on 2006-02-11
Ok.
I'm going to give this a shot but I just have one quick question...

Not to sound like a complete newbie, but as I more or less am still dripping wet and trailing my umbilical cord behind me in the linux dirt, what do you mean by 'commented out'...? My complete experience so far with anything programming related was a grade five class using logo over twenty years ago. I'm late to this whole scene...

I take it that this refers to the pairs of semi colons?
If they are present then the line is ignored?

Just checking, I'm getting both strangely used to and slightly more timid about tinkering and breaking things these days.

Thanks very much for the help!



Mike_SMD.

---

### Post by kabus on 2006-02-11
> I've been having problems getting sound to run on the game Chromium and I tried to use a fix that came from another thread. I typed the following command at the terminal;

$ sudo usermod -G audio [username]

That's some very bad advice, because the "usermod -G" command doesn't just add a user to a group, it also removes him from all groups he was already a member of that aren't explicitly listed after the -G.
Which thread did that come from ?

---

### Post by Mike_SMD on 2006-02-12
Hi Kabus...
So that's what it does? Damn, it actually explains quite a bit about all the other ridiculous problems that I had as a result. Unfortunately it could very well have been my own fault as opposed to simple poor advice, I was following another thread entirely and trying to interpret it on my own rather than having it given as a response to a particular question. The origional thread it came from was here...

[http://www.ubuntuforums.org/showthread.php?t=75581](http://www.ubuntuforums.org/showthread.php?t=75581)

Other than that still haven't had the opportunity to try anything else related to Chromium. Never enough free time... 

Never enough free time!
But tonight I'll give it a go and then post my results.

Have a nice day!


Mike.

---

### Post by Mike_SMD on 2006-02-13
Well, a big old thanks goes out to cwaldbieser!
The fix you provided seems to do the trick and so far has had nothing in the way of negative side effects as far as I can tell. Just for my own personal benefit, what exactly did those lines of code do? I have suspicions, but nothing all that concrete... 

At any rate, nice job and thanks!


Mike_SMD.

---

