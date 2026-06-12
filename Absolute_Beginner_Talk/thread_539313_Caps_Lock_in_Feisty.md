---
title: "Caps Lock in Feisty"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by imputerate on 2007-08-31
vanilla feisty install: Caps Lock does not work in the tty; 
not on the bash command line;
not in emacs;
Caps Lock works fine in xterm [command line and emacs];
how come?
there a fix?
and, while i'm at it, could i have a Caps Lock which would apply not only to the keys with letters on them, but also to the keys with numbers, like 3/#, and other "double" keys, like ./>? 
imputerate

---

### Post by aitorcalero on 2007-08-31
Try to configure your keyboard through System/Preferences/Keyboard menu. Check if your keyboard model match the one selected there.

---

### Post by imputerate on 2007-08-31
aitorcalero; thanks; your fix worked wonders for X.

 system > preferences > keyboard > layout options > capslock:                            
 Default >  "Capslock toggles Shift so all keys are affected"         
 did the trick;

but, sad to say, in the tty's [terminals], the Caps Lock key is still impotent;

i am still googling to find the "model" of my Adesso PCK308B keyboard, 
it may not be the "Generic 105-key (intl)" Feisty thinks it is.

---

### Post by imputerate on 2007-09-25
system > preferences > keyboard > layouts: "Keyboard model":

i have selected several different models from the long list, one at a time;

no selection results in Caps Lock working in the tty, neither on the command line, nor in emacs;

does telling gnome about my keyboard fail to tell the part of the os which governs tty's?

the keyboard maker was unable to specify a keyboard "model" for my Adesso.

is there some utility or config file where i can see what signal the Caps Lock key is actually sending to readline?

thanks; imputerate

---

### Post by imputerate on 2007-09-26
attention, ubu rois:

i just hooked up another keyboard, usb this time, a really weird jobby [three-piece COMFORT ergonomic];

and its Caps Lock key turns the green light on, like Adesso's, but it doesn't work either;

so, this must be some screw up at a pretty deep level of the OS, no?

---

### Post by imputerate on 2007-09-28
more data:

1/ using a sinble keyboard which is kvm-switched to my feisty and to a slackware box:
  a/ ssh from slackware box [bash in xterm or tty] into feisty [presumably bash in tty]:
      Caps Lock works fine;
  b/ ssh from feisty [bash in xterm] to slackware box [also bash in tty?]:
      Caps Lock works fine;
   c/ ssh from feisty [bash in tty] to slackware box [also bash in tty?]:
       Caps Lock is DEAD!

2/ Caps Lock is dead not only in feisty's tty with the bash shell, but also with these other shells:

/bin/sh, /bin/csh, /bin/tcsh

---

