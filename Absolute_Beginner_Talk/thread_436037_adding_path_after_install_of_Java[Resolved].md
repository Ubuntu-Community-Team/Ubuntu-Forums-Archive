---
title: "adding path after install of Java[Resolved]"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by spearfish on 2007-05-07
Hi,

I just installed Java from the Sun web site, jdk1.6.0_01, and I tried following their instructions to add the java directory to my PATH.  However, it doesn't seem to work.  

I still get:

bash: javac: command not found

when I type:

>javac

can anyone help me out with adding the correct path to my .bash_profile file?

I've got java installed in my home directory:
/home/me/jkd1.6.0_01

thanks,

A

---

### Post by fakie_flip on 2007-05-07
First create a backup of anyfiles you edit.
cp filename filename_backup
add to your .bashrc
PATH=$PATH:/home/me/jkd1.6.0_01/bin
I am not sure if that is the exact path to the bin folder, but you should look for the bin folder. It is probably under a jdk folder, not jre. The changes to your path won't take place until you relogin. Hit control alt backspace to do that.

---

### Post by fakie_flip on 2007-05-07
Does that help?

---

### Post by spearfish on 2007-05-07
Hi!

Thank you, that did the trick.  I was adding the PATH line to .bash_profile instead of .bashrc 

cool :)

-A

---

### Post by fakie_flip on 2007-05-07
Are you installing jdk for a programming class at school? I did my java programming assignments at home in Ubuntu when I was taking some classes. The last one I finished was Data Structures.

---

