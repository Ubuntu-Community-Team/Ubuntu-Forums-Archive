---
title: "my &quot;groups&quot; command and no admin"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by djlilyazi on 2006-01-09
heloo...

my "groups" command and no admin...how do i get it back ?

---

### Post by earobinson on 2006-01-09
Im not sure i understand your question. are you asking how to run stuf as root (admin)

if so use sudo <command> then user password.

---

### Post by djlilyazi on 2006-01-09
[QUOTE=earobinson]Im not sure i understand your question. are you asking how to run stuf as root (admin)

if so use sudo <command> then user password.[/QUOTE]

when i go to the terminal i type groups this is what i get :

djlilyazi dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner

see if u type it on ur pc u will "admin" also in that list...

---

### Post by djlilyazi on 2006-01-09
some told me i can fix with using my live cd....but how ?

---

### Post by lha on 2006-01-09
No need for live cds. Open a terminal, type (or copy&paste)
```
sudo adduser djlilyazi admin
```
and press enter. It will ask for your password before you are added to group admin.

---

### Post by djlilyazi on 2006-01-09
[QUOTE=lha]No need for live cds. Open a terminal, type (or copy&paste)
```
sudo adduser djlilyazi admin
```
and press enter. It will ask for your password before you are added to group admin.[/QUOTE]


really ?... wow i will give that a try maybe after that i willhave permission do do stuff on the computer since right now i have no permission what sooo everrrrrr

---

### Post by Mustard on 2006-01-09
I'm having some doubts as to the usefulness of that solution, since sudo is apparently not going to be functioning for that user.

---

### Post by djlilyazi on 2006-01-09
[QUOTE=lha]No need for live cds. Open a terminal, type (or copy&paste)
```
sudo adduser djlilyazi admin
```
and press enter. It will ask for your password before you are added to group admin.[/QUOTE]


no that did not work at all...what can i do to add admin back to the group ?

---

### Post by GreyFox503 on 2006-01-10
[quote=lha]No need for live cds. Open a terminal, type (or copy&paste)
```
sudo adduser djlilyazi admin
``` and press enter. It will ask for your password before you are added to group admin.[/quote] 
This is the right command, but of course the problem is that you cannot give yourself sudo privileges using the 'sudo' command.

Reboot your computer, and at the GRUB menu, choose "recovery console" or something to that effect.  It should drop you into a root terminal.  *Then* try entering it, without the sudo:

```
adduser djlilyazi admin
``` 
When you're done type 'exit' and then test to see if you can 'sudo' as a regular user.

---

### Post by lha on 2006-01-10
[QUOTE=Mustard]I'm having some doubts as to the usefulness of that solution, since sudo is apparently not going to be functioning for that user.[/QUOTE]

One does not have to be in admin to have sudo rights. Sudoers can be listed in /etc/sudoers and I thought you had your username there. Tweaking Ubuntu is hard without ability to sudo. Ubuntu just allows sudoing for everyone in admin as default.

In your situation, GreyFox503's instructions will help.

---

