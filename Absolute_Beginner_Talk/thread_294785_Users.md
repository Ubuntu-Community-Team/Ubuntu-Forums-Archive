---
title: "Users"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by spinflick on 2006-11-07
Why is it that when I type in "users" or "who" in my terminal I get two spinflicks? :eek:  I'm not paranoid really ;)

---

### Post by boban on 2006-11-07
> **spinflick said:**
> Why is it that when I type in "users" or "who" in my terminal I get two spinflicks? :eek:  I'm not paranoid really ;)

Open up another terminal and check again :)

---

### Post by xpod on 2006-11-07
dad@dad-desktop:~$ who
dad      :0           2006-11-07 09:36
dad      pts/0        2006-11-07 11:20 (:1.0)
dad      pts/1        2006-11-07 11:23 (:1.0)

Hey 3 dads......i wondered why i had sooo many kids;)

---

### Post by boban on 2006-11-07
> **xpod said:**
> dad@dad-desktop:~$ who
dad      :0           2006-11-07 09:36
dad      pts/0        2006-11-07 11:20 (:1.0)
dad      pts/1        2006-11-07 11:23 (:1.0)

Hey 3 dads......i wondered why i had sooo many kids;)

:D

---

### Post by xpod on 2006-11-07
I got 5 so 2 are going to be pretty pi**ed to hear there aint enough dads to go round it seems..](*,) 

What i really want to know though is what all that means and what the dates are??.....before i start getting paranoid:D

---

### Post by spinflick on 2006-11-07
This is what I'm getting.........

spinflick@home:~$ users
spinflick spinflick
spinflick@home:~$ who
spinflick :0           2006-11-07 09:50
spinflick pts/0        2006-11-07 11:34 (:0.0)
spinflick@home:~$

---

### Post by boban on 2006-11-07
This is how I understand that (it doesn't mean that it is correct :) ): 
Every time you open terminal, you get another login on virual console. (pts/X). And the dates from who (try who -H) is time when that user has logged in (so in case of pts/X you'll have time column is telling when that terminal was opened)

:)

---

### Post by xpod on 2006-11-07
ARRHHHHH..i was reading the dates as the 11th of july 2006...DUH!!!

Now it makes more sense......well,sort off.

---

### Post by spinflick on 2006-11-07
I can maybe see that working for the "who" command but the "users" :confused:

---

### Post by boban on 2006-11-07
> **spinflick said:**
> I can maybe see that working for the "who" command but the "users" :confused:
From manual:

users  -  print the user names of users currently logged in to the cur&#8208;
       rent host

So it lists all logged in users - and if you are logged into Gnome and opened terminal (another login), you get 2 users logged in... Try opening few more terminal, and you'll see that 'users' will list one more "spinflick" for every terminal.

---

### Post by xpod on 2006-11-07
It`s the London air........must be:D

---

### Post by spinflick on 2006-11-07
**OMG !** I'm being cloned, that's against the law in my country :mrgreen:

---

### Post by boban on 2006-11-07
> **spinflick said:**
> **OMG !** I'm being cloned, that's against the law in my country :mrgreen:

:mrgreen:

---

### Post by xpod on 2006-11-07
> OMG ! I'm being cloned, that's against the law in my country 

I`ll bet that aint stopping it going on though...somewhere.

---

### Post by 3rdalbum on 2006-11-07
Cloning humans (for research) just became legal in my country! So I've just opened up 10 tabs in Gnome Terminal and typed "who" in the last one, to excerise my new-found freedom.

---

