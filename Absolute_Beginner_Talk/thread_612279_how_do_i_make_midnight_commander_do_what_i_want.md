---
title: "how do i make midnight commander do what i want"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by 900donuts on 2007-11-13
i'm running midnight commander in the console and i've configured my computer to run movies with mplayer using the framebuffer and i was wondering how to get midnight commander to open my movie files with mplayer so that i don't need to type a long command (or remember how to spell the name of the file) every time

---

### Post by rudeboyskunk on 2007-11-13
Don't know how to do that, but if you're typing in the terminal and don't want to type out the entire file name, just start typing it, then hit the TAB key, and it will finish the file name for you.

---

### Post by 900donuts on 2007-11-13
the computer is an old laptop that i'm making so i can laugh at mainstream media player users (zunes and ipods mostly) and i don't want them pointing out flaws and lots of typing would be considered by them to be a flaw

are you sure there is no "open with" sort of thing in midnight commander (or any console file manager) like there is in nautilus

---

### Post by 900donuts on 2007-11-13
could some one at least tell where i could go to have a better chance at finding answers:confused:

---

### Post by Joe Dinmore on 2007-11-13
Don't know about Midnight Commander, but Gnome Commander does that.

---

### Post by wuzzerd on 2007-11-13
Command->Edit Extension file

This is documented with a lot of comments.

---

### Post by 900donuts on 2007-11-14
it looks very confusing could you provide an example of an edited extension file?

---

### Post by wuzzerd on 2007-11-14
Ok, go into the extensions file and search (press the F-6 key ) for include/video

You should find something like this:

include/video
        Open=see %f
        #Open=(mplayer %f   &)
        #Open=(gtv %f >/dev/null 2>&1 &)
        #Open=(xanim %f >/dev/null 2>&1 &)

Put a #  in front of Open=see... , and remove the # on the line with mplayer in it.  

include/video
        #Open=see %f
        Open=(mplayer %f   &)
        #Open=(gtv %f >/dev/null 2>&1 &)
        #Open=(xanim %f >/dev/null 2>&1 &


The Open statement tells mc  what program to use when you press the enter key.  %f refers to the file that is highlighted.  >/dev/null 2>&1 thhrows all text output into a black hole.

---

### Post by 900donuts on 2007-11-14
good i'll try that but how do i add the -framedrop option

also is there a way to open up the file in another screen (using screen) or terminal so that i could easily flip back and forth with out the (for lack of a better word) "residue" that frame buffer apps leave on the screen when they're closed (no one need s to answer this paragraph its just an after thought)

---

### Post by 900donuts on 2007-11-14
never mind i figured it out
just change this

include/video
#Open=see %f
Open=(mplayer %f &)
#Open=(gtv %f >/dev/null 2>&1 &)
#Open=(xanim %f >/dev/null 2>&1 &

to this

include/video
#Open=see %f
Open=(mplayer -framedrop %f &)
#Open=(gtv %f >/dev/null 2>&1 &)
#Open=(xanim %f >/dev/null 2>&1 &

---

### Post by 900donuts on 2007-11-14
new problem midnight commander didn't recognize a .flv that i loaded as a movie how do i tell it to execute mplayer -framedrop on a specific extention

---

### Post by wuzzerd on 2007-11-14
The default file doesn't mention flv so it should be real simple.

Try this just above where we fixed the video player.

regex/*.flv$
          Open=mplayer -framedrop %f

Here we are assuming that the extension is lowercase.

---

### Post by 900donuts on 2007-11-14
thanks that worked

movie time!:popcorn:

---

### Post by wuzzerd on 2007-11-14
Yay!  mc  is one of my favorite programs, I guess because I've been using it years.  I even prefer it when running a GUI. :lolflag:

Enjoy your movies.

---

### Post by 900donuts on 2007-11-15
new problem (before you gave me the fix) i linked one of my files to a mplayer command and it screwing things up for that file how do i unlink it?

---

### Post by wuzzerd on 2007-11-15
Did you link it in mc?

---

### Post by 900donuts on 2007-11-15
yes i navigated the file menu a selected the link option and typed mplayer into the dialog box and now its screwing the file up

---

### Post by wuzzerd on 2007-11-16
Ouch. A link links a new name to a file.  There must be a new file in the directory called mplayer.   If there is one and it is the same size as the original delete the one named mplayer.   meant for you to chhange

---

### Post by 900donuts on 2007-11-16
deleting the new file name mplayer is the first thing i tried and the file is still doing it

---

### Post by wuzzerd on 2007-11-17
Hmm now, I'm at a loss.  Do you have a backup of the file to restore so you can try again?

---

