---
title: "Finishing installation after reconfiguring"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by AgelessDrifter on 2007-04-11
Ok, so I receive this "no screens" error when I boot up the LiveCD. I've seen in a few places, and been told by a member here, that if I

```
sudo dpkg-reconfigure xserver-xorg
```

and screw with some of the driver settings (change the default video card drivers from nvidia to vesa) I can get past this problem.

I tried it, and I encountered this problem:

After the reconfiguration is complete, I get put back at the command prompt. Linux code is greek to me, and I don't know much of anything about how the LiveCD is configured, so I don't know how to continue running the installation/Live desktop from this point. All I could think to do was

```
sudo reboot
```

which causes me to lose any of the changes I've made to the xorg.conf because I'm still trying to run all this from the LiveCD and nothing is on the hard-drive yet.

What do I do?

---

### Post by heimo on 2007-04-11
If I understand your question correctly, after you've changed xorg.conf you should start gdm. Hmm... I'm not actually sure if Live-CD uses that. So maybe one of these will start your Xorg.

```
startx
sudo /etc/init.d/gdm start

```

---

### Post by AgelessDrifter on 2007-04-11
Wow, it was that simple. All I put in was xstart, and it went straight to the UI. Thanks a lot.

Now though, when I went to shut down (System, shut down on the top menu), everything froze. When I hit CTRL+ALT+F2 to get to a command terminal (forgive me, I don't know the terminology ^_^; ), I got this response:

[IMG]http://img127.imageshack.us/img127/2934/picture144cu4.jpg[/IMG]

Thoughts?

edit: Oh, and nothing I typed once reaching this screen illicited any response at all.

---

