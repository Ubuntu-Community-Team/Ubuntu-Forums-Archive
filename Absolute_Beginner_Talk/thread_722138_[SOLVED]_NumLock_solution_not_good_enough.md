---
title: "[SOLVED] NumLock solution not good enough"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by gobuntu on 2008-03-12
Dear friends,

It seems to me that the solution:
[COLOR="Blue"]--------------------------------------------------
 In Gutsy, edit /etc/gdm/Init/Default. For older versions of ubuntu edit /etc/X11/gdm/Init/Default instead.

Find the line
            exit 0
Add the following code above that line

if [ -x /usr/bin/numlockx ]; 
then /usr/bin/numlockx on
fi
-------------------------------------------------[/COLOR]

needs some improvement, because with this solution my NumLock does not trigger until the Desktop appears.

This means that when Ubuntu asks for the name and password, I still can not use the numeric keypad.

WHEREAS, what seems to be happening is this:

1. My laptop turns- on with NumLock ON

2. GRUB is running with NumLock ON

3. Once Ubuntu STARTS BOOTING, it actually TURNS OFF the NumLock key, and keeps it OFF when it asks for the name and password.

So, to me, it seems that Ubuntu SHOULD NOT turn OFF the NumLock OFF when booting; what for? It should just leave NumLock as it is, would say.

Does anyone know of another solution, other than the above, that would have NumLock ON when Ubuntu is asking for the Name and PW?

If not, perhaps this should be fixed by the  Distro?

Thanks.

---

### Post by bollix47 on 2008-03-12
You could try installing numlockx using synaptic.  It's in the universe repository.  Not sure if it will solve your problem as I use automatic login and can't test it, but I believe it activates as soon as 'X' is up.

Good Luck!

---

### Post by gobuntu on 2008-03-12
> **bollix47 said:**
> You could try installing numlockx using synaptic.  It's in the universe repository.  Not sure if it will solve your problem as I use automatic login and can't test it, but I believe it activates as soon as 'X' is up.

Good Luck!

Thanks, Bollix,

I'll try it later and hope it activates sooner.

By the way, is automatic log-on the same as having no password?:confused:

---

### Post by bollix47 on 2008-03-12
> **gobuntu said:**
> Thanks, Bollix,

I'll try it later and hope it activates sooner.

By the way, is automatic log-on the same as having no password?:confused:

My user name still has a password.  As I'm the only one using this computer I don't need to login.  You can activate it by going to System > Administration > Login Window > Security > Enable Automatic Login and selecting your user name.

You still have to enter your password when doing administrative tasks.  There is a way to eliminate that need too but it's not recommended as it is a security risk.

---

