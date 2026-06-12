---
title: "how to create a shortcut (link) to an application with specific user?"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-05-27
Hi
Thank you for reading my post
is there any way to create a shortcut (link) to an application with ROOT user?
I have an application and I create a link for it in my desktop but it does not work correctly.
if i run the application from command line console and use sudo then it works.

I think i should create the link with root user or somehow give it some root permission.

thnaks

---

### Post by Ocxic on 2007-05-27
yes simply add "gksu" without the quotes, infront of you command in the properties dialog for you shortcut.

so right click on you shortcut, and find the "command" line in there somewhere and add gksu to the front so it would look like this "gksu my-root-prog" and you'll be all set.

---

