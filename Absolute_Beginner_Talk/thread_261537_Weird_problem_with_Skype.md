---
title: "Weird problem with Skype"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by Jeeks on 2006-09-20
Hello

I am using now the latest Skype (1.3.0.37) that I downloaded and isntalled because the older one stopped working.

Here's the story:

After I installed ubuntu, one of the first apps that I installed was Skype. Without any hassle or trouble it worked perfectly fine, I held a couple of audio conversations and I used skype out as well. Worked like a clock. I have absolutely no idea why one day it started giving me "Problem with sound device". The error happens immediately when I place a call or when I receive one.

I browsed through threads here and on the skype forums looking for solutions and trying without even caring about the consequences and still nothing happened.

Then a friend pointed out the release of the new version, so I rushed to get it. Downloaded, installed and immediately started testing.

Using OSS, the behaviour is exactly the same as the older version.

Using ALSA, the program rings the contact but when the other side answers, it gives me the error "Problem with sound device".

Using ALSA, when I make a skype-out call, immediately it says Connecting, then it says Call failed.

Any help will be greatly appreciated.

Thank you :)

---

### Post by Jeeks on 2006-09-20
Bump :D

---

### Post by Jeeks on 2006-09-23
Another bump :(

---

### Post by perce on 2006-09-23
Skype has a forum for Linux users: [http://forum.skype.com/](http://forum.skype.com/) have you tried to ask there?

---

### Post by user1397 on 2006-09-23
> **perce said:**
> Skype has a forum for Linux users: [http://forum.skype.com/](http://forum.skype.com/) have you tried to ask there?you might have missed this: >  I browsed through threads here **and on the skype forums** 

---

### Post by Jeeks on 2006-09-29
It seems that no one can help me with this.

---

### Post by KhaaL on 2006-10-05
I too would like to get help with this...

---

### Post by sailor2001 on 2006-10-05
did you go to synaptics and search for alsa pkgs? apparently you are missing some library for alsa. there are quite a few alsa pkgs

---

### Post by KhaaL on 2006-10-05
um, what alsa pgks exactly? it passed the dependency check...


Jeeks, when you run skype in the terminal, do you also get:

ALSA lib pcm_dmix.c:801:(snd_pcm_dmix_open) The dmix plugin supports only playback stream

When trying to make a call? also, what devices do you have selected in gstreamer-properties ?

EDIT: I've trying to run skype with aoss and setting the sound device to oss, but it resulted in a spam of: "read error, res = -1 , handle = 25"

---

### Post by Jeeks on 2006-10-06
I killed ubuntu from my system and now I am using Gentoo. Thanks for all the help (or lack of it). You may close this thread.

---

### Post by Dafydd on 2006-11-04
> **Jeeks said:**
> I killed ubuntu from my system and now I am using Gentoo. Thanks for all the help (or lack of it). You may close this thread.

shame. i've given up on ubuntu twice (moving back to windows, and then to suse 10.0 and 10.1) but have come back to ubuntu now for quite a while.

still, i have the same problem with skype when running the vsound skype-rec script.

But if I run skype normally everything is fine.

mmmmmm
Dafydd

---

