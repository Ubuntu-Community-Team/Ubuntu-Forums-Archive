---
title: "NooB, Problem, im not the owner"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by r2000 on 2007-03-29
I want to be able to create directories without having to type a yellow pages, just to move a file or make a directory.

How do i get the GUI file manager to just let me do, what i want to do................

I understand the security behind the system, but why be logged in as root if you dont have priveledges of root? bit Irish it seems....lol..

Basically i am trying to install java, i wanted to move the .bin file to the directory to where i wanted it to install, but it does not let me move files or folders where i want them to be.

Also, i wanted to put some basic html files in the directory that Apache reads from, and it wouldnt let me.  I just wanted to get rid of the default loading page when i go to [http://localhost](http://localhost)

Ive also installed Webmin to make things easier, and effortless.

Im sick of typing s*** loads of crap, in terminal just to accomplish a very very very simple task.


Any help would be most appreciated.

Thank you.

---

### Post by Bachstelze on 2007-03-29
To run the file manager as root, do :

```
gksudo nautilus
```

and prepare for major breakdown...

---

### Post by taurus on 2007-03-29
You just need to calm down when you ask for help.  If you need to move something outside your $HOME directory, put the sudo in front of a command.

Applications -> Accessories -> Terminal
```
sudo cp filename destination
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Bachstelze on 2007-03-29
> **taurus said:**
> You just need to calm down when you ask for help.

Yep. I think the "Read before posting"-thngie should mention that if answers are to be given in a friendly way, questions should, too...

---

### Post by r2000 on 2007-03-29
Sorry if i came across as a " Stressed lunatic"...lol

Cheers for the help, i will test it tommorrow...

Ive had enough for one day......

:)

"Why type a book, when you can click and play"  ----- This is just a phrase, dont take it seriously

---

### Post by Bachstelze on 2007-03-29
Because only kinds buy a book for the pictures. Then they learn to read and write ;)

---

### Post by r2000 on 2007-03-29
Lol, 

"Quick thinkers, think alike"

---

