---
title: "remove password"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by HunkieChan on 2007-07-06
ok guys everywhere i go.. synaptic, install something, it asks for password.. how can i disable that ? thanks

---

### Post by Circus-Killer on 2007-07-06
i would highly recommend that you do not do this. whats happening is that when you click on an admin application, it is automatically running gksudo to give you admin priviledges. this is necessary to do such things as installing software and make system wide changes.

try out [this link]("http://www.gratisoft.us/sudo/") to read more. one of the reasons linux is secure is that unlike winows, you are not running as administrator most of the time. you only need to assume admin privilidges when absolutely necessary.

---

### Post by hartz on 2007-07-06
I agree with Circus-killer 100% - the inconvenience of having to enter a password a few times is nothing compared to the gained security.

Basically, a Virus or Trojan program cannot get elevated privileges without you entering your password.  Something like the Network Config tool, Date/time settings, and synaptic installer each uses gksudo to give it root privileges, allowing it to make changes to the system.  A virus or trojan can still erase or infect the files which are owned by your login ID, but cannot make changes to the files which are part of the running system or installed programs.

Once your computer is set up and running you will find that you don't often need to enter the password, so this is only "an issue" during installation or upgrade time.  If you find it such a big issue, set a password which is easy to type (but not easy to guess).  Then once you have completed your set up, you can set a stronger password again.

Welcome yo the world of safe computing!

---

### Post by HunkieChan on 2007-07-06
thanks bro..well then is there anything in linux like texter ( its by lifehacker.. its like autotext.. you enter email and  then space then it types out your whole email address).. is there anything like that ?

---

### Post by hartz on 2007-07-07
Hi HunkieChan,

I recommend you start a new thread about this as the question is not related to the topic of this thread.

Personally I don't know of such a utility but I'm almost 100% sure that there will be something like that;  It would particularly make sense for it to be in the accessibility category as it would make it easier for people with disabilities to type.

I don't have time now but I would search for "predictive text input" or something similar.

---

### Post by HunkieChan on 2007-07-07
thanks bro, ill open a new thread..thanks alot

---

