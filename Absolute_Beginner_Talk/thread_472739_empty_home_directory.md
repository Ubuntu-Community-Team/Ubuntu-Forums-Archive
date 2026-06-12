---
title: "empty home directory"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ColmOsiris on 2007-06-13
I'm going thgough the navigation pages in <http://www.linuxcommand.org/lts0020.php> and when I typed in 'ls' I got nothing but a prompt. I assume this means the directory is empty. Is this a problem? I am still in the directory I was in when I logged on (/home/username).

---

### Post by dannyboy79 on 2007-06-13
well yeah! are you sure that you're in your user's home directory? did you accidentally do a rm -rf or any type of command that would delete stuff? what does pwd return? also, what does 
ls -la
return, this should not only show you files and dir's but also their permissions and owner info.

---

### Post by notwen on 2007-06-13
Have you created/saved any folders or files in your home directory yet?  Try this to show all hidden folders and files.

```
ls -a
```

---

### Post by ColmOsiris on 2007-06-13
Thanks.

Starting from the beginning, I'm using the Terminal app on my Mac to access the Linux server PC over an ethernet network.

I typed "ssh -v -C username@10.0.0.8". This is what a friend told me I needed to do to access the machine via the network.

It gives me shedloads of stuff, then asks for the password for the user. Then it gives me:

> username@internalcolmhost:~$

I type 'pwd' and I get:

> /home/username

I type 'ls' and I just get the prompt.

If I type 'ls -la' I get this:

> total 32
drwxr-xr-x 3 username username 4096 2007-05-02 13:48 .
drwxr-xr-x 3 root       root       4096 2007-03-19 15:23 ..
-rw------- 1 username username  528 2007-05-03 22:24 .bash_history
-rw-r--r-- 1 username username  220 2007-03-19 15:23 .bash_logout
-rw-r--r-- 1 username username  414 2007-03-19 15:23 .bash_profile
-rw-r--r-- 1 username username 2227 2007-03-19 15:23 .bashrc
-rw------- 1 username username   35 2007-03-19 17:07 .lesshst
-rw-r--r-- 1 username username    0 2007-03-19 15:51 .sudo_as_admin_successful

---

### Post by dannyboy79 on 2007-06-13
well, then you're alright! not sure what linux server you're sshing into but the reason I thought somehting may be wrong is because I though you were talking about a Feisty Desktop, if you were, there's always a Desktop folder that you should have seen at a min, What the ls -la does is show you hidden files as well which is another thing I was thinking. so you're doing alright!

---

### Post by Nythain on 2007-06-13
files and directories with a . in front of them are hidden... ls -a shows all files and folders including hidden ones

in your graphical file browser/manager there should be an option somewhere "Show hidden files" or something like that

---

### Post by dannyboy79 on 2007-06-13
> **Nythain said:**
> files and directories with a . in front of them are hidden... ls -a shows all files and folders including hidden ones

in your graphical file browser/manager there should be an option somewhere "Show hidden files" or something like that

he's ssh'd into his server, so don't think that would work in this situtation but good tip none the less.

---

### Post by ColmOsiris on 2007-06-13
> **dannyboy79 said:**
> he's ssh'd into his server, so don't think that would work in this situtation but good tip none the less.

The server I'm using doesn't have a GUI installed, and I'm doing everything remotely from the Mac's Terminal, so no, but in other future circumstances it might. I am aware of hidden files, cos the Mac has them too.

It's good to know I've not done anything stupid. I'll just carry on, then.


Thanks all.

---

