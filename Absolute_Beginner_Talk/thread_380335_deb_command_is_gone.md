---
title: "deb command is gone"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by Jordan-D on 2007-03-09
i installed ubuntu 6.10 i used the deb command and it worked, but now it's gone. when i type this deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn in the terminal it gets this message bash: deb: command not found

how to get the deb command back

i was installing some apps via Easyubuntu. maybe this is the reason...

pls help
10x

---

### Post by nereid on 2007-03-09
Why don't you just edit the /etc/apt/sources.lst file? Just add your line at the end of the file.

---

### Post by Jordan-D on 2007-03-09
yes it works. but it was such a nice command :)
thank you

---

### Post by bratliff on 2007-03-28
Same problem, what is the solution?

ratliff



> **Jordan-D said:**
> i installed ubuntu 6.10 i used the deb command and it worked, but now it's gone. when i type this deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn in the terminal it gets this message bash: deb: command not found

how to get the deb command back

i was installing some apps via Easyubuntu. maybe this is the reason...

pls help
10x

---

### Post by halitech on 2007-03-28
I don't think you can download the deb files using deb, I thought you had to use wget http:// to get the file and then used either gdebi to install it or deb-i filename.deb to install

---

