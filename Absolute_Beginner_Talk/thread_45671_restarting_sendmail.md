---
title: "restarting sendmail"
date: 2005-07-01
forum: Absolute Beginner Talk
---

### Post by kobiewolke on 2005-07-01
Hi

I am new to linux and I would just like to know how to restart sendmail from the command line. Can anyone help?

---

### Post by emmet on 2005-07-01
Hi

Are you using sendmail or it's simpler cousin - postfix. For compatibility reasons, postfix installs an executable called sendmail, but the service is actually postfix.

So, just do the following:

sudo /etc/init.d/postfix restart

If you _are_ using sendmail, then you should be able to do:

sudo /etc/init.d/sendmail restart

Best regards,

Emmet

---

