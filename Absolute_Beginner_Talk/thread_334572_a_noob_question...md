---
title: "a noob question.."
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by Fastball on 2007-01-09
how to unpack? thx :mrgreen:

---

### Post by sardion on 2007-01-09
What do you mean by "unpack"?

Are you talking about like zip files or .tgz or .tar.gz ?

If so, you should be able to just double-click on them.

---

### Post by Fastball on 2007-01-09
its the tar.gz one..

---

### Post by xyz on 2007-01-09
> **Fastball said:**
> its the tar.gz one..
Hi,
Try this:
[Tag: Install Targz]("http://wordpress.com/tag/install-targz/") and find out about more stuff as well.

It's too bad that the [How to install Anything]("http://monkeyblog.org/ubuntu/installing") link's been down for a while now!!

---

### Post by Fastball on 2007-01-09
thanks!

---

### Post by Ben Sprinkle on 2007-01-09
```

sudo tar -xvf package.tar.gz

```
;)

---

### Post by az on 2007-01-09
> **Goat Spirit said:**
> ```

sudo tar -xvf package.tar.gz

```
;)

Don't use sudo to unzip - you will end up having to use sudo to delete the directory it creates!  Use sudo to install the software, if you need to.  Otherwise, you can install it as your user in your home folder.  That is often more secure since we are not dealing with an application from the repositories.

---

### Post by Toxicity999 on 2007-01-09
Just double clicking on the file will start KDEs or Gnomes default archive tool.

---

### Post by Ben Sprinkle on 2007-01-09
> **azz said:**
> Don't use sudo to unzip - you will end up having to use sudo to delete the directory it creates!  Use sudo to install the software, if you need to.  Otherwise, you can install it as your user in your home folder.  That is often more secure since we are not dealing with an application from the repositories.

It doesn't create a folder unless it already has a folder zipped inside of it. Plus what if you are in / or something and need to extract?
I think if people are going to mess up thier system, that's their fault. They should just watch what directory and things they are in and they will be fine, I mean, how can you 'accidently delete ubuntu' lol. ;)

---

### Post by Sunflower1970 on 2007-01-09
If you do a google search for "how to install anytyhing" the links come up, and instead of clicking on the actual link, click on the "cache" link instead. The page comes up: 

[http://tinyurl.com/y8txgu](http://tinyurl.com/y8txgu)

Hope that helps.

[www.archive.org](www.archive.org) might be able to pull the monkeyblog.org pages up too.

---

### Post by az on 2007-01-09
> **Goat Spirit said:**
> It doesn't create a folder unless it already has a folder zipped inside of it.;)

Whatever.  Then the extracted files will need sudo priviledges to delete them.  A user will drop them into the trash, but the disk space won't be freed.  It's a hassle to then go into the .trash folder and delete them as root.

It just doesn't need to be done and can cause a hassle.

> **Goat Spirit said:**
> 
 Plus what if you are in / or something and need to extract?
I think if people are going to mess up thier system, that's their fault. They should just watch what directory and things they are in and they will be fine, I mean, how can you 'accidently delete ubuntu' lol. ;)

What in the world could you want to extract to /?  

For someone who is discovering Ubuntu to have trouble writing files to the root directory - that's a good thing.

---

### Post by Ben Sprinkle on 2007-01-09
I know the pain about it in the trash, happens to me alot. :D
Hmm, you could extract rpm's and .debs/data.tar.gz/ in /.
:D

---

