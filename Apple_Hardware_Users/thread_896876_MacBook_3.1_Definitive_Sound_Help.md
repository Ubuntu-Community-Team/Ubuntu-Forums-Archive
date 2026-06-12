---
title: "MacBook 3.1 Definitive Sound Help?"
date: 2008-08-21
forum: Apple Hardware Users
---

### Post by 3strandchords on 2008-08-21
Hi all...

Is there a definitive thread for addressing sound card issues with a MacBook 3,1?

I've got just such a MacBook... And while the install instructions here ([https://help.ubuntu.com/community/MacBook_Santa_Rosa#Wireless%20Setup](https://help.ubuntu.com/community/MacBook_Santa_Rosa#Wireless%20Setup)) helped me get the machine installed flawlessly, I'm still completely unable to get the sound working.

I've followed the steps outlined on that page to DL/configure/install the ALSA drivers, but I'm still getting nothing out of the speakers.  All the various pages seem to be mixing/matching their instructions for 3.1 and 4.1 MacBooks.  If someone's written a guide specific to the 3.1 MacBooks, I'd love to know.

Thanks.

---

### Post by cyberdork33 on 2008-08-21
> **3strandchords said:**
> Hi all...

Is there a definitive thread for addressing sound card issues with a MacBook 3,1?

I've got just such a MacBook... And while the install instructions here ([https://help.ubuntu.com/community/MacBook_Santa_Rosa#Wireless%20Setup](https://help.ubuntu.com/community/MacBook_Santa_Rosa#Wireless%20Setup)) helped me get the machine installed flawlessly, I'm still completely unable to get the sound working.

I've followed the steps outlined on that page to DL/configure/install the ALSA drivers, but I'm still getting nothing out of the speakers.  All the various pages seem to be mixing/matching their instructions for 3.1 and 4.1 MacBooks.  If someone's written a guide specific to the 3.1 MacBooks, I'd love to know.

Thanks.They are mixed for 3,1 qnd 4,1 because they are the same.
The wiki page says nothing about dowloading and compiling ALSA.
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#Fix%20Sound](https://help.ubuntu.com/community/MacBook_Santa_Rosa#Fix%20Sound)

---

### Post by 3strandchords on 2008-08-22
TY for the post, Cyberdork (not being offensive, that's just your name).


Sorry for being unclear: 
1) I followed the instructions from the wiki you linked after a clean install of ubuntu 8.04.  It didn't work.  The speakers still aren't putting out noise.

2) So, I went through the ALSA steps listed in the article I linked.  Still no sound.

Anyone have any idea what I might be missing?  I'm willing to start over - from scratch - if I need to in order to get this working.

Thanks,   3strand

---

### Post by cyberdork33 on 2008-08-22
> **3strandchords said:**
> TY for the post, Cyberdork (not being offensive, that's just your name).I am never offended by the term.


> **3strandchords said:**
> Sorry for being unclear: 
1) I followed the instructions from the wiki you linked after a clean install of ubuntu 8.04.  It didn't work.  The speakers still aren't putting out noise.
Well, you and I linked to the same page so I don't know how the instructions are different I guess... You do not need to recompile ALSA for your hardware.

> **3strandchords said:**
> 2) So, I went through the ALSA steps listed in the article I linked.  Still no sound.
can you post the output of the following commands:
```
cat /proc/asound/version
cat /proc/asound/card0/codec#0
amixer
```

---

### Post by 3strandchords on 2008-08-25
A bump, a thanks, and a final request:


Well, I finally got the sound 'working' on my 3.1 MacBook.  Twice I reinitialized the partition and reinstalled ubuntu 8.04 until the published fix (linked in the thread above) finally worked.

Don't ask my why it seemed to fail the previous two times.  I don't know, and don't particularly care.  :)

I do have one linger question however:  I'm experiencing the 'tinny' sound issue now.  While this is an improvement over where I was before, it's still kinda lame.

Both published fixes (which involve using either the Volume Control or the Gnome Alsa mixer to access the SURROUND SOUND settings) aren't working.  The main reason:  Surround isn't listed as an option for checking/unchecking/unmuting anywhere.

Is there a config file I can hack to get it back right?

EDIT - Same problem being experienced in the thread over here:
[http://ubuntuforums.org/showthread.php?t=895191](http://ubuntuforums.org/showthread.php?t=895191)

I'd ask that f'ups be posted there, lest I be guilty of more multi-posting.


Thanks much...

---

