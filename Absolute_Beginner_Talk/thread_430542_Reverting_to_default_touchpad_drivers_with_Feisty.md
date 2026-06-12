---
title: "Reverting to default touchpad drivers with Feisty"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by huzzak on 2007-05-02
I tried to follow [this guide]("http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide") to add more functionality to my touchpad, and instead lost that which I'd had.  I suspect that the problem might be with having run the following command:

$sudo apt-get install xserver-xorg-input-synaptics

How do I undo what I did with this command, that is to say, how do I revert to the good old drivers that worked?  Thanks.

---

### Post by Dangling on 2007-05-02
I would try re-installing the drivers again:

$sudo apt-get install xfree86-driver-synaptics

---

### Post by huzzak on 2007-05-03
Thanks for the suggestion ... I tried that and it did not work.  Somehow, though, in my thrashing about I managed to fix it.  I installed qsynaptic and modified the xorg.conf file per to a how to on the ubuntu wiki.  Hooray?

---

