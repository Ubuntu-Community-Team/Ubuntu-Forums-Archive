---
title: "How to initiate new  process from terminal?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by almightybunghole on 2007-04-19
Hi folks,

I reckon this is really simple but my web searches so far haven't produced results :confused: :confused: . 

Could somebody please tell me what the command syntax is to fire up a new process from within a terminal window - in other words, say I want to run a remote desktop session, how do I prefix the command so it doesn't then tie up the terminal window until I quit the remote desktop client?

I'm sure this is very easy!

Thanks in advance.

George

---

### Post by proalan on 2007-04-19
postfix & to the command

eg 

gedit &

will launch the gedit program as a process in the background and allow you to continue to work in the same terminal

---

### Post by Jeremy23 on 2007-04-19
But watch out - if you close the terminal, the remote desktop session will bomb out. You might want to do it like this instead:

```
$ nohup the_command &
```

---

