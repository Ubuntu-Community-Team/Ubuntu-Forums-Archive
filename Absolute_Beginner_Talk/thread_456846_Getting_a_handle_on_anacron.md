---
title: "Getting a handle on anacron"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by arragon on 2007-05-28
I'm trying to get a handle on all the stuff running on my box.  Unbuntu 7.04.  I am getting email from anacron:

> /etc/cron.daily/logrotate:
> kill(16166, 12)
> signal 12 sent to process 16166

I'm assuming this is an error, and hence would like to sort.  Tried Google but the post and answer were in German...

Any pointers welcome.

Cheers

David

---

### Post by Viskovitz on 2007-05-28
I also googled for it and found that thread in the German Debian lists. They say that there is nothing to worry about, it's just a trick for xdm to work properly. I think the whole story comes from this bug:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=285871](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=285871)

---

### Post by arragon on 2007-05-28
Thanks.  I'd like not to get the emails, but aas long as there is nothing odd going on fine.  Thanks for the translation.

David

---

