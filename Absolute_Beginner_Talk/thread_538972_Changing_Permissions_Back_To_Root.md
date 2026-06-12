---
title: "Changing Permissions Back To Root"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by larry Gaminde on 2007-08-30
I changed the /etc files to my username to add a file, now How do I change all the /etc files back to root.

---

### Post by Majorix on 2007-08-30
By doing the reverse of course. How did you change them to your name in the first place and more importantly why did you choose that way? Its insecure and can collapse your system too.

---

### Post by larry Gaminde on 2007-08-30
I have done the reverse a number of times and permission is denied, I cannot use the sudo command just   chown -R root:root /etc.

The reason I did it this way is because I do not know another way.

If I did I guess I would not be asking this question so there is another way to put a file into the /etc directory without changing permissions using gui.

---

### Post by jspangler on 2007-08-30
You can open nautilus as root, giving you access to all the root files, including in the /etc folder, by running:

```
gksu nautilus
```

---

### Post by larry Gaminde on 2007-08-30
this allows me to make a new file and install it into the /etc directory or just view files.
 I ran this command and  it said that /etc was 666 and needed to be 444 or something like that. I  then ran it again and nothing happened. I would really like to restore the /etc directory back to root and nothing works nor do any of my books show how to do this.
I am no longer able to use the sudo command guess because I no longer have root for this directory

---

### Post by jspangler on 2007-08-30
This will allow you to create new files, delete files, change files, or anything else you want (assuming those files are actually owned by root!).

As for the second part of your question, what command did you run that told you that the files needed to be set to 444? Knowing that would be helpful.

---

### Post by larry Gaminde on 2007-08-30
Ok this is what I did to get into this mess
SUDO CHOWN -R LAURA:LAURA /ETC
I then made a file using the edit screen like gkedit and saved the file to the /etc directory
now I can't change the permissions of /etc back to root

HELP PLEASE
I hope I did't really mess things up

---

### Post by jspangler on 2007-08-30
OK, we might be able to get you out of this. Did you try running:

```
sudo chown -R root:root /etc
```

---

### Post by larry Gaminde on 2007-08-30
Thats the problem these files are no longer owned by root I want to make them owned by root again.
I just ran gksu nautilus and it said /etc is this 600 something and should be 400 something

---

### Post by larry Gaminde on 2007-08-30
yes sudo command will not run now

---

### Post by jspangler on 2007-08-30
OK, that last command I gave you should let you make the /etc folder and all of it's files owned by root again. Go into the terminal and type in:

```
sudo chown -R root:root /etc
```

and see if that works. Tell us what the terminal says when you do that.

---

### Post by larry Gaminde on 2007-08-30
This is what happens when I run sudo


~$ sudo chown -R root:root /etc
sudo: /etc/sudoers is mode 0666, should be 0440

---

### Post by jspangler on 2007-08-30
I have another question. Have you ever made any backups of your system? On my backup program, /etc and all of it's files are included by default. If you have a backup that might help you.

---

### Post by splintercellguy on 2007-08-30
No ****, the wonderful /etc chown earlier is screwing sudo. Run that command from Recovery Mode without the sudo command.

---

### Post by larry Gaminde on 2007-08-30
> **jspangler said:**
> OK, we might be able to get you out of this. Did you try running:

```
sudo chown -R root:root /etc
```




This is what happens


~$ sudo chown -R root:root /etc
sudo: /etc/sudoers is mode 0666, should be 0440

---

### Post by larry Gaminde on 2007-08-30
> **jspangler said:**
> I have another question. Have you ever made any backups of your system? On my backup program, /etc and all of it's files are included by default. If you have a backup that might help you.

now I really feel stupid 
NO backup

---

### Post by jspangler on 2007-08-30
OK, did you ever make a backup of your system? On my backup program, /etc is included automatically, so I always have a backup of that. If so, that could help you out.

EDIT:
Sorry double post.

---

### Post by larry Gaminde on 2007-08-30
> **splintercellguy said:**
> No ****, the wonderful /etc chown earlier is screwing sudo. Run that command from Recovery Mode without the sudo command.


Ok what is recovery mode

---

### Post by splintercellguy on 2007-08-30
Again, do the command in Recovery Mode without the sudo prefix? Single-user == root.

---

### Post by jspangler on 2007-08-30
When you boot your computer, GRUB should come up (if it doesn't, hit escape after the initial system screen). One of the options will show the newest kernel version (probably 2.6.20-16-generic), and there will be a version called recovery mode. Select this, and eventually you will come to a terminal prompt. Then type in the command you need:

```
chown -R root:root /etc
```

(Good call splintercell)

---

### Post by larry Gaminde on 2007-08-30
Im not really sure what recovery mode is 
is this when I reboot and get to it that way by hitting the esc key

---

### Post by larry Gaminde on 2007-08-30
Ok going off line and will try this out be back

---

### Post by jspangler on 2007-08-30
> **larry Gaminde said:**
> Im not really sure what recovery mode is 
is this when I reboot and get to it that way by hitting the esc key

Yes. Just hit esc and choose the recovery option.

---

### Post by larry Gaminde on 2007-08-30
Ok 
thank you all the recovery worked !!

I will never mess with it again (NOT)

I have to admit I cannot keep my hands 
off it thanks for the help I was getting that feeling in my gut
the Oh crap feeling

---

### Post by jspangler on 2007-08-30
Cool! Remember, you can use gksu nautilus to add or remove files in /etc (or other root-owned folders), but you probably shouldn't mess with it too much. It's even better to use the command line in the terminal to add or remove files owned by root.

When I want to copy a file from my user directory to /etc, I just say:

```
sudo cp ~/file /etc/
```

If I want to edit a file in /etc (such as /etc/fstab), I use:

```
gksudo gedit /etc/fstab
```

Good luck.

---

### Post by larry Gaminde on 2007-08-30
Ok I wrote all this down on my command pad (everything I learned so far) so what I needed to do was make my file save it to my directory then copy it (cp) to the /etc directory and done.

---

### Post by jspangler on 2007-08-30
> **larry Gaminde said:**
> Ok I wrote all this down on my command pad (everything I learned so far) so what I needed to do was make my file save it to my directory then copy it (cp) to the /etc directory and done.

Yeah, that sounds like a good method. You'll be cruising the command line like an old-timer in no time.

---

### Post by larry Gaminde on 2007-08-30
> **jspangler said:**
> Yeah, that sounds like a good method. You'll be cruising the command line like an old-timer in no time.

I would hope so 
I am an OLD-TIMER

---

### Post by CD27 on 2008-03-15
Okay guys, did a little searching, found this thread (or a friend found it for me). So i was an idiot and gave /etc root permissions, well, all permissions, and now nothing works in command line. I did the command you show up there, but it's not working. It goes through like it did work, but I keep getting teh same thing as that guy did. any help?

---

### Post by CD27 on 2008-03-15
Anyone?

---

### Post by CD27 on 2008-03-15
WTC, someone post back already!

---

