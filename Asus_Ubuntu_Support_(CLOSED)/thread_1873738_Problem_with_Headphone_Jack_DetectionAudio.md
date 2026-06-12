---
title: "Problem with Headphone Jack Detection/Audio"
date: 2011-11-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by dirkmcg78 on 2011-11-01
Hey gents, hoping you could help out a noob with an audio problem. I'm trying to play audio on my headphone jack, but it doesn't seem to recognize that I want the audio to play on only the jack, not the built-in speakers. I've seen a few different fixes for this problem, but none specifically for my laptop, an aging ASUS K50IJ laptop.
Not really sure if this should be in the multimedia forum, but this is my first post. Grant me mercy, Gods of Ubuntu.
**Update: ASUS laptop K50IJ, Intel Pentium Dual-Core CPU T4200 @ 2.00GHz × 2, 3GB RAM, running Ubuntu 11.10 (64-bit).

---

### Post by muzikayise on 2011-11-02
I have same problem with headphone jack

my machine: Asus N53SV-S1830X Intel Core i7 - 2670QM 2.2GHz, 8GB RAM 750GB 
Intel HD3000 Graphics Card + NVidia GeForce 540M CUDA 1GB

built in speaker work perfect but as soon as i plug-in headphones then No Sound

---

### Post by muzikayise on 2011-11-02
> **dirkmcg78 said:**
> Hey gents, hoping you could help out a noob with an audio problem. I'm trying to play audio on my headphone jack, but it doesn't seem to recognize that I want the audio to play on only the jack, not the built-in speakers. I've seen a few different fixes for this problem, but none specifically for my laptop, an aging ASUS K50IJ laptop.
Not really sure if this should be in the multimedia forum, but this is my first post. Grant me mercy, Gods of Ubuntu.

i found a fix and its easy just do the following:

```
 echo "options snd-hda-intel model=asus" | sudo tee -a /etc/modprobe.d/alsa-base.conf 
```[B]Reboot

[/B]original thread: [http://ubuntuforums.org/showthread.php?t=1774627&page=2]("http://ubuntuforums.org/member.php?u=577099")

thanks to [Idex]("http://ubuntuforums.org/member.php?u=577099") his one of the "ubuntu Gods" hehe

---

### Post by Dessel on 2012-04-10
> **muzikayise said:**
> I have same problem with headphone jack

my machine: Asus N53SV-S1830X Intel Core i7 - 2670QM 2.2GHz, 8GB RAM 750GB 
Intel HD3000 Graphics Card + NVidia GeForce 540M CUDA 1GB

built in speaker work perfect but as soon as i plug-in headphones then No Sound
Hey I have the same laptop and presumably the same issue but I found a temporary fix, unfortunately not a permanent one yet. If you install GNOME alsa mixer and look and the slider labeled speaker with headphones plugged it will probably be at 0, if you slide it back up it should start playing from the headphones. Unfortunately you have to redo this everytime you plug in the headphones.

---

### Post by dirkmcg78 on 2012-04-16
@Dessel, thanks for the suggestion, I think that did it. Mildly annoying, but hey, it works.
Thanks for all the help, folks. Here's hoping 12.04 has fewer bugs.

---

