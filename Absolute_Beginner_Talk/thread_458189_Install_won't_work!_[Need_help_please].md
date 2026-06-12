---
title: "Install won't work! [Need help please]"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by -Soul_Reaper- on 2007-05-29
/bin/sh: can't access tty; job control turned off
(cinitramfs) [some numbers] ata 2.01 failed to set xfermode

That is the error message i always when i go to install. I tried using 'acpi=off', that doesn't do anything.
I am sure that the cd is fine...i have no clue what is the matter. :(

---

### Post by oilchangeguy on 2007-05-29
found this thread:
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)
be warned, it's a long thread, i hope you find your answer.

---

### Post by -Soul_Reaper- on 2007-05-29
> **oilchangeguy said:**
> found this thread:
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)
be warned, it's a long thread, i hope you find your answer.

Thanks this helps...kinda. Still can't find a solution! 

Would it help if i format my HD before installing Ubuntu?

---

### Post by -Soul_Reaper- on 2007-05-29
IT WORKS!!! Thank you everyone that helped, especially iolchangeguy! It is finally working! :D I am installing right after i finish this post. 
Ps. the first solution worked!

 Originally Posted by Aldebran  View Post
I think I have some solutions :

The first solution is (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'all_generic_ide'

The second solution is more complex but i think it's better (with the live-cd) :
- Select 'Other options' with F6
- Remove 'splash', 'quiet' and '--'
- Add 'break=top'
A shell will appear, so :
- Write 'modprobe piix' (after you will see some text)
- Finally, write 'exit'

The third and the four solutions are not really good so don't use it if the first or the second works :
- You can let a floppy disk in your computer and "maybe" it will work.
- You can use the option "Install with driver CD" with the live-cd, and press Enter without changing the CD (two times), and "maybe" it will work.

---

