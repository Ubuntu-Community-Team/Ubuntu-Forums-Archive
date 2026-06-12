---
title: "How do I Shut Down?"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by charlie. on 2006-04-24
As my first post to this forum, ever, I have prepared a really unique question that must set new records for first posts: **How do I shut Down...** from the terminal?

I know that there is the 'shutdown' command and that it must be run as root. This is what I did:

sudo -i
<my password>

This gave me an interactive root terminal, similar to su.

shutdown --help | less

Gave me some help. After reading this, I decided to...

shutdown -hn now
... and several variations of above ...

Alas, that only replayed the help message.

Please... excuse the pun... then... HELP!

---

### Post by mostwanted on 2006-04-24
To shut down:

```
sudo halt
```

To reboot:

```
sudo reboot
```

---

### Post by uzi09 on 2006-04-24
if you would like to use the shutdown command, you can do it the following ways:

reboot: sudo shutdown -r now
(u can also sub in 0 (zero) for now or put some other time, like +10 for 10 minutes later)

shutdown: sudo shutdown -hP now
-h = halts computer (remember the good ol' days with win95 where that nice orange text would come up saying "It is now safe for you to turn off your computer" - this is pretty much what this does)
-P = turn power off after halting

u can see shutdown --help for more info - or man shutdown for even more :D

good luck
uzi

---

### Post by charlie. on 2006-04-24
Thanks all.

'halt' and 'reboot' are nice.

I tried both 'man shutdown' and 'shutdown --help', although only the last one was mentioned in my post. The documentation that was printed gave the impression that '-n' was the switch to use to set the shutdown timer, and '-r' for restart. In my mind, that means '-rn' should have worked.

No matter, all is well now.

---

