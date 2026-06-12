---
title: "help installing vmware please"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-11-27
i downloaded the tar.gz for vmware player from the vmware website..i dont know what to do from here to install it and was wondering if someone could help me get this installed please...right now the tar.gz file is on my desktop...do i need to move it before i install it?? all help is greatly appreciated...thanks

---

### Post by LLRNR on 2006-11-27
Take a look at [this HowTo](http://ubuntuforums.org/showthread.php?t=183209), believe me, it's actually great !! ;)

LLRNR

EDIT - Oups I now see you downloaded the Player not the Server... well apparently the Server works great (at least for me), maybe you're willing to give it a try.

---

### Post by swp6499 on 2006-11-27
i just realized i need the server...does that post have the install instructions for vmware server?

---

### Post by LLRNR on 2006-11-27
Yup, it sure does :D It worked great for me (don't freak out if you get an error at install, the guide has a "troubleshooter" section too). 

Also, there are the detailed instructions on downloading / installing VMware Server.

Give it a go! Good luck! ;)

LLRNR

---

### Post by AndyCooll on 2006-11-27
> **swp6499 said:**
> i just realized i need the server...does that post have the install instructions for vmware server?

Yes that post is all about the server installation.

If you just want VMware Player, you can install this using Synaptic (assuming you have enabled the universe/multiverse repos). VMware server lets you create your own images, VMware player lets you play pre-compiled images.

:cool:

---

### Post by redDEADresolve on 2006-11-27
yup player can be found in the repos and server can be set up using this how to [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

---

### Post by swp6499 on 2006-11-27
i got it set up thanks for all your help i really appreciate it

---

### Post by ixtok on 2006-11-28
I had good luck installing vmware player using automatix and then creating the vmx file at [www.easyvmx.com](www.easyvmx.com)

---

### Post by swp6499 on 2006-11-29
it worked thanks for all your help...

---

### Post by syrleb on 2006-11-29
i try to install vmware server but it tells me i already have vmware installed, i have removed everything to do with vmware from my laptop, went through synaptic and removed it, done everything and it tells me i still have a preivious installataion

ali@ali-laptop:~$ cd '/home/ali/Desktop/vmware-server-distrib' 
ali@ali-laptop:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl 
A previous installation of VMware software has been detected.

Failure

Execution aborted.

any help will be appreciated

---

### Post by swp6499 on 2006-11-29
have you tried removing it with the uninstall.pl from terminal?

---

### Post by redDEADresolve on 2006-11-29
I ran into the same problem nothing worked and I ended up having to reinstall Ubuntu completely. I had a thread on the subject that I can't find, but nothing worked.

---

### Post by yabbadabbadont on 2006-11-29
Did either of you try removing the /etc/vmware directory and all of its contents?  It sometimes gets left behind and will cause the error you are seeing.

---

### Post by syrleb on 2006-11-30
yes i tried that, i tried it all but for some reason it still thinks its installed, im really stuck and pissed off

---

