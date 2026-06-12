---
title: "what to do to install a tar.gz?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by rami_daivs on 2007-08-09
**ADMIN CAN LOCK DELETE THIS THREAD, AS NO ONE KNOWS/WANTS TO GIVE ME STRAIGHT ANSWER.**Is it that damn hard to tell me what to click/type to get this thing up going?  

***_ORIGINAL MESSEGE DELETED AS IT NO LONGER ******* MATTERS, BECUASE NO ONE HERE GIVES A ****, IT SEEMS._***

THATS ALL I WANTED! I dont need warnings telling me to just stick to the repositories!  It didn't come from there! you asked for ls of the tar.gz, and you got it. **I** do what you tell me, as you are **SUPPOSED** to be helping me, not giving me **BS, BABY GUIDE LINES!**.............Help me, or have the thread deleted.

---

### Post by overdrank on 2007-08-09
> **rami_daivs said:**
> I need to install a program, from a tar.gz file. after unpacking the tar to a temp folder, i see a file called install.pl, and a folder called installer with a file called services.sh... plus a bunch of other folders with a bunch of files in them, but nothing in those to do with installing, that i can.
what do i do to install, as i have always just apt-get'd everything besides this befor now.


any way, someone tell me what i need to do here, please?

Hi and maybe this link will help
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by Ek0nomik on 2007-08-09
Is there a README file or INSTALL file?  These will usually have instructions for you.

Here is a very generic way of installing from source:

First, install build-essential if you haven't already:

```
sudo apt-get install build-essential
```

Then 'cd' into the directory where you extracted the files.

Now these commands are the most common for installing software:

```
./configure
make
sudo make install
```

---

### Post by MenZa on 2007-08-09
Before running any of the above steps, could you do "ls" and paste the output here?

---

### Post by rami_daivs on 2007-08-09
none of the files have any extensions, besides a file named install.pl

double click this, run in terminal, or am i looking a source code that needs to be compiled.

will trying to do the make install command hurt anything, assuming its already compiled?
how can i tell if i have source code, or precomiled files?

<i r such the n00b>:confused:

---

### Post by MenZa on 2007-08-09
Right, first, try and paste all the output of ls in here. I don't care whether they have extensions or not, they could be helping. Also, what application is it you're trying to install?

---

### Post by rami_daivs on 2007-08-09
_bin  doc  etc_  FILES  _installer  lib  man_  **vmware-install.pl**    <----     <---   run/double click this file?



I have underlined folders. FILES, and vmware-install.pl are files, not folders, and they both have lock icon on thier file icons.

-----------do you want me to list each folder content also?

program is vmware workstatin, given to me by freind. ( he is out of state, and i can not contact him right now.)

---

### Post by aysiu on 2007-08-09
You can install VMWare with Synaptic Package Manager.

Read more here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by MenZa on 2007-08-09
Yes, do what aysiu says. You don't want to install third-party applications which are found in the repositories, unless you have a really good reason to do so.

---

### Post by rami_daivs on 2007-08-09
the version on there is player. the one i have is workstation. already down loaded and tried player. not what i needed. THIS is what i need. (if i can install it.)

---

### Post by rami_daivs on 2007-08-09
> **MenZa said:**
> Yes, do what aysiu says. You don't want to install third-party applications which are found in the repositories, unless you have a really good reason to do so.
was not from the repositories. was from a cd given by a friend.

---

### Post by MenZa on 2007-08-09
Ah yes; bad phrasing there. What I meant was that you shouldn't install any software other than from the repositories, if the repositories have packages for the application.

---

### Post by aysiu on 2007-08-09
Since the one in the repositories doesn't do what you want, this may do the trick. Assuming the *vmware-install.pl* file is on your desktop, you can paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd Desktop
chmod +x vmware-install.pl
sudo ./vmware-install.pl
```

---

