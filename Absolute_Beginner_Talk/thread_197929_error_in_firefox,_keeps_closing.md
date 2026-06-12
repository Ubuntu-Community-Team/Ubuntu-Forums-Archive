---
title: "error in firefox, keeps closing"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by ikilledclown on 2006-06-16
my firefox web browser keeps suddenly closing without warning, I was told to check any errors in the terminal, and when it happened this came up - 

> The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 290 error_code 167 request_code 144 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

it happens on a regular basis, and usually at the same place over and over again, but then it will stop doing it there and do it somewhere else.
Very strange.
Does anyone know what is up?

Cheers

---

### Post by Dr. Nick on 2006-06-16
Most crashes ive seen with firefox have been caused by flash player. Do the sites it crashes on have any flash content?

You can type 

```
about:plugins
``` into the address bar to see all plugins installed, If you have flash it may be the problem. All the flash plugins in synaptic seem to cause trouble so I would check that first

---

### Post by ikilledclown on 2006-06-16
They do have flash on, and I have flash installed, how would I get rid of it?
Sorry about my stupidity!!

---

### Post by bruce89 on 2006-06-16
i386 or AMD64?

---

### Post by Dr. Nick on 2006-06-16
[quote=ikilledclown]They do have flash on, and I have flash installed, how would I get rid of it?
Sorry about my stupidity!![/quote]

Having flash installed isnt necessarily a bad thing, It just depends on what version of flash you have, some can cause problems like this.

If you are in gnome then open synaptic and search "flash"

Make sure that neither of these 2 are installed

flashplugin-nonfree
libflash-mozplugin

or any other macromedia flash things you see listed

If they are I would remove them and see if that helps.

---

