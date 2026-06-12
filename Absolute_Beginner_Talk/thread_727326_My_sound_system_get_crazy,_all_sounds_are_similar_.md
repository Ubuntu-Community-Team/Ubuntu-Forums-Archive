---
title: "My sound system get crazy, all sounds are similar to what come through a long pipe :("
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-03-17
Hi
Thank you for reading my post
I tried to use some mplayer command to use sdl sound, 
```

mplayer -ao sdl

```

but after that, all sounds in my computer looks to come from a very long distance and through a spiral pipe :(

I tried and restart the sound system using the following command with no luck

```

/etc/init.d/alsa-utils reset

```

Can some one let me know what went wrong?

Should I restart the computer for this problem? it is not a good idea to restart the machine for every problem :(

Thanks

---

### Post by duncan.hawthorne on 2008-03-18
restarting your computer isnt going to harm anything.... thats the first thing to do always

do sounds play strange through mplayer, or through everything, say rhythmbox

look in the volume control for any channels that are unmuted but not what you want, and mute them. you can see more channels in the preferences, check them all

if it is just mplayer, delete ~/.mplayer folder

---

### Post by Xiong Chiamiov on 2008-03-18
Yes, I find rebooting to be the easiest fix to many problems on any operating system.  Even if it *shouldn't* do anything, computers are not always as logical as we like to believe :) .  This is assuming, of course, that you're not running a server or some such.

Also, Duncan's suggestion is a good one.  If we can determine whether or not it's the application or some broader problem witht eh sound, that will help greatly.

---

