---
title: "Owner's Permissions"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by james.ash on 2006-10-20
I have just installed Ubuntu Dapper Drake and everything worked fine except Firefox, I discovered from reading the forums that My NIC probably didn't suport ipv6 so I attempted to disable it by commenting out '#alias net-pf-10 ipv6' from /etc/modprobe.d/aliases and adding 'blacklist ipv6' to /etc/modprobe.d/blacklist

I couldn't save any changes to these files and was given message I could not save changes I was not the owner and didn't have permission.  How do I edit files that I don't have permission for?

I solved the firefox problem by using another method by entering about:config in the address bar and then typing ipv6 in the filter field and double clicking on network.dns.disableIPv6

I tried fooling around with the permissions  but I can't figure out how to give my user root permissions????

---

### Post by christhemonkey on 2006-10-20
You shouldnt give your user root permissions. (big security issues an all) If you still want to do that, then there are howtos on the forums.


To edit these files properly, you should use gksudo or sudo.

```
gksudo gedit /etc/modprobe.d/aliases 
```

Or if you like the command line editing software:
```
sudo vi /etc/modprobe.d/aliases 
```

---

### Post by james.ash on 2006-10-20
I apologize for being a bottomless well of ignorance but how do i use  gksudo? 

is it an application I can open?  I dont see it anywhere in my menu structure


NEVER MIND!  I figured it out, (open terminal, type in: 'gksudo gedit'

---

### Post by Brownedwg89 on 2006-10-20
type ```
gksudo gedit /etc/modprobe.d/aliases
```in terminal

---

### Post by CatKiller on 2006-10-20
> **christhemonkey said:**
> Or if you like the command line editing software:
```
sudo vi /etc/modprobe.d/aliases 
```

Crikey, that's a bit hardcore for a newbie, isn't it? I've seen vi in action, and know a bit about how to work it, but I'm still scared of it. **sudo nano ...** would be my choice, since that's what I generally use.

---

### Post by christhemonkey on 2006-10-21
vi isnt that hard :)

Quit without saving
:q!

Quit with saving
ZZ

Insert text
i

Exit insert
`esc`


All you need to start!



I find nano annoying cos the keyboard shortcuts are different and i have to look up to see them.

---

### Post by CatKiller on 2006-10-21
> **christhemonkey said:**
> vi isnt that hard :)

I find nano annoying cos the keyboard shortcuts are different and i have to look up to see them.

Ah, see, I'm already looking at the screen. I wouldn't recommend vi to a beginner since it's likely to be **so** different to anything they've used before, and all they want to do is edit one line of a text file. Each to their own though, and I won't mention it again.

---

### Post by christhemonkey on 2006-10-22
Fair enough!
Its probably just me being arkward, but anyway, its good that the OP solved their problem, which ever way they did it.

---

