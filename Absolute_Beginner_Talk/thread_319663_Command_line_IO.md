---
title: "Command line I/O"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by mdecler2 on 2006-12-16
I am having general command line I/O issues. I am using tethereal to moniter some packet traffic, and I want to read that output on the command line as it comes, but also store the output to a file at the same time.

I used a "sudo tethereal | 2>&1 ~/someFileFoo" 

First of all  got an error saying "someFileFoo" does not exist (why didn't it make a new one?).
When I created an empty file called someFileFoo in the home directory I get a "permission denied" despite the "sudo"!

Tethereal also reported that it captured 4 packets when I ended its process, but they never came out on the cmd line :( . So I must be going about this completely wrong.

Any help appreciated concerning I/O; tips and comments included.

---

### Post by K.Mandla on 2006-12-16
Did you try giving it a full path for the file, like 

```
sudo tethereal | 2>&1 /home/your_user_name/someFileFoo
```
?

---

### Post by wastrel on 2006-12-16
> **mdecler2 said:**
> I am having general command line I/O issues. I am using tethereal to moniter some packet traffic, and I want to read that output on the command line as it comes, but also store the output to a file at the same time.

I used a "sudo tethereal | 2>&1 ~/someFileFoo" 

First of all  got an error saying "someFileFoo" does not exist (why didn't it make a new one?).
When I created an empty file called someFileFoo in the home directory I get a "permission denied" despite the "sudo"!

Tethereal also reported that it captured 4 packets when I ended its process, but they never came out on the cmd line :( . So I must be going about this completely wrong.

Any help appreciated concerning I/O; tips and comments included.

2 problems.

1.  sudo and file IO redirection don't really play well together.  I recommend you become root with sudo -i and run the command from the root shell.

2.  | is a pipeline operator, used to send output to another program.  > is a file redirect operator, which is used to send output to a file.  Use one or the other, not both.  In this case you want >.

Something like this should work:
```

% touch ~/someFileFoo
% sudo -i
# tethereal 2>&1 /full/path/to/someFileFoo
```

---

