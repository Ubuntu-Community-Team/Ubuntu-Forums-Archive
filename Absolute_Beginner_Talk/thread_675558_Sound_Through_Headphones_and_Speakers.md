---
title: "Sound Through Headphones and Speakers"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Kymac on 2008-01-22
When I plug in my headphones I get sound from both the speakers and headphones.

The Device is HDA Intel (Alsa Mixer).  The volume controls are Master and PCM, and the switches are for Caller-ID, and off-hook.  I can also switch device to Realktek ID 268 (OSS Mixer), which only has a single 'volume' control.

Can some of you please help me with this?

---

### Post by Arthur Archnix on 2008-01-22
This link here fixed the issue on my hp530 laptop.
[http://ubuntuforums.org/showthread.php?t=502833](http://ubuntuforums.org/showthread.php?t=502833)

---

### Post by PurposeOfReason on 2008-01-22
While that is too broad for me to give much advice (computer model would be great), the /etc/modprobe.d/aliases will be what you're looking for. You'll end up adding a line like
```
 options snd-hda-intel model=vaio 
```
 Obviously you won't use vaio unless that's what you have.

---

### Post by Kymac on 2008-01-22
The manual says it's Satellite A200/A205 Series.  I'm sorry, where would I add a line?

EDIT: I just found [http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/](http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/), and will try that.  (Just found it really far down on google, sorry.

---

### Post by PurposeOfReason on 2008-01-22
> **Kymac said:**
> The manual says it's Satellite A200/A205 Series.  I'm sorry, where would I add a line?

EDIT: I just found [http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/](http://taufanlubis.wordpress.com/2007/11/26/fix-no-sound-for-ubuntu-in-toshiba-satellite-a205-s4707/), and will try that.  (Just found it really far down on google, sorry.
If that get's confusing, here is a two line command that will do it for you.


```

sudo apt-get install build-essential ncurses-dev gettext && wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2 && tar xf alsa-driver-1.0.15.tar.bz2 && cd alsa-driver-1.0.15 && ./configure --with-cards=hda-intel && make && sudo make install && cd ../ && sudo rm -rf alsa-driver-1.0.15
```Then
```
sudo depmod -ae && sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
```

---

### Post by Kymac on 2008-01-22
I finally gave up on the blog thing.  Therefore, I tried your code (I'm very thankful for you posting that).

I restarted the computer, and now when i try to open volume control, it says

 > No volume control GStreamer plugins and/or devices found.

Is thee anything i can do to fix this?

---

### Post by PurposeOfReason on 2008-01-22
What I think happened is what you first tried upgraded all three parts of alsa (which when I did that in Ubuntu, it broke), instead of just the driver. Try opening synaptic and installing all the alsa again. Then try my code again but do each modprobe on the second part as it's own thing to make sure it is loaded.

---

### Post by Arthur Archnix on 2008-01-22
Huh. Sound was working, it's just that auto-mute wasn't working. I can't say that building and installing new alsa drivers would have been my first... second or third try. Hopefully it works for you.

If not, upon a clean re-install you want to look at adding an option for your specific laptop / audio card in /etc/modprobe.d/alsa-base

The link I provided has more detailed instructions, as well as the option line that fixes my HP's automute problem. Your toshiba may require a different line. Purpose of Reason suggested a different line in comment #3. The point being, I'd try a few different option lines in that file (reboot after each required) before attempting to upgrade to the latest version of alsa.

---

