---
title: "[SOLVED] Make /usr/bin/[subfolder] Executable?"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-14
If I place bash scripts in /usr/bin and make them executable I can type their titles into Alt-F2 and they run without a prompt.

However if I create a folder in usr/bin, I can't access the scripts I put in there without entering the entire path.

What are some ways to make the Alt-F2 (and what is that called by the way?) command-line thing aware of the subfolder without entering the path every time? Thanks!

---

### Post by taurus on 2008-01-14
You just add that new directory in your ~/.bashrc.

```
PATH=$PATH:/usr/bin/new_path
export PATH
```

---

### Post by p_quarles on 2008-01-14
You can add the sub folder to your paths in /etc/environment. First, you should make a backup:
```
sudo cp /etc/environment /etc/environment.bak
```
Then,
```
sudo nano /etc/environment
```
In the PATH= line, you'll see a series of folders within quote marks, and separated by colons. Using the same format, add the new path to this series.

---

### Post by jjsonp on 2008-01-14
p_quarles: your solution works - thanks!

taurus: your solution does not, but thanks anyway. I tried yours first but there was no change. It seems like Alt-F2 does not interpret bash shell, because it doesn't work with aliases either. It probably worked fine in the terminal though (as aliases do also).

p_quarles, do you know of a way to alias via the environment variables? Anyway, this works for what I'm trying to do at the moment, so many thanks!

---

### Post by p_quarles on 2008-01-14
> **jjsonp said:**
> p_quarles: your solution works - thanks!

taurus: your solution does not, but thanks anyway. I tried yours first but there was no change. It seems like Alt-F2 does not interpret bash shell, because it doesn't work with aliases either. It probably worked fine in the terminal though (as aliases do also).

p_quarles, do you know of a way to alias via the environment variables? Anyway, this works for what I'm trying to do at the moment, so many thanks!
/etc/environment defines the executable path for all users and shells, which is why that's working but .bashrc settings aren't. Basically, the run dialogue in Gnome seems to not use Bash (and this is something I didn't know until today). 

The key to adding it to your user settings, I think, would be to add a setting related to the shell in use to your ~/.profile. You would then be able to use aliases with that shell, presuming it supports them.

---

