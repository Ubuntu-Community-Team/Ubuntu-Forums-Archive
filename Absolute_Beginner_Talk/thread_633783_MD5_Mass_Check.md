---
title: "MD5 Mass Check"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-12-06
hey all,

I know there are multiple threads out there on how to check MD5 checksums of 1 or 2 files but is there a way I can do it for multiple fiiles (err lots lol) and then (of course not manually) check if the sums match

thanks in advance

im new to ubuntu and lovin it ^_^

---

### Post by MikeBenza on 2007-12-06
You can run the following code:

```

cd /to/where/your/files/are/
openssl md5 ./* > /tmp/my.md5s.txt
```

That will produce a list of md5 checksums in my.md5s.txt (which will be placed in the /tmp/ directory).  Find your other set of files and do the same, but instead of using /tmp/my.md5s.txt use something like /tmp/otherset.md5s.txt

Now you'll have two files with two lists of md5s for two sets of files, which hopefully are the same.

The most basic tool for comparing two files is *diff*.  However, it's output is a real pain to read, so I suggest a graphical tool called *meld*.  You can install it with:
```
sudo aptitude install meld
```

You can now run
```

meld /tmp/my.md5s.txt /tmp/otherset.md5s.txt

```

You can of course try it with *diff* instead.

- Mike

---

### Post by bodhi.zazen on 2007-12-06
put the md5 sums in a file "foo"

Make sure you have the correct format, you can 

md5sum file_to_check >> foo

put foo in the same directory as all your files

then

```
md5sum -c foo
```

[http://ubuntuforums.org/showthread.php?t=290339&highlight=md5sum](http://ubuntuforums.org/showthread.php?t=290339&highlight=md5sum)

---

### Post by JasonBourneLinux on 2007-12-07
thanks!

---

