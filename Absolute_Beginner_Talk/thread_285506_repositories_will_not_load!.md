---
title: "repositories will not load!"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by CyclopsU on 2006-10-26
Foolishly, while trying to get automatix to work I managed to screw up all of my repositories. I get this message when trying to update (reload) my repositories. How do I edit (correct)] this error I caused?](*,) 


E: Type 'wget' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type 'wget' is not known on line 1 in source list /etc/apt/sources.list
E: Unable to lock the list directory

---

### Post by DSn0wMan on 2006-10-26
Check this link to help fix your repositories

[http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories)

---

### Post by chippy99 on 2006-10-26
Try commenting out (put a # in front of line) the first line of /etc/apt/sources.list. 

Lock problems usually mean you are not root (type sudo in front of command) or you already have a program running that is locking a file.

If all else fails post a copy of your sources file here.

---

### Post by CyclopsU on 2006-10-26
I'm clueless. I do thank you for your quick reply though. It appears that I may have "saved" something with 'wget' in the text and my Ubuntu just doesn't like it.

---

### Post by chippy99 on 2006-10-27
Ok I will try to go through it step by step.

1. Open a terminal window (applications -> accesories -> terminal
2. Backup your existing sources.lst in case anything goes wrong -
   sudo cp /etc/apt/sources.lst /etc/apt/sources.sav
3. Edit your sources.lst file.  sudo gedit /etc/apt/sources.lst
4. The editor should now open showing the contents of your sources.lst.  I suspect line 1 begins with wget......
Comment out that line by inserting a hash (#) in front of it.
5.  Save the file.

Retry running whatever package manager you were trying to use and see if the error has gone away.

Good Luck

---

