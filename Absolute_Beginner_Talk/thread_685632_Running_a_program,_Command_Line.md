---
title: "Running a program, Command Line"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by Shiva-Shinken on 2008-02-02
A beginner to Linux, so please forgive my noobish question.

I figured out that one can run a program (let's call it "xyz") by typing:```
./xyz
```and let's say I have verified it actually will run.  But to make it run, I have to be inside the folder it is in.  Let's say if it is inside folder AA and subfolder BB, I would do the following...```
cd /AA/BB
./xyz
```

BUT... if I go to the root folder and type ```
./AA/BB/xyz
``` or even ```
./AA/BB xyz
```that does not work... how come?  Am I doing something wrong?

CC

---

### Post by njparton on 2008-02-02
Probably because the permissions of folders AA and BB won't let you - you may only have read access to them.

Do "ls -la" in a terminal at each level of the path to see the permissions granted to you.

---

### Post by Bill_MI on 2008-02-02
Be aware that "." means "the current directory".

Now, your example...

./AA/BB/xyz

Replace "." with the current directory and you get...

/AA/BB/AA/BB/xyz
...which isn't what you want.

/AA/BB/xyz is the complete path that should work from anywhere.

Also be aware the current directory is NOT searched for executable files (unlike MSDOS/Windows).  Thus, you need ./xyz when xyz is in your current directory (or if /AA/BB is in your path, just 'xyz' works).

EDIT:  Ah... I see what you mean.  Going to the root directory should allow that to work - it does here.  If you have rights to the file one place it shouldn't change.

HTH - I'm a 20-year newbie but would love to hear clarifications if I goofed anything. :)

---

### Post by Shiva-Shinken on 2008-02-02
OK, so if I am in the root directory, and with only 1 command want to run the program, how would I do so? (what would I type :)

CC

---

### Post by Shiva-Shinken on 2008-02-02
> **njparton said:**
> Probably because the permissions of folders AA and BB won't let you - you may only have read access to them.

Do "ls -la" in a terminal at each level of the path to see the permissions granted to you.

Regarding the folder permission, I set all the folders and subfolder to full read/write (777) but that did not resolve the issue.

CC

---

### Post by Bill_MI on 2008-02-02
> **Shiva-Shinken said:**
> OK, so if I am in the root directory, and with only 1 command want to run the program, how would I do so? (what would I type :)CC
Which of these works?  They all work here...

```
cd /
/AA/BB/xyz
./AA/BB/xyz
AA/BB/xyz

cd /AA/BB
./xyz
/AA/BB/xyz
```

---

### Post by Bill_MI on 2008-02-02
I want to learn something, too.  I'm not exactly sure why some errors did occur when I ran the following...
```
sudo mkdir /AA
sudo mkdir /AA/BB
sudo echo 'echo "Yes it works"' > /AA/BB/xyz
  bash: /AA/BB/xyz: Permission denied  *** WHY?
sudo touch /AA/BB/xyz
sudo echo 'echo "Yes it works"' > /AA/BB/xyz
  bash: /AA/BB/xyz: Permission denied  *** WHY?
sudo chmod 777 /AA/BB/xyz
sudo echo 'echo "Yes it works"' > /AA/BB/xyz
/AA/BB/xyz
  Yes it works
cd /
./AA/BB/xyz
  Yes it works
AA/BB/xyz
  Yes it works
cd /AA/BB
xyz
  bash: xyz: command not found
./xyz
  Yes it works
```
See if this sequence works for you?

EDIT: On a secondary note, my "why?"s do not occur in embedded Linux (OpenWrt) using ash and logged in as root.  Can someone confirm this is some subtle shell difference ash/bash?  TNX

---

### Post by scorp123 on 2008-02-02
> **Bill_MI said:**
>  I want to learn something, too.  I'm not exactly sure why some errors did occur when I ran the following...
sudo mkdir /AA
sudo mkdir /AA/BB
sudo echo 'echo "Yes it works"' > /AA/BB/xyz
  bash: /AA/BB/xyz: Permission denied  *** WHY?
 Only the first "echo" gets executed with root's priviledges, the redirection " > " not. The message is therefore correct, you don't have permission to do that. And besides: You shouldn't mess around with "sudo" and create directories where they don't belong.

> **Bill_MI said:**
>  sudo touch /AA/BB/xyz
sudo echo 'echo "Yes it works"' > /AA/BB/xyz
  bash: /AA/BB/xyz: Permission denied  *** WHY?  "touch" ran with root's priviledges via "sudo", the file you just created belongs to "root" now. The following "echo" has the same problem as the previous one: Only the first part gets executed with root's priviledges, the latter part not. The error message is therefore correct.

> **Bill_MI said:**
>  sudo chmod 777 /AA/BB/xyz
sudo echo 'echo "Yes it works"' > /AA/BB/xyz
/AA/BB/xyz
  Yes it works
 Yes, because in the previous step you gave that file dangerous "word readable, world writable, world executable" permissions, e.g. anyone can write to the file and execute it.

> **Bill_MI said:**
>  cd /AA/BB
xyz
  bash: xyz: command not found  The directory "/AA/BB" is not in your current search path, e.g. when you type a command the system will not search for executable binaries there. You can check this with executing this command: **echo $PATH**
Result from my system here: ```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

> **Bill_MI said:**
>  ./xyz
  Yes it works  "**./**" (= dot + slash) means **"right here"** in UNIX lingo, with this you circumvent the **$PATH=** variable set by the system and tell the system to search for an exectuable "xyz" in the directory "right here, right now, where I am". Or to formulate it differently: "./xyz" == "execute this program right here right now and don't bother looking anywhere else for this one: xyz".

---

### Post by Bill_MI on 2008-02-02
> **scorp123 said:**
> Only the first "echo" gets executed with root's priviledges, the redirection " > " not. The message is therefore correct, you don't have permission to do that.That's golden.... thanks, Scorp!

Besides sudo -i, I'm at a loss how to form the redirect to file so it also has the privileges.  Is it possible?

---

### Post by asmoore82 on 2008-02-02
> **Bill_MI said:**
> That's golden.... thanks, Scorp!

Besides sudo -i, I'm at a loss how to form the redirect to file so it also has the privileges.  Is it possible?

the `tee` command writes to a file while also duplicating to **standard output**
so, piping to `sudo tee` a good substitute for redirecting output to avoid an interactive root shell...

```
echo "sometext" >somefile
```
(permission denied)
could become
```
echo "sometext" | sudo tee somefile
sometext
```

---

