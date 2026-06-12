---
title: "No sound"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2007-03-20
Just started my computer and all of a sudden I have no sound.  The volume control at the top right showed muted so I unmuted and turned everything up.  Still no sound.  It has worked for months and all of a sudden nothing.

Any suggestions.

---

### Post by Dr. Nick on 2007-03-20
Did you do anything to your user account, Like change groups? Or any type of updates?

---

### Post by gentlemanmasher on 2007-03-20
the automatic updates were installed that is it.

---

### Post by zvacet on 2007-03-20
In the menu layout>system tools and pick ubuntu data base or  sttings manager(I don´t remember).Whit one of these you can chek your audio and video.And you can install alsa mixer.

---

### Post by wilberfan on 2007-03-20
> **gentlemanmasher said:**
> Just started my computer and all of a sudden I have no sound.  The volume control at the top right showed muted so I unmuted and turned everything up.  Still no sound.  It has worked for months and all of a sudden nothing.

I just booted up my backup Edgy box -- and I've got the same problem!  Worked fine for months--and now, suddenly, no sound at ALL!  :confused:

i noticed my speaker icon was muted, so I un-muted it...but I've got no login sounds...no sounds at ALL.    This is very odd...  I DO have alsa-mixer installed, and in System > Administration > User Settings > Properties   "use audio settings" IS checked.

[edit] It would seem there are others experiencing this problem?:   [http://www.ubuntuforums.org/showthread.php?t=377197](http://www.ubuntuforums.org/showthread.php?t=377197)

---

### Post by gentlemanmasher on 2007-03-21
So i take it we have no fix yet then?

---

### Post by thefoolisme on 2007-03-21
I would be interested in this too.  I'm having this problem too, although when I unmute everything and turn it up I do have sound...but that was after I changed the sound card from Automatically detect to manually choose.   I thought once I unmuted everything it would be fine, but when I turned on the machine last night, I had the same problem.  Everything was fine before the updates I did in the past couple of days.  I'm beginning to think there is something in the updates.

---

### Post by RichPicker on 2007-03-21
Same problem here.

---

### Post by dracomordag on 2007-03-21
system->preferences->sound
sounds tab, very bottom: "Default sound card:"
choose yours.

Chances are it's not the one Ubuntu auto-selects (Ubuntu chose Intel ICH5 for me, i just switched it to the only other option)

---

### Post by thefoolisme on 2007-03-21
Draco, 

I discussed manually choosing the sound card in my post, but it will only stay that wasy for the session.  You shouldn't have to reset the sound everytime you log into your machine.  I think there's another issue here.

---

### Post by dracomordag on 2007-03-21
in your post you said you changed something from autodetect... nothing i said should involve that.

lemme post screens of what i mean

[img]http://stashbox.org/15236/devicestab.jpg[/img]
[img]http://stashbox.org/15237/soundstab.jpg[/img]

^^ mine was at INTEL ICH5, and i changed it over to the soundblaster.

---

### Post by gentlemanmasher on 2007-03-21
that did nothing for my sound.  Not sure about any of the rest of  you.

---

### Post by wilberfan on 2007-03-21
> **thefoolisme said:**
>   I'm beginning to think there is something in the updates.

That's what I think, too...    I changed no settings (I don't even use this box that much--it's my backup.)

I DID apply whatever updates were available--but I couldn't tell you what they were at this point...   

As to dracomordag's  System > Preferences > Sound suggestion, I only have ONE choice there, and it's still selected...but still no sound whatsoever...

---

### Post by gentlemanmasher on 2007-03-22
I hate to have to re-install again.  Does anyone else have anything else that they tried.

---

### Post by wilberfan on 2007-03-22
For what it's worth, I've just restored a partition image I had from Dec 23rd, and my sound is back.  (Google Earth works, again too...)

This reinforces the idea that one of the updates is responsible for my sound (and previously unmentioned OpenGL) issues in the last few days...?

If I had the time (and patience) it might be interesting to install the updates a few at a time to see which one(s) are responsible--but I think I'm just gonna wait for Feisty!  ;)

---

### Post by thefoolisme on 2007-03-22
I found this in another thread about sound problems.  I don't know if it will work, because I haven't tried it yet.  

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

Looking through the boards, there are a lot of sound problems popping up.  This leads me to believe that it was definitely in one of the updates I downloaded this week.  The problem is, since I only installed it last weekend, I don't have an older image; and since I installed it last week, when I downloaded updates, I downloaded like 71 of them.  I have no clue which one it might be.  I sure would like to know which one it is, and how to uninstall it.

---

### Post by RichPicker on 2007-03-22
I hadn't noticed that Google Earth wasn't working, until I read your post. My sound works , it's my mic that doesn't work.

So.... We wait for another update that will fix it? Or for Feisty, which is the next generation that's soon to be released?

Google Earth and the mic aren't critical to 'my' existence. But it's interesting to follow the progress of these issues. 

Freedom ain't cheap, but it's well worth the price.

---

### Post by wilberfan on 2007-03-22
It's probably NOT related (because I restored that earlier partition image), but when I logged into my xubuntu desktop, I had no sound!  (But, you'll recall, the sound was restored on my gnome desktop)...

