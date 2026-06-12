---
title: "apt-get acting wierd"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by Kyzon on 2006-06-07
Well, I tried an apt-get install nvu in the terminal and i was under my /usr/bin folder and it gave me a "permision denied" response, so i typed in cd to go back and tried it again and got the same output.

---

### Post by kaamos on 2006-06-07
apt-get does not install to the directory you are in and so it always requires root permissions. Use "sudo apt-get install nvu".

---

### Post by Kyzon on 2006-06-07
[QUOTE=kaamos]apt-get does not install to the directory you are in and so it always requires root permissions. Use "sudo apt-get install nvu".[/QUOTE]

That was what i typed to get the error. I just forgot to put sudo in my first post.

**edit** - I got it working. Thanks for the help.

---

