---
title: "net view equivalent"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-04-11
What is the shell command that is the equivalent to "net view" in DOS?  I want to see all the other PCs on my network through the shell by name or IP; it doesn't matter which but i prefer by IP.  Thanks.

---

### Post by cwaldbieser on 2006-04-11
[QUOTE=echo $USER]What is the shell command that is the equivalent to "net view" in DOS?  I want to see all the other PCs on my network through the shell by name or IP; it doesn't matter which but i prefer by IP.  Thanks.[/QUOTE]
You could do it with "fping".  For example, on a 192.168.0.0/24 network, this shows me the IP address of all hosts that respond to the ping:
```

$ fping -c 1 -g 192.168.0.0/24 2> /dev/null

```

---

### Post by echo $USER on 2006-04-12
[QUOTE=cwaldbieser]You could do it with "fping".  For example, on a 192.168.0.0/24 network, this shows me the IP address of all hosts that respond to the ping:
```

$ fping -c 1 -g 192.168.0.0/24 2> /dev/null

```[/QUOTE]

Thanks, but what does this part do "2> /dev/null"?

---

### Post by xenmax on 2006-04-12
>  Thanks, but what does this part do "2> /dev/null"?
This routes the STDERR - standard error output to /dev/null, which in my [minimal] knowledge is like a vortex which gobbles up everthing without a trace - it does not display on terminal nor is it stored to any file

---

### Post by echo $USER on 2006-04-12
Thanks xenmax.

---

