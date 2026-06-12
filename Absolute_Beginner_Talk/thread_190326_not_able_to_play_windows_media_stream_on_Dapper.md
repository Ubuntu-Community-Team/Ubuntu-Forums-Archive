---
title: "not able to play windows media stream on Dapper"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by harys on 2006-06-06
hi, i've gone on this site [http://www.bbcworld.com/content/template_clickonline.asp?pageid=666&home=1](http://www.bbcworld.com/content/template_clickonline.asp?pageid=666&home=1)
and try to listen to window media with totem xine and i have the message that i don't have the necessary plugins installed.
i then installed mplayer from the synaptic package manager (mplayer skin,mozilla mplayer, mplayer fonts, mplayer 386) i use the media player connectivity.with /usr/bin/X11/gmplayer i do have the file directed to my mplayer but when i click on the link and then on the link in media player connectivity i have this message error after the opening of mplayer "failed to open[http://212.58.231.99:80/nfs01/BBCWorld/encodedfiles/worl_010606_show](http://212.58.231.99:80/nfs01/BBCWorld/encodedfiles/worl_010606_show)...........

could you please tell me the trick to resolve this problem and so be able to play windows media stream.
thanks a lot.
harys

---

### Post by Bd0g on 2006-06-06
Do you have the w32codec pack installed & are you running on 32bit or 64bit cpu plattform?

---

### Post by frodon on 2006-06-06
As Bd0g said, you need to install the w32codecs packages to read windows media videos, you will find some instructions in this wiki page : 
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by harys on 2006-06-06
thanks for your prompt reply, 
i had already the w32codecs installed. how to know if i'm running on a 64bit or 32bit cpu platform. 
thanks.

---

### Post by frodon on 2006-06-06
Type "uname -a" in a terminal to see which kernel you run. If you downloaded the X86 CD of ubuntu you run the 32 bit version.

---

### Post by harys on 2006-06-06
that is the result of uname -a from the terminal 
Linux harys 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

could you please tell me what to do to be able to play windows media codecs either from totem xine or mplayer.
thanks.

---

### Post by frodon on 2006-06-06
It's strange because it worked like a charm for me after the w32codecs install, if i remember well there a tab in mplayer to set the w32codecs library path, maybe this path is not set.
By the way wich instructions did you follow to install the w32codecs ? Are you using dapper or breezy ?

---

### Post by Perfect Storm on 2006-06-06
Try with VLC and see if you like it.

By the way did you install the mozilla mplayer plugin?

---

### Post by harys on 2006-06-06
hi, since i'm working under a proxy limitation, i downloaded on my key usb and unpacked it on my pc. 
thanks

---

