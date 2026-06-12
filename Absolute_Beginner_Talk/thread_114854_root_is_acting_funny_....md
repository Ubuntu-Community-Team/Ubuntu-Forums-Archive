---
title: "root is acting funny ..."
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by djlilyazi on 2006-01-09
HI,

when i try to access system --> adminstration --> and then any of the tools there i cant access them anymore it asks for the password then thats it ...nothing else happens...what do i do to fix this...i dont know what typer of user i am either now... oh god........

---

### Post by earobinson on 2006-01-09
did you enable the root account? if so it is asking your your user password not the root password.

---

### Post by djlilyazi on 2006-01-09
[QUOTE=earobinson]did you enable the root account? if so it is asking your your user password not the root password.[/QUOTE]


i use to just put my password and everything would work how i reset the whole root thing ?

---

### Post by djlilyazi on 2006-01-09
what i try to do anything it says i dont have permission... even after i put my password.....i just want to reset the whole root thing is that a way i can do that ?

---

### Post by djlilyazi on 2006-01-09
[QUOTE=djlilyazi]what i try to do anything it says i dont have permission... even after i put my password.....i just want to reset the whole root thing is that a way i can do that ?[/QUOTE]


i tryed everything...what can i do now...

---

### Post by paulmilliken on 2006-01-09
Can you still sudo on the command line?  For example type
"sudo ls" and it will ask for your password.  If this works then at least you have the correct password.

---

### Post by djlilyazi on 2006-01-09
[QUOTE=paulmilliken]Can you still sudo on the command line?  For example type
"sudo ls" and it will ask for your password.  If this works then at least you have the correct password.[/QUOTE]


yes taht works.... :) but i still can use anything in system---admin---any of the tools

---

### Post by earobinson on 2006-01-09
what about gksudo from the comand line?

---

### Post by djlilyazi on 2006-01-09
[QUOTE=earobinson]what about gksudo from the comand line?[/QUOTE]

when i use the command "groups"

there is no "admin"

how do i get it back ?

---

### Post by patholio on 2006-01-26
curiously, exactly the same thing has just happened to me.
i have been unable to access anything that requires the root password (or my user password) since the last updates.
My user is no longer a member of admin either.

---

### Post by Koobi on 2006-01-26
what do you see when you type in the following in the terminal?
```

whoami

```


if it doesn't say root that means your'e not logged in as one.




[QUOTE=djlilyazi]when i use the command "groups"

there is no "admin"

how do i get it back ?[/QUOTE]

you mean "root" don't you? because that's the linux equivalent of "Admin" on windows to a certain extent




try invoking one of those admin tools via terminal.

for example, try this:
```

sudo synaptic

```

and enter the password when it asks for it and see if it actually loads synaptic

---

### Post by bscbrit on 2006-01-26
No, the OP is correct.

The 'admin' group is used to give users sudo powers.  In fact, the sudoers file simply grants root rights to all members of the admin group.  If, in response the the command 'groups', there is no admin group then that would explain perfectly why the user cannot get root access.

I'm not sure that 'sudo ls' is a valid check because, even if it fails, ls will simply run with normal rights.  But 'sudo synaptic' which you have also suggested, should be a better test.

---

### Post by bscbrit on 2006-01-26
If you have lost the 'admin' group, I think that the easiest way to recover it (without having sudo access) is to reboot the computer in recovery mode (i.e. when the grub menu is displayed, select the kernel and 'recovery mode').  This will put you at the command line as root.

You can then add the group admin and check that your usual username is a member of that group.

Reboot as normal and you should be back in control.  I can give you more details once we know the response to Koobi's last question.

---

### Post by qwazert on 2006-01-26
Editted.

---

