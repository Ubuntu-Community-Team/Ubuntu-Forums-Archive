---
title: "unable to open display error"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by dondad on 2007-04-11
This is my first post, and I would like to take the time to thank all that put in time here. I finally got tired of Windows (and Vista scares me) and decided to go to Linux. I ran Xandros for a little while, but it is too proprietary for me. I have had Ubuntu running for a few days now and like it much better. I have been cruising through the threads and managed to get my NTFS partition r/w, all of my mail etc. imported, found replacements for most of the things that I use most,and so far I like the way it runs.I know little about Linux and have a few questions. I plan to go through the documentation and try to fix at least some of that. I apologize if I should be posting in separate posts.

I think that I did a bad thing before I read enough, and enabled the root login, which I  now understand is not a good idea. Can you tell me how to fix that and get it back to the way it was when I first installed it? I saw a couple of threads that mentioned removing the root password, but no mention of how to do it.

Not sure if it is related to enabling the root, but whenever I try to run much in the console, I get an "unable to open display" error. This is for such things as xev. (I have a logitech mouse and want to get the buttons working as soon as I figure out how to keep from breaking stuff ;-)). I get the same for "gksudo gedit" and many others. What did I do to the system?

The last one is trying to get to shared folders on the ubuntu box from a windows box on my home network. it asks for a name and password, but I never set anything that I know of. I tried all combinations of user names and passwords from both machines and nothing works. I can see the windows box fine from this one.

Again, I have gotten a lot of info searching the threads and appreciate all of the time spent.


I got everything resolved except the share. I see a few threads about that, so will read through them and if I still can't get it to work, I will repost that part. Thanks to all for the help.

---

### Post by heimo on 2007-04-11
I'll only try to answer one part of your question.

You could try setting DISPLAY variable like this:
```
DISPLAY=:0.0 gksudo gedit
```
Does it launch gedit?

Make sure that your regular user is able to run commands with sudo - eg. try running:
```
sudo -i
```
It should ask your password (if you haven't run sudo in last couple minutes) and change prompt from $ to #. If that works, you can "disable" root with:
```
sudo passwd -l root
```

---

### Post by dondad on 2007-04-11
Thanks!!. If I put in the display=:0.0 in, it works. It appears that I need to do this every time I want to run it. Is this normal? Can it be made permanent? (I closed gedit, then tried it again without the display stuff and it gave the error again.) I finally found the run (alt-f2) and can run gksudo gedit from there. Is that the same as invoking it from the console? This is a fairly steep learning curve for me. Haven't had this much fun for a long time.


I tried the other command you gave and the prompt changed to the #, so I did the sudo passwd -l root and everything is still working, so hopefully......

Now if I can just get to be able to see the ubuntu box from the windows one, I will have 90% or better of what I need.

---

### Post by heimo on 2007-04-11
I don't know why your display variable is messed up. You can try to put it in (dot) .bashrc file in your home directory with command:
```
echo export DISPLAY=:0.0 >> .bashrc
```

Then you'll have to open a new terminal before this change takes effect. Or just run:
```
. ~.bashrc
```
(there is one dot in the beginning, space, tilde and another dot before bashrc)

---

