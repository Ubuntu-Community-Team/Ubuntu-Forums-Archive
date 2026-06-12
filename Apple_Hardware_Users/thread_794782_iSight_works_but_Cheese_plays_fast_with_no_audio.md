---
title: "iSight works but Cheese plays fast with no audio"
date: 2008-05-14
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-05-14
Hi,
I'm on 8.04 with a Macbook Air. My iSight gets a fine preview and records in Cheese, but any video I record in Cheese plays back at a hyper fast speed and I cannot get any audio with the recorded video. 

I tried different sound settings in the preferences, but nothing worked there. Cyber linked me to the cheese site at one point to check for updates but I can't say I found anything...

Thanks for any pointers or hints,...
Frank B.

---

### Post by cyberdork33 on 2008-05-15
Well you need to figure out whether your Mic is just off first. Run alsamixer make sure the channel is unmuted. Additionally, a "Capture" channel needs to be unmuted as well. Try using the sound recorder app to work on the Mic and that will determine if it is an issue with cheese or just your system in general (and probably needs it's own thread).

Your video playback issue sounds like it is cheese or gstreamer. I would suggest sending an email to the cheese mailing list and see if anyone has an answer for you there, and/or file a bug report against cheese in bugzilla.

Mailing list:
[http://mail.gnome.org/mailman/listinfo/cheese-list](http://mail.gnome.org/mailman/listinfo/cheese-list)

Bug Tracking System for Cheese:
[http://bugzilla.gnome.org/](http://bugzilla.gnome.org/)

---

### Post by benanzo on 2008-05-15
I've experienced the same issue.  Unfortunately Cheese in SVN requires recompiling some core Gnome libraries from cvs (which I don't really want to do) so I haven't been able to test for fixes upstream.  However, cheese-0.2.3 (the version in Gutsy) still works great and without the nasty video frame drops.

If you want to install the old Cheese on Hardy without uninstalling or overwriting the current version you can do this:

Open a terminal (Applications -> Accessories -> Terminal) and type:
```

$ sudo apt-get build-dep cheese

```
This will install all the libraries required to build Cheese from source.
```

$ cd $HOME/Desktop
$ wget https://launchpad.net/ubuntu/gutsy/+source/cheese/0.2.3-0ubuntu1/+files/cheese_0.2.3.orig.tar.gz
$ tar -zxvf cheese_0.2.3.orig.tar.gz -C ./
$ cd cheese-0.2.3
$ ./configure --prefix=/usr/local
$ make
$ sudo make install

```
This configures the older version of Cheese to install itself starting in /usr/local rather than /usr (which is where the current version is installed.)  This allows us to have two separate versions without them overwriting each other or otherwise getting in the way.

Important to note, if you run "cheese" on the command line you'll be launching the Hardy default version because /usr/bin is checked *before* /usr/local/bin.  If you want to launch the old version (the one we just installed you need to run:
```

$ /usr/local/bin/cheese

```
You might notice that the old entry for Cheese in the Gnome menu has disappeared and moved to Applications -> Accessories.  By default this still just calls "cheese" so it will launch the Hardy version.  If you want it to use the old version then change the command from just "cheese" to "/usr/local/bin/cheese" --

If you want to uninstall the version of Cheese that we just installed just go back into the source directory "$HOME/Desktop/cheese-0.2.3" and do:
```

$ sudo make uninstall

```
If something got messed up and the Hardy version of cheese is acting funny after installing/uninstalling the old version just do:
```

$ sudo apt-get install --reinstall cheese

```
That will reinstall the default version shipped with Hardy.

Good Luck!

---

### Post by Brightbelt on 2008-05-15
Thanks Benanzo. ...The older version solves the speedy playback problem, but I still have no sound. 

I may need to do some cross-application testing for my mic as Cyber suggested, but I have already turned up the mic volume in my Alsa Gui and that still does not help the problem.

Many Thanks, Frank B.

---

### Post by Brightbelt on 2008-05-16
Ok, I tried the Sound Recorder and no sound seems to record or playback. So I guess that this is a system problem and not necessarily related to Cheese.
 
Thanks, Cyber....

Frank B.

---

### Post by yousufinternet on 2008-05-16
i have the same problem 
with gtk-recorder 
there is no sound

---

### Post by cyberdork33 on 2008-05-16
I may not have explained this well before, but for your microphone to capture audio, you also have to enable a "capture" channel and increase it's level in order for your machine to capture audio. This is in addition to the mic channel level. 

Use the commandline tool 'alsamixer' as it will show every channel available to you, while the gui mixer often hides some options unless you enable them some other way. 

There is also a Microphone how to in the Macbook wiki page. It may be worth trying for you machine as well:
[https://help.ubuntu.com/community/MacBook#head-a089225bf23ccb59d5bc846e89776ea9890305a3](https://help.ubuntu.com/community/MacBook#head-a089225bf23ccb59d5bc846e89776ea9890305a3)

---

### Post by Brightbelt on 2008-05-16
Thanks, Cyber. Yes some clarity there helped me at least. And the community how-to on Sound taught me a lot!!

So now: 
1- I have my mic unmuted in the sound settings and the gain is up. 
2 - I have enabled the volume on a Capture Channel in the Alsa Mixer.
3 - I have even set my device preference in Sound Preferences to 'Mic' 

But still, I no sound will record. Here are some odd points I'm curious about:

- In the Sound Recorder, there exists an input choice for 'Mic Boost' but not 'Mic'. Also there is a 'Capture' option there for the input. Which should I choose?

- In the Sound Preferences (the menu from the speaker icon etc), both Mic and Capture are listed in the Device Preference list. Which Should I choose?

Hopefully these points will help. As always,

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-16
> **Brightbelt said:**
> Thanks, Cyber. Yes some clarity there helped me at least. And the community how-to on Sound taught me a lot!!

So now: 
1- I have my mic unmuted in the sound settings and the gain is up. 
2 - I have enabled the volume on a Capture Channel in the Alsa Mixer.
3 - I have even set my device preference in Sound Preferences to 'Mic' 

But still, I no sound will record. Here are some odd points I'm curious about:

- In the Sound Recorder, there exists an input choice for 'Mic Boost' but not 'Mic'. Also there is a 'Capture' option there for the input. Which should I choose?

- In the Sound Preferences (the menu from the speaker icon etc), both Mic and Capture are listed in the Device Preference list. Which Should I choose?

Hopefully these points will help. As always,

Many Thanks, Frank B.

In sounds recorder, I think you have to choose Capture. I will have to mess with this more tonight as I do not have a machine to experiment on right now.

In the Sound preferences, you can add the other channels by going to file > properties, or something like that. there is a way to select what channels to show. My iMac has more than 1 capture channel so you might want to check for that too.

---

### Post by Brightbelt on 2008-05-16
Thanks Cyber. Yes, I've tried the Sound Recorder with the setting set to 'Capture' and I've tried it with the 'Capture 1' setting as well. Still no recorded sound.

It feels like some of the pieces are at least coming together. 

I need to reference to Benanzo for a bit regarding the old Cheese Software. I installed it and it solved the fast playback, but I still got no audio. 

Also, I couldn't delete ANY of the video tests I recorded. Whenever I chose a video and selected 'move to trash', the program simply shut down and the video was there again when I restarted the program. 

So I had to delete the old Cheese program and go back to the Hardy version. I don't have a lot of space on my Ubuntu partition, so I can't afford to have video files pile up on me. 

Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-16
> **Brightbelt said:**
> So I had to delete the old Cheese program and go back to the Hardy version. I don't have a lot of space on my Ubuntu partition, so I can't afford to have video files pile up on me.Yea I think I remember that bug. The files are located in a hidden directory in your home folder (.cheese i think), so you can delete them manually.

---

### Post by cyberdork33 on 2008-05-16
> **cyberdork33 said:**
> In sounds recorder, I think you have to choose Capture. I will have to mess with this more tonight as I do not have a machine to experiment on right now.

EDIT: While messing with things and writing the below instruction, everything just quit working. I started alsamixer instead and hit [TAB] a couple of times to get all the channels to show, then maxed out everything and hit [ESC]. Then I started up gnome-sound-recorder again and everything worked just like before. There is apparently something fishy going on, but I don't know what it might be. Hopefully, this info helps.

OK,  I right-clicked on the speaker Icon in the tray, and selected "Open Volume Control". In the window that opens, I checked under File > Change Device and made sure that my audio card was selected (0: HDA Intel Alsa mixer) I went to Edit > Preferences, and put a check mark in every box. This will make every channel and switch available in the gnome mixer.

For my iMac5,1 I have to turn up both the Master and PCM channels to hear anything.

On the Options Tab, you can set the input device to use for each of the available capture channels. (Top one is Capture, and Bottom is Capture1... I think). Additionally, on the recording tab, I unmuted the "Capture" Channel (using the microphone icon button below the slider) and raised the level all the way.

In gnome-sound-recorder (Applications > Sound & Video > Sound Recorder) I could select "Capture" or "Mux" and still record sound as long as the "Capture" channel was unmuted.

---

### Post by Brightbelt on 2008-05-17
I appreciate all your efforts Cyber and I've followed them to the letter. But still no recorded sound in Sound Recorder.

I apologize ahead of time for the following rant:
I don't know about other distros in this regard, but with Ubuntu, I think this method involving "Capture" and the alsamixer, which isn't included by default, is extremely anti-intuitive.

I work in computer audio and use Mac audio programs everyday. I've used windows-based pro audio programs as well.

This method in Linux looks like a mix and match between several disparate elements that, when set right, somehow work together. It's maddening trying to figure out the logic going on. 

I understand the logic behind 'Capture' needing to be set. I understand that...but when one person says "check only these 2 elements in the list" and another says "check them all", who knows what's really going on?? 

End Rant.

As Always,....Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-17
> **Brightbelt said:**
> I appreciate all your efforts Cyber and I've followed them to the letter. But still no recorded sound in Sound Recorder.

I apologize ahead of time for the following rant:
I don't know about other distros in this regard, but with Ubuntu, I think this method involving "Capture" and the alsamixer, which isn't included by default, is extremely anti-intuitive.

I work in computer audio and use Mac audio programs everyday. I've used windows-based pro audio programs as well.

This method in Linux looks like a mix and match between several disparate elements that, when set right, somehow work together. It's maddening trying to figure out the logic going on. 

I understand the logic behind 'Capture' needing to be set. I understand that...but when one person says "check only these 2 elements in the list" and another says "check them all", who knows what's really going on?? 

End Rant.

As Always,....Many Thanks, Frank B.
I understand the frustration. For some reason, the Macs always seem to be the oddball case with ALSA. IDK when the Capture channel thing started, but I too thought it was a bit cumbersome. I guess if I had several inputs to add to a mix, something like that might desired. Sorry I couldn't help you more.

---

### Post by Brightbelt on 2008-05-17
Thanks Cyber. I know Ubuntu and I know sometimes one has to wait and let time do its thing and a solution will come along.

That's the way of Linux sometimes...;)
Frank B.

---

