---
title: "Sound is very, very low.."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by wastedfluid on 2007-05-26
Hi guys..

Sound is very, very quiet..

Acer 5100, Ubuntu 6.06LTS.

It's about 50%, if that, of what it is on Windows.  volume is all the way up.  My volume keys on my laptop work, and control the volume level.. just at 100%, it's STILL not loud.

I've done some researching.. but it appears to be a case by case basis.  Help??

Thanks!

---

### Post by Happy_Man on 2007-05-26
Have you opened up gnome-volume-manager and checked that EVERY SINGLE SLIDER is up to max?

---

### Post by wastedfluid on 2007-05-26
Yes.  ALL Sliders(I have 5) are all the way up.

---

### Post by cymen on 2007-05-26
Hmm, I have an Acer 5101 and Gnome (albeit in Edgy) was a bit finicky with me. Only one speaker would work after each reboot until I muted and unmuted the sound. Now I use Xubuntu that problem has gone, and I think the top volume might be higher too, although in Gnome I never thought it was very quiet...

I can only think to check alsamixer, and play around with all the sliders there.

```
alsamixer
```

---

### Post by wastedfluid on 2007-05-26
wastedfluid@wastedfluid:~$ alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument
wastedfluid@wastedfluid:~$

---

### Post by cymen on 2007-05-26
Eh, try this instead.

```
gnome-alsamixer
```

If it's not installed, then install it!

```
sudo apt-get install gnome-alsamixer
```

If you manage to get the sound working the way you like it, I think this command will save your settings:

```
sudo alsactl store 0
```

---

### Post by wastedfluid on 2007-05-26
Wow.  So THAT'S what my laptop sounds like!!! 10x louder!!

However,

```
sudo alsactl store 0
```

returns..

[i]
wastedfluid@wastedfluid:~$ sudo alsactl store 0
alsactl: get_control:149: Cannot read control info '2,0,0,Capture Volume,1': Invalid argument
wastedfluid@wastedfluid:~$
[/i]

---

### Post by cymen on 2007-05-26
Hmm. As far as I can see you have two choices. You can either be content with editing gnome-alsamixer after every reboot, because I don't think it'll last but do try it and see, or you can try and fix alsamixer so that you can save your settings. 

[This page]("http://www.burghardt.pl/wiki/articles/installing_and_using_debian_on_acer_aspire_5102wlmi") seems promising if you choose to do the latter - scroll down until you see where he had the same alsamixer error as you. Some of the comments look a bit interesting for tinkering things too. 

Good luck if you try it, but at least you have one way of getting some sound. :)

---

### Post by wastedfluid on 2007-05-26
Thanks guy.

There's no permanent fix.. but what I did was followed his instructions.  I couldn't get his driver to reload, so I just added this to session start up:

alsa -F -f /root/asound.state restore

And now when I restart, it just fixes the volume on boot.

There's no "permanent" fix for it.. but that'll do.  Just a small patch.

Thank you SO much.

---

### Post by cymen on 2007-05-27
Girl, actually. ;) But you're most welcome. Patches are better than nothing!

---

### Post by wastedfluid on 2007-05-29
Sorry.

"Thanks guy" where I'm from is the same as Thanks..

Thank you, girl. :)

---

