---
title: "can't copy-paste header files-how do I change the ownership?"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by christina_svats on 2007-09-14
I need to paste a header file in the directory "include", in order to compile and run a program written in c++. However, I cannot, since I am not recognized as root. How do I change the ownership of these files?
Thanks

---

### Post by mcduck on 2007-09-14
Don't change the ownership, change your own rights ;)

Just run 'gksudo nautilus' to open the file manager as root, use that to do what you want and then remember to close t again as soon as you don't need it any more.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by christina_svats on 2007-09-14
I think I did something stupid before I read the reply.
I did sudo chown and I changed the ownership, so, now I can paste the header file I wanted. Could you explain what the locks means? (after I changed the ownership, locks appeared on the files that were already in the c++ folder). 
And, anyway, can I undo now what I did and do the thing you advised me to do?
I should also mention that, even though I did paste the header file, when I try to compile the program, it still says that there is no such file or directory.

---

