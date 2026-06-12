---
title: "[SOLVED] How would I do this?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Bruce M. on 2008-04-02
Hi Folks,

I tried this in a bashrc thread because I though an "alias" in my bashrc might do it

I was wrong.

As a new person to Linux, I find myself in terminal looking at MAN pages a lot.
Then I started doing this:
```
man foo>~/Manuals/foo.txt
```
and I thought that has to be a way to have "foo" as a variable so I could use: m2t foo

m2t (man to text) would be a small program, script ... something, what do I know?

```
m2t foo
m2t foo2
```
and have that create ~/Manuals/foo.txt
and  ~/Manuals/foo2.txt

Is that possible and if so

[LIST=1]
[*] How?
[*] Would it go directly in the bashrc?
[*] Or would it be a script like conkyrc?
[/LIST]

Thanks
Bruce

---

### Post by Athelstan101 on 2008-04-02
You could create a script like this:
```
#!/bin/sh -e
man $1 >~/Manuals/$2.txt;
```

Then make it executable:
```
chmod u+x m2t
```

Then run it like this:
```
$ ./m2t.sh pwd foo
```

---

### Post by doorknob60 on 2008-04-02
Try this:
```

#!/bin/bash
man $1>~/Manuals/$1.txt

```

You could save that file and call it m2t, and make it executable with this:
```

chmod +x m2t

```

Then, if you want, copy it to /usr/bin so it's in your path:
```

sudo cp m2t /usr/bin/

```

EDIT: The difference between mine and Athelstan101's is that mine makes the .txt file the same name as the man page like in your example, but with Athelstan101's you can make the .txt file a different name than the man page.

---

### Post by Bruce M. on 2008-04-02
> **doorknob60 said:**
> Try this:
```

#!/bin/bash
man $1>~/Manuals/$1.txt

```


Did all that and I get:

```
bruloo@bruloo:~$ mt bash
mt: invalid argument `bash' for `tape operation'
bruloo@bruloo:~$ mt chmod
mt: invalid argument `chmod' for `tape operation'
bruloo@bruloo:~$ mt sudo
mt: invalid argument `sudo' for `tape operation'
bruloo@bruloo:~$ 
```

Help :)

Changed it to **mt** because with **m2t** Movie Player wanted to control it.  :)

---

### Post by doorknob60 on 2008-04-02
Hmm, weird, I've made other scripts like this before that work fine, I'll look into it and post back.

EDIT: Oooh...mt is another system command :P Try renaming it to something else. I renamed mine to mantxt and everything's working fine now, but you could think of a shorter name for it if you want. Just make sure it's not already a system command.

---

### Post by Bruce M. on 2008-04-03
> **doorknob60 said:**
> Hmm, weird, I've made other scripts like this before that work fine, I'll look into it and post back.

EDIT: Oooh...mt is another system command :P Try renaming it to something else. I renamed mine to mantxt and everything's working fine now, but you could think of a shorter name for it if you want. Just make sure it's not already a system command.

Just my luck ... mt, another command.

 OK I have it as **/home/mantext**

It looks like this:
```
#!/bin/bash
man $1>~/Manuals/$1.txt
```
and I get:
```
bruloo@bruloo:~$ chmod +x mantext
bruloo@bruloo:~$ mantext bash
bash: mantext: command not found
bruloo@bruloo:~$ 

```
And it is set as executable.

Am I jinxed or what?

**EDIT:** changed the name to **mantxt**
Did
```
sudo cp mantxt /usr/bin/
```
and it works like a dream

**Thanks doorknob60**

---

