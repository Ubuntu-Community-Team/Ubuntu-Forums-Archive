---
title: "Can’t login to Ubuntu 6.06.1 LTS"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by CShane on 2007-04-01
System
Dell PowerEdge 1900
2 Dual core Xeon Process 3.0 Mhz
2 Gig Ram
80 Gig Hard Drive

OS: Ubuntu 6.06.1 LTS (this is a new install on a new PowerEdge 1900 with no OS installed)

If I try to login I can not enter the password.  At the user name prompt <ubuntu login:> when I type nothing shows up on the screen till I hit enter then the user name that I typed in shows up on the screen and I am prompted for the password.  I type in the password and again nothing shows up on the screen till I hit the enter key and then I get <Login incorrect> and then if I hit enter again I get another line with ubuntu login: that has the password I typed in.  This sounds confusing to me so I will try and demonstrate it.

#) = what I typed in or key I hit


* Running local boot scripts (/etc/rc.local)     [ok] 
1) <enter> The server pauses at the above line till I hit the enter key
Ubuntu 6.06.1 LTS ubuntu tty1
Ubuntu login: 2)<username> (I typed “username” and nothing shows on screen) 
3)<enter>
Ubuntu 6.06.1 LTS ubuntu tty1
4)<enter>
Ubuntu login: username (the username I typed in at number 2 above 
Password: 5)<passwrd123>
6) <enter>
Login incorrect
7) <enter>
Ubuntu login: passwrd123 (the password I typed in at number 5 above 
Password:


It just repeats this cycle.


But, if I boot from the recovery mode I can login.

In recovery mode when I get the prompt

root@ubuntu:~# 1)<login>
2) <enter>
unbuntu login: 2)<username> shows up on screen as I type
3)<enter>
Password: < passwrd123> nothing happens on screen when I type
4)<enter>
username@ubuntu:~$


I am able to login

---

### Post by land0 on 2007-04-01
Linux is preprogrammed so that when you type your password in at the command prompt line it will not show any feedback for security purposes . As for your password not being accepted that is strange. By chance is your cap locks on?

---

### Post by ac7ss on 2007-04-01
oops...

---

### Post by ac7ss on 2007-04-01
Upon re-reading your post...

a: Try using another tty (ALT-F2) and see if that helps.

b: Do you use X? what happens at the login screen?

c: Using the root login (as you were before) go to /var/log and ```
grep keyb *
``` it should read the same for both of the last few startups (using the safe vs the regular boot.) (identified by which dmsg file or the datestamp on the kern or message files.)

d: Are you sure the kernel is the same between boots. check the grub command line for the safe vs regular boot.

---

### Post by CShane on 2007-04-01
:)  

The alt-F2 was the key.  After pressing it I got the screen cleared and I got another login prompt and when I typed the the screen responsed with what I typed and I was able to login.

Thanks a million for the help.  

The caps lock was not on.

What does the Alt-F2 do?

I am new and I am not sure what X is.  
I tried to install 5.10 from the live CD and got an error regarding X. (i thinks it's the desktop version)

I download Ubuntu 6.06.1 LTS and that is what's on the computer now.

Should I still check c and d of your post?


I am totally new and this is my 1st experince with linux so any suggestion would be great.

---

### Post by zvacet on 2007-04-02
Don´t fix it if it is not broken.

---

### Post by ac7ss on 2007-04-02
> **CShane said:**
> :)  

The alt-F2 was the key.  After pressing it I got the screen cleared and I got another login prompt and when I typed the the screen responsed with what I typed and I was able to login.

Thanks a million for the help.  

The caps lock was not on.

What does the Alt-F2 do?

I am new and I am not sure what X is.  
I tried to install 5.10 from the live CD and got an error regarding X. (i thinks it's the desktop version)

I download Ubuntu 6.06.1 LTS and that is what's on the computer now.

Should I still check c and d of your post?


I am totally new and this is my 1st experince with linux so any suggestion would be great.

alt-f2 switches to the second virtual console. (there are usually 5 or 6) it is possible that there is something in the kernel log that changes the terminal settings.

No, don't worry about the other tests. like the former post stated, if it ain't broke...

X (short for X windows) is a Graphical User Interface (GUI) that uses a mouse interface. (Like windowz, but Much better.)

If you want to run X, (most new users do, many experienced users do.) post the error in a new post, or, even better,  search for the error message within the forums.

The desktop version would be fine, (just has different default options.)

---

### Post by CShane on 2007-04-03
Again, Thanks a million ac7ss for your help.  I will leave the X alone for now and take zvacet on not fixing whats working.

I am sure I will be posting a lot for questions soon.

---

