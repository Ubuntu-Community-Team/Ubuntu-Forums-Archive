---
title: "Change computer name"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-09-05
Hi, it's me again :)

I want to change my computer's name. Right now, I'm <username>@<username>-laptop, and that's boring. I want to change it to what I have affectionately named the old Compaq Evo, and I found a thread that said to edit the file /etc/hostname

However, there was also a post in that thread that claimed making that change brok things, and there were no more posts after that. Will it break things? Should I be concerned, or can I just go ahead and change the name?

It's a small thing, but after yesterday's conversation about this laptop, I just have to rename it. Chalk it up to being weird; but for me a computer's name is simply important.

Thanks,
Mimsy

---

### Post by croak77 on 2006-09-05
It could break sudo. You'll have to edit /etc/hostname and /etc/hosts.

---

### Post by whizbaby on 2006-09-05
There's a command to do that: hostname
type **man hostname** to see what it does.

---

### Post by Mimsy on 2006-09-05
Breaking sudo sounds bad. What's the worst thing that can happen?

And is there anything in particular I should remember about the editing?

Thanks,
Mimsy

---

### Post by jd65pl on 2006-09-05
>  	There's a command to do that: hostname
type man hostname to see what it does.

I think that will be your safest option like whizbaby said

---

### Post by Mimsy on 2006-09-05
Hostname it is. Thank you everyone! :-)

/Mimsy

---

### Post by jd65pl on 2006-09-05
Found an easier way to do this,

Goto:
[I]
SYSTEM > ADMIN > NETWORKING[/I]

Select the general tab and change the host name

log off

log back on

---

### Post by Mimsy on 2006-09-05
Sweet! The laptop has a less boring name, and works beautifully. Thanks! :-)

/Mimsy

---

