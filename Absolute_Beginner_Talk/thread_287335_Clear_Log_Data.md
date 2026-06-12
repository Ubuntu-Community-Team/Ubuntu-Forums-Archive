---
title: "Clear Log Data"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by doconnor on 2006-10-28
How do you safely clear out the info in log files, in particular the ones that would be in /var/log?  I found one place that said "> /var/log/sylog".  When I tried this I got a message that said I was not authorized.  I tried using sudo without any luck.
Thanks,
Dale

---

### Post by whizbaby on 2006-10-28
So what did you try?

---

### Post by doconnor on 2006-10-28
I tried "> /var/log/sylog" from a terminal window.  Then I tried "sudo > /var/log/sylog".  I also tried a couple of other log files.  

I don't know much about Linux.  What I found said to clear your log do this: "> /var/adm/sylog".  

I am trying to clear out enough in /var to do a distribution upgrade instead of a complete reinstall. I will probably wind up increasing the size of /var and doing a complete reinstall.
Thanks,
Dale

---

### Post by taurus on 2006-10-28
```

sudo cat /dev/null > /var/log/syslog
sudo cat /dev/null > /var/log/messages
...

```

---

### Post by dillbertdabomb on 2006-10-28
logs are important! don't delete them, if you have a problem they could have important info in them!

---

### Post by whizbaby on 2006-10-29
> **doconnor said:**
> I am trying to clear out enough in /var to do a distribution upgrade instead of a complete reinstall.
No need to do that for a distributio upgrade. Leave /var alone as long as you don't know what you're doing.

---

### Post by speje on 2006-12-06
> **taurus said:**
> ```

sudo cat /dev/null > /var/log/syslog
sudo cat /dev/null > /var/log/messages
...

```

tried that, didnt work, reply:

"bash: /var/log/syslog: Permission denied"

---

### Post by taurus on 2006-12-06
> **speje said:**
> tried that, didnt work, reply:

"bash: /var/log/syslog: Permission denied"
Did you run it with the sudo in front?

---

### Post by whizbaby on 2006-12-06
That can't work because sudo only influences the cat command (in what you wrote before) and "> ..." has no root privileges. Type

sudo xterm

and then in the new terminal again the commands without sudo in front of 'em. 
But don't do it since clearing out logs is silly.

---

### Post by speje on 2006-12-06
> **whizbaby said:**
> That can't work because sudo only influences the cat command (in what you wrote before) and "> ..." has no root privileges. Type

sudo xterm

and then in the new terminal again the commands without sudo in front of 'em. 
But don't do it since clearing out logs is silly.

that worked - thank U all

I use it for some debugging, it gets kinda big - so need to clear it.

---

