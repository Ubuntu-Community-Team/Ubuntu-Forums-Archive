---
title: "I wanna play MP3s!"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by AmazingAnt on 2007-03-28
I've got Ubuntu 6.10 on an old machine, which has no internet connection. Which of course means that I can't install much of anything in the "Add/Remove" thing.
Can anybody tell me where I can get what I need to start playing mp3s on there? It'd be nice to be able to play everything else I have on my iPod as well, but I'll worry about that later.

---

### Post by ceeg on 2007-03-28
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You will need an internet connection.

---

### Post by eljalill on 2007-03-28
You yould check for programs on the install CD 
For this, enable it as a source in synaptics (Setting>repositories), and use the search.
Rythmbox or the like might as well be on there.

Oh, and best disable the internet repositories, if you don't want to end up with loads of error messages, saying, that it can't reach the server :) .

---

### Post by AmazingAnt on 2007-03-28
> **ceeg said:**
> You will need an internet connection.
Well then that needs to be changed. There's gotta be some way this stuff could be downloaded by one computer, and then moved via Flash Drive, or something.
> **eljalill said:**
> You yould check for programs on the install CD 
For this, enable it as a source in synaptics (Setting>repositories), and use the search.
Rythmbox or the like might as well be on there.

Oh, and best disable the internet repositories, if you don't want to end up with loads of error messages, saying, that it can't reach the server :) .
Actually, it installed Rythmbox by default. It just keeps telling me it doesn't have the right codecs, hence my problem.](*,)

---

### Post by rajeev1204 on 2007-03-28
hi

go to packages.ubuntu.com. Select ur version.

get ur packages and u r good to go

---

### Post by ceeg on 2007-03-28
> **AmazingAnt said:**
> 
Actually, it installed Rythmbox by default. It just keeps telling me it doesn't have the right codecs, hence my problem.](*,)

Rhythmbox will not come with proprietary format codecs. This will make the distribution of Rhythmbox illegal, unless it pays for the explicit right to use the MP3 format.

As the poster above me said, you can download the deb from the above website and do this:

```

sudo dpkg --install xxx-xx-x.deb

```

---

### Post by AmazingAnt on 2007-03-28
> **rajeev1204 said:**
> hi

go to packages.ubuntu.com. Select ur version.

get ur packages and u r good to go
It took me about 50 packages, but I got it. And now for some reason no sounds work at all.:shock: Even booting from the CD, the startup sounds worked.

At any rate, it plays the mp3s now, I just can't hear them. :(
So I'm gonna try booting from the CD, I'll re-install it, and then use all the packages again. (Still on my flashdrive.)

---

### Post by balloons on 2007-03-28
you need this:

[http://mirrors.kernel.org/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.2.debian-1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.2.debian-1_i386.deb)

it should install rythmbox and gstreamer by default, this adds mp3 support

---

### Post by AmazingAnt on 2007-03-28
> **ceeg said:**
> Rhythmbox will not come with proprietary format codecs. This will make the distribution of Rhythmbox illegal, unless it pays for the explicit right to use the MP3 format.

As the poster above me said, you can download the deb from the above website and do this:

```

sudo dpkg --install xxx-xx-x.deb

```
Didn't see that, but I can understand the need for keeping them separate. It could still be made a bit easier.

---

### Post by djsroknrol on 2007-03-28
Seeing as you don't have internet, I would D/L the files onto a flash drive on a computer that does have access and install them from there....

---

### Post by AmazingAnt on 2007-03-28
> **AmazingAnt said:**
> ... and then use all the packages again. (Still on my flashdrive.)> **djsroknrol said:**
> Seeing as you don't have internet, I would D/L the files onto a flash drive on a computer that does have access and install them from there....
Yes, I planned on that already.:D

---

### Post by AmazingAnt on 2007-03-29
> **AmazingAnt said:**
> So I'm gonna try booting from the CD, I'll re-install it, and then use all the packages again. (Still on my flashdrive.)
On top of the hour and a half or so installing Ubuntu and then putting all my settings back how I wanted them, it took about another 30 minutes to install all the packages. But, it works, and I can now play everything I have on my iPod except for the stuff I bought through iTunes.
Anyway, thanks to everyone for helping.

But, I do have one comment to add. I'm glad I moved this computer over to Ubuntu, because being a 500MHZ computer, it locked up all the time under WinXP. Now it's playing video podcasts:popcorn:  just as fast as any other computer would with no problem. Yay Linux!

---

