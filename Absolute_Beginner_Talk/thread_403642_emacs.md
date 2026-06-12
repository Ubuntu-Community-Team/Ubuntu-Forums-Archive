---
title: "emacs"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by bry2o on 2007-04-07
I am currently working on my laptop and have connected to my schools linux computer using:

ssh -X [email]username@server.edu[/email]

This was so that I could run emacs in seperate windows and not have to work in the terminal, but for some reason when i open a file using emacs test.cpp & it takes a long time to load up. Is something wrong with my computer or is it the schools computer? Is there anyway to speed up the load time? or is this normal.

When I just connected without the -X and run emacs, it runs inside the terminal, but it loads instantly...

---

### Post by spin2cool on 2007-04-07
The problem is network latency.  Sending all of the information for the GUI and window wrapper takes much longer than the small, highly optimized emacs console mode.  

My suggestion is to use sshfs to mount your drive at school as though it's a local drive:
[http://ubuntuforums.org/showthread.php?t=275856](http://ubuntuforums.org/showthread.php?t=275856)

Then you can run emacs locally, and it'll just be opening and saving files that takes slightly longer.  (though if they're typical small scripts, you may not even notice).  I have a similar situation, and this solution worked great.

---

### Post by dstew on 2007-04-07
Doing X windows over ssh is probably not very efficient, but I really don't know for sure. I remember trying to do X by telnet in the past and it was pretty slow. You have so much overhead with fonts etc. when using X.

---

