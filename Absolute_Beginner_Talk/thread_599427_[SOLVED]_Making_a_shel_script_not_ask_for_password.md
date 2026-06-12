---
title: "[SOLVED] Making a shel script not ask for password"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-11-01
I need a shell script to execute on login, but it needs a password entry. I have tried adding the script's location to sudo visudo, with the following entry:

```
myusername ALL = NOPASSWD: /home/myusername/.networkrestart.sh
```

i have also ```
chmod +x .networkrestart.sh
```

i fail to see why this shouldn't work, its probably an elementary mistake

SuperAndy

---

### Post by ddrichardson on 2007-11-01
I think that needs to be```

myusername ALL = (ALL) NOPASSWD: /home/myusername/.networkrestart.sh
```But I'm a little rusty.

---

### Post by SuperAndy on 2007-11-01
i think that works! i wont jinx it, but i will restart and see if it works.

---

### Post by SuperAndy on 2007-11-01
alas no, it is still prompting for a password

---

### Post by ddrichardson on 2007-11-01
The only other thing I can think of is giving the host name explicitly instead of ALL.  I'm pretty familiar with /etc/sudoers but never disable passwords so hopefully someone with more experience than me can assist.

---

### Post by SuperAndy on 2007-11-01
ok, cheers for the attempt anyway :)

---

### Post by MaximusTG on 2007-11-01
I was writing a backup script yesterday, and found this workaround:

if you use 

```

echo yourpassword|sudo -S commandyouwanttorun

```

sudo will take the standard input as password. Just make sure you make the file readable only by you!

---

### Post by SuperAndy on 2007-11-01
good plan! i cant reboot and try it now since i am running some huge copy, but i will give it a shot later on and get back to you!

---

### Post by SuperAndy on 2007-11-01
That works!

However, I haven't taken away any privelags yet. Am I right in thinking that if i chmod -r the file, I will loose any ability to execute it without using sudo, and hence defeating the point?

---

### Post by spec-chum on 2007-11-01
You can do ```
chmod og-r file

```
That will remove read permissions from the file for (g)roup and (o)thers leaving it readable only by the owner, i.e. you.

---

### Post by SuperAndy on 2007-11-01
hmm, that still doesn't work. I just get told I dont have permission.

---

### Post by MaximusTG on 2007-11-01
That's probably because you would have to do that command as root.. 

sudo chmod og-r file

or try 

sudo chmod 611 file

---

### Post by SuperAndy on 2007-11-01
yea, i tried it as root anyway. if it is such a simple thing, it can't be this difficult :P i have experimented with different options in chmod, and they either let everyone read it, or only root.

---

### Post by SuperAndy on 2007-11-01
ok, the original suggestion worked. as in, adding it to sudoers.

my sudoers now has the following appended:
```

myusername ALL = (ALL) NOPASSWD: /home/myusername/.networkrestart.sh

```

and the contents of .networkrestart.sh are:
```

#! /bin/bash

/etc/init.d/networking restart
```

The reason it was prompting for a password was becuase I (stupidly) had a sudo before the command in the script. Its not needed, since the entire point of the first part is to be able to run it by typing sudo .networkrestart.sh without typing a password.

Works now!

SuperAndy

---

### Post by ddrichardson on 2007-11-01
Good, I thought I was going mad.

---

### Post by Jose Catre-Vandis on 2007-11-01
IME

If you point at your script from the rc.local file, you don't need to worry about password?

---

### Post by SuperAndy on 2007-11-01
yea, but i want it to run at login, since i'm not entirely sure why i need to restart the networking in the first place, something dodgy with the module in gutsy i am guessing. Doing it in the login script seems more reliable.

---

### Post by Jose Catre-Vandis on 2007-11-03
> **SuperAndy said:**
> yea, but i want it to run at login, since i'm not entirely sure why i need to restart the networking in the first place, something dodgy with the module in gutsy i am guessing. Doing it in the login script seems more reliable.

That is exactly what I am doing. My network configuration (/etc/interfaces file) caused too many problems on boot and after login and didn't connect me to my nfs shares, so I wrote a script which allowed for a straightforward network set up, then restart networking with a new one after login. (Simply, two interfaces files, one simple, one complex, copied then copied over after restart of networking) This script is referred to in the rc.local file. Slows things down a little bit after login, but it works.

---

### Post by SuperAndy on 2007-11-05
ah, so rc.local is run on login?

---

