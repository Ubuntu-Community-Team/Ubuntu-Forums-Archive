---
title: "[SOLVED] root level permissions"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by nuttycat on 2006-02-06
Hello everyone,
I have a query about the permissions for a user on Ubuntu.(hope this is the correct forum)

I am trying to install compile and build some software that needs the use of libraries such as libnet and libpcap. 

Both of these are packet filtering and packet generating libraries. From the documentation for both i see that they require root level permissions to run.

I've not been able to compile a single version of this and related libs in Ubuntu. Is this related to the fact that Ubuntu by default disables root level permissions?

(I've seen these programs compile and work like a charm in PCQ-2004, where the user was Root] 

so basically i guess my question is : will programs that need root level permission at compile as non root? I've tried 
```

sudo gcc -o lcap lcap.c

```
but even this produces errors at link time, which is why i suspect the root level permission to be the culprit.

any pointers would be really appreciated.
thanks,
Nuttycat

---

### Post by carlosqueso on 2006-02-06
nope...tha'ts not the culprit because sudo gives you root-level permissions, if you type ```
sudo bash
``` you'll see the root shell you're used to.  See [https://wiki.ubuntu.com/RootSudo?highlight=%28RootSudo%29](https://wiki.ubuntu.com/RootSudo?highlight=%28RootSudo%29) for more details. It's gotta be something else.  It may be that you're using a gcc 4.something which came with ubuntu and it expects gcc 3.4.  If that is the case, there's an easy way to change the version, but I don't know it so someone else will have to help you.

---

### Post by nuttycat on 2006-02-06
Thanks for the suggestion about "sudo bash".
I'll try that and get back to you.

Cheers
-nuttycat

---

### Post by newuser111 on 2006-02-06
try sudo -s -H

---

### Post by bartbes on 2006-02-06
sudo bash is so called 'unsafe'
on the ubuntu wiki they recommend using ```
sudo -i
```

---

### Post by nuttycat on 2006-02-07
:( 
I tried all the above, but all the time I get the same old errors.
maybe there is something else that is buggy.

but I don't get it...how could the same program and package that run perfectly in PCQ, give me linker errors in ubuntu?

thx for all the responses.
I'll keep you updated on any progress
Nuttycat

---

### Post by nuttycat on 2006-02-12
sorry for the delay,

I got the bug fixed. I needed to use a sudo commnd along with another command to tell gcc to use a certain library.

sudo gcc -o<object> <file> -<special library name>  was what finally worked.

Thanks everyone who posted.
-Nuttycat

---

