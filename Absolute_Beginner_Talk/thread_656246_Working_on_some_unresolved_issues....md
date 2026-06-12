---
title: "Working on some unresolved issues..."
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by thumper13 on 2008-01-02
This year, one of my resolutions for the New Year was to make my computer entirely M$ free. First thing I did was install Ubuntu... I just need some assistance from the community to get my last bugs out.

First, hats off to the people at Ubuntu. I last used Ubuntu when version 4.? was the latest. Gutsy is so much easier to operate, especially for a novice like me. Kudos to the people in the forums as well, since they're always eager to help me... This Beginner's group that's stickied on the top of the forum is an excellent idea, I wish I'd thought of this. But now, on to the cake of this post, enough with the icing.

1) My first issue is interesting. When the computer is booting up (after the post), my monitor brings up a little blue box that says the signal is unreadable. Once the login screen comes on, it's smooth sailing there on in. I'm guessing this has something to do with the resolution of the boot up screens. Is it possible to modify the resolution of that said screen? Currently, I'm running at 1280x1024 on my desktop.

2) Issue 2 is more of an annoyance than an actual problem. I use the number pad a whole lot, and at default, the number pad is set to off... Thus, I have to push num lock in order to type using those buttons again, but I forget to do it, and then it just works like the arrow keys. Is it possible to change this to be "on" by default?

3) After reading a plethora of walkthroughs and HowTos on how to install World of Warcraft (My greatest vice) on Ubuntu, issue 3 is the last thing unresolved. I may be asking for help in the wrong place, but it's worth a shot. The game's video works fine, it loads and exits perfectly, the only issue I'm having is that when the game loads (just before entering the world... the World of Warcraft I suppose), my speakers make a disgustingly high pitch beep. It's also extremely loud. I like the game's sound, so I'd rather not play without sound (the game works fine without sound as well.), but I'd also like to keep my speakers and my hearing intact. If anyone has any kind of insight to this, feel free to send me a message, or reply to my post, or even drop me an email (the address is in my profile)...

Other than these 3 issues, my pc is much more happy with Ubuntu than windows. If anyone can help me out with this, that would be greatly appreciated.

Thanks, T.):P

---

### Post by bone2006 on 2008-01-02
#2

[http://easylinux.info/wiki/Ubuntu_dapper#How_to_tu%20rn_on_Num_Lock_on_GNOME_startup](http://easylinux.info/wiki/Ubuntu_dapper#How_to_tu%20rn_on_Num_Lock_on_GNOME_startup)

 How to turn on Num Lock on GNOME startup

    * Read #General Notes
    * Read #How to add extra repositories 

sudo apt-get install numlockx
sudo cp /etc/X11/gdm/Init/Default /etc/X11/gdm/Init/Default_backup
gksudo gedit /etc/X11/gdm/Init/Default

    * Find this line 

...
exit 0

    * Add the following lines above it 

if [ -x /usr/bin/numlockx ]; then
 /usr/bin/numlockx on
fi

    * Save the edited file

---

### Post by erginemr on 2008-01-02
#1

This is a standard Ubuntu splash screen problem. Please refore to this thread:

[http://ubuntuforums.org/showthread.php?t=628833](http://ubuntuforums.org/showthread.php?t=628833)

and my posts over there.

---

### Post by erginemr on 2008-01-02
#2

Also there is a setting to change Numlock status on login in Alt+F2 -> gconf-editor under the key:
/desktop/gnome/peripherals/keyboard

---

### Post by thumper13 on 2008-01-03
Thanks all around. Seems to be resolved as for now. I wish I had you guys earlier when I somehow managed to change the permissions on my /home/thumper folder to something "thumper" cant access... and I got to format the pc again. You live you learn I guess... but again, thanks, these two issues are seeming to be fixed.

Thanks, T.

---

### Post by erginemr on 2008-01-03
You are most welcome. To rule out the 3rd problem, please scan the following threads:

[http://ubuntuforums.org/showthread.php?t=560990](http://ubuntuforums.org/showthread.php?t=560990)
[http://ubuntuforums.org/showthread.php?t=25655](http://ubuntuforums.org/showthread.php?t=25655)
[http://ubuntuforums.org/showthread.php?t=422772](http://ubuntuforums.org/showthread.php?t=422772)

I believe your sound card is also AC'97 as in those threads. I do not play WoW (or any games for that matter), but depending on whether you are playing it via Wine or Cedega, the a/m pages have come up with a few suggestions such as using artsd sound server, playing with wine settings,

Also getting the latest version of Wine from [www.getdeb.net](www.getdeb.net) might lead you to the solution.

I had once fiddled with ZSnes (SNES emulator), where the sound coming from the emulator was crackling. I have managed to get rid of the crackling noise by creating an ".asoundrc" file and configuring some settings of ALSA sound server. The following page is on how you can do this:

[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)

All the best...

---

### Post by thumper13 on 2008-01-06
erginemr, thanks for the info, i got it working... sort of...

Now, when I boot world of warcraft, some of my textures are coming up psychedelic... like Aurora Borealis, theres a rainbow on the skybox at all times.. Now, i'm down with the funky 60s theme, but I know its not supposed to look like an acid trip... 

Here's some system specs.

Ubuntu Gutsy (running single boot, no m$ on this machine.)
AMD 3800+ 64bit cpu
1 gig of ram
160 gig hard drive
ATI x200 onboard video <- most likely the culprit
AC97 Realtek onboard sound

Now, i hear ATI makes craptastic drivers for Linux... does anyone know of a source I can get better developed ones from? I do like my ati card, and in windoze, i get normal fps (30-40 range)... on linux, occasionally it works great, but I tried some older drivers (someone posted somewhere that 8.37 was better for gaming, rather than 8.433) and the game wouldnt load at all, nor would Teewars, which work excellent on 8.433.

Thanks again for the assistance, T

---

### Post by erginemr on 2008-01-07
You are welcome.  For the color thing, can you please try the following:
[http://ubuntuforums.org/showthread.php?t=579378&page=122](http://ubuntuforums.org/showthread.php?t=579378&page=122)
[http://forums.wow-europe.com/thread.html;jsessionid=77996A7CC5D3EA484FAF0E132CFAAFA0.app03_01?topicId=285139220&postId=21110224181&sid=1#255](http://forums.wow-europe.com/thread.html;jsessionid=77996A7CC5D3EA484FAF0E132CFAAFA0.app03_01?topicId=285139220&postId=21110224181&sid=1#255)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9429](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9429)

In the third link, look for the line:
...OpenGL seems to work (M2UseShaders 0 to solve strange colors, UIFaster 2 to solve corrupt icons)...

I hope this will help with your situation.

---

### Post by thumper13 on 2008-01-07
I can happily say the issue is now resolved. To be honest, I dont know what I did, but I did something, and now not only does warcraft work perfectly, the sound glitches i was experiencing before are gone. And I can even run Rhythmbox in the background while I play, no errors :)

Again, thanks for the helps.

---

### Post by erginemr on 2008-01-07
):P Though I wish you knew how you did it, as there are many people on the forums who suffer from WoW compatibility issues.

Have Fun!

---

