---
title: "$PATH question"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-10-25
I must add "export PATH=$PATH:/home/kent/bin/" before I execute a script located in my bin dir if I am in a different dir than bin.

It looks like my **.bash_profile** already has the code to add my bin path.

So why do I have to add the path on the command line to execute a script in my bin directory?


This is the last section of my ~/.bash_profile file should this not add my bin to the PATH?
```

# set PATH so it includes user's private bin if it exists

if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

---

### Post by bswilson on 2006-10-25
It all depends on when you created your ~/bin directory.  If you created the directory during this current session, it won't work.  You must first source your **.bash_profile** file with this command:

```
. .bash_profile
```

Yes, that is a dot, then a space, then the filename **.bash_profile**.  That effectively 'refreshes' the settings for your current shell.

---

### Post by kent41 on 2006-10-25
> **bswilson said:**
> It all depends on when you created your ~/bin directory.  If you created the directory during this current session, it won't work.  You must first source your **.bash_profile** file with this command:

```
. .bash_profile
```

Yes, that is a dot, then a space, then the filename **.bash_profile**.  That effectively 'refreshes' the settings for your current shell.

This is what I get when I try that code
```

kent@linux-2:/$ . .bash_profile
bash: .bash_profile: No such file or directory
kent@linux-2:/$ sudo . .bash_profile
Password:
sudo: .: command not found

kent@linux-2:/$

```

---

### Post by kent41 on 2006-10-25
Is it possible that the .bash_profile code does not work in Breezy?

---

### Post by po0f on 2006-10-25
kent41,

Have you tried logging out and back in?

---

### Post by kent41 on 2006-10-25
> **po0f said:**
> kent41,

Have you tried logging out and back in?

Yes I just installed Breezy on this hard drive yesterday and the code for .bash_profile was already included but it does not look like it works to me.

I just want to add my bin path so I dont have to manually do it each time I want to execute a script.

---

### Post by po0f on 2006-10-25
kent41,

Try adding the following to ~/.bashrc and see if it works:
```
PATH="/home/kent/bin:${PATH}"
```

---

### Post by skymt on 2006-10-25
Put ". ~/.bash_profile" in ~/.bashrc. .bash_profile is only run when you use Bash as a login shell, which isn't the default for xterms like gnome-terminal. .bashrc is always run.

---

### Post by kent41 on 2006-10-25
> **po0f said:**
> kent41,

Try adding the following to ~/.bashrc and see if it works:
```
PATH="/home/kent/bin:${PATH}"
```

Thanks that worked - but should the code in .bash_profile work?

---

### Post by po0f on 2006-10-25
I use rxvt-unicode:
```
$ cat ~/.Xresources
(snip)
urxvt.loginShell: true
(snip)
```

I probably realized the ~/.bash_profile being sourced only on login shells on a subconscious level.  :)

---

