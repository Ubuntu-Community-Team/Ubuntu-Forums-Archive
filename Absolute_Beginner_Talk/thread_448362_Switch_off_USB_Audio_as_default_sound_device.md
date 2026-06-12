---
title: "Switch off USB Audio as default sound device?"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-05-19
I found a command which I entered into the terminal and forced my USB sound card to be my default audio device but I am on vacation now and want to go back to the internal speaker but I can for the life of me remember what the command was. It wasnt in reply to one of my own posts so I can't search for it that way. It was only a single line of code. Anyone know what it much be and how to switch back to my internal sound hardware?

I have changed system>prefs>sound and tried right clicking on the speaker icon but these dont help.

Curiously when I type alsamixer I get this message. 

```
tabby@tabby-laptop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

also this is the result of my cat/proc/soundcards

```
tabby@tabby-laptop:~$ cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at 0xd0100c00, irq 11

```

Any ideas?

---

### Post by nivenmk1 on 2007-05-19
Rather much of a noob myself, so take my $0.02 for what it's worth, but  System > Preferences > Sound may have some answers for ya.  I use it to switch between the USB headset and external speakers on one of my boxes.  I just use the dropdown boxes to select the proper output/input devices.

Sadly no clue on the alsamixer portion of your post, don't know enough yet! =D

---

### Post by tabithaboof on 2007-05-19
I tried that but unfortunately I get an error

"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."

when trying to switch to ALSA

---

### Post by sonicborg on 2007-05-23
much in a similar state, i have a usb headset, and external speakers. in XFCE i load up the mixer program, select the USB headsetup as my device, but still sound just comes out of the external speakers.

I find that in Xmms and audacious i can select the device in the program and it plays the music through the USB headset then.

But i would really like to be able to do it quickly and easily via the mixer settings so that it effects across the entire system. when in xmms/audacious, it only effects those programs. I would like it so i can watch movies, play games etc via the headset by simply changing the device in the mixer.

Or even better, like in windows, when i just simply plugin the usb headset, it becomes the default sound device for everything

---

### Post by d-rothe on 2007-05-27
for me

/usr/bin/asoundconf set-default-card <card number>

does the trick. You will have to restart your player to make the changes take effect.
asoundconf is in the package alsa-utils.

But I'd like to know how to do this without restarting the player. It would be possible to trigger the plug-in event of the usb device with some entry under /etc/udev/rules.d/, but I still need some tool to communicate with the alsa libs after the player started.

---

### Post by paradoc on 2007-06-02
Hi!...........there's usually a quick no-brainer way:

System>sounds (sound playback) > USB audio(from choices) > test >sine wave sound..........sorted, eh!!

---

### Post by paradoc on 2007-06-02
So sorry I jumped in too soon on this thread:(,

I can get USB playback on these self-powered speakers in Edgy, but on further testing, not in Feisty, which I've recently installed. They test OK in Feisty, but they don't work.....help/obs please?

Originally I got them for a tinny-sounding laptop, which was fine: they work with Edgy, but not with Feisty--and I have updated it, and installed Adamant1988's sticky thread(thanks Adam..!)

Work in progress...(sigh)

---

### Post by paradoc on 2007-06-03
(following day,further to previous post.........found I couldn't play USB sound in Feisty)

     With System>preferences>sound>USB Audio...the 'test' is ok--- leave settings as, and Close.
Ubuntu Sax.ogg (in examples), now plays from both HD installation and (if setup the same) on liveCD  in Feisty
If left on Autodetect though,(in sound preferences), the USB speakers will be silent when the main speakers are turned off.

   All of which now seem to be quite a normal response if setup is as above.
   The self-powered USB speakers are independent of sound cards, as they have their own built-in sound.

It was a little confusing at first to me,  I hope this helps someone with the same problem.

__________________________________

'And who are you?' said he---'Don't puzzle me', said I     (Tristram Shandy)

---

