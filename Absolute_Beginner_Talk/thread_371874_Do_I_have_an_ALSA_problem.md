---
title: "Do I have an ALSA problem?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by Baasha on 2007-02-27
Hi,
I am running Ubuntu 6.10.  I tried to edit my GRUB menu boot delay and this is what I got:

```

bob@ubuntu:~$ sudo gedit /boot/grub/menu.lst
Password:
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.surround51.card'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib confmisc.c:242:(snd_func_getenv) error evaluating default
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_getenv returned error: No such file or directory
ALSA lib conf.c:3936:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM surround51

```

Do I have a problem with my ALSA configuration?  I have no idea why ALSA would be called when editing a text file.  ALSA documentation seems to be pretty sparse, especially considering the high volume of sound problems on the various forums.  With the exception of a couple of obvious items in the ALSA mixer, it is a mystery what most of the channels actually do or what the best configuration would be for any particular system.  It sure would be nice if someone could rewrite the ALSA documentation so non-experts could understand what they should do, and why.

Bob

PS: There is lots of advice about diagnosing sound problems on the forums and elsewhere, but none of it contains simple instructions for setting  up the ALSA mixer.  Perhaps if some initial instructions were written the forums wouldn't be so clogged with sound problem questions.

---

### Post by mikewhatever on 2007-02-27
It seems very strange that you get such things after calling a text file editor. Has the menu opened at all? Do you always get them when editing any text file? Are there any sound problems?

---

### Post by Baasha on 2007-02-27
Hi Mike,

When you say "Has the menu opened at all", what exactly are you referring to?

I often get these messages when using the terminal.  I can't say for certain that it always happens only when doing something with a text file, but that is probably true since so many files in Ubuntu are text based.

I am not sure whether I have sound problems or not.  I do get sound on my 5.1 system, but because of the virtually non-existent help files for ALSA I have no idea whether I have it configured correctly or not.  Many of the channels in the ALSA mixer are undefined with respect to what they do or how to set them up correctly for a particular type of hardware.

Bob

---

### Post by mikewhatever on 2007-02-27
I meant the menu.lst by menu. So, every time you try opening a text file, you see ALSA lines like that? What happens if you use another editor like 
sudo nano /....? I think it might be a good idea to contact ALSA developers about this, unless of cause someone here knows what's wrong.
[http://www.alsa-project.org/](http://www.alsa-project.org/)

---

### Post by not_a_commie on 2007-04-11
I have the same problem since I updated to Edgy. I see this running gvim and gnome-sound-properties. Any idea how to fix this yet?

---

### Post by gringogrande on 2007-04-18
Still no clues how to fix it?

---

