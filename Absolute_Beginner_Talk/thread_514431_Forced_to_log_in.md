---
title: "Forced to log in?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by ryanfx on 2007-07-31
I tried to do a search for this but it doesn't yield any results, so sorry if this is a n00b question that has already been answered.

I booted ubuntu from the live CD and I wanted to try out beryl (I figured if I tried to install it, and I broke something, it wouldn't matter since it was just a live CD)

After I did that and restarted however, whenever I try to boot from the live CD, it now forces me to try and log in as opposed to before when it would automatically log you in.  Is there any way to clear a set of files so I can have a "clean" live CD boot up again?  Linux is not installed anywhere on my system.

---

### Post by lisati on 2007-07-31
It is possible that your system isn't booting from the CD but from your hard drive. During system startup there should be a key you can press to "choose boot order" (the wording might be slightly different on your machine)

---

### Post by ryanfx on 2007-07-31
but if I don't have linux installed anywhere, how could it be booting from my HD?  It will give it a try none the less

---

### Post by Dirk Lately on 2007-07-31
I have a similar problem; I can't figure out how to boot to an "open" system rather than having to login.

Similarly, I think I've messed something up with my wireless: the passphrase for my wireless is stored in my keyring thingie, but whenever I boot I have to input my keyring password, I assume so it can give the wireless passphrase to the wireless driver.

(Does anyone else find that sentence exhausting?)

Please help!

---

### Post by ryanfx on 2007-07-31
ok, I completely unplugged the HD's and it did the same exact thing, so now I chose "memory test" from the ubuntu boot CD in hopes that it will zero out some cached sectors in my ram... I'm hoping that's what's wrong.

---

### Post by ajgreeny on 2007-07-31
I don't think you do it that way using a live CD!  If you really want to try it, install beryl and any dependencies, together with beryl-manager.  Now start beryl-manager using the terminal.
Then, using beryl manager, you can try out beryl by right clicking on the red jewel in the taskbar and choosing beryl from the options there.
On the live CD, every time you restart you lose everything that you installed, as it is only sitting in a ram disk, not on a proper hard disk install, so when you restart, no beryl, etc.

---

### Post by ryanfx on 2007-07-31
I might have figured something out.  I used the check CD utility and it said there was a file corrupted on the CD, I'm assuming it was loading but errored or something enough to make it act weirdly, but not enough to make it crash!

I'm also going to take this time to use the 32 bit version instead of the 64 as I read the incompatibility to programs is not worth the increase in speed.

---

