---
title: "swfdec?"
date: 2007-04-15
forum: Apple PPC Users
---

### Post by indica on 2007-04-15
hey, ok i've been running ubuntu on my backup comp for years, finally decided to go totally ubuntu when i bought an ibook g4 awhile back.  i've been struggling with it, (and you were all very patient with me and my ridiculous problems so far) i'm both not  particularily efficient at using ubuntu to begin with, and all the trials and tribulations that seem to come with ppc.  so i have a particularily nooob question for you guys.  can someone please, in idiot-speak, tell me how to get swfdec working on my laptop?  i've read everywhere that swfdec is the only way to get macromedia flash sites like youtube to work on a ppc.  i've found the site to dl the tar from but it's not very intuitive from there.  anyone want to take pity on me?

---

### Post by Auria on 2007-04-16
ive not done it so these instructions may or may nor apply. these are just general instructions that work with most open-source stuff

Is it a source tarball? If so you should install development tools (build-essentials i think) and then follow the instructions in INSTALL file, usually ./configure && make && make install

---

### Post by gevans on 2007-04-18
I successfully compiled and installed swfdec on my G3/500-Pismo under Ubuntu 7.04, however it just crashes firefox on loading youtube and things. It seems to me that it is not working yet.

---

### Post by Who on 2007-04-21
> **indica said:**
> hey, ok i've been running ubuntu on my backup comp for years, finally decided to go totally ubuntu when i bought an ibook g4 awhile back.  i've been struggling with it, (and you were all very patient with me and my ridiculous problems so far) i'm both not  particularily efficient at using ubuntu to begin with, and all the trials and tribulations that seem to come with ppc.  so i have a particularily nooob question for you guys.  can someone please, in idiot-speak, tell me how to get swfdec working on my laptop?  i've read everywhere that swfdec is the only way to get macromedia flash sites like youtube to work on a ppc.  i've found the site to dl the tar from but it's not very intuitive from there.  anyone want to take pity on me?

I _just_ compiled and installed it an the browser plugin and it worked well. I needed to get quite a few dev packages to make it make (I.E it configured without them but wouldn't make) so expect some quality time with synaptic, if you can't find all the right packages then post here and I'll try and help out.

It seems to work _ok_ - slightly jerky playback, but I haven't played with ways to optimise it yet. Better than nothing, for sure!
See [http://swfdec.freedesktop.org/wiki/Installation](http://swfdec.freedesktop.org/wiki/Installation)

---

### Post by bradskins on 2007-04-28
Could you please post the binary files?  I have tried many times to compile swfdec but it is just not working for me.

Thanks

-bradskins

---

### Post by ditsch on 2007-04-29
I also tried with swfdec 0.4.3 and, as gevans said, it is crashing on youtube. Flash ads are working mostly, though :evil: 

Gnash does not work for YouTube, either, but it does not crash the browser. This is a clear advantage if you browse to a website with a YouTube video embedded, as you can imagine...

---

### Post by Auria on 2007-04-29
> **ditsch said:**
> I also tried with swfdec 0.4.3 and, as gevans said, it is crashing on youtube. Flash ads are working mostly, though :evil: 

Gnash does not work for YouTube, either, but it does not crash the browser. This is a clear advantage if you browse to a website with a YouTube video embedded, as you can imagine...

i think there will soon be a new gnash version that can play youtube and other simialr websites

---

