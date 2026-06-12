---
title: "evolution: filter incoming messages"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by evaristegalois on 2007-10-10
I am setting up Evolution to receive emails from different accounts. The idea is to apply a filter to incoming messages and sort them into their respective folders. Everywhere the instructions to do this say: go to edit > preferences > mail accounts > edit > receiving options > options and then click on something like "apply filters to incoming messages". However, I do not get a tab or a button called "options" when I am in "receiving options". Mystifying, as far as I am concerned. Please help if you can. My accounts are POP3 accounts, and I already have filters defined.

---

### Post by julian67 on 2007-10-11
edit>Message Filters

---

### Post by ab4nk on 2007-11-15
Same to mee...
the worst is , my office email server using da*n microf*ck Exchange......

please guys any one have patch or updating from evolution..or any suggest to use other program that could connect to microf*ck Exchange ?


:)

---

### Post by medotin on 2007-12-05
I'm not sure if this is related to the OP question, but it seems to be relevant to ab4nk's comment.

incoming exchange mail filtering appears to be fixed with the evolution-exchange module at rev 1502 and later.  The first release after 1502 is 2.21.2, tagged at rev 1504.

[http://svn.gnome.org/viewvc/evolution-exchange?view=revision&revision=1502](http://svn.gnome.org/viewvc/evolution-exchange?view=revision&revision=1502)
[http://svn.gnome.org/viewvc/evolution-exchange?view=revision&revision=1504](http://svn.gnome.org/viewvc/evolution-exchange?view=revision&revision=1504)

You could checkout from trunk and build/install yourself to fix this, or wait for this change to make it into the repositories.

---

### Post by plucky on 2007-12-05
evaristegalois

1) Set up your email accounts

2) On evolution main page create a new folder for each mail account e.g.
          [indent]**myusername1@isp1.co.uk**[/indent]
           [indent]**otherusername1@isp2.co.uk**[/indent]

3) Create sub folders in each mail account of **inbox,sent,etc**

4)In evolution **EDIT> MESSAGE FILTERS**
    
 4a) Set up incoming filter rules first  **>ADD**. For each account add **recipient** contains **myusername1@isp1.co.uk** then move to **myusername1@isp.co.uk/inbox**
     
4b) Do the same for outgoing messages **EDIT > MESSAGE FILTERS >OUTGOING >ADD**
For each account add **sender** contains **myusername1@isp.co.uk** then move to folder **myusername1@isp.co.uk/sent**

5) Once all the filters have been set up you need to go **EDIT > PREFERENCES**

6)  select an account and **EDIT>DEFAULT** Click on **SENT** and the relevant folder

7) Do the same for **DRAFTS**

8) do the same for each account

Clear as mud!!!

Test and enjoy...

---

