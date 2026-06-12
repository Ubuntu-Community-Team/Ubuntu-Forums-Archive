---
title: "uninstall startup manager which was installed from source?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by genbuntu on 2007-11-10
Hi

I just installed the new version of 'startup manager' from source (1.9.9) and now decided to remove it. How can I remove it?

I installed it by typing the following line in terminal because it was not installing through the normal process of "./configure && make && make install" :

```
python setup.py install
```  <-- this was mentioned in its Readme file

Thanks

---

### Post by Inxsible on 2007-11-10
cd into the source folder and do

```
sudo setup.py uninstall
```If the script has an install target, it "should" probably have an uninstall target too.

OR you can actually open the setup.py in your favorite editor and check if it has an uninstall target

---

### Post by genbuntu on 2007-11-10
Nope, no success  :(
Here's my efforts:
```

sid@zis:~/startupmanager-1.9.9$ sudo setup.py uninstall
Password:
sudo: setup.py: command not found
sid@zis:~/startupmanager-1.9.9$ sudo python setup.py uninstall
usage: setup.py [global_opts] cmd1 [cmd1_opts] [cmd2 [cmd2_opts] ...]
   or: setup.py --help [cmd1 cmd2 ...]
   or: setup.py --help-commands
   or: setup.py cmd --help

error: invalid command 'uninstall'
sid@zis:~/startupmanager-1.9.9$ 
```

(Setup.py file attached)

---

