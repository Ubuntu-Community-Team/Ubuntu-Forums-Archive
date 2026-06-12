---
title: "connecting to DSL"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by chelseachelsea on 2008-02-29
when I run:
sudo pppoeconf

I get the message:
Sorry, no working ethernet card could be found.

It suggests I might want to run modconf
then nothing happens

If I use a new terminal window to run modconf,the message says it could not be found

what do I do next?

I also have a Linksys router, but after setting it up on the windows computer and comnnecting to Ubuntu, nothing

---

### Post by kinghowdy on 2008-02-29
It sounds to me like Ubuntu does not like your ethernet card. Go to System -> Administration -> Network and see if it shows your ethernet port. Alternatively in the terminal you may type ifconfig and you should see on the far left eth0 as well as lo and a bunch of information. If you only see lo and its information that means your ethernet is not being detected in Ubuntu. If not find out the make & model and search in the forums for drivers. Once you get your ethernet working you should just be able to connect your computer to the router.

---

