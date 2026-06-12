---
title: "/dev/dsp + macbook + karmic - where is it?"
date: 2010-08-25
forum: Apple Hardware Users
---

### Post by bkbroiler on 2010-08-25
Hi,
 I have karmic koala installed on my macbook pro and I can't seem to find '/dev/dsp'?

 My sound works perfectly fine, but when I try to open up /dev/dsp to do some audio recording via python/perl it complains that the specified file does not exist.  Sure enough it doesn't.

  A look around showed that 
/dev/snd exists and takes the following form,
ls /dev/snd -1
by-path
controlC0
hwC0D0
pcmC0D0c
pcmC0D0p
pcmC0D1p
seq
timer

  but 'dsp' is nowhere to be found and none of the apparent alternatives seem to work for recording or catting or other good fun.

  Any insight would be appreciated!

---

### Post by bkbroiler on 2010-08-26
Any thoughts, anyone?  I've never seen this before and it's making me a bit crazed.

---

