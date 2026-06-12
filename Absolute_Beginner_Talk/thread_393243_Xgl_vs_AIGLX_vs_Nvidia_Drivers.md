---
title: "Xgl vs AIGLX vs Nvidia Drivers?"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by craizd on 2007-03-25
First time Ubuntu (and Linux) user here. I just installed the official Nvidia drivers yesterday, 
([http://www.nvidia.com/object/unix.html)](http://www.nvidia.com/object/unix.html)). But certain things (beryl for one) seem to be running pretty sluggish. I was wondering if switching to either Xgl or Aiglx would help and how hard it would to make the switch (there seem to be tons of tutorials about installing on the web, not so much about uninstalling. hehe).

Thanks in advance for anyone that helps.

---

### Post by lonce on 2007-03-25
Here is a link to tweak Beryl.  It worked really well for me and was Dugg on the front page with 1041 votes.

[http://tvease.net/wiki/index.php?title=Tweak_beryl_for_speed](http://tvease.net/wiki/index.php?title=Tweak_beryl_for_speed)

---

### Post by lawrens on 2007-03-25
There's a tutorial on the beryl's wiki regarding xgl, it does take a few more steps over the nvidia native, but the guide show you how to create a session just to run xgl step by step, so you can log back into your regular non-xgl session if you don't like it:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

Hope that helps =)
About aiglx, I don't know either, I was reading somewhere that nvidia's driver already contains its own method of aiglx so enabling it in xorg.conf doesn't do a thing, so I never got around into testing out aiglx, however xgl runs better than nvidia native on my machine interms of effects, but sluggish using desktop-wall, sadly >_<

---

### Post by rusty4r on 2007-03-25
According to what I read you need nvidia + aiglx or nvidia +glx

---

### Post by craizd on 2007-03-25
Thanks for all the help guys:

lonce: the quick fix worked really well!

lawrens and rusty4r: I think I'm gonna swith to glx once I have the time. I'll keep you posted as to the results.

---

