---
title: "dpkg interrupted"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Twig E. Pottox on 2007-08-10
When attempting to use the Add/Remove programs feature I get the following:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is a new  re-install of 7.04

---

### Post by overdrank on 2007-08-10
> **Twig E. Pottox said:**
> When attempting to use the Add/Remove programs feature I get the following:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This is a new  re-install of 7.04

Hi just run that command in the terminal
```
sudo dpkg --configure -a
```
Terminal is located under applications,accessories, terminal
Thats it ! :)

---

### Post by Seisen on 2007-08-10
You need to run

```
sudo dpkg --configure -a
``` in a terminal.

---

### Post by Twig E. Pottox on 2007-08-10
Thanks for help but im thinking something is uncooperative with this new install.

steve@steve-p4-26:~$ sudo dpgk --configure -a
Password:
sudo: dpgk: command not found
steve@steve-p4-26:~$ su
Password: 
su: Authentication failure
Sorry.
steve@steve-p4-26:~$ sudo su dpgk --configure -a
su: unrecognized option `--configure'
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

steve@steve-p4-26:~$

---

### Post by Seisen on 2007-08-10
I spelled mine wrong that is why it isn't working I will edit it but what overdrank put is correct also and spelled correctly. :lolflag:

---

### Post by Twig E. Pottox on 2007-08-10
Thanks for pointing that out I thought I was going nuts. dpkg ran succesfully .  Isnt dpkg supposed to run during install? is the following additional problem related?

also - this new install is not behaving well. when I try to minimize a program with the _ in the upper  right corner it simply disappears, not to be found. For instance i tried to minimize firefox and it dissapeared. However when I re-started it and went to the forum I was still logged in?????

thanks again

---

### Post by Seisen on 2007-08-10
Does it do it will all programs or just firefox?

---

### Post by Twig E. Pottox on 2007-08-10
> **Seisen said:**
> Does it do it will all programs or just firefox?

It soes the same with the terminal, open office , add/remove  I believe its a pattern.  Also ( if it has any connection) the switch workspaces tab  dosen't work.   Has the evil genie whacked my re-install?

---

### Post by forestpixie on 2007-08-10
Have you deleted the windows list from the panel ? You can put it back if you right click the panle and go to Add To Panel.

Firefox always logs me in to the forum cos I ticked the little box that makes it remember.

---

### Post by Twig E. Pottox on 2007-08-10
Thanks for solving the issue, there were alot of open items hidden!

---

### Post by forestpixie on 2007-08-10
ghreat - can you mark the thread solved :)

---

