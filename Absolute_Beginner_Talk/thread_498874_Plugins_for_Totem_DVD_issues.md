---
title: "Plugins for Totem? DVD issues"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by leialte on 2007-07-11
Okay, I tried searching for this and I tried solving on my own, but I'm still having issues.

My dvd player (a.k.a. PS2) is old and decrepit and can't handle DVDs anymore (gotta gut it and fix it again, but I'd rather just use my computer). I tried using Totem to play the DVD, and it says "Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it." I tried searching for totem plugins and I kept coming across solutions by installing libdvdcss2 and w32codecs, which I have installed.

(Proof they're installed:)
```
amanda@ubuntu:~$ sudo apt-get install libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdcss2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
amanda@ubuntu:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.

```

Is there an actual totem plugin that I can't find/don't know where to look? Am I garishly showing off my newbiness by not having something I need to begin with?

Thanks.

---

### Post by ramjet_1953 on 2007-07-11
Follow this link:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

It will show you how to install all of the codecs that you need.

Also this link may be of help to you with any other issues that you may encounter:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Regards,
Roger :cool:

---

### Post by Seisen on 2007-07-11
Try installing totem-xine.

---

### Post by leialte on 2007-07-11
> **ramjet_1953 said:**
> Follow this link:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

It will show you how to install all of the codecs that you need.

Also this link may be of help to you with any other issues that you may encounter:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Regards,
Roger :cool:

Whoops! Didn't see that. *attempts*

---

### Post by leialte on 2007-07-11
How do I change the permissions so I can edit sources.list?

Not to mention, that's ultimately telling me to install libdvdcss2 and w32codecs, which I, I repeat, already have done.




How do I install totem-xine? EDIT: installed via system ---> administration synaptic package manager. Totem now tells me the same thing in a different way: Totem could not play 'dvd:/'.

---

### Post by johnnyb01 on 2007-07-21
Same problem here. Haven't tried totem-xine, but it doesn't sound like it will help.

---

### Post by kelvin spratt on 2007-07-21
Totem zine has a completly different engine to gsteamer i had problems and changed to zine, also Kaffine is good does a first time check and will tell you if the codecs are missing

---

### Post by mgmiller on 2007-07-21
Do you have more than 1 optical drive in this computer?  I have 2, a dvd-rom and a dvd-burner and I can only play dvd movies in one of them (I forget which), the other will give me the same error message you get.  Also, you can try playing the movies with mplayer or vlc instead of totem.

---

### Post by johnnyb01 on 2007-07-21
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

"Note: If DVD playback fails, and you've never played any DVD before on your system, you may need the regionset package to initially set the drives region."

I had to install 'regionset' from the command line, but it worked after that.

---

### Post by adam_kimber on 2007-07-25
Was this ever resolved? I have never managed to get Totem-gstreamer to play DVDs from the drop down menu - play disc option. Open location dvd:// and autorun DVD works but to eject the DVD and to get it to autorun again is a faff.

---

### Post by lemonseed on 2007-07-25
> **adam_kimber said:**
> Was this ever resolved? I have never managed to get Totem-gstreamer to play DVDs from the drop down menu - play disc option. Open location dvd:// and autorun DVD works but to eject the DVD and to get it to autorun again is a faff.

I have the same problem and I'm pretty sure it is a known bug with Totem. The DVD will play on autorun but choosing Play Disc "NAME_OF_MOVIE" will always give me the "cannot play this media. get the proper plug-ins". :/

---

### Post by Steve_Barker on 2008-01-27
Using the instructions on:

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

by either method I am not able to add the Medibuntu repository to the file - always get read only. How do I change to make either editable?

---

### Post by rkd on 2008-01-27
Your description isn't completely clear.  I'm guessing that you mean that when you try to add the lines for medibuntu to the file /etc/apt/sources.list, you get a message about having only read permission for sources.list -- is that a correct guess?

If so, could it be that you did not type one of the commands shown for starting the editor, but started the editor some other way?  That file is protected so that only the root user can modify it (this is for your protection). When you want to modify it, you must start the editor to run as the root user.  That is what the gksu or sudo commands do.

Now if I guessed wrong about what the exact problem is, please explain more clearly what is giving you the error and someone will help you out.

---

### Post by Steve_Barker on 2008-01-27
Thank you for your patience, sorted it now. I was entering the command as per box with the $ sign.:roll:

---

### Post by rkd on 2008-01-27
Oooo, that's a subtle bug. I'm glad you figured it out.

---

### Post by chewit on 2008-01-27
I'm soory, I'm not really going answer your question. But why don't you just buy a new DVD player, in the Uk you can pick one up for about £10 from ASDA (WalMart).

I think its better watching it on the sofa on a TV screen.

---

### Post by Steve_Barker on 2008-01-27
> **rkd said:**
> Oooo, that's a subtle bug. I'm glad you figured it out.

Thanks for prompting me to look at the problem again. Totem, and Ogle both playing DVDs perfectly now;)

---

### Post by Steve_Barker on 2008-01-27
> **chewit said:**
>  But why don't you just buy a new DVD player.

Never watch TV and only watch DVDs when I have the time to enjoy them. Hence, I actually have a licence to say that there is no TV at my house. Another PC playing DVDs gives us more flexibility as to where I can watch a good film:popcorn:

---

