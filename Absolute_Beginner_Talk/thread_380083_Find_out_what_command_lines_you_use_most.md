---
title: "Find out what command lines you use most"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by xyz on 2007-03-09
Hi folks,
I did not come up with this myself but found out about it on the [French Ubuntu Forum]("http://forum.ubuntu-fr.org/viewtopic.php?id=97488")

This was posted by **Yannick_LM**
In a terminal, copy/paste:
```
 history | cut -b8- | cut -d' ' -f1 | sort | uniq -c | sort -rg | head
```
while **teke** suggests you put it in your ~/bash_aliases :
> hy() {
history | grep -vE -e "[0-9]{1,4}  hy |history" | grep -iE -e $1 | less
}
Of course, you all know that running
```
history
```
will also reveal the command lines you used but only as a list.
*Yannick's* command line gives it to you by numbers which can be helpful in creating aliases.

---

### Post by bapoumba on 2007-03-09
Hello :)
As a side note to this, CTRL-R will recursively search through previous commands a matching set of letters or key word:
```
(reverse-i-search)`res': sudo cp /etc/resolv.conf_maison /etc/resolv.conf

```

---

### Post by yannick_LM on 2008-02-10
Hello bap :)

I should come up here more often ... 

Well, time have passed and I've made progress.
So here is a better command :


```
sed -e 's/sudo //' $HOME/.bash_history | cut -d' ' -f1 | sort | uniq -c | sort -rg | head
``` 

If you're using Zsh : 
```
sed -e 's/sudo //' $HOME/.histfile |  cut -d' ' -f1 | sort | uniq -c | sort -rg | head
```

As in the French forum, it could be interesting to know what commands do you folks use most.  (1)

Warning : it could reveal a lot about yourselves :cool: 
Here is the [URL="http://forum.ubuntu-fr.org/viewtopic.php?id=184370"]link 
[/URL]  if you want to see the results for the French speaking forum.

(1) In this case, maybe this thread should be moved to forums games

---

### Post by lespaul_rentals on 2008-02-10
Apparently "nano...", "cd", and "su".

---

### Post by brennydoogles on 2008-02-10
For me it appears to be ```
 47 cd
     41 ls
     38 aptitude
     29 javac
     27 java
     23 gedit
     22 bname
     21 ssh
     20 chmod
     14 server

```

with bname being the command to run a batch rename script (which I use a lot as a wedding photographer) and server being the alias I have set to ssh into my home file server.

---

