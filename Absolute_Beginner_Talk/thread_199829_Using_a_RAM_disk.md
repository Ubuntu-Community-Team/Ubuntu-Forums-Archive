---
title: "Using a RAM disk?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by linux_student_user on 2006-06-19
Is it possible to use a proportion of RAM as a virtual drive, I know applications are available for Windows that allow this. If there is such a program could someone direct me in the right direction please. Thanks for your help. 

Mike

---

### Post by tribaal on 2006-06-19
Yeah sure. You're looking to mount a tempfs filesystem.
There's enough info to get you started [here]("http://www.raditha.com/blog/archives/000527.html"), and you'll probably find loads more by using google.

I personally use a tempfs mount on one of our production server (to ensure that some read only files are always in RAM), and it's working really well. Be sure to be picky on security though.

- trib'

---

