---
title: "Shortcut issue"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by drafael on 2007-07-06
Hey,
I've assigned my left start key to start a terminal. It worked fine for a while, but after one or two reboots it's stopped working. I've tried reassigning it to ctrl+r, or the F keys, but no luck.. Either nothing happens when I try the shortcut, or the screen blinks. The other shortcuts seems to work fine (alt+f2 etc.).
I'm running ubuntu 7.04 (Feisty>?) which I installed the other day, so I'm pretty wet behind the ears with this stuff... 
Anyway, any suggestions would be much appreciated!
:KS

---

### Post by drafael on 2007-07-06
Bump :[

---

### Post by p_quarles on 2007-07-06
I did exactly the same thing with my left start key. Seems like a useful way to reclaim that extra button.

But: I haven't had any problems like that. Did you make any changes (particularly as the root user) prior to the boot where it stopped working? Can you still open the terminal at all? 

Aside from that, if you have a Windows machine around, you might try plugging the keyboard into it and seeing if the button isn't simply jammed or broken.

---

### Post by drafael on 2007-07-06
I don't really remember, but it was probably before I used Automatix to install... everything, which helps I'm sure ^_^" I also did a few manual installs, but the only files I myself edited were xorg.conf and the list for application sources (for beryl). I have a backup of the original xorg.conf, should I try restoring it?

I dual boot windows, but I have to say ubuntu has me pretty enthralled now... It's freakishly fast. The left start key works if I assign it to something else, and the terminal shortcut doesn't work no matter what I assign it to... =/

Thanks again!

Edit: Forgot to mention, yes I can still open the terminal.

---

### Post by p_quarles on 2007-07-06
> the terminal shortcut doesn't work no matter what I assign it to... =/

Interesting. But the terminal still runs if you open it with the menu launcher, correct? 

My *guess* here is that whatever file keeps track translating key-strokes into bash commands got changed. Both Beryl and Automatix are likely culprits, as they cause weird bugs on lots of systems. Beryl, especially, would probably reconfigure keyboard commands. 

Unfortunately, I don't know what file that would be. Anyone else?

---

### Post by drafael on 2007-07-07
Bump... It's a minor thing, but really annoying me. >_<

Is there an alternate way to map the terminal to the left start key? Or manually do it?
Doesn't have to be left start, ctrl+r would be fine as well...

---

### Post by drafael on 2007-07-07
Hooray, restored my xorg.conf backup, restarted, and it's working!

=)

---

### Post by drafael on 2007-07-07
Okaaaay nevermind. By restoring the old xorg.conf, I disabled Beryl, which makes it work.

So it's as a result of Beryl... But I like beryl, so I guess I'll have to just go without my precious shortcut key unless there are any other suggestions...?

---

### Post by drafael on 2007-07-07
Ok, finally fixed. For those who want to know:

I put "gnome-terminal" under Command0 in the beryl manager.
I then edited the shortcut for Command0 to <Control>r.

---

