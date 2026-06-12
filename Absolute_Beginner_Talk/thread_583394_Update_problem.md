---
title: "Update problem"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by alb@nian on 2007-10-20
I have a problem auto update , when I was installing the updates I've got an power system break down. After I restarted and tried to began it again it says:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Please, some advice :(

---

### Post by Daveth on 2007-10-20
paste

```
dpkg --configure -a
```

into a terminal, then enter and off you go. You find a terminal by Applications/accessories/terminal

---

### Post by alb@nian on 2007-10-20
Why it showing me this:

```
dpkg: requested operation requires superuser privilege
```

I have only one user and is this one I'm using.

---

### Post by NilsE on 2007-10-20
put sudo in front of the command to gain root permissions for that function
```

sudo dpkg --configure -a
```

---

### Post by dhruva023 on 2007-10-20
its because you have to became root to run that command.

type this.

```

sudo dpkg --configure -a


```

it will ask for password.  enter it. (remember you can not see password in terminal )

---

### Post by Daveth on 2007-10-20
yes, sorry- forgot to sudo my post:(

---

### Post by alb@nian on 2007-10-20
I thought I tried that :confused:, it's working now thnx.

---

