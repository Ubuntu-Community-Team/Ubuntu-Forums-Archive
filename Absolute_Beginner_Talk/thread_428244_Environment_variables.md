---
title: "Environment variables"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Joseaa on 2007-04-30
Can anyone shed some light on environment variables 

1. How to setup a value for environment variable ?
2. In which file is it getting stored ?
3. How to check the current value of an environment variable ?

---

### Post by Najand on 2007-04-30
1.
```

$ export FOO=blah1:blah2:blah3

```

2. You can add it to any of the following files:
I "/etc/profile File"
II "/etc/environment File"
III ".profile File"
IV ".env File"
They function differntly though. For example the ones starting with /etc would be set up the variables for all users, though the one starting with a . (dot) would set environment variables for the user the file exists in his/her home directory.
Also you need to write the export command when dealing with profile files.

3.the "env" command
Also you can check the value of the evironments by:
```

$ echo $FOO

```

---

### Post by Joseaa on 2007-04-30
If I simply specify "$ export FOO=bla" in the terminal will it set the environment variable. At least temporarily till the next restart ?

---

### Post by Joseaa on 2007-04-30
Specifying "export FOO=blah1:blah2:blah3" in ".profile" seems to be having no effect but directly giving export FOO=blah1 in terminal seems to change the value of the variable. 

Am I doing it wrong ? Anyone ?

---

### Post by Churnd on 2007-04-30
You can also add the export line to your ~/.bashrc file, which is also good for aliases.

---

### Post by Skrynesaver on 2007-04-30
in fact ~/.bashrc will be processed for xterm whereas .profile/.bash_profile will only be processed for logins (IE TTY 1-6) so .bashrc is a better place to set up environment variables, aliases and the like

---

### Post by Joseaa on 2007-04-30
I've set up "export foo=value" in .bashrc but the problem is,  value of the variable is not updated when I use "$echo $foo" or "$env". Does the value of the variable actually gets updated, If so, how can I cross check it ?

---

### Post by YoG%*@ on 2007-04-30
try 
```

source .bashrc

```

---

### Post by Skrynesaver on 2007-04-30
If you start a new bash session 
```

bash
echo $foo

```
is the value now set?

---

### Post by Joseaa on 2007-05-02
> **Skrynesaver said:**
> If you start a new bash session 
```

bash
echo $foo

```
is the value now set?

Yes. Starting a new bash session seemed to have solved the problem. Thanks a lot.

---

