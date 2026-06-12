---
title: "Something I just fail to understand"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by sc0undrel on 2006-11-04
I haven't been a Linux user for very long, since I've had a hell of a lot of problems and have had to fall back to Wind0ze quite a lot of times.

Anyway, there is something I just fail to understand.

If you guys can add a whole bunch of extra stuff, make XGL and all kinds of bells and whistles, then why is it that with every Linux distro that I try, some problems keep coming back again and again and again and again?

Just to name a few:

1) No sound in flash in Firefox
2) Refresh rate / resolution

I've made a lot of threads about the refreshrate/resolution problem, but I've managed to solve it in Ubuntu 6.10 with the help of ubuntuguides.org's guide to install the ATI drivers.

However, when I tried the [ubuntuguide.org's solution](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox) for getting the sound working in flash in Firefox, I got this error message:

```
Package alsa-oss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package alsa-oss has no installation candidate
```

... in spite of this error message I continued and did "gksudo gedit /etc/firefox/firefoxrc" and replaced FIREFOX_DSP="" with FIREFOX_DSP="aoss". At last I got the sound working, but now when I watch videos on youtube.com, I won't hear any sound with Rythmbox. *sigh*


As far as I remember, on every computer, with every single Linux distro, the sound problem in flash in Firefox has always, always been a problem to me.

So, I don't get it. Why add all the pretty eye-candy and bells&whistles, when the CORE problems remain? Not everybody is so stubborn as me to stick with Linux, and they are simply unable to use this OS with these persistent problems.

I simply don't care about all the pretty effects and things like that, when for example I can't get the simplest of things to work properly. So why not FOCUS on fixing them first, before moving onto something totally irrelevant? :(

---

### Post by bulldog on 2006-11-04
Well from your point of view you're right ofcourse.

But I,and I think a lot of other users,don't have any problem with their sound and flash.

You can try another soundcard if the trouble persist,I myself use a soundblaster 5.1,and no trouble with it.

I use a geforce 6800 Ultra and had no problems with my resolution or drivers.

Maybe it's just the combination of your hardware which causes the trouble.

---

### Post by woedend on 2006-11-04
have you tried installing the flash9 beta?  it fixed a lot of issues...i never really had sound issues, though...more of sync.

---

### Post by sc0undrel on 2006-11-04
Okay, I went to [System] - [Administration] - [Software Sources] and replaced the default selection in the "Download from" box, which was "server for Estonia" to "Main server" and ticked all the universe/multiverse checkboxes.

Then I entered this command again:
```
sudo apt-get install alsa-oss
```

This time it installed ALSA just fine, and when I restarted Firefox, I could now hear music in flash and Rythmbox at the same time. ^_^



[QUOTE=bulldog]You can try another soundcard if the trouble persist,I myself use a soundblaster 5.1,and no trouble with it.[/QUOTE]

Well, I have tried it on several computers and a couple of laptops, all with different sound cards, and this problem has always been present.

[QUOTE=woedend]have you tried installing the flash9 beta?  it fixed a lot of issues...i never really had sound issues, though...more of sync.[/QUOTE]

Thanks for the suggestion, but no, I haven't tried the flash9 beta yet. I think I'll wait for the stable version before installing it. :)

---

### Post by bulldog on 2006-11-04
But your main problem is solved??

Are the repo's for Estonia different as the main?
Strange,should be the same.

---

### Post by sc0undrel on 2006-11-04
[QUOTE=bulldog]But your main problem is solved??[/QUOTE]


Yeah, I'm not exactly sure, but it seems to be working great now. :)

Now I can finally actually start doing something, thanks to ubuntuguides.org's guides. ^_^


[QUOTE=bulldog]Are the repo's for Estonia different as the main?
Strange,should be the same.[/QUOTE]

Hmm, I don't know if this was the cause of the problem at the moment.

By default the "multiverse" and "universe" checkboxes were unchecked, so I cheked them and I guess this is what made the difference. :)

---

### Post by bulldog on 2006-11-04
You could take a look at automatx2,it's a very usefull app to add programs for you and codecs as well.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

Be sure you have the right one for your distro ie. Ubuntu or Edgy.:D

---

### Post by 3rdalbum on 2006-11-04
The Flash problem is not Linux's fault; it's because Flash uses an obselete sound API that causes problems. Flash 9 Beta for Linux uses the current sound API, so you shouldn't have any trouble there now.

Obviously the best solution for sound trouble is for all programs to move to the current standard, but since that's not always happening there is a new system in development, called PulseAudio, which should put an end to all the troubles.

Let's not forget that legacy programs on Windows XP have *exactly* the same sound trouble as the legacy programs on Linux. Try playing a file in Windows Media Player, and playing the game 'Elastomania' with sound on, and see what happens. Of course, there's no way to pipe Elastomania's sound output through another sound system on Windows...

---

### Post by maaronB on 2006-11-04
> **sc0undrel]
If you guys can add a whole bunch of extra stuff, make XGL and all kinds of bells and whistles, then why is it that with every Linux distro that I try, some problems keep coming back again and again and again and again?
[/QUOTE]

3rdalbum answers that question.

[QUOTE=3rdalbum said:**
> The Flash problem is not Linux's fault; it's because Flash uses an obselete sound API that causes problems. Flash 9 Beta for Linux uses the current sound API, so you shouldn't have any trouble there now.


All of the common big basic problems; Modems, Video, Flash, MP3, and various other audio/video codecs stem from the fact that so many things are proprietary and for some reason or another the maker has chosen not to support them.  There is just not much that the Linux developers can do about that fact so they work on things that they can fix.  Such as XGL.

---

