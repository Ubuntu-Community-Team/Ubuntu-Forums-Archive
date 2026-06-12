---
title: "How can I make a directory alias/link? (in bash)"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-10-15
I want to run a small chatroom on my site that uses simple cgi scripts, which I have located in the directory /usr/lib/cgi-bin/chat

I've read that in order to have it on my site I should make an alias to my chat scripts in my web root directory.

How can I do this?

Thanks for any help you can give me

Peace

---

### Post by anemptygun on 2007-10-15
I'm not familiar with cgi scripts or anything like that... but to make a link, a hard link specifically you can use the *ln* command

for instance
```
ln file1 /web/dir/file2
```

So file1 is the original file, and file2 is the linked file you want to put in your web directory.

---

### Post by Xarok on 2007-10-15
Well it didn't allow a link to a directory but it allow a link to one of the cgi files.

the CGI still doesn't seem to be running thought V_V

[http://higher9productions.com/chat.cgi](http://higher9productions.com/chat.cgi)

---

### Post by anemptygun on 2007-10-15
> **Xarok said:**
> Well it didn't allow a link to a directory but it allow a link to one of the cgi files.

 Are you logged in as root?

---

### Post by Xarok on 2007-10-15
yeah, I have to use sudo for most of this stuff.

I got this message:

ln: `/usr/lib/cgi-bin/chat': hard link not allowed for directory

---

### Post by wormser on 2007-10-15
> **Xarok said:**
> yeah, I have to use sudo for most of this stuff.

I got this message:

ln: `/usr/lib/cgi-bin/chat': hard link not allowed for directory

Try a symbolic link instead.  Use -s in the command.

---

### Post by mysurface on 2007-10-15
We usually use symlink instead of hard link, check out some [examples]("http://linux.byexamples.com/archives/19/how-to-create-symlink/") of how to create symlink.

---

