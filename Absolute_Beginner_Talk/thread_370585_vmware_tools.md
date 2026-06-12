---
title: "vmware tools"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by fongs on 2007-02-25
having problem installing vmware tools could some one please help ihave read everything on this and still same result please
dab@dab-desktop:~/Desktop/vmware-tools-distrib$ sudo ./vmware-install.pl
sudo: ./vmware-install.pl: command not found

---

### Post by scxtt on 2007-02-25
try supplying the full path:

[indent]dab@dab-desktop:~/Desktop/vmware-tools-distrib$ **sudo /home/dab/Desktop/vmware-tools-distrib/vmware-install.pl**[/indent]

and make sure it's executable.

---

### Post by Strider on 2007-02-25
Take a look at this page to do it:

[http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html](http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html)

Basically you need to unzip the tar.gz file to a temp location and then run the perl script.

-Mike

---

### Post by fongs on 2007-02-25
> **Strider said:**
> Take a look at this page to do it:

[http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html](http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html)

Basically you need to unzip the tar.gz file to a temp location and then run the perl script.

-Mike

sudo: /home/dab/Desktop/vmware-tools-distrib/vmware-install.pl: command not found
so how do i make it executible and run as perl scrpt

---

### Post by Maestro23 on 2007-02-25
> **fongs said:**
> sudo: /home/dab/Desktop/vmware-tools-distrib/vmware-install.pl: command not found
so how do i make it executible and run as perl scrpt

Try this:

> sudo chmod +x vmware-install.pl
./vmware-install.pl


---

### Post by fongs on 2007-02-25
chmod: cannot access `vmware-install.pl': No such file or directory

---

### Post by Maestro23 on 2007-02-25
> **fongs said:**
> chmod: cannot access `vmware-install.pl': No such file or directory

Are you in the directory that the file is in?

In terminal:

> pwd

Tells you you current directory.

---

### Post by fongs on 2007-02-25
> **Maestro23 said:**
> Are you in the directory that the file is in?

In terminal:



Tells you you current directory.

not sure what you mean by that

---

### Post by Maestro23 on 2007-02-25
> **fongs said:**
> not sure what you mean by that

Where did you download the file to?  In a terminal, the command "pwd" will display the current directory you are in.

You need to get to the directory that you downloaded the file to and run those commands I posted earlier on the file.

---

### Post by fongs on 2007-02-25
> **fongs said:**
> not sure what you mean by that

dab@dab-desktop:~/vmware-tools-distrib$ sudo chmod +x vmware-install.pl and nothing happend

---

### Post by fongs on 2007-02-25
> **fongs said:**
> dab@dab-desktop:~/vmware-tools-distrib$ sudo chmod +x vmware-install.pl and nothing happend

ok  i'm in the directory and i get  :          
Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

Unable to create the directory /mnt/hgfs.

Execution aborted.

root@dab-desktop:/home/dab/vmware-tools-distrib# 

thank for the advice on the directory

---

### Post by fongs on 2007-02-26
> **Maestro23 said:**
> Where did you download the file to?  In a terminal, the command "pwd" will display the current directory you are in.

You need to get to the directory that you downloaded the file to and run those commands I posted earlier on the file.

yes thanks for info on directory but heres what happened next

---

### Post by fongs on 2007-02-26
> **Maestro23 said:**
> Where did you download the file to?  In a terminal, the command "pwd" will display the current directory you are in.

You need to get to the directory that you downloaded the file to and run those commands I posted earlier on the file.

yes thanks for info on directory but heres what happened nextUnable to create the directory /mnt/hgfs

---

### Post by Maestro23 on 2007-02-26
.

---

### Post by fongs on 2007-02-26
this is what happens after  root@dab-desktop:/home/dab/vmware-tools-distrib# ./vmware-install.pl
Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

Unable to create the directory /mnt/hgfs.
 please help

---

### Post by Maestro23 on 2007-02-26
> **fongs said:**
> this is what happens after  root@dab-desktop:/home/dab/vmware-tools-distrib# ./vmware-install.pl
Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

Unable to create the directory /mnt/hgfs.
 please help

Don't start a new post about the same thing.  You can't create that directory becasue it is owned by root.  I was reading the installation docs over at the Vmware site, and to run that script is wants the user to be root.

Now you can open a root console that will let you do everything as root.  Be careful in there. You are root while you are in this console. Do just what you have to do to run this perl script.  Open a terminal:

> sudo -i

While in this console, try running that perl script and post what happens.  When you are done, exit/close that root console. 
Read bout it here, at the bottom: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2007-02-26
> **Maestro23 said:**
> Don't start a new post about the same thing. I've merged the two threads.

---

### Post by fongs on 2007-02-26
> **Maestro23 said:**
> Don't start a new post about the same thing.  You can't create that directory becasue it is owned by root.  I was reading the installation docs over at the Vmware site, and to run that script is wants the user to be root.

