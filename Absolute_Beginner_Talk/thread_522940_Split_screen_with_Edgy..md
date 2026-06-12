---
title: "Split screen with Edgy."
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-08-11
I've got a 22 inch widescreen monitor delivering here soon. 

For example, I'm trying to learn how to use Blender, and would like to have the pdf tutorial on one half of the screen-to-be and Blender running on the other half. (Blender takes up the whole screen and I can't simply switch between workplaces since the bottom panel is missing.)

Maybe later on, with a TV card, it'd be nice to have TV on one side and work on the other.

I've looked around for an hour or so and can't  find anything about this. Maybe I'm using the wrong search terms. It's probably a basic function that just about everyone else but me knows about..........which is normal ....

Any help appreciated.

Mike.

PS. This is not an issue with any program other than Blender. I can use qcad in one window and run a tutorial in another easy as, and the wide screen will make it better format-wise. It's just that Blender takes up the entire screen and can't, as far as I can tell, be a separate window.

Thanks to all.

---

### Post by MichaelSM on 2007-08-12
Sorry to add to my own thread, but I did a bit more looking around, and found a command which ought to switch Blender from full-screen mode to a window. The command is, "./blender -w"  but it doesn't work. 

Any ideas? I'll keep looking in the meantime..

Mike.

Found how to do it ...

Run in terminal  'blender -w -p 128 128 1024 768'.

In my case with the wide screen I ran 'blender -w -p 128 128 1680 1050'

I then created a Desktop launcher icon and typed that in the 'command' box.

Hope that helps any other newbies.

Mike.

---

