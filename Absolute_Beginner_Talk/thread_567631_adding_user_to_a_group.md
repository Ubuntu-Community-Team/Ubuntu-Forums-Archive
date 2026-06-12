---
title: "adding user to a group"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-04
How do i add a user to a group.  I installed VirtualBox and need to add myself to that user group.

---

### Post by nowshining on 2007-10-04
open up users and groups - input ur password
 - manage groups - vboxusers 

then once selected at right click properties 

Under Group Members Check mark the Check mark next to ur username then okay, close and then close. :)

---

### Post by bodhi.zazen on 2007-10-04
From the terminal ```
sudo usermod -G <group> -a <user>
```

---

### Post by Dr Small on 2007-10-04
```
sudo addgroup <user> <group>
```

As you can see, there are multiple ways to preform this task.

Dr Small

---

### Post by Elle Stone on 2007-12-28
> **bodhi.zazen said:**
> From the terminal ```
sudo usermod -G <group> -a <user>
```

Thank you very much for giving the command line version of adding a user to a group.  

I am new to linux, but I'm comfortable working at a command line (having learned, over my years as a windows user, the rudiments of more yapls "yet another programming language" than I care to think about).  

I run some very ram-hungery applications, so ram wasted on a pretty and user-friendly interface was just out of the question.  So I installed the cli version of ubuntu and added icewm and xorg and so forth.  

I chose Ubuntu over other linux installations in large part because of the Ubuntu forums - much friendlier and more detailed answers than other distributions (well, gentoo forums are friendly and detailed, but I couldn't get past the "download the third stage" part of the installation).

Often Ubuntu forum answers make the natural assumption that one has gnome installed.  So answers like yours giving the comand line version of how to do something are ***extremely*** appreciated.

Elle

Now if I could just find that "Thanks" button I read about, I'd have thanked you through the button.

---

### Post by popch on 2007-12-28
> **Elle Stone said:**
> 
Now if I could just find that "Thanks" button I read about, I'd have thanked you through the button.

It is below the post you want to say 'thank you' for, just to the left of the 'quote ' button. Look for a green ribbon with a star shaped medal.

---

### Post by Elle Stone on 2007-12-30
> **popch said:**
> It is below the post you want to say 'thank you' for, just to the left of the 'quote ' button. Look for a green ribbon with a star shaped medal.

Hmm, I see the quote button at the bottom right.  But there is no green ribbon with a star anywhere to be seen.  I am using Firefox with noscript - perhaps that is the problem.  By the way, I've noticed that often when I'm looking for advice, a post from you has already answered the question.  Again, thank you, thank you, thank you.  I know it's not an official thank you - I'll see if I can find a way to make the green ribbon appear.

Elle

---

