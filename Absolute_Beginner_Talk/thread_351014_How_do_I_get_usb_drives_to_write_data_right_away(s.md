---
title: "How do I get usb drives to write data right away(synchroniously)?"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Sammi on 2007-02-01
I hate the fact that I have to right click and eject my usb thumb drive to be sure all the data is fully written to the drive, before I physically remove it from the usb port. I've read something about it being because data is written asynchroniously.

Isn't there a way I can configure Ubuntu to write all the data synchroniously and right away, so that I can remove usb storage devices without worrying about data loss?

---

### Post by Jussi Kukkonen on 2007-02-01
I believe you can never be 100% sure that everything is written before umounting (how could you), but *mount* does have the options *sync/async *-- it should work the way you want.

---

### Post by bodhi.zazen on 2007-02-01
If you mount your usb drive sync, as you would like, you can significantly shorten it's expected lifespan.

Here is a link re sync : [http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)

Also see this thread: [http://ubuntuforums.org/showthread.php?t=245962](http://ubuntuforums.org/showthread.php?t=245962)

In the end, IMO, unmounting the device seems best ...

---

### Post by Sammi on 2007-02-01
Thanks for the very informative links. Searching turned up nothing for me, so thanks again :D

But from those links I don't think it's not worth the risk doing :(

---

