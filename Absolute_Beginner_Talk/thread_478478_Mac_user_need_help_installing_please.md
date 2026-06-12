---
title: "Mac user need help installing please"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by SR_Judd on 2007-06-19
So I am interested on installing ubuntu for my macbook then eventually getting beryl. Anyone know how much space Beryl will take? I would like to run both OS X and Ubuntu on the same computer, not simultaneously. Is there a big risk of losing all my OS X files? Basically I have no idea what I am doing, and was just wondering what downloads I need to get. Will bootcamp work for running Ubuntu with OS X? I have heard there are a lot of problems with ubuntu on mac, but they should definitely be fixable, right? If someone could just give me an overview of the install(bootcamp? install versions and ubuntu verisons, etc.) and general information I would really appreciate it. Also, would beryl be complicated once I get ubuntu up and running? Kinda confused on the whole idea of beryl, just know it looks amazing and I need ubuntu to run it.

Thanks in advance

Sorry, it is an intel based mac. So I can partition it and run 2 OS's then without any other software? Ubuntu has that built in?

---

### Post by p_quarles on 2007-06-19
The specifics depend on what kind of chip your Mac is running. If it's a PowerPC, follow these instructions:
[https://help.ubuntu.com/community/Installation/PowerPC](https://help.ubuntu.com/community/Installation/PowerPC)

If it's Intel:
[https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386)

---

### Post by defrex on 2007-06-19
[This]("https://help.ubuntu.com/community/MacBook") should be a good start. You don't need all that much hard drive space for an Ubuntu install with Beryl. I few gigs would do the trick (though you should think about using more, since you may need it eventually).

Beryl is not to hard to install. It's as simple as running this at a command line:
```
sudo apt-get install beryl emerald-themes beryl-manager
```

And for the record, you can run Beryl on any modern Linux desktop, not just Ubuntu (though of course, I'm not saying you shouldn't use Ubuntu anyway)

---

