---
title: "Text to Speech"
date: 2009-07-04
forum: Assistive Technology &amp; Accessibility
---

### Post by davidlarg on 2009-07-04
I am looking to have Ubuntu read text that I select.  I have tried kttsmrg but it reads a few words then skips to the next sentence.  The problem happens on both my desktop and my laptop.   On windows I use naturereader and it works great.  Is there another program besides kttsmrg to read text in ubuntu?  

Is there a setting in kttsmrg that I need to change to have it read without skipping words?

---

### Post by UbuKunubi on 2009-07-04
Hello!

I use Festival for this purpose. On 8.04 I used a combination of Python and espeak, but there is some amiss with espeak on 9.04!

This is one of those times when I wish I had bookmarked a site I found, because it contained a 'how-to' to make a launcher for a program that speaks selected text - it is out there I'll see if I can find it for you.

Ubu

---

### Post by davidlarg on 2009-07-05
It sounds like ubuntu 8.04 might be more stable for text to speech.  How hard is it to down grade to ubuntu 8.04?  Do I have to repartion my hard drive?

Thanks

---

### Post by hayden92 on 2009-07-05
I agree with UbuKunubi: Festival

"sudo apt-get install festival"

You can set up voices so that the reader sounds much better, but the default is fine for now.

echo "Hello " $USER ", and welcome to Ubuntu" | festival --tts
or you can try:
festival --tts NAME_OF_A_TEXTFILE

---

### Post by davidlarg on 2009-07-05
Thank you for the info.  
Using the terminal instead of kttsmrg works great ! ! !

:p

---

