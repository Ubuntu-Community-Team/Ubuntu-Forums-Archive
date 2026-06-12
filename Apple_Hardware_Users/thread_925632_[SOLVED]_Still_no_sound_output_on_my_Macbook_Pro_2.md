---
title: "[SOLVED] Still no sound output on my Macbook Pro 2,1"
date: 2008-09-20
forum: Apple Hardware Users
---

### Post by dsmoot on 2008-09-20
I've read the FAQ but I think the FAQ assumes gnome and not Kubuntu.

I'm still not able to get the sound working.  I've done the following from the wiki:
```

sudo apt-get install build-essential linux-headers-$(uname -r)
module-assistant alsa-source
sudo dpkg-reconfigure alsa-source
sudo module-assistant a-i alsa-source

```

And I added the recommended line to /etc/modprobe.d/alsa-base:
```

install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel

```

But at this point the FAQ diverges from Kubuntu territory.  The FAQ says 
> 
2. Increase the volume (both using the key combination and the system tray applet) tomunity Ubuntu Documentation                                        [https://help.ubuntu.com/com](https://help.ubuntu.com/com)
  its maximum possible value. Also make sure the speaker is selected under the tab
  "Switches" of the system tray applet (double click the sound system tray applet).
  3. Right-click on the volume applet and choose Preferences. Select "PCM" as the
  device to control.
  4. Open the Sound preferences (System-Preferences-Sound in GNOME). Select
  "PCM" as the device to control.


And I am lost.  Google and forum search has not yet yielded anything.

How do I get it working?

David

---

### Post by cyberdork33 on 2008-09-21
you can run alsamixer to control the channel levels.

I am not sure how you set which channel to control via keyboard in KDE though.

---

### Post by dsmoot on 2008-09-24
Sigh.  Experience is what you get when you didn't get what you wanted.

Problem is solved and I learned a lot.  Boy was the screwup annoying.

I did not have a wired ethernet connection while I was setting up.  So I pulled up the Ubuntu Macbook Pro FAQ page under OS X while connected wirelessly and then did a print to PDF so I could refer to the instructions while I was working under linux.  Problem is the stupid font I got in the pdf made underscores look like dashes.  So the clear and perfectly correct instructions in the FAQ were botched by me because I mistook the underscores in the instructions on editing the configuration files as dashes.  

But a couple of other lessons for any searchers that might stumble on this thread:
Kmix is the mixer for kubuntu.  Right click on it to set the output channel.

David

---

### Post by stuv829 on 2008-09-25
An exasperated mother, whose son was always getting into mischief, finally asked him, "How do you expect to get into Heaven?" The boy thought it over and said, "Well, I'll run in and out and in and out and keep slamming the door until St. Peter says, 'For Heaven's sake, Dylan, come in or stay out!'"[wow gold](http://www.mmoinn.com),[world of warcraft gold](http://www.mmoinn.com),[wow power leveling](http://www.mmoinn.com/mmoinn_pl/)my site [http://www.mmoinn.com](http://www.mmoinn.com)

---

