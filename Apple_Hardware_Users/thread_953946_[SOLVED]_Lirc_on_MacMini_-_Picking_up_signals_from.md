---
title: "[SOLVED] Lirc on MacMini - Picking up signals from wrong remote"
date: 2008-10-20
forum: Apple Hardware Users
---

### Post by scaine on 2008-10-20
I'm running Ubuntu 8.04 on my Intel Macmini.  And since I used the repos, I'm running LIRC 0.8.3 pre 1.

Lirc itself is running really well.  And I've gotta say - XBMC is amazing.  It really blows Elisa out the water and I thought Elisa was amazing when I first saw it.

**So, enough waffle... the problem** - the exact problem is detailed here : [http://www.nabble.com/Macmini-on-Hardy-Heron-td16930001.html#a16930001]("http://www.nabble.com/Macmini-on-Hardy-Heron-td16930001.html#a16930001")

To summarise - when I press a remote key, IRW senses it correctly.  Then I press (say) volume up on my amp's remote control and Lirc detects the key press as the last key I pressed on the apple remote!  So if I press "Left" on the apple remote, I can send a bunch of lefts to my mac just by pressing the volume keys on my amp.  Very annoying.

Apparently, the guy on nabble wrote a bunch of patches to Lirc which he submitted to 0.8.3 pre3, which I assume (or hope) were subsequently added to 0.8.4.

**So the million dollar question** - does anyone know of a way to install 0.8.4 on an Ubuntu box?  I've checked Intrepid and it's still using 0.8.3.

And when I ask that question about how to install it, I very much mean "without compiling", since I have no idea how to do that.  I can't even compile "Hello World" programs.  If, by some miracle, they claim to have compiled, then they still don't work.  Having looked at the install instructions for Lirc, I know when I'm out of my depth.

So, a PPA, a Deb, a repo, a static binary even.  The closest I could find was an OpenSuse 10.2 RPM, but that didn't include lirc-x, so still wasn't any use, even if I'd figured out how to use alien.

It's a real bummer actually, cos I even managed to put together a bunch of apple remote codes in a single lird.conf file giving me about 18 codes which I could stick into my Harmony universal.  I'm telling you, OSX and FrontRow has absolutely nothing on this set up.  I'll say it again, XBMC (or "Plex" if you run the OSX version) is stunning.

If you can help with a deb of lirc and lirc-x, I'll be a very happy man indeed.

---

### Post by cyberdork33 on 2008-10-20
I think you are stuck compiling unless someone creates a deb for you, but you will need to post your kernel information and stuff for that to work. (uname -a).

You also might file a bug and note that the newer version fixes things and the newer version could be added to Intrepid.

---

### Post by scaine on 2008-10-21
Good call on the bug report - I might stand a chance of a backport that way.  I'll look at the compiling again, but I think I might have more chance of landing a plane with my EEE than successfully compiling Lirc for my MacMini.  I know my limits and past experience at compiling has seriously dented my confidence at that stuff.  Gimme a router, firewall, tricky VPN or virtual machine any day.  You know where you stand with that stuff.

Still, if anyone comes across this thread and knows a good Ubuntu deb, lemme know.

Thanks.

---

### Post by scaine on 2008-11-10
Just a short note to say that the 0.8.3 lirc install in Intrepid has fixed this issue.

I'm not sure if 0.8.4 is actually out yet, but where Hardy used 0.8.3-Pre1, Intrepid appears to be using the final 0.8.3 release, which incorporates all the pre1-3 patches.

XBMC and Lirc on the Mini is superb as a media centre.

---

