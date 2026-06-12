---
title: "Segmentation fault"
date: 2005-07-09
forum: Absolute Beginner Talk
---

### Post by Buran on 2005-07-09
My firefox keep falling time after time.
Opened it whith terminal - got this as output after the program closed (in the hundred and one time...) :
> ...:~$ firefox
NP_Initialize
New
SetWindow
SetWindow
SetWindow
SetWindow
NewStream
WriteReady
Write
DestroyStream
Segmentation fault


What i should do  to prevent my Firefox app close itself all the time ?

---

### Post by Buran on 2005-07-15
Somebody? please ! help !
Same thing on Thunderbird.
Crashes all the time.
Reinstalled SDK, but nothing is changed...
 ](*,)

---

### Post by Wolki on 2005-07-15
Are you using the official Ubuntu version?

---

### Post by Buran on 2005-07-15
Downloaded it from this place, yes i think... :neutral:

---

### Post by Wolki on 2005-07-15
[QUOTE=Buran]Downloaded it from this place, yes i think... :neutral:[/QUOTE]

and did you install it with synaptic/apt-get?

because the official ubuntu version from the repository should work fine.

oh, and which architecture do you use?

---

### Post by Buran on 2005-07-15
Installed with synaptic.

architecture :

Intel III
128 X 3 - memory (SDRAM)
Voodoo 3 - videocard
Audigy 2 ZX - for audio card

I really don`t know what is relevant to my problem... :confused:

---

### Post by wellery on 2005-07-15
Maybe it's some sort of ram problem. Try downloading [memtest](http://www.memtest86.com/) and see if your ram is ok. I was getting segmentation faults with some programs and I found out it was my RAM that was the problem.

---

### Post by Buran on 2005-07-16
The memory seems to be good (was good for gigantic WIN XP).

Ran Firefox in some site and got this : (may be there is an explanation)

> NP_Initialize
New
SetWindow
SetWindow
SetWindow
NewStream
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
New
SetWindow
SetWindow
SetWindow
WriteReady
Write

(many times)

WriteReady
Write
Improper call to JPEG library in state 202
Unable to read JPEG data
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
WriteReady
Write
DestroyStream
WriteReady
Write
WriteReady
Write
Improper call to JPEG library in state 202
Unable to read JPEG data
Segmentation fault

---

### Post by freakzilla on 2005-07-19
I've been getting the same problem.  Seems some websites cause it more than others.  I'm starting to think its caused by flash or java on some web pages.  Whatever the cause it makes surfing real annoying. ](*,)  Hope someone has an answer.

---

### Post by wellery on 2005-07-19
Can you please post the url that you tried to cause this crash. You could also try 

the support forum:
[http://forums.mozillazine.org/viewforum.php?f=38](http://forums.mozillazine.org/viewforum.php?f=38)

or the irc channel:

[http://www.mozilla.org/support/firefox/](http://www.mozilla.org/support/firefox/)


or report it on bugzilla

[https://bugzilla.mozilla.org/](https://bugzilla.mozilla.org/)

---

### Post by poofyhairguy on 2005-07-20
I have a solution. I usually do. But like many of my (pratical) solutions, you might not like it- don't use Firefox. Use epiphany. I think its a little better anyway:

> sudo apt-get install epiphany

---

### Post by emrys on 2005-07-28
I have the same problem.

Part of the output is: 

(...)
INFO: Running IndexWebContent
DEBUG: Debug Mode!
Indexing
DEBUG: SendAsync
DEBUG: Close
DEBUG: Done
Segmentation fault

I am with Breezy on an AMD 64. Official Firefox 1.0.6.

Steps to reproduce:

1.Open [www.nytimes.com](www.nytimes.com)
2.Click on Technology link (left menu)
3.Go Back with the up-menu arrow.

---

