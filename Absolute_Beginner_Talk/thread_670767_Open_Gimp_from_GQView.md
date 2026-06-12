---
title: "Open Gimp from GQView"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by ofb on 2008-01-17
I didn't find the answer to this when searching Ubuntu Forums, so I'm posting it here for others.

In GQView, you can right-click an image and select Edit In The Gimp, but that no longer works with 7.10.

So open GQView preferences, and select the Editors panel. You'll see the menu item for Gimp runs the command 'gimp-remote -n %f'. Change that -n to -s. Gimp can now be launched by right-click selection again.

----

For the curious, here's how to figure out that sort of thing.

Start GQView with terminal by entering 'gqview'. Now try the failing operation, which in this case is right-click-select Edit In The Gimp. The terminal will show an error about -n not being recognized.

So have a look in the manpage for gimp-remote by entering 'man gimp-remote' in another terminal. Have a look at the options, and you'll see there is no -n listed. How curious.

Also if you read the description of gimp-remote, it appears to do exactly what is wanted in GQView, so we have no hint about what extra function was intended by that -n.

So to Google with a search for GQView and gimp-remote, and voila: -n used to be the way to order no-splash in gimp-remote, but that's been changed to -s.

Which leaves only the question of what is that '%f' for? Dunno. There's no reference to it in the manpage for gimp-remote. Probably it's just Linux being a little sloppy and showing its knickers -- like %f is a special character for line-end or somesuch. So I left it there and only altered what was needed. All done.

---

### Post by nikoPSK on 2008-01-17
% is a job. :)

---

### Post by someonestolemyname on 2008-01-17
Yeah, i'm pretty sure that the %f passes the filename to Gimp.

Nice job, btw.

---

### Post by ofb on 2008-01-17
So, it's for scheduling? Sets priority at less than queue a through e?

Why is it used here? What would be default?

Just curious. I'm quite out of my depth now.


EDIT: I've just tried without it, and Gimp fires up with the desired image normally, so it's not about passing the filename.

---

### Post by nikoPSK on 2008-01-18
I would say this is in tutorials or testimonials? :) 

nikoPSK

---

### Post by ofb on 2008-01-18
Ah, here we go. From GQView's Help > Release Notes:

> ======== Editor command macros                               [section:editors]

 Any one of the following filename markers may be used:

    %f  Replaced with list of selected files, may occur once.
    %p  Command is run once for each selected file, may occur multiple times.
   none When neither %f or %p exist, list of files is appended to command.

 Use of the following to display output window for the command:

    %v  Display result of command in output window, must occur as first two
        characters in the command, or immediately after the "%w" macro.
    %V  Like v above, but when used with %p, only displays output window for
        multiple files. The output of a single file is suppressed.

 Additional macros:

    %w  Prevent full screen from deactivating when command is executed,
        must occur as the first two characters.

---

### Post by rjbgbo on 2008-05-20
\\:D/

Good! Friend.

---

