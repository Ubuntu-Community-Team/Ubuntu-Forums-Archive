---
title: "Problem mount harddrive"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Malekay on 2006-10-23
I have two SATA disks that I just can´t figure out how to mount. In he filebrowser I don´t have the permission.
The two disks are emty, so there´s nothing to worry about.
I will be happy for help.
mvh /Malekay

---

### Post by jorn on 2006-10-23
Are they windows partitions?
Or linux?
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by lloyd_b on 2006-10-23
> I have two SATA disks that I just can´t figure out how to mount. In he filebrowser I don´t have the permission.
The two disks are emty, so there´s nothing to worry about.
I will be happy for help.

Um, if the disks are blank, then you won't be able to mount them.  They have to be partitioned and formatted first....

Lloyd B.

---

### Post by Ben Sprinkle on 2006-10-23
```

sudo mount -o loop <hda>
```
Try.

---

### Post by Malekay on 2006-10-23
I&#314;l try your guy&#347; tips and nothing happens.
My problem is that I don´t know how to explain for ubuntu that Im a superuser and want to mount that disk.
They are both linux disks btw.

---

### Post by CatKiller on 2006-10-23
You tell it that you want to run a command as superuser by using "**sudo**" before the command (**s**uper**u**ser **do**). You tell it that you want to mount a partition into the filesystem by using the "**mount**" command. There is a lot of information on this forum about both of them.

---

### Post by Malekay on 2006-10-23
> **CatKiller said:**
> You tell it that you want to run a command as superuser by using "**sudo**" before the command (**s**uper**u**ser **do**). You tell it that you want to mount a partition into the filesystem by using the "**mount**" command. There is a lot of information on this forum about both of them.

Yes that&#347; right. The thing is that I can´t find the answer .. not even here.

---

### Post by Malekay on 2006-10-23
> **synectics said:**
> ```

sudo mount -o loop <hda>
```
Try.

bash: syntax error near unexpected token `newline'

That&#347; what I get.

---

### Post by Ben Sprinkle on 2006-10-24
```

sudo mount -o loop <hda> <hda-where-will-be-mounted>
```
Sorry.

---

