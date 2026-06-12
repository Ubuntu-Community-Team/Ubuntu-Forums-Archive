---
title: "problems with .sh files"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by schneider707 on 2008-01-10
ok so my dad passworded some .rar files and can't remember the passwords. I figured I could help him out so I grabbed this program called rarbrute. However, it comes as an .sh file. 

I cd'ed to the files and ran > chmod u+x rarbrute.sh

Then when  I ran > ./rarbrute.sh it gave me  this output

> mikey@Optimus:~/Desktop/rarbrute_sh_v_2_1_final$ ./rarbrute.sh
rarbrute - v.2.1
update: 27-12-2005
by aciddata 

 usage: 
  ./rarbrute.sh <*.rar> -n number
  ./rarbrute.sh <*.rar> -d <wordlist> 


So what's the next step??

btw I got this off of sourceforge if anyone is wondering...

Thanks ahead of time

---

### Post by Blutack on 2008-01-10
It wants you to pass it the rar files you want it to crack, along with a dictionary list.
Is there not a tutorial/readme on the site?

---

### Post by Hospadar on 2008-01-10
yeah, it's not an installer, it's the actual program.  I'd guess that number 'n' is either the number of tries or maximum password length, see if they have a readme.

---

### Post by timbounceback on 2008-01-10
try this:

./rarbrute.sh yourarchive.rar -d  /usr/share/dict/words

:-)

---

### Post by Blutack on 2008-01-10
> 
try this:

./rarbrute.sh yourarchive.rar -d /usr/share/dict/words



Just as a warning, that won't work if your dad has done anything smart like mix in numbers/use proper nouns.

---

### Post by timbounceback on 2008-01-10
that's correct, you may have to brute-force it if this doesn't work. this is assuming that your dad chose a password that can be found in the dictionary.

---

### Post by NovaAesa on 2008-01-10
If he chose a good password (like all good computer users do :) it won't work :( ) You should ask him though, he should at least remember if it's a dictionary word or not.

---

### Post by schneider707 on 2008-01-11
no he said he definitely picked a crazy one....he said it would look something like this as his password:

412#rr

Would that be too much for this program?

---

