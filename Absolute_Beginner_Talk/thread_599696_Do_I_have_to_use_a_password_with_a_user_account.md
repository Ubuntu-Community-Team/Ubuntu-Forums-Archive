---
title: "Do I have to use a password with a user account?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by jolt459 on 2007-11-01
I have recently installed Ubuntu, and somebody in my family would like to have there own account. The trouble is, they really don't need or want a password. It's just a pain for them to have to type it in, I so what I'm asking is there a way to by-pass using a password? Thanks.

---

### Post by Pumalite on 2007-11-01
As far as I know every user has a password.That's the beauty of Linux. You can have one computer and thousands of users, each one keeping his stuff separate.

---

### Post by n3tfury on 2007-11-01
i don't think there's a way to circumvent that, but even if there was, i would advise against it.  have the lazy user stay logged in then.

---

### Post by Paqman on 2007-11-01
You can set it to automatically log a user in without prompting for a password. After that they should only be prompted if they try to administer the system (which i'm assuming you'd lock them out of anyway)

---

### Post by Shiva88 on 2007-11-01
I don't think Ubuntu protects against weak passwords, does it?  Why not just use something extremely simple... say, "pass" for the password?  This would create minimum hassle while still preserving some degree of security.

---

### Post by steve.horsley on 2007-11-01
I don't know how to set a blank password, but I know how to set a one-letter password if you really must (I don't advise it if your machine is connected to the internet). Just use the command **sudo passwd username**. You will be prompted for your own password, then the new users password. This bypasses the normal checks for password strength.

---

### Post by Kitsun on 2007-11-01
IMHO someone who doesn't want to deal with passwords shouldn't be using a computer.

Kinda like living in a house and not wanting to deal with keys.

---

### Post by n3tfury on 2007-11-01
> **Kitsun said:**
> IMHO someone who doesn't want to deal with passwords shouldn't be using a computer.

Kinda like living in a house and not wanting to deal with keys.

quoted for future sig.

---

### Post by sloe on 2007-11-01
In my quick testing, no, a password is required.  I tried manually updating /etc/passwd and /etc/shadow, but it wouldn't let me in even with no password.

There are some advanced techniques to do this, but you're basically disabling the security of your box by doing so.  Have this individual pick a pw that's easy to type, and tell them to deal with it.  It only has to be 6 characters.

-sloe

---

### Post by brownbat on 2007-11-01
"As far as I know every user has a password.That's the beauty of Linux."

Increased security is a huge plus, but another beautiful thing about linux is user choice. In that light, you might try this approach, which I lifted from another topic:

> **Skrynesaver said:**
> 
```

sudo useradd  -m -c "Guest user" -d /home/guest  -s /bin/bash guest
sudo passwd guest

```
enter a password twice, now 
```

passwd -d guest

```


That last command, the "passwd -d guest" seems key.

---

