---
title: "Dual-boot question: What's in a name?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by obform on 2008-01-02
A nervous newbie question I couldn't find answered in other threads...

I ran Gutsy live on an ancient (and otherwise unused) Dell laptop, liked what I saw, and am now preparing to make my newer Windows XP machine dual-boot. As I read tutorials, I see that Ubuntu will ask for a machine name.  Should it be the same as the Windows machine name, i.e. referring to the box, or should it be different, i.e. referring to the OS installation/Ubuntu half of the machine?

I searched for "machine name dual boot install" and didn't find anything. If I've missed something in existing threads, please forgive, and point me there.

Thanks,
--obform

---

### Post by thelatinist on 2008-01-02
Set it to whatever you like.  The values don't need to match, but can if you like.

---

### Post by LowSky on 2008-01-02
name it Billy, Sebastian or Frog, it doesn't matter. Name it what ever ypou want

---

### Post by meborc on 2008-01-02
i call my computer "drizzt" ... i also have "snow" and "bpos"

:) the name is just a nic you give your computer... that is what will show up when you connect to other computers via lan... and that is what will show up in your terminal

mine could look like this:

meborc@drizzt:

so don't make it long... make it short and funny

---

### Post by PeterJS on 2008-01-02
And you can earn nerd street cred if you have a clever name or coherent theme of names for multiple machines. My first dual boot was named Janus, still amuses me.

---

### Post by obform on 2008-01-02
So if they don't need to match, does that mean that the two halves are separate machines in some important sense?

--obform

---

### Post by bindatype on 2008-01-02
It should be noted that you can always change the hostname (which is precise name for what we are talking about) later on. And refrain from using periods in the hostname.

---

### Post by PeterJS on 2008-01-02
It's the name other machines on the network will use to referrer to the machine, for file sharing and things like that. Having them named different may make it convenient for file shares, so that you know that if you can connect with a given name that a share will be there. As a point of historical consideration, dual booting is a relatively new concept, for most of this history of computing there has been a one to one correspondence of name to physical device. It's not required but is convenient knowing that the name xyz refers to the machine that is physically sitting under my desk regardless of th OS loaded.

Long story short having the host names match isn't required but is a historical it's always been done that way, but I'm sure if you thought long enough about it you could find a good reason to give each OS a separate host name.

---

### Post by Daveski on 2008-01-02
> **obform said:**
> So if they don't need to match, does that mean that the two halves are separate machines in some important sense?

Yup. A dual boot machine is just like two seperate machines although they CAN share data. With a dual boot you will never be running both OSes at the same time. If you were to invert Windows and use it as a virtual machine INSIDE Linux, then although they are still seperate machines, they will probably be networked - in this case you probably do NOT want the host names to be the same.

---

### Post by dstew on 2008-01-02
> So if they don't need to match, does that mean that the two halves are separate machines in some important sense?To be correct, you would say that two different *systems* can run on the same *hardware*. To some people, the word "machine" means hardware.

---

