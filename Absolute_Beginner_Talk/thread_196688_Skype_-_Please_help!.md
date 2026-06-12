---
title: "Skype - Please help!"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by henkk78 on 2006-06-14
Hi,

Skype installed fine and all, but the first time I made a call I could hear the other person but they couldn't hear me.

After that, trying to call anyone has Skype give an error saying: "Problem with sound device".

Also, all sound on my PC is now gone! (mplayer for example)

At one point I also got an error saying: During the previous startup, Knotify crashed while instantiating Knotify. Do you want to try again or disable aRts sounds output?

If you choose to disable aRts output now, you can re-enable it later or select an alternat sound player in the System Notifications control panel.

Any advice? 

I have an nForce3 motherboard and am using onboard sound. 

Henk

---

### Post by d3dtn01 on 2006-06-14
This sounds like a typical problem with skype. From what I understand, after using skype, skype neglects to close some audio device or something and therefore the audio isn't available for other applications. There are a lot of threads about this. The simple solution is apparently to install skype-dsp-hijacker.

To get the hijacker package, first open your sources.list file

```
sudo gedit /etc/apt/sources.list
```

then add the following text to the bottom of your /etc/apt/sources.list file

```
deb http://users.lichtsnel.nl/~seveas/ breezy-seveas extras
```

Now install the hijacker:

```
sudo apt-get install skype-dsp-hijacker
```

You'll need to run the hijacker before you start skype. An easy way to do this is to just change the command that is run when you click on the skype menu item. To do this, right click on the applications menu at the top left of the screen. Choose Edit Menus. This will open the alacarte menu program. Find skype (it's probably under the Internet icon in the left column of alacarte). If you right-click on skype and choose properties, you'll see that you can change the command. Type in the location of hijacker (probably: /usr/local/bin/skype_dsp_hijacker).

Hope this helps.

---

### Post by Ma_USMC on 2006-06-14
I'm having this exact problem using Google Talk.  Is the dsp-hijack package specfic to skype? Or could this apply to Gtalk as well...

---

### Post by henkk78 on 2006-06-15
Hi,

Thanks for the help so far. 

skype hijacker did prevent Skype from stuffing up my general sound settings. However, I had no luck actually getting skype to work.

anything else i need to do?

---

### Post by henkk78 on 2006-06-15
I only just noticed that my microphone doesn't seem to work, period. 

I checked that my mic is not muted in Volume Control (which says "NVidia CK8S (Alsa Mixer)" if that's relevant).

help will be much appreciated!

---

### Post by user1397 on 2006-06-15
double click on the volume icon, and go to Edit > Preferences, and make sure the following **are** ticked: Master, PCM, Line-in, CD, Microphone, Mic Boost, PC Speaker, and Capture.  Then close that, and mess around with the volume of each one until u can hear your recording, using this program: applications >sound & video > sound recorder.

---

### Post by henkk78 on 2006-06-18
Thanks Erik,

You got me on the right track there! 

The problem was that the switch for 'Mic Front Input' was not enabled in Volume Control. 

Once I enabled that, Skype was working. Though for Sound Recorder, I also had to make sure the Capture slider was not crossed out for Mute or for Audio Capture. Skype automatically got these going! 

cheers,

Henk

---

