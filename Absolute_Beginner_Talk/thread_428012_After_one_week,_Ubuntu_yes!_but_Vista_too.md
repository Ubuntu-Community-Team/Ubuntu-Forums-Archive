---
title: "After one week, Ubuntu yes! but Vista too"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by on.journey on 2007-04-29
I've made several helping threads throughout the last seven days and you always replied quickly and in every case helped me, thanks for that.

I managed it to get Ubuntu working on my Dell6400 and all the essential programs as well.

No, as a little feedback for the system I want to say following. I'm astonished by it, got more  than I expected. It looks much better than Vista (after Beryl), yet is four or even five times faster (except for the boot). Most importantly though, there's no crap stored on the system from the beginning and it makes a lot more sense as a whole. I've only learned the most important commands so far, but I think I'm already capable to look behind the scenes.

Thus, I'm gonna keep on using Ubuntu in University for notes, emailing, internet and presentations as its faster, cooler (still a newbie :) ) and just more convenient for those purposes.

However, as for at home I will stay with Vista for now since it appears to have, obviously as I'm not too familiar with all the possibilities in Ubuntu yet, the better support for the media, which is an important part of my use for a computer (rent at least 16 movies a week)

Again, I wanna say thank you for your help so far, and for what is yet to be aided with :KS 
[SIZE="2"]
Please excuse my poor English[/SIZE]

---

### Post by starcraft.man on 2007-04-29
Ubuntu can play ANY file format, I don't believe you could throw a format out it can't play.

The best solution is to install all codecs that Ubuntu needs for AVI, MP3 and other such formats it can't support native. For that, I send you to this. [http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Codecs]("http://http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Multimedia_Codecs")
Even though its for edgy, you can use the same command to install all the regular codecs. Cut and paste it into your terminal, make sure you read the note at bottom.

You can also search for any other codec with gstreamer :

```
sudo aptitude search gstreamer
```

That will show you which are installed, i on the left means installed, p is unistalled, v means it was installed as a dependancy.

Note: Make sure you have medibuntu as a repo, you need that to get most of them. Look [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") for that.

Don't forget, VLC is also available and there isn't a format it doesn't play I don't think.

---

### Post by on.journey on 2007-04-29
Well, I'll try that out, thanks mate, although I realized it before and considered the quality rather poor as opposed to what Vista offers me.

---

### Post by starcraft.man on 2007-04-29
> **on.journey said:**
> Well, I'll try that out, thanks mate, although I realized it before and considered the quality rather poor as opposed to what Vista offers me.

I don't understand what you mean by poor quality... if Totem has the codec you need it plays back good quality video. It does playlists too. As for music manager, have a look at Exhaile, Listen and or Amarok. There are many alternatives.

Enjoy, I go now, I'm a wee bit tired. Don't count Ubuntu out before you try those for media.

---

### Post by on.journey on 2007-04-29
Well, I already got the required codecs for the Totem player, but videos for incidence lag a considerable whereas they run smoothly under Vista.

---

### Post by meman63 on 2007-04-30
OK,Vista is easier in some areas,but do you want to have to buy another copy every time you buy a new computer?

Anyway,no bashing(sorry).Mplayer is also a very good video player.It has a lot of the codecs built-in,too.Plus a cool interface!

      Regards,
                   Monica

---

### Post by ZeroWing on 2007-04-30
Just FYI:

 This will make upstart to run the boot processes in parallel and speed up the boot process.
sudo kate /etc/init.d/rc
Find and change the line:
CONCURRENCY=none
to:
CONCURRENCY=shell

Make sure to check your spelling, one little mistype here and you won’t be able to boot!!!
This one seems to do best if you are using SATA or SCSI but even on my old computer with the old ATA it does make the KDM login screen show up a little bit faster.
There could actually be that this tweak slows down your boot if you are using old hardware…

=================================================

 There is a option to grub called profile which will profile your startup. What it does is that it kind of indexing all the files read during boot/startup and later on it will find and read those files quicker.

Hit the escape button when booting to get to the grub menu.
Select your default boot kernel and hit the e button.
Go down to the second line and hit the e button again.
Add profile to the end of the line and press enter.
Hit the b button to boot with your new option.

The first time it will take a little bit longer to boot because it has to build the index (or whatever they want to call it) but every boot after this will be a lot smoother.
You need to do this every time you update your kernel or have made other huge changes to your system that might affect the files needed during boot.

---

### Post by jfinkels on 2007-04-30
> **on.journey said:**
> Well, I already got the required codecs for the Totem player, but videos for incidence lag a considerable whereas they run smoothly under Vista.

If I understand correctly, you are experiencing some lag between audio and video? Make sure to post a new thread if you have a problem so that we can help you out...don't keep it to yourself! You may want to try out VLC media player, it plays pretty much any media you could imagine. To install it, type the following in the terminal:
```

sudo aptitude install vlc

```

---

### Post by Nythain on 2007-04-30
dont underestimate the solution to my most annoying screen tearing in video problem... xine-ui... cant believe i lived without it for so long... with it i now put ubuntu above windows with media support and handling... our xp laptop randomly crashes when trying to play certain avi's in media player so we have to use windvd for those, and others crash windvd so we have to use media player for those... on my linux box i can play anything and everything (except i still cant get wmv to play) in xine-ui perfectly.

once you get the codecs installed Amarok makes an AWESOME music player... with support for any and all audio formats.

i havent had a chance to play with vista yet seein as how i dont have hundreds of dollars to throw at an operating system... its hard enough coming up with the hundreds of dollars for the hardware, never understood charging that much money to make the hardware work

---

