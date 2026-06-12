---
title: "USB Thumb Drive Owner - can't change"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by mikex on 2007-08-22
I'm stuck. On my external USB hard drive, I used gparted to reformat, re-partion, and also re-assign permissions, such as the owner, all worked.

On my USB thumb drive, I cannot change the Owner no matter what I try. I did gksudo and went to the /media dir, and tried to change the owner there - refused. How can root be refused anything? I then deleted the partition on the thumb drive (everything) re-partitioned, reformatted, and it still has the same name as the owner as before, and refuses root to change the name. I even tried chown command.  Why can't I change the owner as easily as I can the external USB HD? I think this device is owning me!

---

### Post by Jimmyfj on 2007-08-22
Have you tried:

sudo chown -R USERNAME:USERNAME /media/devicename ?

---

### Post by mikex on 2007-08-22
> **Jimmyfj said:**
> Have you tried:

sudo chown -R USERNAME:USERNAME /media/devicename ?

I did do that but with out a -R, does that matter? Why won't going in as gksudo nautilus allow me to change the owner?

---

### Post by schorsch on 2007-08-22
What is the output of
```
mount
```

---

### Post by mikex on 2007-08-22
> **schorsch said:**
> What is the output of
```
mount
```

I'm at work now, so can't test that. Can you give me a short list of things to try later?

---

### Post by schorsch on 2007-08-22
Right at the moment I would guess it is some kind of filesystem problem. But I cannot give you a list right now .... sorry

---

### Post by mikex on 2007-08-22
> **schorsch said:**
> Right at the moment I would guess it is some kind of filesystem problem. But I cannot give you a list right now .... sorry

Yea that's why I nuked the whole drive and repartitioned, reformatted, etc. I don't get it. But do you guys agree I should have been able to change the owner the way I did it. I guess at least that will tell me I wasn't doing a dumb thing, it just didn't work due to a hardware problem.

---

### Post by Jimmyfj on 2007-08-22
-R, --recursive        operate on files and directories recursively

 I found an extensive explanation  for the command here:

[http://www.opengroup.org/onlinepubs/009695399/functions/chown.html](http://www.opengroup.org/onlinepubs/009695399/functions/chown.html)

---

