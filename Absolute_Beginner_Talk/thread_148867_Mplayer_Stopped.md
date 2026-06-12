---
title: "Mplayer Stopped"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-03-22
Hey,
I tried searching for this and can't find an answer.

When I use mplayer to watch embedded video, it buffers and then just says "stopped".  No errors, nothing.  I have installed all the codecs I know how!

Any ideas?

---

### Post by celloandy on 2006-03-22
I assume when you say "embedded," you mean it's the mplayer plug-in within Firefox, or something along those lines?  If so, I've seen it exhibit this behavior sometimes when another program is using the Xv extension.  If you're not familiar with X, it's a bit technical, but basically, a current limitation of the way the graphics system on Ubuntu is designed is that only one program can be using the X Video extension at a time.  If you have totem, or another mplayer, or something else video-ish running, try closing it and see if the thing starts playing.

Andrew

---

### Post by brandoncolorado on 2006-03-23
Hey celloandy,

Thanks,

I did mean the embedded player in Firefox, sorry I should have been more specific.  I have tried with only the one window of Firefox running.  Still the same problem.  I thought it may have been because I had two windows running, but no.  The only other media type program I may have had running was rhythmbox.  I tried with that closed.

Still no go.
:(

---

### Post by celloandy on 2006-03-23
Try right-clicking on the embedded mplayer box and clicking "Copy URL," then, from a terminal, running "mplayer [pasted url]" and seeing if it works.  That'll help determine whether it's mplayer or the plugin that's at fault, and if it's mplayer, it might provide an error message that may help in diagnosing the problem.

Andrew

---

### Post by brandoncolorado on 2006-03-23
Hi again,

So here is what it said at the end

MPlayer interrupted by signal 11 in module: decode_video
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
alsa-uninit: pcm closed

---

### Post by brandoncolorado on 2006-03-23
I hope you CAN and WILL help because I don't know how to do what it asked.
:D

---

### Post by brandoncolorado on 2006-03-23
Update:

I uninstalled the w32codecs package and reinstalled.  Looks to have done the trick.

---

### Post by celloandy on 2006-03-23
Well, that's certainly good, because I'm not quite sure what I would have recommended, next, except to try compiling your own mplayer, though I'm not sure that that would have fixed it, either... anyway, glad you got it working.

Andrew

---

