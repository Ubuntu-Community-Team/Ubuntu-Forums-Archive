---
title: "[SOLVED] CompizFusion - how to stop cube from rotating on its own"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by bluepowder7 on 2007-11-25
ok, so on my 7-sided cube, i'm working on a document on one cube face, while another has VLC with a playlist of tunes / videos.  the bugger i'm getting is that each time VLC jumps to the next item in the playlist, it's making the cube spin to VLC's face and takes me away from my word document - so, my train-of-thought is interrupted and i need to flip back to the document view to continue writing.  this is irritating to say the least...  where in the settings do i stop it from doing that???  is it somehow tied to a window becoming active?

---

### Post by DutyDuty on 2007-11-25
Now, I'm not sure this will work since I use amaroK, but can you close the window and still have the music play? It works with amaroK and Banshee, I'm sure. 

If not, can't you just move both windows to the same desktop face, or switch to amaroK or Banshee?

---

### Post by lazyart on 2007-11-25
or maybe minimizing VLC is enough for it to quit stealing focus.  Maybe there is a VLC setting that enables/disables taking focus on the start of each track?

---

### Post by sailor2001 on 2007-11-25
what binding did you use to start rotation? I changed my keystroke to z, but now I have to use a uppercase z when typing si it doesn't start ...esc stops the spin

---

### Post by bluepowder7 on 2007-11-25
Aaaahh!!!  damn, i might just do that.  for some weird reason, i now get these ugly blue "shadows" from all the pull-down menus and any window that happens to overlap the video portion of the player.  reminds me of WinNT's blue-screen-of-death.  *shudder*

hmm, when i close VLC, the tunes stop.  if i minimize it, then as soon as it moves to the next track in the playlist, the cube spins to it and the VLC player comes out of hiding.

as for keeping it on the same desktop face as my OpenOffice, that would work if i'm ONLY working on OO stuff.  but if i do OO and take a short break to poke around in Firefox, it'll just spin me back to wherever the VLC player is.  so, the problem comes back.  :(

i'm wondering it it's a CompizFusion issue or a VLC-wants-to-feel-important issue.

---

### Post by bluepowder7 on 2007-11-25
> **sailor2001 said:**
> what binding did you use to start rotation? I changed my keystroke to z, but now I have to use a uppercase z when typing si it doesn't start ...esc stops the spin

Que?  which menu item are you referring to?  most of my bindings are the defaults.

---

### Post by DutyDuty on 2007-11-25
I can tell you to turn off the reflections plugin in CCSM. that is probably what creates the shadows.

---

### Post by bluepowder7 on 2007-11-25
hmm, reflections plug-in was off, and oddly enough i didn't see that weird blueness yesterday.  but that's a much less irritating issue than the cube auto-rotating.

hmm.  i'm playing saved YouTube vids (mostly for their music), so maybe that's why?  i'll try this with purely audio tracks, and see if VLC / Compiz still spin me around like that.  if they do, i'll try another player.

stay tuned...

---

### Post by bluepowder7 on 2007-11-25
ok, seems like it's only doing the crazy spinning when i have videos loaded.  seems to work just fine and stay "in the background" when playing MP3 files (audio only).

guess i can't use video files for their audio track only unless i run ffmpeg to extract the audio into a separate file for background use.

i think i can mark this as solved....

---

### Post by jken146 on 2007-11-28
In Advanced Desktop Effects, in General Options, there is an option in the Focus tab called Auto-Raise.  Perhaps this is what you're looking for.

---

### Post by bluepowder7 on 2007-11-28
> **jken146 said:**
> In Advanced Desktop Effects, in General Options, there is an option in the Focus tab called Auto-Raise.  Perhaps this is what you're looking for.

hmm, entirely possible.  though, i use auto-raise a fair bit when i have two related windows open on the same desktop and am too lazy to press a button or hit Alt-Tab to switch between them, so i'd probably keep that plug-in activated no matter what.  :P  the good thing is that the auto-spin doesn't happen with music files, just videos, so i can work my way around that.

---

