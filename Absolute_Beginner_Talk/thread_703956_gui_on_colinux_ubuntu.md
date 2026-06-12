---
title: "gui on colinux ubuntu?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by mooseye on 2008-02-21
I want to set up a desktop in ubuntu running in colinux.
Is it possible and if so how?
 I got the console running last night for the first time.
 Oh yes, I am green as a gourd on linux of any kind. I do have some dos background if that is any benifit.
 I would like to try kde but if gnome is already in there some where I will be happy to start with that.
 Like I said, brand new to linux so don't assume I will understand what lug/pug or ~t/x-y means. Looks like algebra to me and I slept through the whole class. I am, however, decent at following instructions.
 Thanks in advance for any help, as I am very interested in learning about linux.

P S   this is the one I installed from a package (ubuntu7colinux3gb.fs) running on a laptop with 1024mb mem and about 16gb freespace. Let me know if there is other info needed to answer.

P P S  In case it is important, I am running from command line at present.

---

### Post by spiderbatdad on 2008-02-21
[http://ubuntuforums.org/showthread.php?t=81444](http://ubuntuforums.org/showthread.php?t=81444)

You asked how.  A great first step is asking questions here, but obviously any answers are like to come in the form of what looks like algebra. In no time at all, it be more and more familiar.

---

### Post by mooseye on 2008-02-21
Thanks, I found that thread in a search but didn't see the relavance to what I am asking. I must have missed it in the translation.
 Exactly which post/link is it that pertains to my question?

---

### Post by spiderbatdad on 2008-02-21
I guess what I got out of the thread was to go ahead and set up a dual boot with Ubuntu as normal. Once your comfortable with that, move on to creating the colinux instance. The author describes how he obtained colinux, installed it, and configured it to run Ubuntu.

---

### Post by mooseye on 2008-02-21
Sorry, but you missed my question entirly.
 I have ubuntu running via colinux now. What I want to know is if and how to set up a GUI such as gnome or kde.

---

### Post by spiderbatdad on 2008-02-21
DOH!  :redface: 

Sorry I don't know enough about this topic. I would assume to start with installing ubuntu-desktop and xserver, but i really don't know. I did see discussion in that thread though, and a link in the last post referring to nfreex. Good Luck. and here's to you getting some real help!

---

### Post by littlemog on 2008-02-21
i didn't succeed when i was on colinux but i think there's a thread somewhere on the colinux users list that stated this. you tried there yet?

---

### Post by mooseye on 2008-02-22
OK, I thought I had figured it out but after installing gnome and rebooting I got this:

[http://i198.photobucket.com/albums/aa112/mooseye/ubuntuscreenshot-1.jpg](http://i198.photobucket.com/albums/aa112/mooseye/ubuntuscreenshot-1.jpg)

Anyone?

---

### Post by mooseye on 2008-02-22
bump
Is there anyone that can help?

---

### Post by mooseye on 2008-02-22
Ok, I gave it a try. I must say that after all the hype about how supportive the linux community is supposed to be I am quite disappointed in the lack of response on any of the several message boards on which I have posted questions. It has very quickly disintegrated my interest in linux as a whole.
 Thanks

---

### Post by PeterJS on 2008-02-22
Sorry we haven't been more helpful, but do understand that you're working with a very exotic case that not many people have heard of. I've heard of co-linux, but I thought the project died off a long time ago, it's not that we don't want to help, but frankly I have no clue how it works.

EDIT:

Looking at the screen shot the error that jumps out at me is that get-edid isn't installed, get-edid is in the read-edid package in the universe component of the repository. My suggestion would be to enable the universe if you haven't done so already, and install read-edid with:
```

sudo apt-get install read-edid

```
Try again, and post back any errors, I can't promise anything better than trial and an error as I don't know the mechanics of colinux.

EDIT2:

Another option would be andLinux, lifehacker just did a piece on it. I don't know how it stacks up to colinux but it might be worth a look as a fall back option:
[http://lifehacker.com/358208/seamlessly-run-linux-apps-on-your-windows-desktop](http://lifehacker.com/358208/seamlessly-run-linux-apps-on-your-windows-desktop)

---

### Post by foolsh on 2008-03-11
I would just like to add my two cents if anyone cares.

I saw that same article and tried andlinux out.
I had previously done something like this with putty, cygwin and ubuntu running on a different box. Running X, logging in with X forwarding through putty and running apps over the Ethernet. meh.. it was slow what can I say.
but with colinux running on the same cpu as windows.
I have to say It is fast very fast near as fast as when run ubuntu natively. 

something that could be better while using andlinux
1. not defaulting to the root account, just create a new user and change the root password
2. the whole kmenu thing is kinda cool but useless thing in the tray area. its better to disable it and just open the andlinux console and run kicker & close the window. giving you the whole toolbar from kde.

---

