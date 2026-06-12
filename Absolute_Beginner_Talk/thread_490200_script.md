---
title: "script"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by alaskaman on 2007-07-02
any one  have any idea where i can go to find out how to make a script on my box so when do like !ircd it will give you list of ircd to untar

---

### Post by rillip on 2007-07-02
Sounds like you want to make a bash script.  Quick googling brought up this link and many others.

[http://www.ibm.com/developerworks/library/l-bash.html]("http://www.ibm.com/developerworks/library/l-bash.html")

---

### Post by alaskaman on 2007-07-02
what trying to do is make it so when user does a command like !eggdrop or Ircd  it untar the files for them if some one could give me an explame on how to do this it would be a big help

---

### Post by eternalsword on 2007-07-02
sorry, but what's a list of ircd to untar?  If I knew what that was, I could probably write up a script for you.

are you referring to an internet relay chat daemon?  if so it depends on what software you are using.  I'm still not quite clear what you are trying to accomplish.

---

### Post by alaskaman on 2007-07-02
yes talking about irc chat daemon im going have copy of the most commom ircd used and when they do !ircd i want it to give them list of the software i have so if they were to pick unreal option it would then untar unreal for them trying to do the same thing for eggdrop bot

---

### Post by Golyadkin on 2007-07-02
Ahh, so you want to write an IRC script, not a BASH script. It depends on your IRC client what language you should use.

---

### Post by alaskaman on 2007-07-02
no i am trying to do it from shell  i am going to hopfully sell some shell

---

### Post by eternalsword on 2007-07-07
irc daemons have their own scripting environment, you can't just make a shell script.  You probably have to write a plugin.  it could be in c or c++ or ruby or python depending on what ircd you are using.

---

