---
title: "commands not working with sudo precursor"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by oscar78 on 2007-01-10
I'm confused...commands for programs I have previously installed (that are in my path) work fine, but when I use sudo bash doesnt recognize them for some reason.  I've added their paths to the .bashrc in the root directory, but that still doesn't do anything.

Does anyone have any ideas?

---

### Post by bodhi.zazen on 2007-01-10
> **oscar78 said:**
> I'm confused...commands for programs I have previously installed (that are in my path) work fine, but when I use sudo bash doesnt recognize them for some reason.  I've added their paths to the .bashrc in the root directory, but that still doesn't do anything.

Does anyone have any ideas?

How did you add the path in /root/.bashrc ?

Don't forget to

export PATH

```
PATH=$PATH:additional/path1:additional/path2
export PATH
```

---

### Post by oscar78 on 2007-01-10
at the end of the /root/.bashrc document I added 

PATH=$PATH:/path/to/my/excecutable/

After logging out and back in I try to run the program, and get the following error:  

sudo: simulaid: command not found   (simulaid is the program).

I just dont understand.

---

### Post by taurus on 2007-01-10
Or just make a link to your program.

```
sudo ln -s /path_to_program/simulaid  /usr/bin/simulaid
```

---

### Post by bodhi.zazen on 2007-01-10
> **oscar78 said:**
> at the end of the /root/.bashrc document I added 

PATH=$PATH:/path/to/my/excecutable/

After logging out and back in I try to run the program, and get the following error:  

sudo: simulaid: command not found   (simulaid is the program).

I just dont understand.

LOL oscar. You need to change "/path/to/my/executable/" to the path to the command(s) you want to add to the path

Then export PATH

Example:

```
PATH=$PATH:/home/user_name/bin
export PATH
```

where user_name is your log-in name ....

---

### Post by oscar78 on 2007-01-10
Thanks!

---

