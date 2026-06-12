---
title: "arithmetic formulas don't work in shell scripts?"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by sgargabonzi on 2006-12-24
Hi guys,

I am a novice, but very glad with my first steps with Ubuntu.
I am following a beginner tutorial for script shell and I am using the Ctrl-Alt (F1 to F6) keys to have my prompt, and create files .sh.

First steps with "echo" ... so far so good.

Now I got stuck with calculating simple products like X*Y. I am trying many variations of the sintax but for example:

echo "I will work out X*Y"
echo "Enter X"
read X
echo "Enter Y"
read Y
echo "X*Y = $X*$Y = $[X*Y]"

prints me the actual string "$[X*Y]" and not its value (e.g. if X is 2 and Y is 3 I would expect to have "6" on the screen).

Also the + operator doesn't seem to be recognized. Do anyone know how to correct this? Should I install any additional packages to the ones that come with Ubuntu distribution?

Thank you very much in advance fellows!

---

### Post by meng on 2006-12-24
I think you need to use expr for this purpose:
[http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html](http://pegasus.rutgers.edu/~elflord/unix/bash-tute.html)
Also, feel free to post in Programming Talk - possibly might get more focused attention there.

---

### Post by speedman on 2006-12-24
You can use bc for calculation functions.

man bc for more information.


SM

---

### Post by sgargabonzi on 2006-12-24
Thank you guys.

speedman- I am going to check the bc command but I don't think using this command should be necessary.. In several tutorial I am seing they seem to work this out without bc.

meng- I tried with expr, checking your link and implement the suggestion but still o success. Finally I followed your invitation and posted the same issue on the Programming Talk section.

Thanks you both,

sgargabonzi

---

