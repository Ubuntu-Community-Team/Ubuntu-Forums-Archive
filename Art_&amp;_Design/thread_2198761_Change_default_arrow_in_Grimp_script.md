---
title: "Change default arrow in Grimp script"
date: 2014-01-10
forum: Art &amp; Design
---

### Post by magpie03 on 2014-01-10
Starting to use Gimp everyday now to put arrows on images. I've installed the arrow.scm fu script, but I have to change the default pariminters every time. Can I change the defaults?
I modified the script found in home/.gimp-2.6/scripts and home/.gimp-2.8/scripts but it dosen't work. There is no arrow script in /usr/share/gimp/2.0/scripts.

The default is:

Length of wings  -2.5......I want it set at -12.5
Percentage size of notch of arrow head 75....I want it set at 50
Brush Thickness -25.....I want it set at -100

Part of the orginal script is:
SF-ADJUSTMENT  "Length of wings (LoW = AL/X) *" '(**-2.5** -100 500 10 1 1 1)
  SF-ADJUSTMENT  "Angle between arrow and wing in degree" '(25 5 85 5 15 0 0)
  SF-TOGGLE      "Fill head of arrow?" TRUE
  SF-ADJUSTMENT  "Percentage size of notch of arrow head\n(only valid if head of arrow is filled)" '(**75** 0 100 1 10 0 1)
  SF-ADJUSTMENT  "Brush Thickness* (BS = AL/X)" '(**-25** -500 500 1 10 0 1)

After backing up the orginal, I changed it to:
SF-ADJUSTMENT  "Length of wings (LoW = AL/X) *" '(**-12.5** -100 500 10 1 1 1)
  SF-ADJUSTMENT  "Angle between arrow and wing in degree" '(25 5 85 5 15 0 0)
  SF-TOGGLE      "Fill head of arrow?" TRUE
  SF-ADJUSTMENT  "Percentage size of notch of arrow head\n(only valid if head of arrow is filled)" '(**50** 0 100 1 10 0 1)
  SF-ADJUSTMENT  "Brush Thickness* (BS = AL/X)" '(**-100** -500 500 1 10 0 1)

This does not work. Can it be done? I've never wrote a script before.

Gimp 2.8.2
Ubuntu 12.10
Asus M2N-SLI
6 GB ram
Many thanks all
magpie

---

### Post by ofnuts on 2014-01-12
I'm more familiar with the python-fu scripts...

It looks like it should work.If you are using GImp 2.8 then the .SCM should indeed be put n ~/.gimp-2.8/scripts.

If you start Gimp from a terminal with the --verbose parameter, you will get startup diagnostic messages. Look for either a syntax error or a message about duplicate script definition. 

You can also check "Edit/Preferences" -> Folders -> Scripts to see which folders Gimp searches for scripts.

---

### Post by magpie03 on 2014-01-22
Many thanks Ofnuts. I beleive the script is a python-fu but I'll try what you suggested. Thanks again


magpie

---

### Post by ofnuts on 2014-01-22
No, if the file ends in .scm it's written in Scheme and is therefore a script-fu. Python-fu scripts are technically plugins(*) and are files ending in .py, marked executable on platforms where it matters (Linux, OSX and other Unixen), and kept in the "plugins" subdirectory. 

(*) you can do a lot more with Python than with Scheme

---

