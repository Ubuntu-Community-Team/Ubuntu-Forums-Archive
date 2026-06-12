---
title: "question about handling commandline to update"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by maduranga on 2007-10-17
Hello.. Is it possible to give the update, upgrade and dist-upgrade commands in a single comand? to execute one after the other? 

 what is the difference between upgrade and dist-upgrade? 


 This comes as the result of the command "sudo aptitude upgrade" , what is it? is it normal?

 **W: The "upgrade" command is deprecated; use "safe-upgrade" instead.**


thought of asking some update related question. thanks for replies :)

---

### Post by llamakc on 2007-10-17
Yes.

```

sudo aptitude update && sudo aptitude safe-upgrade

OR

sudo apt-get update && sudo apt-get dist-upgrade


```

---

### Post by jingo811 on 2007-10-17
I don't know the answers to your question but here's a nice way to make Synaptic auto update without bugging you.

```
**System -> Administration -> Software Sources**
Click the updates tab
Click the radio button next to install updates without confirmation.
```

---

### Post by Beggar on 2007-10-17
Im a fan of 

```
update-manager --dist-upgrade
```

---

### Post by ThrobbingBrain66 on 2007-10-17
> **maduranga said:**
> 
 This comes as the result of the command "sudo aptitude upgrade" , what is it? is it normal?

 **W: The "upgrade" command is deprecated; use "safe-upgrade" instead.**

thought of asking some update related question. thanks for replies :)

All the message is saying is that 'aptitude upgrade' isn't recognized as a command anymore

for a regular upgrade you use 'aptitude safe-upgrade'....for a dist-upgrade you use aptitude full-upgrade'

---

### Post by maduranga on 2007-10-18
thank, but still can't understand the difference between upgrade, dist-upgrade, safe-upgrade and now full-upgrade. :confused:

---

### Post by FredB on 2007-10-18
> **jingo811 said:**
> I don't know the answers to your question but here's a nice way to make Synaptic auto update without bugging you.

```
**System -> Administration -> Software Sources**
Click the updates tab
Click the radio button next to install updates without confirmation.
```

Could be an answer. But sometimes, there are updates which are buggy, so...

---

