---
title: "where to find mysql-admin and phpadmin ?"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2006-03-10
Hello. I just installed apache, mysql and php on my Ububtu Linux
machine. I also installed mysql-admin and phpadmin but cant find them.

I try to go to my machine's ip-address 10.0.0.12/phpadmin
or 10.0.0.12/mysqladmin but cant find them.

I guess there are som configurations I have to do first, but I dont
know what. Any suggestions ?

---

### Post by dermotti on 2006-03-10
hmm, did you install phpmyadmin?

---

### Post by chrisdee on 2006-03-10
I think so. How do I check this out ?

---

### Post by dermotti on 2006-03-10
Did you download with synaptic? If so just do a search and see exactly what you installed....

You could also do a search from command line.


sudo updatedb (takes a few mins)

locate mysqladmin
locate phpadmin
locate phpmyadmin

see if that finds anything....

---

### Post by chrisdee on 2006-03-10
I found mysqladmin under /usr/bin/mysqladmin.
I could not find phpmyadmin. Do I need phpmyadmin to
create, edit and maintain mysql databases and tables via webbrowser
when I have mysqladmin installed ?

In so case how do I add/install phpmyadmin ?

---

### Post by dermotti on 2006-03-10
MySQL admin , when i installed it, showed up under my start menu.

Applications --> system tools --> MySQL administrator

or type mysql-admin



PHPMYADMIN installed on

[http://127.0.0.1/phpmyadmin](http://127.0.0.1/phpmyadmin)

PHPMYADMIN is the web browser one. You can download if off synaptic. I personally prefer it.

---

### Post by chrisdee on 2006-03-10
Ok, I see.
How do I install phpmyadmin ?
Do I do this with synaptic ?

---

### Post by dermotti on 2006-03-10
Yes, just type  phpmyadmin in the synaptic program and it will go to it.

or from console, type **sudo apt-get install phpmyadmin**

---

### Post by chrisdee on 2006-03-10
Thank you very much for your help:)

---

### Post by dermotti on 2006-03-10
No problem, Welcome to the forums :-)

---