Now you can open a root console that will let you do everything as root.  Be careful in there. You are root while you are in this console. Do just what you have to do to run this perl script.  Open a terminal:



While in this console, try running that perl script and post what happens.  When you are done, exit/close that root console. 
Read bout it here, at the bottom: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sorry about the other post 
could you please explain the perl script

---

### Post by Maestro23 on 2007-02-26
> **fongs said:**
> sorry about the other post 
could you please explain the perl script

You are going to get back to the spot before you got your error.  Just do it from the root console. Get back to the same directory and try to run that file.  Make sense?

---

### Post by fongs on 2007-02-26
> **Maestro23 said:**
> You are going to get back to the spot before you got your error.  Just do it from the root console. Get back to the same directory and try to run that file.  Make sense?

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware-tools] 

The path "/usr/lib/vmware-tools" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware-tools] 

The path "/usr/share/doc/vmware-tools" does not exist currently. This program 
is going to create it, including needed parent directories. Is this what you 
want? [yes] 

The installation of VMware Tools 5.5.3 build-34685 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] 


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

Unable to create the directory /mnt/hgfs.

Execution aborted.

[SIZE="5"]root@dab-desktop:/home/dab/vmware-tools-distrib# 
[/SIZE]  and as you can see iam in root if this is what you mean if not please explain to me 
greatful for your help

---

### Post by fongs on 2007-02-26
> **Maestro23 said:**
> You are going to get back to the spot before you got your error.  Just do it from the root console. Get back to the same directory and try to run that file.  Make sense?

still stuck my friend i've  tried as root as u can see above but to no avail 
please help

---

### Post by Maestro23 on 2007-02-26
Looks like it installed w/success.  Let's check though. Get out of that root console and open up a normal one.  Then run this command:

> whereis vmware-tools

Should come back with the path to vmware-tools.

Over at the vmware forums, I ran a quick search on that [COLOR="Red"]/mnt/hgfs [/COLOR]and came up with a lot of hits.  You really need to head over there yourself and do some researching on their forums and in the user documentation for the program.  Might also look for other posts on these forums discussing Vmware as well, I know there are some.

---

### Post by fongs on 2007-02-26
> **Maestro23 said:**
> Looks like it installed w/success.  Let's check though. Get out of that root console and open up a normal one.  Then run this command:



Should come back with the path to vmware-tools.

Over at the vmware forums, I ran a quick search on that [COLOR="Red"]/mnt/hgfs [/COLOR]and came up with a lot of hits.  You really need to head over there yourself and do some researching on their forums and in the user documentation for the program.  Might also look for other posts on these forums discussing Vmware as well, I know there are some.

thanks it came up with :dab@dab-desktop:~$ whereis vmware-tools 
vmware-tools: /etc/vmware-tools /usr/lib/vmware-tools
dab@dab-desktop:~$ 
where do i start it if it has finished

---

### Post by scxtt on 2007-02-26
vmware tools generally starts on boot [ of the VM ] - you'll generally know that it has worked cause you don't need to hit CTRL + ALT to release the mouse ... if you want to use some of its other features, just typing vmware-toolbox should invoke it ...

---

### Post by Maestro23 on 2007-02-26
> **fongs said:**
> thanks it came up with :dab@dab-desktop:~$ whereis vmware-tools 
vmware-tools: /etc/vmware-tools /usr/lib/vmware-tools
dab@dab-desktop:~$ 
where do i start it if it has finished

That looks good from what I can remember from the forums over there.  I found this "How-To" on our forums here that might help(could have used this in the beginning LOL): [https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29](https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29)

I don't use Vmware myself, so I'm glad I could help you get this far.

---

### Post by fongs on 2007-02-26
> **Maestro23 said:**
> That looks good from what I can remember from the forums over there.  I found this "How-To" on our forums here that might help(could have used this in the beginning LOL): [https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29](https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29)

I don't use Vmware myself, so I'm glad I could help you get this far.

brilliant thanks for the support to me had i have seen that las bit i would have thought it had loaded properly .
 now i have : dab@dab-desktop:~$ whereis vmware-tools 
vmware-tools: /etc/vmware-tools /usr/lib/vmware-tools
dab@dab-desktop:~$ whereis vmware-toolbox
vmware-toolbox: /usr/bin/vmware-toolbox /usr/X11R6/bin/vmware-toolbox /usr/bin/X11/vmware-toolbox what should i do now.

---

### Post by Mach1US on 2007-09-15
My vmware tools install failed and now every time i try to run the script all i get is 
```
A Previous installation of VMware software detected 
Failure
Execution aborted
```
I'm running feisty on xp-pro.
Any ideas ???

---

