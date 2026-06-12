---
title: "Noob issue -- Rythymbox won't play anything"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by bcdeck on 2006-05-04
I'm an utter Linux noob, but fairly familiar with getting around a computer. I'm running Ubuntu on a Compaq Presario laptop.

When I try to play an audio stream (I've tried Shoutcast, Magnatune and the NPR radio station WAMU), I get nothing. I click on the stream and choose the play with Rythymbox option, and rythymbox starts, but the player window is empty. :confused: 

The Rythymbox version I have is 0.9.0.

Help?

---

### Post by therunnyman on 2006-05-04
Seems to me...

Let me try something here.  Okay, nab the URL of the stream in question.  Open Rhythmbox.  Under "File" up top, there's an option called "New Internet Radio Station".  Click that.  That brings up a little, I hat calling them this, window with three text fields.  Paste the URL in the bottom one, then in the top one, call it whatever you like.

It should appear now amongst your Radio stations, off to the left of your library view.

That work?

therunnyman

---

### Post by hw-tph on 2006-05-04
[QUOTE=therunnyman]That brings up a little, I hat calling them this, window[/QUOTE]

Try "dialog box" instead of "little window". :)


Håkan

---

### Post by therunnyman on 2006-05-04
"Dialog box" it is.

therunnyman

---

### Post by mostwanted on 2006-05-04
You probably haven't installed mp3 support:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by bcdeck on 2006-05-06
Lack of MP3 support was the issue -- got the updated packages and all's well. Thanks, all!

---

