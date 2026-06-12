---
title: "$PATH question..."
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Q4U on 2006-03-15
Hi

Just added Firefox from mozilla.org to my Kubuntu (Dapper) system.

I installed in /opt, but noticed the directory was not included in the PATH variable.

So, I did: 

PATH=$PATH:/opt
export PATH

However, upon looking again at $PATH, I saw that it contains "No such file or directory" at the end. Of course, /opt exists in my system (and in spite of this error, Firefox seems to run just fine).

1. What is the cause of this error? Is it normal, maybe?
2. In order to make sure that I am able to start Firefox everytime I log in I have to add this to my .bash_profile, right?

Thanks.

---

### Post by kaamos on 2006-03-15
If I do the above and use "echo $PATH" to check it, /opt is added to the end of the path and everything is ok.

You should add it to .bashrc as well. But the simplest way would be to create a link to for example to /usr/local/bin/.

---

### Post by Q4U on 2006-03-15
Thanks, I went for the link option, worked flawlessly.

How does one delete directories from the PATH?

---

### Post by xenmax on 2006-03-20
The PATH variable will be set in 1 or more of bash init files - /etc/profile , ~/.bash_profile ,  ~/.bash_login , ~/.profile , ~/.bashrc
Just edit the file in which the directory you want removed is set in to fix the PATH var.

---

