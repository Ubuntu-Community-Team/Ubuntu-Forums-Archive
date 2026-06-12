---
title: "Upgraded to Dapper--Now X won't start!"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Steggy on 2006-05-21
Hello all,

Earlier today, I asked about creating a separate /home partition. After reading about what I needed to do, I just decided to go ahead and do a clean install of Breezy, using the expert mode to set up a /home partition. So I backed all my important files up, then reinstalled Breezy.

I had absolutely no problems during the install, and Ubuntu booted just fine afterwards. Once I made sure everything was working correctly, I installed my browser of choice (Opera), and surfed around to find out how to upgrade to Dapper (I figured it was better to do that now, on a fresh install, then later after I had made a bunch of changes.)

So, I followed the instructions I found, and editted my sources.list, uncommented the lines for the universe, then changed every instance of "breezy" to "dapper." Then I did apt-get update and apt-get dist-upgrade.

Everything seemed to go fine--at least there were no errors at the end of the process, though I didn't watch it actually do the upgrading. Some of it worked, anyway, because I know my wallpaper had changed to say "Dapper Beta" or something similar when I came back to the computer.

I decided to restart the computer to make sure everything was working fine, and that's when my problems started.

Instead of booting to Ubuntu log-in screen, I got a blue screen telling me my xserver wasn't working. I "Okay"ed through everything until I back to a log-in prompt. I logged in and tried "startx." The screen turned black for a moment, then  it printed out a bunch of errors:
```
(EE) GART Init: Unable to open /dev/agpgart (No such device)
(EE) I810(0): No Video BIOS modes for chosen depth
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection resert by peer) on Xserver "0:0"
        after 0 requests (0 known processed) with 0 events remaining.
```

Then it just gives me a prompt again.

So, I booted up from my Breezy Live CD, which worked fine, and came back to these forums to do a little searching. After looking around, I tried this:

```
sudo dpkg-reconfigure xserver-xorg
```

I ran through the configure file, and it autodetected everything. So I tried to do "startx" again, and go the exact same errors as above.

I booted from my Live CD again, did some more searching, and decided to try the reconfigure again, but choose VESA (I think that's right) instead of the correct i810. This got rid of the "(EE) GART Init: Unable to open /dev/agpgart (No such device)" error and changed the second error to refer to VESA instead of I810, but I still can't start X.

And so here I am, completely out of ideas and ready to just reinstall Breezy. However, I'd like to give Dapper a try, and I was hoping someone here would know how to help me.

Thanks,
Steggy

P.S. There are only two things I can think of I might be doing wrong when I reconfigure X: first, it asks how much memory my graphics chipset will use of my system memory, since it has none of its own. Not knowing what to put, I just leave this blank, though I did try putting in 256 one time to see what would happen. No change.

Second, when I set up my monitor I just do a "medium" set up, choosing 1280x1024 60hz as the highest resolution my monitor can display (that's the resoltuion I use in Breezy.)

P.P.S On additional thing I just thought of, in my first install of Breezy, I had to edit the xorg.conf file manually to get it to allow the 1280x1024 resolution. I hadn't done this in my second install of Breezy, however (the one I tried to upgrade to Dapper.) Not sure if that matters, though.

---

### Post by catlett on 2006-05-21
I feel for you. [http://www.ubuntuforums.org/showthread.php?t=178903](http://www.ubuntuforums.org/showthread.php?t=178903) I don't know why you can't get in after dpkg reconfigure. You might end up reinstalling like me. My advice (since your data is safe in home) is to reinstall Breezy to get working again. Then either download and make a cd of the latest Dapper release or wait for the official release of the stable version June 1st before you upgrade.

---

### Post by macdo on 2006-05-21
It happened to me, too. I ended up doing a clean reinstall of Dapper, from disc.

---

### Post by Steggy on 2006-05-21
Well, I'm back on a new install of Breezy now. I'll definitely remember this experience the next time an Ubuntu/Linux zealot tries to tell someone reinstalling operating systems is for "windoze lusers."

---

### Post by Sef on 2006-05-21
> Well, I'm back on a new install of Breezy now. I'll definitely remember this experience the next time an Ubuntu/Linux zealot tries to tell someone reinstalling operating systems is for "windoze lusers."

I often find that a reinstall is just plain easier than figuring out where I screwed up.

---

### Post by macdo on 2006-05-21
[QUOTE=Steggy]Well, I'm back on a new install of Breezy now. I'll definitely remember this experience the next time an Ubuntu/Linux zealot tries to tell someone reinstalling operating systems is for "windoze lusers."[/QUOTE]

Who said that? That's just plain dumb! 
One of the best things about linux is that if your home directory is on a separate partition, you can easily reinstall, and keep all your stuff - including the config dfiles of your programs.
I suggest you reinstall Dapper from disc - I haven't heard of anyone having problems with that (well, no problems that Breezy didn't have, anyway). My guess is that they're just too far apart to have a reliable dist-upgrade process.

---

### Post by nickle on 2006-05-21
[quote=macdo]Who said that? That's just plain dumb! 
 if your home directory is on a separate partition, you can easily reinstall, and keep all your stuff - including the config dfiles of your programs.
[/quote]

This is a very important tip for beginners. It is a pity that the standard install dumps everything into one partition. ALWAYS set up a home partition or other partitions for distro independent stuff.

This makes ne installs a breeze if you have a fst machine and a good broadband connection.

---

