---
title: "Can't move file into lib"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by ausbun on 2007-01-04
I installled a poker game that  I originally bought for Windows (which I'm not running any more) but which I discovered was also Linux compatible. I ran into a Java error and went to the software firm's website, where I was told how to fix my problem:

Download libstdc++-libc6.2-2.so.3, place it in your /usr/lib from the root directory and make sure it has 555 permissions with the command chmod 555 libstdc++-libc6.2-2.so.3 You may need to enter su (super user) and copy it into your /usr/lib directory using the command line in the shell.

I downloaded the file to my desktop, but when I went to move into my "lib" file, I was told I didn't have authorization to do that. I don't understand the last sentence of the above instruction, either. Does this mean to use a sudo command in terminal?

Thanks for any help in this.

---

### Post by jvc26 on 2007-01-04
Yes it does you need to move it with a sudo command - you could just do sudo nautilus and then move it via the nautilus window from /home/user/Desktop to the /usr/lib directory. Another route via terminal would be to 

```

sudo mv /home/user/Desktop/filename /usr/lib

``` 

You may also need to change its permissions via the chmod command - more info I think is on a post in this forum, and there is definitely stuff on wiki about the chmod to change permissions.
Hope that helps,
Il

---

### Post by ausbun on 2007-01-04
When I do this, it tells me "usr/lib" is not a directory.

I get the same message when I change "usr" to my username.

I know I'm doing something wrong here, but I can't tell what.

Thanks

---

### Post by ausbun on 2007-01-04
I was able to move it with the Nautilus window. Now, when I click on the program and tell it to run, nothing happens. I'm going to see what I can do about the 555 issue.

---

