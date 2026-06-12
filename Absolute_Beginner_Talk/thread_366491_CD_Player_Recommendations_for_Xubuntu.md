---
title: "CD Player Recommendations for Xubuntu"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by harryc on 2007-02-20
i am looking for a lightweight CD player that works well on Xubuntu. I tried the built in gxine player, but it skips and drops out on CD play. Any ideas on fixing the skips on gxine or recommends on a different player? This is on a old Thinkpad, 600e, PII 400Mhz, 384MB RAM.

---

### Post by ashmew2 on 2007-02-20
how about VLC player ?

if u want it , goto a terminal and type

```
sudo apt-get install vlc
```
Let me know if u liked VLC

---

### Post by C-A on 2007-02-20
what about kaffeine? is that light weight enough for your needs?

---

### Post by grumpymole on 2007-02-20
harryc,

I also run Xubuntu on a TP 600E and found the [same problem]("http://grumpymole.blogspot.com/2006/10/playing-audio-cds-on-tp-600e-required.html").  This blog post has some tweaks that got things to a workable state.  There is an [open bug]("https://launchpad.net/ubuntu/+source/xine-lib/+bug/29296") about this.

---

### Post by harryc on 2007-02-21
Warren, ashmew2,  thanks for the replies. I tried the gxine buffer tweak and it did not fix the problem (yes I did restart gxine). Interestingly enough, VLC does play CD's well. It begins to skip in VLC if I start doing anything with the system, even a simple task like open email. So,, I'm not sure where the answer lies, but I suspect this is a system resource problem that needs to be looked at by developers. I am unsure how to report it or how to quantify it though. Keep the ideas coming, it's appreciated.

---

### Post by ronniew on 2007-04-22
xfreecd is in the repositories.. I use it and it works great.... you will have to create your own launcher for it... Its a gtk based cd player..

hope this helps

---

