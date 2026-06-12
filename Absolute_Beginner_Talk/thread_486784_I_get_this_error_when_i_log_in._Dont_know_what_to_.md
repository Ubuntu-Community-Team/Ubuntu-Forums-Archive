---
title: "I get this error when i log in. Dont know what to do"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by ross350 on 2007-06-28
Hi
things have been a bit shaky for me over the last couple of days after learning of ubuntu.
Learning to love it that is. but yeh this isn't a fan post.

Fellow users I have a problem. 
when i first login I get the orange square in the top corner(might be different for some people but i haven't changed it around too much) anyway, the square tells me i need to run package manager ,
so, i do 
and it gives me this error:-

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Could not open file /var/lib/dpkg/status - open (2 No such file or directory), E:The package lists or status file could not be parsed or opened.'


can i just reinstall the package manager or what do i do, the system runs fin and i have beryl finaly working after figuring out what login as xgl meant.

an i have some help
Ross

---

### Post by Seisen on 2007-06-28
Which version of Ubuntu are you using?

---

### Post by ross350 on 2007-06-28
Hi
I am using feisty fawn, 7.04, the 32-bit

---

### Post by Seisen on 2007-06-28
Put this in the terminal

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_backup
```
That will rename the corrupted status file so apt won't see it anymore.

Next run this:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```
To restore an old status file that is ok

Then
```
sudo apt-get update
```

---

### Post by ross350 on 2007-06-29
thanks
but on the very first command i got this reply :-

mv: cannot stat `/var/lib/dpkg/status': No such file or directory 

thats why i think i need to reinstall the package manager but i am still learning.
it was telling me there was a problem on line 46 of one of my list files before i asked a question here.

so i found that list file and just deleted the 46th line (i'm still learning ) that probably was a bad thing rite?

Thanks 
Ross






EdIt:- i just skipped the first step and it all worked . you are a life saver, how do i become one of these people that are so helpful to this programs users

---

### Post by ross350 on 2007-06-29
hi again.
It was fixed but not properly .
I have mucked around since it seemed fixed and my new mission is to get google earth working.
but i cant . now i am getting a different error

E: Type 'echo' is not known on line 53 in source list /etc/apt/sources.list


when i use:- sudo apt-get update

i am sorry , i still need to learn more about what to do for myself

---

