---
title: "Using Mbrola with Espeak"
date: 2010-03-07
forum: Assistive Technology &amp; Accessibility
---

### Post by go_beep_yourself on 2010-03-07
I've been trying multiple ways of example commands I find on the internet to use espeak with mbrola, none of which have worked.


 $ espeak -v mb-en1 "some text" | mbrola -e /usr/share/espeak-data/voices/mb/mb-en1 - - | aplay -r16000 -fS16
Binary number format error
You are probably using a version of /usr/share/espeak-data/voices/mb/mb-en1 incompatible
with your machine architecture.
Get the right one from the MBROLA project homepage :
   [http://tcts.fpms.ac.be/synthesis](http://tcts.fpms.ac.be/synthesis)
aplay: playback:2297: read error


 I am trying to develop my software to use mbrola voices and epeak because it gives better command line options, but if I can't make this work from the command line, I am unable to further my software. I've started a google code project, but I want it to be decent before I release it out to the public. Would someone help me understand how all this works? BTW, I am using 64-bit Ubuntu, and it gave me an error about about machine architecture.

---

### Post by Sef on 2010-03-07
$>  espeak -v mb-en1 "some text" | mbrola -e  /usr/share/espeak-data/voices/mb/mb-en1 - - | aplay -r16000 -fS16
Binary number format error
You are probably using a version of  /usr/share/espeak-data/voices/mb/mb-en1 incompatible
with your machine architecture.
Get the right one from the MBROLA project homepage :
   [http://tcts.fpms.ac.be/synthesis](http://tcts.fpms.ac.be/synthesis)
aplay: playback:2297: read errorSee Question 2 of their [FAQs]("http://tcts.fpms.ac.be/synthesis/mbrola/mbrfaq.html").

Question 2 answer:

> You are not providing a MBROLA database to the software. Many possible  causes: either you got quite an old MBROLA database, so fetch a new one [**here**]("http://tcts.fpms.ac.be/synthesis/mbrola/mbrcopy.html#DATABASES")**  , **or you gave a wrong file. A typical error is to type *"mbrola  fr1 bonjour.pho test.wav"*   instead of *"mbrola fr1/fr1  bonjour.pho test.wav". *Another common problem is to FTP your  database across your local net, and forget to use the BINARY mode while  transferring.

---

### Post by go_beep_yourself on 2010-03-14
So could you show me an example of how to use mbrola voices with espeak properly?

---

### Post by go_beep_yourself on 2010-03-18
bump!

---

### Post by Sef on 2010-03-19
>  		So could you show me an example of how to use mbrola voices with  espeak properly? 	

Have you tried the 3 solutions to solve your problem?  If you have and still have problems, I would write to espeak and ask them for help.

---

### Post by go_beep_yourself on 2010-03-25
I found the answers I need in /usr/share/doc.

---

### Post by Sef on 2010-03-26
> I found the  answers I need in /usr/share/doc.

Could you please explain what you did to resolve your problem, so that others may benefit from your experience.  Thank you.

---

### Post by go_beep_yourself on 2010-03-27
> **Sef said:**
> Could you please explain what you did to resolve your problem, so that others may benefit from your experience. Thank you.

Yes, to start, the /usr/share/doc directory is a great source of information. It should be bookmarked in nautilus, so that it shows up in the left pane and under "Places" on the Gnome Panel. Have a look at /usr/share/doc/espeak and /usr/share/doc/mbrola. There are some html files in there as well that will open in Firefox. Most of everything you have installed should have a directory under /usr/share/doc with documentation that can be read.

What I discovered is that none of the Ubuntu packages in Karmic contain the mbrola voices. They must be downloaded as described in /usr/share/espeak/mbrola.html

Also, what I said about Mbrola voices not being included in the repos applied to Karmic. Fred on the Ubuntu Mailing List confirmed that the voices are included in the repos for Lucid.

---

### Post by WitchCraft on 2010-04-24
I'm on Lucid, and for me, this works:

```

espeak -v mb-en1 "Hello World" | mbrola -e /usr/share/mbrola/voices/en1 - - | aplay -r16000 -fS16


Note:    /usr/share/mbrola/voices/en1
and not: /usr/share/espeak-data/voices/mb/mb-en1

```

---

### Post by WasMeHere on 2011-04-02
Thank you WitchCraft,

Your example helped me make the computer speak (in Lucid). I use the following one-line script files for Swedish.
'male'
```
espeak -v mb-sw1 "$*" 2>/dev/null | mbrola -e /usr/share/mbrola/voices/sw1 - - | aplay -r14000 -fS16 2>/dev/null

```
'female'
```
espeak -v mb-sw2 "$*" 2>/dev/null | mbrola -e /usr/share/mbrola/voices/sw2 - - | aplay -r14000 -fS16 2>/dev/null

```

But for many purposes the following simple aliases work well. They make clear voices, although with 'immigrant accents'.

```
alias säg='espeak -v sv -p 65 -s 120 -k10 -a 150 >/dev/null 2>/dev/null '
alias bas='espeak -v sv -p 45  -k10 -a 150 >/dev/null 2>/dev/null '

```

Have fun/Olle

---

