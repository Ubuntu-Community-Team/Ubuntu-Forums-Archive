---
title: "Multiple RemoteLogins"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by majo on 2006-11-29
Hello,

Yes i am newbee too 

Well what i am trying to do is, create multiple logins for my ubuntu edgy.

What i do know is How but what i do not know is how users would be able to login to my ubuntu remotely, i understand there is a way to connect via ssh 

ssh example@x.x.x.x 

But my plan is to have co-workers login to my ubuntu machine either via VNC or any other application that allows that. 

Something similar to windows RDP.

is that possibility ? Yes? what should i look for? do you have tutorial (makes life easier) 

Also if you could answer me this question,

When i boot my Ubuntu, i first have to login LOCALY and then i would be able to run vnc , 

is there a way to boot my ubuntu and login from vnc, 
example of

restarting ubuntu >>ubuntu boots>> and then i type in username & password to login to ubuntu .


Thank you.

---

### Post by nickburns on 2006-11-29
you can ssh a ton of users with no problems.  I have seen more than 50 on a single system with no problems.

VNC / RDP will only work with 1 as far a I have ever got running.

---

### Post by steve.horsley on 2006-11-29
I think package vnc4server is probably what you are looking for.

---

