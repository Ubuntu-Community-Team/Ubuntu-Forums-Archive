---
title: "System&gt;Admin&gt;Network&gt;hosts: delete most?"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by JEBB on 2006-03-25
At the end of that path there are a slew of hosts listed. Two are named 'local host...' and the other seven are:  ip6-localnet, ip6-allnodes, ip6-localgist ip6-loopback, ip6-allhosts, ip6-mcastprefix, ip6-allrouters.  What purpose do those last seven serve?  Can I delete them?  

I ask because between entering my password and when the machine is ready to use is several minutes.  It just sits there with a blank dark screen.  

Thanks

---

### Post by dcstar on 2006-03-25
[QUOTE=JEBB]At the end of that path there are a slew of hosts listed. Two are named 'local host...' and the other seven are:  ip6-localnet, ip6-allnodes, ip6-localgist ip6-loopback, ip6-allhosts, ip6-mcastprefix, ip6-allrouters.  What purpose do those last seven serve?  Can I delete them?  

I ask because between entering my password and when the machine is ready to use is several minutes.  It just sits there with a blank dark screen.  

Thanks[/QUOTE]
Don't delete them, just comment them out with the following command:

sudo gedit /etc/hosts

---

### Post by JEBB on 2006-03-25
I don't understand the verb phrase:  'comment them out'.  Can you elaborate please.

---

### Post by trent dillman on 2006-03-25
put a pound sign at the beginning of the line, like so:

```
# whatever you wanted to delete
```

---

