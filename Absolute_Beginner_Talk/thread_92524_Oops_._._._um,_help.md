---
title: "Oops . . . um, help?"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by Rumor on 2005-11-19
Hello all:

Let's see, less than 24 hours of being windows free but I've borked something good.

I have 3 computers on my home network, two windows XP Pro boxes and my Ubuntu machine. Our printer (HP DeskJet 895Cse) is connected to the computer running Ubuntu. Todayt I tried to share the printer. I got as far as the other computers being able to see it, but they got the message "access denied."

In my efforts to grant them access, I have managed to make my cups server unavailable to myself. When I click System | Administration | Printing, I get the message, " The CUPS server could not be contacted."
When I try to browse it in my web browser, I get the message, "The connection was refused when attempting to contact localhost:631

So, I have two questions:

1) How do I get the printer back on the Ubuntu machine?

2) How do I share the printer so that the two windows XP machines can use it?

Thanks for any help you can give me.

---

### Post by suRoot on 2005-11-19
[QUOTE=Rumor]
1) How do I get the printer back on the Ubuntu machine?
[/quote]

Try

```
sudo /etc/init.d/cupsys restart
```

Failing that working, you will need to look at the logs to determine the nature of the problem.

```
less /var/log/cups/error_log
```

[QUOTE=Rumor]
2) How do I share the printer so that the two windows XP machines can use it?
[/QUOTE]

Maybe this thread will help you:

[http://ubuntuforums.org/showthread.php?t=61863&highlight=share+printer]("http://ubuntuforums.org/showthread.php?t=61863&highlight=share+printer")

---

### Post by Rumor on 2005-11-20
[QUOTE=suRoot]Try

Maybe this thread will help you:

[http://ubuntuforums.org/showthread.php?t=61863&highlight=share+printer]("http://ubuntuforums.org/showthread.php?t=61863&highlight=share+printer")[/QUOTE]

That did the trick, thanks!

---

### Post by niceguy123 on 2008-02-13
[QUOTE=suRoot;505512]Try

```
sudo /etc/init.d/cupsys restart
```

Failing that working, you will need to look at the logs to determine the nature of the problem.

```
less /var/log/cups/error_log
```

My printer box is not coming up. I have tried the above but still not working.

When I try system>administration>printers at first I see the printers box on the bottom bar as if the printers is opening but then it just disappears. 

Any ideas?

---

