---
title: "creating .jar files"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by sponsoredwalk on 2008-03-29
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/28369](https://answers.launchpad.net/ubuntu/+question/28369) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi i am on Ubuntu Gutsy and i am wondering if it is possible to create a .jar file containing text so that i could put it on my phone, i.e. a full book on my phone([www.manybooks.net](www.manybooks.net) is a site that makes this possible). On this site there are thousands of books which can be downloaded in .jar form and i can read them on my phone but i want to be able to make my own ones. On the site it gives a program but it doesn't function under wine because it needs to use microsoft word and there is absolutely no way to alter it from initialising microsoft word and it fails. I have checked google and i have no idea about manifest files etc and cannot find any help, I hope you can help as i would love to put study notes etc on my phone as well to study during (boring) work. Thanx!!!

---

### Post by bswilson on 2008-03-29
A *.jar file is simply a Java Archive.  In fact, there's nothing special about it at all.  It is simply a ZIP file with a different extension.  I downloaded one of the eBooks from the site you referenced.  I simply renamed the file extension from *.jar to *.zip, and you can open it with any program that can read a ZIP file.

Next, I looked inside the archive; the book seems to be broken down into individual *.dat files that contact ASCII text.

I suppose all you need to do is create a text document, save it with a *.dat extension, then compress it and rename the file to have a *.jar extension.  Try this to test if it creates a file that works on your iPhone:

```
$ cat /etc/passwd > foo.dat && gzip -S .jar foo.dat
```

Assuming it does, you can create any kind of text file, compress it with a *.jar extension and drop it onto your iPhone.

---

