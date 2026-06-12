---
title: "umask issue"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by e^(i*pi) on 2007-05-07
I'm working on learning about file permissions and how to change them, and I've noticed something I don't understand that is happening with my umask command.  I cant seem to set the default to give anyone execute permission.  I know that a value of 0 should give a particular category of user all permissions, but I'm only getting read and write out of that.  Any ideas?

---

### Post by vanadium on 2007-05-07
I guess that is the way the system works. It is actually a very bad idea to set any file as "executable" by default. A file should be set executable only if it is really designed to be executed. That is where it makes sense not to let the machine decide whether the file is executable, but to let the user decide that.

Making directories executable by default makes a lot more sense: this allows user to "travel"  through them, even if they can't see them at all if read and write are disabed. Indeed, after an umask 0000, dirs *will* be mode 777.

---

### Post by e^(i*pi) on 2007-05-07
I understand that it is not a good idea to make new files executable by default.  I'm playing around with it though just to learn about it.  I don't actually plan to leave it that way.  I'm more interested in why it won't let me do it.  It seems like I should be able to, even if it isn't the greatest idea.  I've also noticed as I've been searching around for answers to this that some times people write their umask codes with three digits and some people with four.  Why is that?

---