:confused:

[edit] no, wait...now the sound is not working on the gnome desktop, too...     But I had some HAL errors (?) and my partitions are slightly different now than they were back in December when I made that partition image...  

But the sound DID return immediately after restoring that partition image, so...   Oy.

Let's just ignore this post for now, shall we?

---

### Post by SMS on 2007-03-22
hey guys i think i have got it
i rcently got that "there are updates for your pc" (i got it this morning)
and i remebered some of the updates, and one of them was called "file"
so i thought Hmmmmmm
whats this and looked at it dependancies, and it is related to all of my installed media player and a lot of my libaries,
Is this is culprate?????

---

### Post by ricardisimo on 2007-03-23
Right-click on Master Mono control if you've got it up on your top toolbar, and select "Open Volume Control". [If not, type "alsamixer" in terminal.] Edit > Preferences and check some of the obvious ones: Master, Master Mono, Surround, CD, Video, etc. If you don't know what it is, you probably shouldn't check it. Anyway, try turning them up to full one at a time.

If this doesn't work, you might have to turn something down. happened to me once where one of the mic volumes was at full and shutting down everything else somehow. Bizarre, but it happens.

Good luck.

P.S. - "alsamixer" controls are different. "m" toggles mute as I recall, and arrows raise and lower volume... I think.

---

### Post by RichPicker on 2007-03-23
I know nothing, but it seems like this is the result of an update. Nothing else has changed on my system. I do have sound, but no microphone (and no GoogleEarth). The forum links to the fixes don't do anything. Something changed to this system beyond my useage.

I've heard mention of updates forthcoming. Any news about those?

---

### Post by pureblood on 2007-04-10
This workaround might work but it is not a solution:
[http://ubuntuforums.org/showthread.php?p=2430827#post2430827](http://ubuntuforums.org/showthread.php?p=2430827#post2430827)

---

### Post by elevel on 2007-04-18
I had the same problem under Feisty. I solved it by completely removing the following alsa packages and then reinstalling them. So in my case the problem was due to some faulty configuration. However, I like to mention that I tryed all the hints above and the one just referenced above, so playing with the mixer settings and switching on or off devices did not help in my case!

alsa-base
alsa-oss
alsa-utils
gnome-alsamixer
libpt-plugins- alsa

please note that you might have to reinstall other packages that were dependent on the once above and have been removed to. In my case these have been: ubuntu-minimal, gdm, ubuntu-desktop, ekiga

hope this helps someone out there.

---

### Post by lancest on 2007-04-18
**Nothing but problems with Intel sound on Fiesty since the start! ** ASUS W7J laptop. Everything works properly except sound. Now have horrible permanent high pitched squealing noise when booting (since last update.) Feisty updates are current.
[COLOR="Navy"]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/COLOR]
Had it working mostly before (except Gnome slider prob & static pop at boot). Never 100% (Edgy& Suse worked perfect)
 Terrible. So I had to uninstall Alsa. This must be a kernel problem. Isn't Feisty near release?

---

### Post by amaan on 2007-05-01
I also have the Asus W7J, I'm running under Ubuntu 7.04. I get sound but the volume does not change, and everytime i reboot, I get the volume on full. 

Does anyone know of a solution? TIA!

---

