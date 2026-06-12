---
title: "totem crashes while trying to play any file"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by snypercore on 2007-12-29
i copied over my MP3's to my new ubuntu laptop and installed the MP3 plugins for totem and now whenever i tell totem to play any media file it opens then closes just as quick, any ideas?

---

### Post by Hallvor on 2007-12-29
Try running Totem through the terminal (launch it with ```
totem
``` from the command line) and see what comes up when Totem closes.

---

### Post by snypercore on 2007-12-29
dave@dave-laptop:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 49 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
dave@dave-laptop:~$ 


i did read somewhere while setting up this new laptop that with desktop effects on totem will crash when playing a video unless i change it to play using something x or something sorry im a newbie and i cant remember but this happens with just MP3's not videos.

---

### Post by Hallvor on 2007-12-29
What happens if you disable desktop effects?

---

### Post by snypercore on 2007-12-29
works fine then

but how can i make it work with them on?

---

