---
title: "[SOLVED] Reinstalled Feisty, what about multimedia now?"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-10-27
I know how to enable DVD playback and all that in Feisty, but there's a big problem...The medibuntu repo doesn't seem to exist anymore...

How can I obtain the libdvdcss2 w32codecs packages now?

I had to do a fresh install of Feisty after Gutsy decided not to work for me. Any ideas would be very appreciated!

Thanks

---

### Post by AndyCooll on 2007-10-27
You may well be trying the old location for the Medibuntu repositories. Try the following:
```
$ sudo su -c 'echo deb http://packages.medibuntu.org/ feisty free non-free >> /etc/apt/sources.list'
$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

:cool:

---

### Post by isaacj87 on 2007-10-27
Sorry all,

I should of looked better...it was staring me right in the face...Guess they just restructured the repo...

Here's the info for anybody else that needs it! :)

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Long live ubuntu!

---

### Post by isaacj87 on 2007-10-27
> **AndyCooll said:**
> You may well be trying the old location for the Medibuntu repositories. Try the following:
```
$ sudo su -c 'echo deb http://packages.medibuntu.org/ feisty free non-free >> /etc/apt/sources.list'
$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

:cool:

Thanks Andy! but I found it...guess I should of looked better...:lolflag:

Marking thread as solved.

---

### Post by mcmakin50 on 2007-10-27
Go to the Medibuntu site below.  There are instructions on downloading and installing the repository.  I downloaded the entire repository and then loaded the files you mentioned.  Worked great.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Good Luck,

John

---

