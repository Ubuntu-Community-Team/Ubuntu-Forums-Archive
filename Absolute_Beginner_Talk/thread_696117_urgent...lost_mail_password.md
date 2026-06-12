---
title: "urgent...lost mail password"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-02-13
hi i changed my password yesterday but i cannot remember it....but pigdin remembers it:)
i also changed secret question so this is not an option...
..so is there any way to recover the password from pigdin like removing the stars or doing something else?

---

### Post by Blutack on 2008-02-13
Go into nautilus (file browser).
Press Control-H to show hidden files/folders.
Go into the .purple folder and open accounts.xml.
Find the correct account and the password will be listed in clear text.

---

### Post by nemilar on 2008-02-13
The above will work, or from the command line you can use:

```
cat ~/.purple/accounts.xml | grep password
```

Which will show you the stored passwords for pidgin.  If you have multiple accounts, and you wanna get really fancy about it, you can use:

```
cat ~/.purple/accounts.xml | grep [your account name] -A 1
```

so for eaxmple:

```
cat ~/.purple/accounts.xml | grep nemilar -A 1
```

Which will output:

```
                <name>nemilar</name>
                <password>[my password appears here]</password>

```

---

### Post by someoneouthere on 2008-02-13
thanks that was really helpful :):guitar:

---

