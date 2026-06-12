---
title: "error message"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by jocaasbe on 2007-09-18
I was downloading and installing updates. I lost power in the middle of the operation.
When I resumed I got this error message. I'm new to Ubuntu and Linux. What do I do to make this happen?


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report

Thanks,
jocaasbe

---

### Post by kelnage on 2007-09-18
Hi there jocaasbe,

Okay, from the sounds of it, the updater has corrupted it's cache. However, it seems it should be pretty easy to fix.

First off, you'll need to start a "Terminal". You can do this by going to Applications -> Accessories and clicking on Terminal.

After a second or so, a white window with black text, saying something like "YOUR USERNAME@YOUR COMPUTER NAME:~$" should appear. What you then need to do is type the following into that window:

```
sudo dpkg --configure -a
```After you've typed that, hit return and a a line will appear asking for your password. Enter your current password (don't worry - there won't be any asterisks appearing when you enter the password - it's added security). If you get it wrong, it'll ask for you to try again, otherwise it will pause for a second and then "YOUR USERNAME@YOUR COMPUTER NAME:~$" will appear on the line beneath again. You can then close the window and next time it tries to update, everything should run smoothly.

---

