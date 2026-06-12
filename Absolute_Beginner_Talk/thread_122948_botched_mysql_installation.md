---
title: "botched mysql installation"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by holiday on 2006-01-28
I did this 

sudo apt-get install mysql-client-4.1 mysql-server-4.1

I came back to find a postfix installation dialog that i didn't want to deal with. I really just wanted a little local mysql db and I didn't see an option that would give me that. So I cancelled. 

Now I can't even remove the botched installation. 

apt-get remove fails with 
```

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mailx: Depends: postfix but it is not going to be installed or
                  mail-transport-agent
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

and apt-get -f install gets
```

dpkg: error processing /var/cache/apt/archives/postfix_2.2.4-1ubuntu2_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_2.2.4-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I guess I'll have to manually remove the installation. 

How do I do that? Or is there another solution?

---

### Post by kcr on 2006-01-28
This may be an over simplification but I'd try

```
apt-get remove mailx
```

or 

```
apt-get remove postfix
```

and then try reinstalling them if you need them after you get mysql working - there is probably a neater way to do it but.

---

