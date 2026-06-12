---
title: "Stuck in 640X480"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Dasien on 2006-04-19
I have tried sudo dpkg-reconfigure xserver-xorg
and it doesn't seem to do anything please help

dasien

---

### Post by Jagot on 2006-04-19
You may need to modify your /etc/X11/xorg.conf, but could you tell us a little bit more about your set up - are you using a laptop/desktop, graphics card, etc.

---

### Post by Dasien on 2006-04-19
I am using a Dell inspirion 1100 laptop 8245G chipset video card built in.

---

### Post by patrick295767 on 2006-04-19
--

---

### Post by nalmeth on 2006-04-19
hmm, look into i915resolution.
EDIT: thanks Jagot 855 is probably his chipset. Check into 855resolution
That *may* help you out. It's an app of somekind that has helped a lot of intel users. I never needed it.
I think there are some bugs in the i810 driver, but in Dapper (the next release), the resolution kinks seem to be all ironed out.
As an extreme resort, you may want to try Dapper instead, as it is now in beta stage, and becoming more stable.
Check out the [Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/Main_Page") and wiki.ubuntu for some info

---

### Post by Jagot on 2006-04-19
I have a Dell Inspiron 1300 and I used 855resolution from the repos to get my resolution correct.  Instructions are included.

---

