---
title: "Audacity freezes when I try to export .wav to .mp3"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by hul on 2007-11-01
I have a bunch of .wav files I want to export to mp3 through Audacity.  I have the lame and libmp3lame libraries installed.  However, when I choose mp3 and hit export, the export process freezes and crashes Audacity about 1/4 of the way through.  It exports to .ogg just fine.  What's wrong?

Truly, I just want to convert these wav files to mp3, so if Audacity is not the right program should I be using something else?

---

### Post by Pumalite on 2007-11-01
Try soundkonverter .

---

### Post by rsambuca on 2007-11-01
There are other alternatives, but I think it would be better to find out 'why' it isn't working.  Try opening Audacity from the terminal, and then doing the conversion.  This should give you error messages so we can make sure there isn't something wrong with your system.

To run Audacity from the terminal, go to Applications -> Accessories -> Terminal.

Just enter the command:  audacity

Use the program as you normally would, but leave the terminal open.  If any errors occur, they should be shown on the terminal.  You can post the results here.

---

### Post by Pumalite on 2007-11-01
In sounkonverter you can convert one whole folder of files with just one click.

---

### Post by hul on 2007-11-01
> hul@hul-desktop:~$ audacity
sh: jackd: not found

** (audacity:9276): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
Segmentation fault (core dumped)


The "sh: jackd: not found" appeared immediately after entering in the program command.  Audacity still ran normally after that.

Also, this is all in Gutsy Gibbon.

---

### Post by skyjacker on 2007-11-01
> **Pumalite said:**
> In sounkonverter you can convert one whole folder of files with just one click.
I was also looking for a "converter" so I downloaded and installed this program. Where are the instructions on how to use it. the help file is a joke.:confused:

---

### Post by Pumalite on 2007-11-01
There is no Manual because the software is just very simple to use. Just start loading files and choosing formats. The rest is done by the program.

---

### Post by rsambuca on 2007-11-01
> **hul said:**
> The "sh: jackd: not found" appeared immediately after entering in the program command.  Audacity still ran normally after that.
** (audacity:9276): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
Segmentation fault (core dumped)

Also, this is all in Gutsy Gibbon.
The clearlooks error is very strange.  It is basically an error with your window manager theme.  I am sorry, but I have no idea why this should cause a problem with audacity converting to mp3's.

---

