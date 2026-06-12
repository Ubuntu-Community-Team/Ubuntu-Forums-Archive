---
title: "[SOLVED] simplifying GRUB"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2008-04-02
This isn't so much a question post as it is a "answer post".  I've seen people ask "how come there are so many options when I boot from the GRUB menu?" and I'm one of them.  I'm sure there's logical reasons for why they're there - and even if not I found a process that you can do to only have what you need or want there.  Here is the link.

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/) <- Article not mine!

I should mention that you should back up anything you do before hand, lest the computer gods come and smack me.  Also, if you don't know what you're doing - don't do it.  Which leads me to a question, actually.  My menu looks something similar to the first screen shot of his menu (but with updated kernels).  What's necessary?

---

### Post by Daveth on 2008-04-02
might  then be a good idea to mark it as "solved", so that the faithful flock to your solution. Not seen that one before.

---

### Post by dannyboy79 on 2008-04-02
> **AnLGP said:**
> This isn't so much a question post as it is a "answer post".  I've seen people ask "how come there are so many options when I boot from the GRUB menu?" and I'm one of them.  I'm sure there's logical reasons for why they're there - and even if not I found a process that you can do to only have what you need or want there.  Here is the link.

[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

I should mention that you should back up anything you do before hand, lest the computer gods come and smack me.  Also, if you don't know what you're doing - don't do it.  Which leads me to a question, actually.  My menu looks something similar to the first screen shot of his menu (but with updated kernels).  What's necessary?

that is not the correct way of doing it however I have to inform you. You should be uninstalling old kernels from synaptic first, then run grub-update which will remove the options from your grub menu. here you go:

[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man8/update-grub.8.gz)

---

### Post by annda on 2008-04-02
> **dannyboy79 said:**
> You should be uninstalling old kernels from synaptic first, then run grub-update which will remove the options from your grub menu.

actually, it is enough to uninstall the old kernels. GRUB will update itself on reboot. so, there is one step less - and all in GUI for those who like it more.

---

### Post by dannyboy79 on 2008-04-02
> **annda said:**
> actually, it is enough to uninstall the old kernels. GRUB will update itself on reboot. so, there is one step less - and all in GUI for those who like it more.

I thought so but didn't want to post that for sure. it's run automatically per this file "/etc/kernel-img.conf" Thanks for pointing that out.

---

### Post by AnLGP on 2008-04-02
Hey thanks!

I'll mark this as solved, except you people seem to have a much better of an idea of what's going on than I do.

For the record, the article isn't mine.

---

