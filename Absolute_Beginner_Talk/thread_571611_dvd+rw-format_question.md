---
title: "dvd+rw-format question"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by bhold on 2007-10-09
I tried to blank a dvd+rw with gnomebaker. Message told me the media does not support this. Next I tried formatting witn gnomebaker, which appears not to work because the file was still there.

I found a thread, someone had been able to do this with dvd+rw-format -blank /dev/dvd. Tried it, got a similar message that this option is not supported by the media. Message also told me I could use the -force option to reformat the dvd. OK, I gave it a try... got a message saying the volume could not be mounted. Now, this particular dvd seems to be toast - whenever I insert it I get the "could not be mounted message"

No problem, they are cheap enough,  but I would like to understand what I did wrong.

Thanks   -- Bob

---

### Post by cameronw on 2007-10-10
Try installing K3B - sudo apt-get install k3b  it's a much better burning application

---

### Post by bhold on 2007-10-10
Thanks for the suggestion, I tried k3b. Just looking for a data dvd burner for backup. k3b has a nice feature - option to move individual dvd files to trash. This would be good for cleaning up dvd contents if you have a file you don't need any more. But I could not get it to work - message said it was unable to run klauncher so did not know how to move to trash. I run gnome on ubuntu 7.04, not kde, so maybe that is a problem for k3b.

For data dvd burning I think k3b or gnomebaker are about equivalent as far as I can tell.

---

### Post by bhold on 2007-10-12
One of my backup tar.gz files is about 3.5gb. k3b handles this fine - message says it is using UDF file system then burns it with no problem. gnomebaker won't burn this file to dvd, I assume because of the size. So k3b wins over gnomebaker for my requirements. Thanks again for the recommendation.    -- Bob

---

