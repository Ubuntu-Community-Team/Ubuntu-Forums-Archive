---
title: "sudo dpkg --configure -a will not work!"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by Kannasu on 2007-09-12
Hello everyone,  I'm posting from a fresh install off the LiveCD.  The problem I'm having is when I try to go to Add/Remove I get an error message:

> 
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I open the terminal and type in "sudo apt-get update" like it says but I run into another problem:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Now this isn't my problem because I know what to do here, or at least what I should do... the problem is typing in "sudo dpkg --configure -a" in the terminal gives me ANOTHER error message!

> dpkg: parse error, in file `/var/lib/dpkg/status' near line 12522 package `libeel2-2':
 `Depends' field, syntax error after reference to package `libglade2-0

This is the point that I get stuck,  I don't know what else to do at this point.  My experience with Ubuntu only goes so far,  I want to see if anyone here has seen this and knows a work around?

---

### Post by por100pre1 on 2007-09-12
Please try this:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_old
```

then:

```
sudo dpkg --configure -a
```

EDIT: BTW, Welcome to the forums.

---

### Post by por100pre1 on 2007-09-12
If that doesn't work put it all together:

```
sudo mv /var/lib/dpkg/status_old /var/lib/dpkg/status
```

Then do this:

```
grep libeel2-2 /var/lib/dpkg/status
```

and post the results...

---

### Post by Kannasu on 2007-09-12
> **por100pre1 said:**
> Please try this:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status_old
```

then:

```
sudo dpkg --configure -a
```

EDIT: BTW, Welcome to the forums.

Thank you!!!  I got it to work with a bit of tweaking but now I can finally access the add/remove

I really like Linux so far, and really want to get as comfortable with it as I was with Windows.

Hopefully I can start helping people out with problems, I jot down all the new fixes I find so I'll never lose them :P

---

### Post by por100pre1 on 2007-09-12
EDIT: Glad to help. 8)

---

