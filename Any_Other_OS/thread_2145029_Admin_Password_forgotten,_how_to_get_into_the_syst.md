---
title: "Admin Password forgotten, how to get into the system and reset the password?"
date: 2013-05-14
forum: Any Other OS
---

### Post by hhtmp88 on 2013-05-14
as titled.
Thanks for any kind of help!

---

### Post by westie457 on 2013-05-14
This one works for me.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by hhtmp88 on 2013-05-15
Thanks a lot westie457!
-> will try it out!

---

### Post by hhtmp88 on 2013-05-27
tried, but no luck!
-> in recovery mode, I need to enter the admin password!
-> I am using an variation of Ubuntu, called startOS, [http://en.wikipedia.org/wiki/StartOS](http://en.wikipedia.org/wiki/StartOS)

---

### Post by newb85 on 2013-05-27
You might be out of luck.  I'm not familiar with StartOS, but it sounds like it was designed to prevent you from resetting the Admin password if you forget it.  And it sounds like its user hierarchy is more like Debian's than Ubuntu's.

---

### Post by Irihapeti on 2013-05-28
There is still another way, but it's a bit more complicated. You need a liveCD for this. I've only done with an Ubuntu environment to fix another Ubuntu install, but I think StartOS liveCD should also work.

The how-to is here: [http://www.makeuseof.com/tag/how-to-reset-any-linux-password/](http://www.makeuseof.com/tag/how-to-reset-any-linux-password/) It's about 4 years old, as is very obvious from the screenshots, but still works. Scroll down to the section that begins with "When you can’t use GRUB"

Note: it's a bit more simplified than the process I normally use, but it seems to work for resetting passwords.

Let us know how you get on.

---

### Post by newb85 on 2013-05-28
> **Irihapeti said:**
> There is still another way, but it's a bit more complicated. You need a liveCD for this. I've only done with an Ubuntu environment to fix another Ubuntu install, but I think StartOS liveCD should also work.

The how-to is here: [http://www.makeuseof.com/tag/how-to-reset-any-linux-password/](http://www.makeuseof.com/tag/how-to-reset-any-linux-password/) It's about 4 years old, as is very obvious from the screenshots, but still works. Scroll down to the section that begins with "When you can’t use GRUB"

Note: it's a bit more simplified than the process I normally use, but it seems to work for resetting passwords.

Let us know how you get on.

I would be interested to know if this works in StartOS.  I would expect it to work in Ubuntu, since Ubuntu doesn't have a root password.

---

### Post by tubbygweilo on 2013-05-28
> **newb85 said:**
> You might be out of luck.  I'm not familiar with StartOS, but it sounds like it was designed to prevent you from resetting the Admin password if you forget it.  And it sounds like its user hierarchy is more like Debian's than Ubuntu's.

Something I was not familiar with until peeking at [https://en.wikipedia.org/wiki/StartOS](https://en.wikipedia.org/wiki/StartOS) & [http://distrowatch.com/table.php?distribution=startos](http://distrowatch.com/table.php?distribution=startos), sorry I can not offer any help.

---

### Post by odiseo77 on 2013-05-28
> **newb85 said:**
> I would be interested to know if this works in StartOS.  I would expect it to work in Ubuntu, since Ubuntu doesn't have a root password.

It works on Debian, which does have a root account. I'd suppose it works on any distro once you have successfully chrooted it, since the 'passwd' command can change the password of any specified user (even root).

---

### Post by Irihapeti on 2013-05-28
I think it would be safe to try it, anyway. It will either work or not - it's not likely to screw anything up.

A quick google search shows references to SuSE and Arch. It's not just an Ubuntu/Debian thing.

---

