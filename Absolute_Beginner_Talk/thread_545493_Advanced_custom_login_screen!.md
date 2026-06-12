---
title: "Advanced custom login screen!?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by JuicedJuice on 2007-09-07
Alright, so I'm trying to determine how hard it would be to make a custom login screen that I want and how. Essentially, I want to be able to place the login bar text box in a custom position, have a looping video play in the background, and have custom sounds play upon boot up and login. I think I understand how to do the custom sounds (just need to figure out how to convert my audio to proper format and use the login window preferences) but am unsure of where to begin on the other things.

---

### Post by diatribe on 2007-09-07
I know that the login box can be moved based on the gdm theme (unsure of how though) and as far as having a looping video play in the background I am fairly sure this is not possible

---

### Post by JuicedJuice on 2007-09-07
Is it possible to have an animated gif in the background? Also, how do I open/edit the themes?

---

### Post by Chris S. on 2007-09-07
A good place to start looking would be with xwinwrap.  That lets you draw over the desktop (or perhaps any window?) with, say, video playback.  You may be able to draw over the login background with that, which may or may not be a root window, desktop, or whatever.

Although, you may not be able to do such things during login.  I have no idea.  Good luck.

---

