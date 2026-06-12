---
title: "[SOLVED] Sending large emails from perl script"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by yanewby on 2008-02-27
I have written a small perl script that emails photographs to my online storage site for backup but Ihave come across a small problem.  It uses MIME::Lite to send the images and, I think, sendmail (or at least the machines default emailing system as I do not have to supply SMTP values).

When I try to email a "large" image (greater than 6Mb although I'm not sure of the exact value) the script chokes and spits out an error that seems to suggest there is a maximum email size I am allowed to send.  My question is, how do I alter this maximum email size so I can send larger emails?

The error message I am getting is:

postdrop: warning: uid=1000: File too large
sendmail: fatal: XXXX(1000): message file too big

where XXXX is my username.

---

### Post by yanewby on 2008-02-27
Solved:

sudo gedit /etc/postfix/main.cf 
message_size_limit = 20480000
sudo /etc/init.d/postfix restart

---

