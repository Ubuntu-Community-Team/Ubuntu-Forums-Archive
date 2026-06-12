---
title: "[SOLVED] bash cannot find any commands in root"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by nuttycat on 2006-02-12
Hi everyone,
another strange occurence that i stumbled upon.

after logging into root using "su", bash reports virtually every command as command not found.

ls, dir, cp  are just some of the commands that have stopped working.
everyone of these returns an error 

bash: ls command not found

anyone knows what I may have done to cause this to happen?

Thanks,
Nuttycat

---

### Post by taurus on 2006-02-12
Maybe your PATH is all messed up!!!  Try this command at the prompt and see what does it say regarding PATH!

set

Otherwise, you need to edit ~/.bashrc (or create one if you don't have it) and include PATH in there...

---

### Post by nuttycat on 2006-02-12
Thanks Taurus,
it was the PATH that had got messed up.

i went in and edited my ~/.bashrc and set the PATH variable as
PATH="$PATH:/some_exisiting_path"

bash now works as before...
Thanks,
Nuttycat

---

### Post by taurus on 2006-02-12
No problem.  Glad to help.

---

