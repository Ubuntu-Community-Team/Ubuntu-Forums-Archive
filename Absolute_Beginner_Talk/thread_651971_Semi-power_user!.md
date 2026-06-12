---
title: "Semi-power user?!"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by burpsmirk on 2007-12-28
Not been getting much luck searching for this. If anyone can point me in the right direction or impart some wisdom, I'd really appreciate it...

I want to add a user to Ubuntu (my partners kid) that will have the ability to install applications they have downloaded, but I do not want them to have complete root access to delete serious/important system files.

How would I go about this? If there is a group already built into Ubuntu that allows this, how does it work?

Cheers

---

### Post by bapoumba on 2007-12-28
Not such a group, as far as I know.
You'll probably have to create a special group and tweak the **/etc/sudoers** file:
[http://linux.die.net/man/5/sudoers]("http://linux.die.net/man/5/sudoers")

---

### Post by burpsmirk on 2007-12-28
Cheers bapoumba.

I hadn't realised it would be such a hack. I thought the kind of security functionality I required was what Linux did best. But then, I suppose in it's own way, it is..! :confused:

---

### Post by LaRoza on 2007-12-28
> **burpsmirk said:**
> Cheers bapoumba.

I hadn't realised it would be such a hack. I thought the kind of security functionality I required was what Linux did best. But then, I suppose in it's own way, it is..! :confused:

You are asking if you can let someone selectively alter the system and expect Linux to be able to know the intent of the user. Linux isn't a mind reader. It does what you tell it to.

---

### Post by burpsmirk on 2007-12-28
I agree, but I'd have thought there would be a clear divide between installing software and modifying hardware, drivers, the kernel, startup applications, services, etc.

---

