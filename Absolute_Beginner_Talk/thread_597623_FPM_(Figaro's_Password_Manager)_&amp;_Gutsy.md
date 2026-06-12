---
title: "FPM (Figaro's Password Manager) &amp; Gutsy"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by dravidan on 2007-10-30
I was using FPM to store all my passwords but since the gusty upgrade, fpm won't run.  Please help, I need the passwords immediately.  Here is the error message when I try it run it from terminal.

Gdk-ERROR **: BadDrawable (invalid Pixmap or Window parameter)
  serial 53 error_code 9 request_code 53 minor_code 0
Gdk-ERROR **: BadDrawable (invalid Pixmap or Window parameter)
  serial 54 error_code 9 request_code 55 minor_code 0

---

### Post by m9ke on 2007-10-30
A quick fix might be to boot your system from the CD for your previous distro (maybe Feisty?) and see if you can access your passwords.  

Don't know much about the password app you are using, but this is the first thing I'd try if I were you.

Good luck,
m9ke

---

### Post by dravidan on 2007-10-31
Thanks for the reply.  It worked, Here is what I did:
1. Boot from Fiesty CD
2. Installed fpm using synaptic (need internet connection), I could not run the old fpm due to folder  permission
3. Copied the file from old ~/.fpm to the new install
4. Ran fpm and exported my passwords as text to jump drive.

I think this was bug with gutsy, but don't know if it was worth reporting it.

---

### Post by m9ke on 2007-11-01
Cool.  Glad it worked.  If you're happy with the solution, you may want to mark this thread "solved".

Cheers,

m9ke

---

### Post by millettjon on 2008-02-08
I have the same problem.  It appears to be some sort of xorg related bug. I am working around it by running fpm with the XLIB_SKIP_ARGB_VISUALS environment variable set to 1.

Example:
XLIB_SKIP_ARGB_VISUALS=1 /usr/bin/fpm

---

