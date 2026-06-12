---
title: "Com Hangs Whenever I Open A WMV file."
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by davio on 2005-09-18
just as the topic reads, my com hangs whenever i open a wmv file. the strange thing is that i can see the thumbnails of the wmv files. but it hangs when ever i open any wmv file.

---

### Post by davio on 2005-09-19
please help? thanks.

---

### Post by mneptok on 2005-09-19
[QUOTE=davio]just as the topic reads, my com hangs whenever i open a wmv file. the strange thing is that i can see the thumbnails of the wmv files. but it hangs when ever i open any wmv file.[/QUOTE]

What version of Ubuntu? What app is trying to open the .wmv? What does /var/log/messages say?

A little more information would be most helpful.

---

### Post by davio on 2005-09-19
sorry. the version is Hoary Hedgehog. the app that is opening the file is totem. there are no error msg. the screen just freezes. yep. thats it.

thanks

---

### Post by davmac on 2005-09-19
Hi,

To see all the error messages, open up a terminal window and type

"cat /var/log/messages"

or to just see the last 50 messages written to the log type

"tail -n50 /vat/log/messages"

HTH,

Dave Mac

---

### Post by davio on 2005-09-19
alright. thanks!

---

### Post by mneptok on 2005-09-20
[QUOTE=davio]sorry. the version is Hoary Hedgehog. the app that is opening the file is totem. there are no error msg. the screen just freezes. yep. thats it.[/QUOTE]

Totem uses the GStreamer media framework for its codecs. By default, as Windows Media is a proprietary codec owned by a litigious company, GStreamer provides no Windows Media decoder.

You might want to try installing VLC from the Universe/Multiverse side of Synaptic/apt. VLC supports decoding of a huge variety of proprietary formats, and I believe Windows Media is one of them.

---

### Post by davio on 2005-09-20
i installed VLC however, there is no sound whenever i play any of my files. did i install wrongly?

---

### Post by mneptok on 2005-09-20
Always be sure to search the forums before asking questions. In many cases, the question has already been answered.

And in this case, there was a trip for getting Windows Media to play with Totem with a Xine backend. Sorry, I missed it, too. But then, I wouldn't touch wmv with a ten foot pole.

[http://ubuntuforums.org/showthread.php?t=25668](http://ubuntuforums.org/showthread.php?t=25668)

---

