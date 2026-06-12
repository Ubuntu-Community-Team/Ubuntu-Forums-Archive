---
title: "Java download failure"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Buster95 on 2007-04-01
Followed the instructions to download JRE. Everything seemed to go OK with the download and it appeared in Tools/downloads.

How do I install it? There are two options "open" and "remove". There is no install option that I can see.

What stupid thing have I done here? What next?

---

### Post by Sasa_Ivanovic on 2007-04-01
open the shell
then type 
```

/home/your_name/Desktop/the_name_of_file

```

---

### Post by FyreBrand on 2007-04-01
How are you installing Java?  You can use add/remove programs to install Sun's Java but I think it will ask you to accept a license.  In that case you would need to watch the detailed screen as it installs and accept the license when it comes up.

Here is a link to another method of installing Java you might want to give it a go: [**Ubuntu Documentation - Java**]("https://help.ubuntu.com/community/Java")

---

### Post by Buster95 on 2007-04-01
Thanks for the help,
This is the return from the terminal enquiry

dexter@dexter-laptop:~$ /home/dexter/Desktop/j*
bash: /home/dexter/Desktop/jre-1_5_0_11-linux-i586-rpm.bin: Permission denied
dexter@dexter-laptop:~$ 

Regarding your second message, I followed the instruction on the Sun website to download it. I'll have a look at your link and see where it leads me.
Cheers

---

### Post by johnny4north on 2007-04-01
Ubuntu 7.04 the easy way to install java is Panel>applications>add/remove,click all, then search Java.  click the check box next to application you need, then click apply. you are done.. close. the link offered - [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)    explains it well.   thanks Ubuntu

---

### Post by Buster95 on 2007-04-01
Thanks,
I didn't realise I could use the synaptic to do it. I'll try.
Cheers

---

### Post by Perfect Storm on 2007-04-01
If you want sun java 1.6 put backports in your sourcelist.



You can sample your sourcelist here: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

then in the terminal;
```
sudo nano /etc/apt/sources.list
```

replace the old one with the new one.

```
sudo aptitude update
sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

