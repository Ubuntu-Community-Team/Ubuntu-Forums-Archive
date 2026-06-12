---
title: "ATI problems :-/"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by illegalamigo on 2006-08-31
Hi,
I can only operate Ubuntu from the Recovery version because the other version has a black screen when I start it up. I was told that it's because Ubuntu has problems with ATI drivers. So I did some searching and found these commands:

sudo apt-get update
sudo apt-get install linux-restricted-modules-$ (uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now

This works until I get to "sudo aticonfig --initial" I get the message:

sudo: aticonfig: command not found

Can anyone help me? I'm trying to get my video card to work. I have an ATI 9800 Pro. Thanks.

---

### Post by illegalamigo on 2006-08-31
I forgot to mention:

It's Ubuntu 6.06 64 bit edition.

---

### Post by toasted on 2006-08-31
What ATI card model do you have?

Oh I just saw you posted it...

---

### Post by nazgulord on 2006-08-31
That's weird.

Try removing and then reinstalling the xorg-driver-fglrx package.

Also, do you just get a blank screen with nothing on it or do you get some error output?

nazgulord.

---

### Post by toasted on 2006-08-31
This is the one I use as the new drivers wont work for me for some reason
Try this how to. It should fix you up

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

---

### Post by illegalamigo on 2006-08-31
Thanks guys. I'll try both of those and update this thread later tonight with my progress. It's just a black screen, no error output.

---

### Post by nazgulord on 2006-08-31
Ok, I may have run into this problem as well.

Try this:

When you get the blank screen, hit Ctrl+Alt+F1, and it should put you back to a terminal. You should also have some X server error output there (that's what happened to me). You could then post this error output here or search the forums for similar issues.

I'm sorry, but I'm probably not going to be much more help solving this as I wasn't able to solve it when it happened to me (It was an old computer, and I switched to another distro for it).

Good luck,

nazgulord.

---

