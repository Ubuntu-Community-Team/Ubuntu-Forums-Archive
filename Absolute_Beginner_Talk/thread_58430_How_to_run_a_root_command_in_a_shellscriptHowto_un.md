---
title: "How to run a root command in a shellscript?/Howto unmount nfs before standby?"
date: 2005-08-20
forum: Absolute Beginner Talk
---

### Post by coaxx on 2005-08-20
Hi
I have a working Suspend to RAM function here with Hoary, but I want to unmount all network filesystems specified in fstab before going to sleep. I noticed the prepare.sh script in /etc/acpi.

Now for unmounting all network filesystems I want to run

```

/etc/rc0.d/S31umountnfs.sh

```

But this command is root only. I tried 

```

sudo /etc/rc0.d/S31umountnfs.sh

```
but it does not work because sudo asks for a password.

Is there any other way to run root-commands (scripts) in a user script?

many thanks for some examples/hints

cheers!
coaxx

---

### Post by nad on 2005-08-20
I think what you wish to do is unmount all network file systems listed in mtab.

Provided that you have permission to unmount the file systems, write a script to do so.

You may use the umount script as a reference, but, any action requiring permission of another user will fail when run as you. Playing with permissions is dangerous to your system and setting suid and/or guid is a security hazard.

---

### Post by poofyhairguy on 2005-08-21
[QUOTE=coaxx]Hi
I have a working Suspend to RAM function here with Hoary, but I want to unmount all network filesystems specified in fstab before going to sleep. I noticed the prepare.sh script in /etc/acpi.

Now for unmounting all network filesystems I want to run

```

/etc/rc0.d/S31umountnfs.sh

```

But this command is root only. I tried 

```

sudo /etc/rc0.d/S31umountnfs.sh

```
but it does not work because sudo asks for a password.

Is there any other way to run root-commands (scripts) in a user script?

many thanks for some examples/hints

cheers!
coaxx[/QUOTE]


Create a root user:

[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

---

### Post by rajsarkar on 2005-09-20
Yeah, if you don't know what you are doing pls do not proceed. Have a look at "ubuntuguide" (url given in the previous post). Most of your answers will be available there.

-Raj

---

