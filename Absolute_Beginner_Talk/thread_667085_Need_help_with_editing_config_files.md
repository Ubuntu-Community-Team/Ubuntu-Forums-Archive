---
title: "Need help with editing config files"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by coax31 on 2008-01-14
Is their an easy way to modify config files besides vi, every time I try to change a file I have problems. How do you  save your changes to config files? How do you exit vi mode? I am using ubuntu server contected to it from ssh

---

### Post by leonidas666 on 2008-01-14
On the command line i prefer nano. I think it's installed by default. All the keyboard shortcuts are listed at the bottom of the screen, so i think you'll be able to operate it more easily than vi.
Otherwise, with X-forwarding, (use ssh -X) you can use any gui editor of your choice, e.g. i prefer kde's kate.

---

### Post by pjkoczan on 2008-01-14
vi has a terrible learning curve. I know many people who fly with vi and they say once you learn it, you are so fast with it...but it takes a lot to learn.

I'd recommend gedit, emacs/xemacs, or pico/nano if you don't want to undertake learning vi. Otherwise, google vi tutorial and go from there.

Best of luck to you. Oh yeah, and use the -X flag when ssh'ing to your remote computer if you want gedit or emacs to open a new window, as was previously said.

---

### Post by ghostdog74 on 2008-01-14
> **coax31 said:**
> Is their an easy way to modify config files besides vi, every time I try to change a file I have problems. How do you  save your changes to config files? How do you exit vi mode? I am using ubuntu server contected to it from ssh

you save changes using :w <filename> or just :w to save to itself.
to exit , use :q or :q!
Whenever you have problems like this, check with google. He can answer almost anything you are not sure with...see [here]("http://www.google.com.sg/search?hl=en&q=vim+reference&btnG=Search&meta=")

---

### Post by ghostdog74 on 2008-01-14
> **pjkoczan said:**
> but it takes a lot to learn.
. 
eventually, you will reach the pinnacle. It goes with anything else. Nothing comes easy the first time.

---

### Post by coax31 on 2008-01-14
Thanks  you guys were a lot of help, I can't believe how much functionality and power is availble with linux. Ubuntu is probably the best contender against Micro$oft of all the distros

---

