---
title: "Trying to do everything right...so what do I do here..."
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by srusso on 2006-08-29
Ok I am trying to install my ATi drivers perfectly, following this link [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910) as I was advised to in an other post... trying to get this part right 

"Create .deb packages:

Code:

chmod +x ati-driver-installer-8.26.18-x86.run ./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper"

AND I KEEP GETTING THIS....

srusso@Prometheus:~$ chmod +x ati-driver-installer-8.26.18-x86.run
chmod: cannot access `ati-driver-installer-8.26.18-x86.run': No such file or directory

How do I get that to point to the file on my desktop?:-k

---

### Post by Jagot on 2006-08-29
This shouold do it:

```
chmod +x /home/srusso/Deskop/ati-driver-installer-8.26.18-x86.run
```

---

### Post by cstudent on 2006-08-29
They are two separate commands
```

chmod +x ati-driver-installer-8.26.18-x86.run

```
```

./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper

```

---

### Post by croak77 on 2006-08-29
I type slow.

---

### Post by srusso on 2006-08-29
This is what I get...

srusso@Prometheus:~$ chmod +x/home/srusso/Desktop/ati-driver-installer-8.28.8.run

chmod: missing operand after `+x/home/srusso/Desktop/ati-driver-installer-8.28.8.run'
Try `chmod --help' for more information.

---

### Post by Jagot on 2006-08-29
You need to leave a space between the +x and /home . . . .

---

