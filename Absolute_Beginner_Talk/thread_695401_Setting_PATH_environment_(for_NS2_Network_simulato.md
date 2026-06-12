---
title: "Setting PATH environment (for NS2 Network simulator) PLS !!!"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by jalal0 on 2008-02-13
[FONT="Arial"][SIZE="3"]Hello,
To begin with, let me be clear that I am an absolute beginner in Ubuntu, so when answering my question, please dont assume that I have any background knowledge.

My problem goes this way:
When trying to install NS2 Network simulator on Ubuntu
[http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04](http://nsnam.isi.edu/nsnam/index.php/Installing_ns2.31_on_Ubuntu7.04)

I get this message after giving the $ ns command:

[COLOR="Blue"]******
Please put /home/jalal/ns-allinone-2.31/bin:/home/jalal/ns-allinone-2.31/tcl8.4.14/unix:/home/jalal/ns-allinone-2.31/tk8.4.14/unix
into your PATH environment; so that you'll be able to run itm/tclsh/wish/xgraph.

IMPORTANT NOTICES:

(1) You MUST put /home/jalal/ns-allinone-2.31/otcl-1.13, /home/jalal/ns-allinone-2.31/lib, 
    into your LD_LIBRARY_PATH environment variable.
    If it complains about X libraries, add path to your X libraries 
    into LD_LIBRARY_PATH.
    If you are using csh, you can set it like:
                setenv LD_LIBRARY_PATH <paths>
    If you are using sh, you can set it like:
                export LD_LIBRARY_PATH=<paths>

(2) You MUST put /home/jalal/ns-allinone-2.31/tcl8.4.14/library into your TCL_LIBRARY environmental
    variable. Otherwise ns/nam will complain during startup.
*****[/COLOR]

Please can some one tell me step by step how this can be done. I had spend the last 48 odd hours running round a circle, trying to figure out what can be done, but every time I complete the circle, I find myself where I started. :confused:

Thanks a lot in advance.[/SIZE][/FONT]

---

### Post by jordanmthomas on 2008-02-13
Easiest way that will work for all users using all shells:
**BE CAREFUL WITH THIS FILE**
```
gksudo gedit /etc/profile
```
Add these lines to the start
```

export PATH=$PATH:/home/jalal/ns-allinone-2.31/bin:/home/jalal/ns-allinone-2.31/tcl8.4.14/unix:/home/jalal/ns-allinone-2.31/tk8.4.14/unix
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/jalal/ns-allinone-2.31/otcl-1.13:/home/jalal/ns-allinone-2.31/lib
export TCL_LIBRARY=$TCL_LIBRARY:/home/jalal/ns-allinone-2.31/tcl8.4.14/library

```

The more proper way would be to add these lines above to your ~/.bashrc
```
gedit ~/.bashrc
``` but if you use a shell other than bash it can sometimes just be easier to put it in the system profile.

After adding this to /etc/profile or ~/.bashrc, you can log out and then back in.

---

