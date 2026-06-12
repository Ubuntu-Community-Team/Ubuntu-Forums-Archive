---
title: "Sound extremely quiet on a new Dapper install"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-01-31
I have a recent install of Ubuntu 6.06 (Dapper) on an Aspire 5102WLMi, I also installed the Kubuntu desktop environment (but I use gnome).

The sound is extremely quiet, I can only hear it slightly if I lift the laptop and place my ears next to the loudspeakers.

Whether it is a video file or an mp3 or an audio CD, its very very quiet.

If I type 'alsamixer' into the terminal I get:

```
alsamixer: function snd_mixer_load failed: Invalid argument
```

some more info:

```
me@ubuntunbk:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by annda on 2007-01-31
can you install/run gnome-alsamixer to adjust the master and PCM levels? (what about kmix, since you also have kde?)

if not, maybe reinstalling alsamixer would do.

---

### Post by PartisanEntity on 2007-02-03
Thanks for the tip, it worked :)

---

### Post by PartisanEntity on 2007-02-03
I was happy too early. It doesnt seem to save the position of the PCM slider in gnome-alsamixer. When I restart the computer the PCM slider is once again at the bottom (hence very quiet).

---

### Post by PartisanEntity on 2007-02-04
bump :)

---

### Post by Moulton on 2007-02-04
I find that some sound mixer settings are not saved across sessions or reboots, especially those involving PCM playback and recording levels.

It might be necessary to insert a command-line entry into .xinitrc to establish personal defaults when an X-Session is begun.

---

### Post by PartisanEntity on 2007-02-04
> **Moulton said:**
> 
It might be necessary to insert a command-line entry into .xinitrc to establish personal defaults when an X-Session is begun.

I'm afraid that sounds like it would be above my rather modest linux skills, could you please show me how that is done? Would be really appreciated. Thanks.

---

### Post by PartisanEntity on 2007-02-06
bump

---

### Post by PartisanEntity on 2007-02-07
just another friendly bump :)

---

### Post by PartisanEntity on 2007-02-07
another monologues bump :)

---

### Post by dannyboy79 on 2007-02-07
hey, how about instead of bumping every day, you actually TRY to find a solution on your own. For example: I typed "alsa-mixer not saving settings" into gogle and found a BUNCH of answers. Here you go: [http://www.linuxforums.org/forum/suse-linux-help/22253-restoring-alsamixer-settings-boot-2.html](http://www.linuxforums.org/forum/suse-linux-help/22253-restoring-alsamixer-settings-boot-2.html)

---

### Post by PartisanEntity on 2007-02-07
Thanks for the link.

---

### Post by PartisanEntity on 2007-02-08
Still no go:

From the thread posted by dannyboy79:

> I had this problem. The solution in my case was that KMix was overiding Alsamixer on reboot.
Click the green icon lower left->Multimedia->Volume control->KMix.
In the window that opens chose the "settings" item in the menu.
From the drop down list chose "configure KMix". Uncheck "Restore volumes on login". That's it.
Now adjusting Alsamixer followed by alsactl store is all that's necessary.

I tried this, and then when I typed in the terminal:
```

sudo alsactl store
```

I get this message:

```
alsactl: get_control:149: Cannot read control info '2,0,0,Capture Volume,1': Invalid argument
```

Here is are the capture volume setting from /var/lib/alsa/asound.state:

```
	control.11 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		iface MIXER
		name 'Capture Volume'
		index 1
		value.0 0
		value.1 0
	}
```

Before I get flogged again, yes I have searched both ubuntuforums and google, havent found anything helpful yet.

Thank you.

---

### Post by dannyboy79 on 2007-02-08
i would suggest following the comprehensive sound guide found within this forum or try this here: [http://users.dslextreme.com/~craig.lawson/linux_notes/audio.html#Troubleshooting_audio_problems](http://users.dslextreme.com/~craig.lawson/linux_notes/audio.html#Troubleshooting_audio_problems)

I just realized why the solution I gave you previsouly didn't work, it's because you can't even get into alsa-mixer to begin with so of course alsactl store isn't going to work.

here looks to be a promising link, it is a link to a guy who talks about owning the exact same laptop as you and how he installed and uses Debian on it. and as you may know, Ubuntu is built upon Debain.
good luck
[http://www.burghardt.pl/wiki/articles/installing_and_using_debian_on_acer_aspire_5102wlmi](http://www.burghardt.pl/wiki/articles/installing_and_using_debian_on_acer_aspire_5102wlmi)

---

### Post by dannyboy79 on 2007-02-08
From that link, down further on the page are peoples comments, here are some promising comments for ya:

-Hi, and thanks for the help I found here. I tried to fix the ALSAMIXER problem on Ubuntu Dapper but it only works on the first reboot. On the following reboot I can't use ALSAMIXER. Do you think I should put this line: "alsactl -F -f /root/asound.state restore" in my /etc/rc-local ? Thanks again. 
      
-Yes, you have to restore it every boot. Also make sure /var/lib/alsa/asound.state are not saved and restored by other boot scripts (or when module is loaded). 
      
-Thank you for this quick answer. So I've checked my /var/lib/alsa and asound.state and it is indeed restored every other boot. Shall I put this line: "rm /var/lib/alsa/asound.state" at the end of my /etc/rc-local ? I don't know how to check for other boot scripts that could load that file. Thanks. Guillaume. 
      
-Look for invocation of program called alsactl. It's store command saves asound.state and restore sets card controls to values defined in this file. 

-Hello there. You gave me the proper hint. I checked the /etc/init.d/alsa-utils script and it explains at the beginning of the file what to do to restore and save mixer levels on shutdown or bootup. I chose not to save at shutdown and hence removed /etc/rc6.d/K50alsa-utils.(this might help someone else). In fact none of the other proposals worked. But this one did ! So thank you very much once again for the great job you are providing and long live Debian and Linux system. Guillaume. 



again, good luck.

---

