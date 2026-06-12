---
title: "How to change machne name?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-04-21
Hi - sorry to ask another such basic question, but I'm afraid of doing the wrong thing and messing up my machine and network.

I have Ubuntu machines on a home network, and would like to give them more meaningful (to me!) names.

So, if one of the machines is called 'Den', how do I change that to, say, 'Athens.'?

Can I do it by making a single simple change somewhere, or will I have to edit multiple files or something?

(I know that when I change the name I'll also have to amend the hosts file on the other computers - but how DO I change the name?

Thanks!

---

### Post by Bachstelze on 2007-04-21
```
sudo -i
hostname Athens
echo "Athens" > /etc/hostname
nano -w /etc/hosts
```

and replace all occurrences of the old hostname with the new one.

---

