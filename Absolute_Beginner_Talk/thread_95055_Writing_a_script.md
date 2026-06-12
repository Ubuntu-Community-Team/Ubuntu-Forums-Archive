---
title: "Writing a script"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by etc on 2005-11-25
I'm writing a bash script and I'm using echo to display what's being done.
For example, I want to download the file example.png from example.com
so

```
echo -e "Downloading example.png\n"
wget http://example.com/example.png
```

How would I get it **not** to display the output wget gives, or the output other commands give?  I read the man pages for echo and it seems -n does something like that but I'm not too sure.

---

### Post by Leif on 2005-11-25
redirect to /dev/null, ie

```

wget http://example.com/example.png > /dev/null

```

---

### Post by etc on 2005-11-25
[QUOTE=Leif]redirect to /dev/null, ie

```

wget http://example.com/example.png > /dev/null

```[/QUOTE]
Thanks I'll try that out right now :p
edit: that didn't work, it still came out

```
wget http://www.google.com/intl/en/images/logo.gif > /dev/null
```
throws out
```
--16:31:47--  http://www.google.com/intl/en/images/logo.gif
           => `logo.gif'
Resolving www.google.com... 64.233.161.147, 64.233.161.99, 64.233.161.104
Connecting to www.google.com|64.233.161.147|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,558 (8.4K) [image/gif]

100%[====================================>] 8,558         --.--K/s

16:31:48 (211.64 KB/s) - `logo.gif' saved [8558/8558]

```

---

### Post by wsanders on 2005-11-25
Add -q to the wget command, i.e.
```

wget http://example.com/example.png -q

```

---

