---
title: "update manager problem"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by bachuu on 2007-05-02
while i was trying to get Kadu program i get a response: malformed line 35 in sources list /etc/apt/sources.list the list of sources could not be read 
now i can't update anth but sys works
during instalation i went follow the instructions but of courses sth in the end was wrong. 
i,m absolutly newbie 
i tried to run Synaptic but response was the same.
i search forum, faq but i couldn't find solution.

ps sorry for my Engl

---

### Post by taurus on 2007-05-02
There is something wrong with line 35 in your /etc/apt/sources.list.  Therefore, you can either edit it

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of line 35 to comment it out.  Then, run

```
sudo aptitude update
sudo aptitude upgrade
```
or post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by bachuu on 2007-05-02
i follow the instrukctions above and it helps
thanks

---

