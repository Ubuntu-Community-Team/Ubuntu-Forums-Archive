---
title: "premmisions"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-12
1.I know you can set premmision on file/folder
read , write and excecute.
are there more premmisions ?
like how can I deny some user from openning a file or a folder ?
I've tried going into the properties of the folder but couldn't set "noune" to one user.
only to everyone... (I used thunder for this case , tring to get nautilius working again).
and are there more premmisions I missing ?
2.about user,group premmisions - I've took a look at them and there aren't so many premmisions like in winxp,2003
like if I want someone to be able to connect to the internet but not be able to make remote connection ?
are there more premmisions I might missing ?

---

### Post by T700 on 2006-07-12
Go [here]("http://www.google.com/search?q=linux+permissions&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official") for all you will ever need to know about permissions.

Paul

---

### Post by MaximB on 2006-07-12
I've took a look at thouse pages and found out tomy complete amaizment that winxp/2003 has much more premissions.
user file and folder premissions....how come ???
I thought that linux was built for it.

---

### Post by digby on 2006-07-12
Windows has more because it's different.  Extra options (i.e. complexity) do not necessarily lead to more secure or better options.  I promise you that you can setup any possible scheme you want using the unix model.

For example to deny someone from opening a directory in linux, you can remove the execute bit (chmod o-x dirname).  To do the same for a file, you simply remove the read bit (chmod o-r filename).  In these two examples, we are telling it to modifiy the permissions (chmod) for others (i.e. not the owner of the file or member of the owning group) by using 'o' and turning of the permissions for read and write (-r and -x respectively)

---

### Post by MaximB on 2006-07-13
yes I know...but it'smore simple...I thought there should be more options
like how do I make somone to be able to connect to the internet but disable to make a remote connection ?
or how do I make GPO (group policy) like if I want that the minimum password lenth would be 8 or that the passord must be complexcive ?
there are handrets of useful things in GPO
thouse linux have a GPO ???

---

### Post by T700 on 2006-07-13
Those are policy actions.  You were talking about file permissions. 

Paul

---

### Post by Miguel on 2006-07-13
Password minimum length:

This can be done. My first linux distro, Mandrake 10.0, had this option on. It asked you for a minimum 6 character and some complexity. AFAIK, Ubuntu doesn't have this on. I have to admit that I can't help you with this one if you want to set it.

Remote conections:

Ingoing ssh logins are configured via /etc/ssh/ssh_config. More info can be found in the man page of ssh_config (5). You can blacklist people here. For outgoing ssh conections it can also be done. A naive way would be making a group specifically for this and only allow the users in that group to use programs like ssh or telnet. However, there is probably an easier way to do this.

---

