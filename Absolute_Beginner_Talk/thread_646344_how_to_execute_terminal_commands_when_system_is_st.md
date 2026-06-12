---
title: "how to execute terminal commands when system is starting"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by mokkai on 2007-12-21
how to execute terminal commands when system is starting

actually always when i start my system 
i want to execute

username@ubuntu7.04:~$cd /home/username/rails/project1
username@ubuntu7.04:~/rails/project1$ruby script/server webrick -p4444 

is there any idea to do this with starting process
so i don't want to execute it in a new terminal after i start my computer


any idea

---

### Post by jachymc on 2007-12-21
for system: look in the /etc/rc.local file
when you want to run something, when you login, it is ~/.bashrc or  ~/.xsession

---

### Post by mokkai on 2007-12-21
i type these in rc.local
`cd /home/username/rails/project1`
`ruby script/server webrick -p4444 `

but not working
any ohter idea....

---

### Post by scxtt on 2007-12-21
what about:

ruby /home/username/rails/project1/script/server webrick -p4444

tho i'm not sure what "script/server" is supposed to be.

---

### Post by mokkai on 2007-12-21
ruby /home/username/rails/project1/script/server webrick -p4444
if i execute it in a terminal then it is working

i added that command in rc.local ,after restart system thats not working.

any idea ...

---

### Post by scxtt on 2007-12-21
try giving it the FULL path to ruby, i.e.:

[COLOR="Cyan"]/usr/local/bin/ruby[/COLOR] /home/username/rails/project1/script/server webrick -p4444
{i don't know what [COLOR="cyan"]that[/COLOR] actually would be, **whereis ruby** will tell you}

and what user are you [ logged in as / running that command as ] -- anything you put in rc.local will be run as root ...

---

### Post by mokkai on 2007-12-22
thank you so much
    now it is working
bye...

---

