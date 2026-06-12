---
title: "Terminal command not working"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by mthalis on 2007-08-24
This happened I edit bash.bashrc using export PATH=$path:/home/dinesh/jdk1.6.0_02/bin
I placed this command last line of the .bashrc file. Now I open the temianl like
this Almost all comand now not working. this what happen I give command to the terminal 

dinesh@dinesh-desktop:~$ chmod 755 soft
The program 'chmod' is currently not installed.  You can install it by typing:
sudo apt-get install coreutils
bash: chmod: command not found

next I try sudo apt-get install coreutils command it give bash: sudo: command not found answer what can i do for it plase quick reply this

This is how terminal behave when I opened it. 
  
bash: lesspipe: command not found
bash: The: command not found
bash: sudo: command not found
bash: dircolors: command not found
bash: The: command not found
bash: sudo: command not found
bash: uname: command not found
bash: uname: command not found
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: [: too many arguments
bash: sed: command not found
bash: complete: is: no completion specification
bash: complete: currently: no completion specification
bash: complete: not: no completion specification
bash: complete: installed.: no completion specification
bash: complete: You: no completion specification
bash: complete: can: no completion specification
bash: complete: install: no completion specification
bash: complete: it: no completion specification
bash: complete: by: no completion specification
bash: complete: typing:: no completion specification
bash: complete: apt-get: no completion specification
bash: complete: install: no completion specification
bash: complete: sed: no completion specification
dinesh@dinesh-desktop:~$

---

### Post by swoll1980 on 2007-08-24
chmod should be in your default install somethings broke try sudo apt-get install ubuntu-desktop sounds like your missing key parts of the os see if this works for you. Are you using ubuntu this sounds like a freespire-ish problem

---

### Post by mthalis on 2007-08-24
its not only da chmod command..
all other commands are also not working.. :(

---

### Post by swoll1980 on 2007-08-24
thats what im saying ubuntu-desktop reinstalls a crap load of stuff it might help fix a bad package or broken link

---

### Post by heimo on 2007-08-24
> **mthalis said:**
> This happened I edit bash.bashrc using export PATH=$path:/home/dinesh/jdk1.6.0_02/bin


There's your problem. Your $PATH no longer has directories like /bin or /usr/bin. Change $path to $PATH. You need to use explicit path to run commands until then (prefix commands with correct path "/usr/bin/vi" or so).

---

### Post by steve.horsley on 2007-08-24
Well spotted heimo.

You may be able to get at the file to correct it with
**/usr/bin/sudo /usr/bin/nano /etc/bash.bashrc**
otherwise you may need to boot a rescue CD, mount the partition and do the edit from there.

---

