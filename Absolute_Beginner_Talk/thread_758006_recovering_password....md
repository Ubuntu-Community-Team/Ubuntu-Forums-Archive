---
title: "recovering password..."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by phydreamer on 2008-04-17
tring to restore my main password i found the "standard" way..
i am curius what other ways are for that kind of job???

---

### Post by LowSky on 2008-04-17
got to love google: [http://www.google.com/search?hl=en&q=reset+password+ubuntu](http://www.google.com/search?hl=en&q=reset+password+ubuntu)

but i fing this to be the easiest way 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by phydreamer on 2008-04-17
how about recovering a password without reseting it is this possible?

---

### Post by spiderbatdad on 2008-04-17
Yes. I believe this will work. Boot into recovery mode. In the terminal enter:```
passwd username -d
```
This will delete the user's password.
Then run:```
passwd username
``` To set a new password for the user. "username" is to be substituted with the actual username.

---

### Post by bodhi.zazen on 2008-04-17
> **phydreamer said:**
> how about recovering a password without reseting it is this possible?

Not directly.

Indirectly there are certain techniques that we know ...

---

### Post by phydreamer on 2008-04-17
> **bodhi.zazen said:**
> Not directly.

Indirectly there are certain techniques that we know ...

hmm i am asking because i suspect to be a "victim" could you give some details?

---

### Post by bodhi.zazen on 2008-04-17
Google will give you all the details you need.

I do not want to appear to be encouraging cracking on these forums.

---

### Post by spiderbatdad on 2008-04-17
There is no magic command that will decode your password. It is encoded with a one-way algorithm. It is not impossible to crack..but difficult. It can be virtually impossible if you use a strong password...minimum of 8 characters, mixing upper/lower case letters and numbers, and symbols. Other vulnerabilities aside, such as rootkits and forms of social-engineering that allows malicious users to capture your keyboard activity...This is best prevented by only downloading trusted software, and keeping ports closed.

---

### Post by phydreamer on 2008-04-17
> **spiderbatdad said:**
> There is no magic command that will decode your password. It is encoded with a one-way algorithm. It is not impossible to crack..but difficult. It can be virtually impossible if you use a strong password...mixing upper/lower case letters and numbers, and symbols.

ok but is there any way to encrypted a bit more?

---

### Post by nhandler on 2008-04-17
There is a package in the official Ubuntu repositories that can accomplish this. Since it is in the repositories, I don't feel that I am violating any rules. If a mod/admin feels differently, feel free to edit/delete this post.

The package you want is called "john", which is short for "John the Ripper". It can use either brute force or a wordlist to attempt to crack the passwords of the users on the computer. John also has many other uses.

I won't explain how to use john here (That would be taking me into a shady area), but a google search should give you all the info you need.

---

### Post by spiderbatdad on 2008-04-17
Yeah if "dog" is your password...watch out for john the ripper....```
man john
```gives you all the information you need.

---

### Post by phydreamer on 2008-04-17
i meant to encrypt the password a bit more....

---

### Post by spiderbatdad on 2008-04-17
I believe you can tell the kernel to use a different hash method of encryption, but the one used is very secure. ```
man passwd
```

---

