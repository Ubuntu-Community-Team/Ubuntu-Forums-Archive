---
title: "YIKES!  What the heck happened?  Update seems to have hosed everything!"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Scut_Farkus on 2008-02-17
Wow.

It looks like after my last update attempt, my entire system got hosed up somehow.  I've been trying to mess with it via terminal (the CTRL+ALT+F1 terminal....the terminal within GNOME is hosed.  Can't use it.  Can't use Synaptic, either.)

Okay, so it looked like things were going well (finally).  I figured out what was wrong with the broken package and I fixed it.  Then I started to install the all the other 176 packages and that's when trouble started.  At one point, I was told to run something like "sudo dpkg --configure -a", but I can't remember the exact code because I can't get back to my system.  Anyway, I ran that code and here's what happened:

There are too many things to list here, but I'll list a couple things that caught my eye:

There are lots and lots of dependancy problems being listed.  The error will say:

firefox-gnome-support depends on libpango1.0-0 (>=1.18.2);however: 
Package libpango1.0-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
dependency problems - leaving unconfigured

This is just one example.  There are so many (in fact) that at the end of this terribly long list, the system just gives up and says, "dpkg: too many errors, stopping"

I have a couple questions for you guys:

1.)  Is my system so screwed up now that I'll need to re-install (again)?
2.)  Is my system so unstable that re-installing isn't worth it?  I've tried this many, many times and now I think I'm back to worrying about hardware problems.  

I blew away all my archives and it seems that every time I try to grab updates, I end up grabbing corrupted ones, or perhaps my system corrupts them after they've been downloaded?  I know that it's all a learning experience, but I AM getting a bit frustrated.  I like Ubuntu, so I think I want to stick with it (as opposed to some other ideas people have given me, which is to switch to another distro).

Once again, any help you can give me would be very much appreciated.

To ward off some obvious questions, here's what I did:

1.)  I grabbed the ISO myself and burned my own CD.  <--maybe I should order one, eh?
2.)  I verified I had the right iso with the ISO code thingy.  It checked out okay.
3.)  I verified there were no problems with the CD by booting to the CD and running CHECK CD FOR ERRORS.
       It checked out fine, too.
4.)  I ran it in Live CD mode for a while.  Things seemed fine, but perhaps someone out there knows of a good battery of tests I could run in Live CD mode to be sure?  Maybe there's a way to verify my hardware is okay?
5.)  Installed it.  Installation went fine and everything runs fine until I try to grab updates.  That's when I ALWAYS run into trouble.  It always seems to be that the updates don't like what's in my archives.  I blow away the archives and things progress a little and then I hit another snag.  I'll fix that, and then WHAM!  Something so catasrophic hits that I scrape my hard drive with DBAN and start over.  I SO don't want to do that again, but I guess I will if I have to.
6.)  Ram memtest86 for about 90 minutes (3 passes).  No errors, so I think the RAM is okay.

---

### Post by spiderbatdad on 2008-02-17
You might try burning a disk from a different mirror.

---

### Post by Scut_Farkus on 2008-02-17
I'll try anything at this point.  Got a good mirror you can recommend?

All my downloads have come direclty from Ubuntu.  I even tried the Torrent, but the code thingy never worked out on that, so I grabbed the iso directly and the code worked.

I'd love a mirror someone else has used successfully.

Thanks for the fast response!

---

### Post by asmoore82 on 2008-02-17
boot up the LiveCD and open a terminal, find out which device your hard drive is like this:
```
sudo fdisk -l
```
it should be something like ``/dev/sda'' or ``/dev/hda''(I'll assume hda for the rest of this post),

then run these commands to test the hard drive(it should take <1 hour)...
```
sudo -s
badblocks /dev/hda && echo "Done."
```

if you see the "Done." message and get a shell prompt back then you know 2 things for sure:
1. the `badblocks` command completed successfully and
2. it found no problems at all.

any variance in output(either a bunch of numbers, or error messages or you get a
shell prompt and never see the "Done." message) would suggest that your
hard drive is failing you.

---

### Post by Scut_Farkus on 2008-02-17
How VERY interesting!

I did as you suggested, and I booted to the Live CD; however, all I got was my familiar Ubuntu wallpaper.  No icons, to taskbars, nothing.  I typed CTRL+ALT+F1 and here's what it's doing:

There's a count whizzing by at mach 10 on the left of the screen that looks like this:

[  390.xxxxxx] <--x's represent numbers that are moving too fast for me to pinpoint

[  390.xxxxxx] SQUASHFS error: sb_bread failed reading block 0x3db1d
[  390.xxxxxx] SQUASHFS error: Unable to read page, block f6b775d, sizeff45
[  390.xxxxxx] SQUASHFS error: zlib_inflate returned unexpected result 0xfffffffd,src length 65536, avail_in 0 avail_out 0

This continues down the entire screen with the same message and the numbers buzzing by on the left.  It's now up to [  790.xxxxxx]

So I'm pretty sure my system is unstable.  I'll shut it down and run your HDD test as that seems interesting, too.

Thank you! :)

---

### Post by Scut_Farkus on 2008-02-17
Thanks, ran badblocks to completion.

No errors.

Returned "Done." (without the quotes.)

Thanks, at least I know my Hard Drive is okay.

---

