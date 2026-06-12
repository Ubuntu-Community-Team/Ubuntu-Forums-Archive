---
title: "checkgmail error"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-10-19
when i run checkgmail, i always get the following error:
```
Error: 500 Can't connect to www.google.com:443 (Bad hostname 'www.google.com')
```

anyone know what this is about?

thanks,
-steve

---

### Post by ReaderRat on 2006-10-19
Shouldn't the hostname be :  **[www.gmail.com](www.gmail.com)**   ??

---

### Post by stevieb on 2006-10-20
i know; you'd think so, right?  how do i change that?  there doesn't seem to be anywhere to do that in the settings dialog box.

thanks,
-steve

---

### Post by jqk on 2006-10-20
Use, this command on terminal:

sudo apt-get install kcheckgmail

Password: *****

Where *****, should be your root password.

---

### Post by srafx on 2006-10-30
> **stevieb said:**
> when i run checkgmail, i always get the following error:
```
Error: 500 Can't connect to www.google.com:443 (Bad hostname 'www.google.com')
```

anyone know what this is about?

thanks,
-steve

I have the same problem.  Its caused on my end because i run wirless and checkgmail starts before the wireless does.  If you exit out of checkgmail, make sure you have an internet connection, then launch checkgmail again (ALT F2)...if should then run fine. :)

---

### Post by batigolix on 2006-11-12
since a couple of days checkgmail stopped showing ne messages. all seems to work well except recognizing new messages (at the end of the day the main function of checkgmail).

i tried to see if it had to do with the problem of loading checkgmail before loading the wirelss, but that is not the case

when i run it in verbose mode i see no errors, only messages regarding cookies.

---

### Post by krige on 2007-05-04
I have the same problem. I am connected through a wired connection and anyway I start checkgmail manually.

---

