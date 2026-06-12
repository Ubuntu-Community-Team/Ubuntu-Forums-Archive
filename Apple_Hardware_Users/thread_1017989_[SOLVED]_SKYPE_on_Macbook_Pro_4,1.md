---
title: "[SOLVED] SKYPE on Macbook Pro 4,1"
date: 2008-12-21
forum: Apple Hardware Users
---

### Post by Chrisj303 on 2008-12-21
I'm having serious issues talking to friends on Skype.

I have been fiddling around for ages. As it stands, I can hear everybody else perfectly - but they can't hear me at all.

What settings do I need to get this to work? 

ANY help would be greatly appreciated.

---

### Post by Chrisj303 on 2008-12-21
Forget it.

Solved it myself. Just tried out every possible combination of driver settings until it worked.

On the MBP 4,1 it appears to be (from the Skype "Sound devices" menu)

Sound In : HDA Intel (hw:intel,2)
Sound Out : HDA Intel (hw:intel,0)
Ringing: Default Device.

---

### Post by Chrisj303 on 2009-01-18
Right, it turns out that isn't the best method by a long shot.

If you do what I said in my last post, you will most likely find that you won't be able to watch Flash or listen to any other audio while making a skype call. Its also quite likely to make firefox crash after a while.

I've been dicking around with this for quite some time - and have finally come up with a method of setting up Skype on the Macbook Pro 4,1 that works like it should - i.e you can listen to multiple sound sources and even adjust the volume independently for each application, Flash and FF also work perfectly whilst on Skype.

After scouring the net, I found the following information, and then after playing around with the Skype/Sound Pref's, I found the solution.

I now undertsand that the problem was to do with PulseAudio. I'm not a techy, so I can't really go further than to say that!

*Please note that this is for UBUNTU 8.10 INTREPID IBEX ONLY*



Anyway, I first backed up and then deleted my previous audio configurations.
>  mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/  

>  sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf

Then made sure I had Adobe Flash and any needed Pulseaudio libraries and config tools.

>   sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree

Made sure "libflashsupport" was NOT installed.

> sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound

Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "PulseAudio". Close the application when you're finished.

. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

Note: If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:
> pulseaudio & pavucontrol



Edit /etc/apt/sources.list:

> gksudo gedit /etc/apt/sources.list

If they don't already exist, add the following lines to the end of this file and save:

> deb [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/psyke83/ubuntu](http://ppa.launchpad.net/psyke83/ubuntu) intrepid main

Update your repositories and upgrade packages:

> sudo apt-get update && sudo apt-get dist-upgrade

*You may be warned that some packages cannot be authenticated - that's normal. Simply press "y" to confirm installation of unsigned packages.*

Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a bug in Intrepid):

> alsamixer -Dhw

*REBOOT*

Open Skype,select OPTIONS > SOUND DEVICES.
Use the following screenshot to make the right selections.

[IMG]http://i330.photobucket.com/albums/l410/TR606/Screenshot-Options.png[/IMG]

Then go SYSTEM>PREFERENCES>SOUND and do the following;

[IMG]http://i330.photobucket.com/albums/l410/TR606/Screenshot-SoundPreferences.png[/IMG]

*Now you should be all set!*

Login to a flash site like you tube and play a video, then in Skype go OPTIONS>MAKE A TEST CALL. You will be able to hear both your voice and Youtube playing back - and nothing will crash!

You can independently adjust applications volume, by using "Gnome Volume Control" ;
> gnome-volume-control

[IMG]http://i330.photobucket.com/albums/l410/TR606/Screenshot-VolumeControl.png[/IMG]

Hope this helps! I found this a really frustrating problem.

---

### Post by ColBuendia71 on 2009-02-21
Thanks so much for this. Cleared up my entire problem. Cheers!

---

### Post by b419kid on 2009-03-23
Hello,

I followed all the directions and I messed up somewhere because I can't get my mic working. I'm really new to *ubuntu* so I could have made a really stupid mistake. 

I could have messed up on the commands but I copy and pasted so I don't think so.

It may be on a setting but i re-checked all settings.

I don't know. 

I'll be working on the settings but if anyone has any idea that would be really helpful.
Thanks in advance.
_________________________________________________________________________

<UPDATE-Mar 23 6:21 pm> I think I found out why- in pulse audio applet my playback stuff is on mute plus in-put and out-put. 

Anything to do with it?

---

### Post by b419kid on 2009-03-23
> It may be on a setting but i re-checked all settings.
Woo it worked! Hope it continues !


cheers!

---

### Post by b419kid on 2009-03-24
Anyone who comes to this forum please note:

On the above instructions I had to change the directions for a step to get my internal mic working. 


file:///home/brandon/Desktop/Skype%20settings

Here's the change... 
HDA Intel (hw:Intel,2) instead of HDA Intel (hw:Intel,0)
<---- In skype settings---->
___________________________________________________________

I can only speak for me so I can't know if its nessary because others have gotten their mic to work with the original steps.

---

