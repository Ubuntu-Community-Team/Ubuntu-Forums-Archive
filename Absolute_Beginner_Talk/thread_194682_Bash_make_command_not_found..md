---
title: "Bash: make command not found."
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by acorn22 on 2006-06-11
Title really says it all. I am using dapper and am trying to get ndiswrapper make'd and stuff, but i gt this error. I have tried sudo as well. I tried to go on without doing that step, thinking it must have already been done or something. That didn't work.

---

### Post by 23meg on 2006-06-11
Install the package "build-essential".

---

### Post by acorn22 on 2006-06-11
how?

---

### Post by 23meg on 2006-06-11
```
sudo apt-get install build-essential
```

---

### Post by acorn22 on 2006-06-11
```
E: couldn't find pakage build
```

---

### Post by 23meg on 2006-06-11
Don't forget the "**-**"; it's "**build-essential**". Just copy and paste the command in my last post.

---

### Post by acorn22 on 2006-06-11
sorry, im doing this on my iBook and linux is on my PC

ok that did not work ```
e: couldn't find package build-essential
```

---

### Post by acorn22 on 2006-06-11
ok i just did it like 3 times in a row (up arrow enter) and now it's working.

---

### Post by acorn22 on 2006-06-11
okay, now ndiswrapper is working

oh, and I neede the cd i think (for anyone elses reading this) to copy files from

---

### Post by acorn22 on 2006-06-11
I guess it did not all work. I didn't notice before, but it says ```
can't find the kernel build files in /lib..
```

Is there something I am still mising? (that goes in this lib/modules/... folder?

---

### Post by taurus on 2006-06-11
You need to install linxu-headers for your kernel...  You can use synaptic to search for it and make sure you use the same version that you are running right now.  If you are not sure which version of kernel you are using right now, type this command at the prompt and it will tell you.
```

uname -r

```

---

