---
title: "edit text"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by dc.manage.service on 2007-09-09
hi there

How do edit text in command line?

---

### Post by aysiu on 2007-09-09
```
nano /path/to/fileyouwanttoedit
``` For example, if you have a file called *test.txt* on your desktop, you'd edit it with this command: ```
nano ~/Desktop/test.txt
``` Any reason in particular you want to edit it from the command-line instead of using a graphical text editor like Gedit, Kate, or Mousepad?

---

### Post by dondad on 2007-09-09
> **dc.manage.service said:**
> hi there

How do edit text in command line?

If you are talking about editing the text in the command line itself, the only way that I have found is to use the arrow keys to position the cursor and type the corrections. I haven't been able to position it with the mouse. Maybe someone knows how to do this.

---

### Post by Pitbull11188 on 2007-09-09
I believe your talking about text editing, which I would second nano.

nano is opened with either

$nano

or

$nano filename (if file does not exist it will be creater)

I also suggest that if you do any serious text editing you give vim a go which is invoked the same way as nano. Vim is a powerhouse, but requires at least one hour to learn to use well, and significantly more to become a master. If you would like to learn vim I suggest vimtutor, if you go through it  once a day for a week you'll be golden.

If you're looking for a more comprehensive and customizable editor you can install emacs and give that a go. emacs can do almost anything, even emulate vim in viper-mode, but it is more resource intensive(not a big deal now a days) and can be a gilded cage for the user who becomes too attached to his unique profile(though it can be put on a storage device and carried with you.

---

