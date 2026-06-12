---
title: "Why does &quot;sudo echo...&quot; never work?"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by rocketman768 on 2007-04-17
For example, this command will not work:

sudo echo 6 > /proc/acpi/processor/CPU0/throttling

It complains about permissions. However, if I do a "su -s" to get into a root shell, then:

echo 6 > /proc/acpi/processor/CPU0/throttling

...works. I suspect this has something to do with sudo not liking the redirection. Or maybe I need to manipulate the command with quotes or something?

---

### Post by askreet on 2007-04-18
Because you're only entering super-user mode in the first command.  The pipe into the file is not part of the sudo'ed command.  It's frustrating, but that's the way =)

- aSkreet

---

### Post by ardchoille42 on 2007-04-18
> **rocketman768 said:**
> For example, this command will not work:

sudo echo 6 > /proc/acpi/processor/CPU0/throttling

It complains about permissions. However, if I do a "su -s" to get into a root shell, then:

echo 6 > /proc/acpi/processor/CPU0/throttling

...works. I suspect this has something to do with sudo not liking the redirection. Or maybe I need to manipulate the command with quotes or something?

It doesn't work because what you are doing has two parts to it..

```

sudo echo 6

```
this works because you are simply echoing a string, and you don't even need sudo for this.

```

> /proc/acpi/processor/CPU0/throttling

```
this **doesn't** work because the system is attempting to write/redirect that string (6) to a system file as USER, not root.. and you don't have the permissions to edit system files without using sudo.


What you need to do is use the "tee" command..

```

echo 6 | sudo tee -a /proc/acpi/processor/CPU0/throttling

```

that will append the echo'd string (6) to /proc/acpi/processor/CPU0/throttling because you are using the tee command with sudo perms. You can read "man tee" for more info about tee.

---

### Post by rocketman768 on 2007-04-18
> **ardchoille42 said:**
> It doesn't work because what you are doing has two parts to it..
What you need to do is use the "tee" command..

```

echo 6 | sudo tee -a /proc/acpi/processor/CPU0/throttling

```

that will append the echo'd string (6) to /proc/acpi/processor/CPU0/throttling because you are using the tee command with sudo perms. You can read "man tee" for more info about tee.

Very nice! Just what I was looking for. Thanks!

---

### Post by askreet on 2007-04-19
Great answer, and I learned something new! :grin:

---

### Post by marklynch on 2008-03-17
With a bit of digging I also found that you can suppress the output of the commands to the screen by appending piping the standard output to /dev/null. So the command would be:

echo 6 | sudo tee -a /proc/acpi/processor/CPU0/throttling > /dev/null

The reason I got onto this subject was a similar power saving crusade I was on.  There are some more power saving tips and tricks here:
[http://www.lynchconsulting.com.au/blog/index.cfm/2008/3/10/Power-saving-tips-for-Ubuntu-on-laptops](http://www.lynchconsulting.com.au/blog/index.cfm/2008/3/10/Power-saving-tips-for-Ubuntu-on-laptops)

Cheers,
Mark

---

### Post by Gen2ly on 2008-03-21
> **ardchoille42 said:**
> It doesn't work because what you are doing has two parts to it..

```

sudo echo 6

```
this works because you are simply echoing a string, and you don't even need sudo for this.

```

> /proc/acpi/processor/CPU0/throttling

```
this **doesn't** work because the system is attempting to write/redirect that string (6) to a system file as USER, not root.. and you don't have the permissions to edit system files without using sudo.


What you need to do is use the "tee" command..

```

echo 6 | sudo tee -a /proc/acpi/processor/CPU0/throttling

```

that will append the echo'd string (6) to /proc/acpi/processor/CPU0/throttling because you are using the tee command with sudo perms. You can read "man tee" for more info about tee.

This is pretty good.  Is it possbile to append to a file this way?

---

### Post by timbounceback on 2008-03-21
Wow, I learned something new :-D. I never knew that...

---

