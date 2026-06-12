---
title: "How do I reset my @#$%%^ Mouse?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by R_U_Q_R_U on 2007-06-12
Another stupid noob question.

I went to to wiki and followed the instructions for enabling the back and forward mouse buttons. Somehow my mouse is very confused. The scroll wheel now acts as forward and back buttons and the side buttons act like page-up and page-down buttons!

What do I need to do to restore the mouse to the default settings when 7.04 was installed?

How do I uninstall IMWheel? It does not appear in the Add/Remove programs and I am too ignorant to get beyond that.:(

Thanks.

---

### Post by dergringo on 2007-06-12
> **R_U_Q_R_U said:**
> 
How do I uninstall IMWheel? It does not appear in the Add/Remove programs and I am too ignorant to get beyond that.:(

Thanks.

Hi. You can remove repository software in the console like this:
sudo aptitude purge *paketname*

I don't know IMWheel but I suggest you try: sudo aptitude purge imwheel


Regards :)

Philipp

---

### Post by R_U_Q_R_U on 2007-06-12
> **dergringo said:**
> Hi. You can remove repository software in the console like this:
sudo aptitude purge *paketname*

I don't know IMWheel but I suggest you try: sudo aptitude purge imwheel


Regards :)

Philipp

Thanks.This worked great. My mouse wheel is back to default behavior. Buttons are disabled but I think I understand how to get them working now.

---

