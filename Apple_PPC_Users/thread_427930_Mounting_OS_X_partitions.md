---
title: "Mounting OS X partitions?"
date: 2007-04-29
forum: Apple PPC Users
---

### Post by travnewmatic on 2007-04-29
I just got Ubuntu to work with my internal AirPort.

Now I'd like Ubuntu to see my OS X partitions.

Any suggestions?

---

### Post by briansvgs on 2007-04-29
Run sudo modprobe hfs. Then run sudo mount -t hfsplus /dev/nameofyourdevice /media/nameoffolder (plugging in device name and folder name). Look here for more help:[http://jclark.org/weblog/2005/05/24/ubuntumount/](http://jclark.org/weblog/2005/05/24/ubuntumount/).

---

### Post by travnewmatic on 2007-04-29
I've followed that guide that you linked to.  It was giving me some crap about permissions.

Actually... let me follow that more closely...

---

### Post by stmiller on 2007-04-30
Are you using Feisty? In Feisty you just open up Nautilus, right click on the os x partition in the left pane, and select 'mount.'

---

### Post by travnewmatic on 2007-04-30
I'm actually upgrading to Feisty as I'm writing this post.  You say it is mountable natively?  That's pretty cool...  what about the other way?  From OS X to Ubuntu?

---

### Post by travnewmatic on 2007-04-30
yeah, i can see my OS X partition now...  just not the internet.  wirelessly that is...

now i got my wireless to work.

I'm curious to see what happens when i reboot if i can see my linux partitions from OS X....

---

### Post by Auria on 2007-04-30
> **travnewmatic said:**
> 
I'm curious to see what happens when i reboot if i can see my linux partitions from OS X....

you can if you install a thrid-party app extFS [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) .but id recommend using it with lots of care since it caused me kernel panics and even once corrupted my linux partition (it was successfully repaired when i booted in linux but still...)

---

### Post by travnewmatic on 2007-04-30
Thanks for the advice.  I might give that a try.

---

