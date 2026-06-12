---
title: "On going sound difficulties...Alsamixer"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Redptc on 2008-01-30
When I go to check Alsamixer I get the following error messages;

Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash (/)
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash (/)

My sound runs in an erratic way. It comes on somtimes when I boot but does not on other occasions. The sound is great when it is there. It is on more often than it is not.

Anybody know how to resolve these error messages. I may have to add a filename? 

redptc

---

### Post by spiderbatdad on 2008-01-30
maybe missing .asoundconf a hidden file in your home directory. If you run```
asoundconf list
```you should see a parameter output. then:```
asoundconf set-default-card parameter
```where parameter would be the output of the first command. This will create a hidden file in your home directory: .asoundconfrc.asoundconf

Also saw these links in another thread:[https://help.ubuntu.com/community/HdaIntelSoundHow](https://help.ubuntu.com/community/HdaIntelSoundHow) to

[http://ohioloco.ubuntuforums.org/sho...d.php?t=530374](http://ohioloco.ubuntuforums.org/sho...d.php?t=530374)

---

### Post by Redptc on 2008-01-30
> **spiderbatdad said:**
> maybe missing .asoundconf a hidden file in your home directory. If you run```
asoundconf list
```you should see a parameter output. then:```
asoundconf set-default-card parameter
```where parameter would be the output of the first command. This will create a hidden file in your home directory: .asoundconfrc.asoundconf

Also saw these links in another thread:[https://help.ubuntu.com/community/HdaIntelSoundHow](https://help.ubuntu.com/community/HdaIntelSoundHow) to

[http://ohioloco.ubuntuforums.org/sho...d.php?t=530374](http://ohioloco.ubuntuforums.org/sho...d.php?t=530374)

[COLOR="#000000"][COLOR="#000000"][COLOR="Green"]Thanks, I'll check that out & get back to you![/COLOR][/COLOR][/COLOR]

---

### Post by Redptc on 2008-01-30
Is there some way of confirming this has been set as default because I have done this before?  Would something knock it off track? 

Thanks for your help!

[COLOR="Red"]redptc[/COLOR]

---

### Post by Redptc on 2008-01-30
> **Redptc said:**
> When I go to check Alsamixer I get the following error messages;

[COLOR="DarkOrange"]Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/": Key/directory may not end with a slash (/)
Bad key or directory name: "/apps/gnome-alsamixer/display_names/": Key/directory may not end with a slash (/)
[/COLOR]
My sound runs in an erratic way. It comes on somtimes when I boot but does not on other occasions. The sound is great when it is there. It is on more often than it is not.

Anybody know how to resolve these error messages. I may have to add a filename? 

redptc

I get this error message, does anyone know why or how to resolve it?

[COLOR="#ff8c00"][COLOR="#ff8c00"][COLOR="Red"]redptc[/COLOR][/COLOR][/COLOR]

---

### Post by spiderbatdad on 2008-01-30
what does your output from asoundconf list look like?

---

### Post by erginemr on 2008-01-30
I have never experienced such an error, but this may be a bug in gnome-alsamixer. There are tweo bug reports filed on this phenomenon:
[http://bugzilla.gnome.org/show_bug.cgi?id=429012](http://bugzilla.gnome.org/show_bug.cgi?id=429012)
[https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768)

As a workaround, you may try adjusting your volume settings from the terminal with the "alsamixer" command.

---

### Post by Redptc on 2008-01-30
> **spiderbatdad said:**
> what does your output from asoundconf list look like?

A brief list; PCI, UART

I set PCI as default.

[COLOR="Red"]redptc[/COLOR]

---

### Post by Redptc on 2008-01-30
> **erginemr said:**
> I have never experienced such an error, but this may be a bug in gnome-alsamixer. There are tweo bug reports filed on this phenomenon:
[http://bugzilla.gnome.org/show_bug.cgi?id=429012](http://bugzilla.gnome.org/show_bug.cgi?id=429012)
[https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768)

As a workaround, you may try adjusting your volume settings from the terminal with the "alsamixer" command.

Many thanks for steering me in this direction, one of the reported bugs was exactly the same. 

[COLOR="Red"]redptc[/COLOR]

---

### Post by spiderbatdad on 2008-01-30
i dont think that is a recognizable parameter. It should be something like I82801CAICH3. Maybe another selection under volume control preferences. Hope you get this resolved soon.

---

### Post by Redptc on 2008-01-30
> **erginemr said:**
> I have never experienced such an error, but this may be a bug in gnome-alsamixer. There are tweo bug reports filed on this phenomenon:
[http://bugzilla.gnome.org/show_bug.cgi?id=429012](http://bugzilla.gnome.org/show_bug.cgi?id=429012)
[https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/184768)

As a workaround, you may try adjusting your volume settings from the terminal with the "alsamixer" command.

'Master' comes up in red and I don't know how to change it.........i think this is a 'mute' indicator!

[COLOR="Red"]redptc[/COLOR]

---

### Post by spiderbatdad on 2008-01-30
red is what is selected...navigate with arrow key left/right...up/down to change value.

---

### Post by spiderbatdad on 2008-01-30
keep going right...beyond what is visible to the pc speaker choice? maybe

---

### Post by Redptc on 2008-01-30
> **spiderbatdad said:**
> keep going right...beyond what is visible to the pc speaker choice? maybe

Everything seems to turned on and at the maximum. Appreciate your help because the failure frequency has dropped and, most times, I have good sound. I think I might just 'leave well enough alone' for the moment.

Thanks for your time and effort! Your help has guided me into areas I woudn't normally consider.

---

