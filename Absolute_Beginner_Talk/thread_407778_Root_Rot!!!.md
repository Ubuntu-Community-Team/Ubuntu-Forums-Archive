---
title: "Root Rot!!!"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by patrickmcb on 2007-04-12
Ok I am a rookie at unix/linux

Just loaded 6.10, attemtping to install plug ins and I discover that all the folders I need have root as the owner I do not have permsissions..GRRR

How do I promote myself to the same admin rights as root.

I loaded Debian on another system for comparison and it does not do this.

:confused:

---

### Post by eljalill on 2007-04-12
If you are doing things in the terminal just type ```
 sudo >command< 
```. Of course >command< is what you want it to do. You can also open an application as root through typing ```
gksu >application<
```. Note, that if you close the terminal window, the application will also close.

---

### Post by altaaa on 2007-04-12
You don't want your user account to have root rights. This is a security measure to stop users from messing up their computers. You can, in a terminal, type in ```
sudo su
``` to temporarily become root.

---

### Post by steve.horsley on 2007-04-12
Following on from what eljalill said, you will probably find 
**gksu nautilus**
very useful. Remember this fiel manager has full rights to traash your whole system, so go carefully. I change the background in mine as a reminder that it's a root-privilege file manager.

---

### Post by LaurelLynn on 2007-04-12
I go to the top panel.  Right click and select ¨+Add to Panel¨

Then I Click on ¨Application Launcher¨  then ¨System Tools¨

In there are two items I prize above all others:

[INDENT]File Browser (root)
Terminal (root)
[/INDENT]

They let me ¨sudo -s¨ and ¨gksu nautilus¨ at a single click. :D

---

### Post by patrickmcb on 2007-04-12
OK,  I have tried everything suggested.

I am attempting to intalll a java plug in for mozilla.

Open terminal, type su root & enter password
change to directory with jave .bin file
type ls and the file is listed
type ./jre-6u1-linux-i586.bin
response is:
./jre-6u1-linux-i586.bin: line 1: syntax error near unexpected token '<'
./jre-6u1-linux-i586.bin: line 1: '<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'

tried rpm version it started the install then bombed out with this line
./jre-6u1-linux-i586-rpm.bin: 370: rpm: not found

---

### Post by az on 2007-04-12
> **patrickmcb said:**
> OK,  I have tried everything suggested.

I am attempting to intalll a java plug in for mozilla.

Open terminal, type su root & enter password
change to directory with jave .bin file
type ls and the file is listed
type ./jre-6u1-linux-i586.bin
response is:
./jre-6u1-linux-i586.bin: line 1: syntax error near unexpected token '<'
./jre-6u1-linux-i586.bin: line 1: '<HTML><HEAD><TITLE>Error</TITLE></HEAD><BODY>'

tried rpm version it started the install then bombed out with this line
./jre-6u1-linux-i586-rpm.bin: 370: rpm: not found

1.  Use sudo instead of su.  By default the root account is dissabled.  To enable it, you give it a password.  But just use sudo.
2. Install java from the repositories. [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by compmodder26 on 2007-04-12
Looks like you are trying to install java, correct?  If so, you can do that from synaptic.  Make sure you have the multiverse repositories enabled and search for "sun" in synaptic.  You should see "sun-java5-jre".  If you are looking for java6 then enable the backports repository.

---

### Post by patrickmcb on 2007-04-12
redownloaded the binary .bin. got it to run,  did not take in mozilla, rebooted still not working

---

### Post by az on 2007-04-12
> **patrickmcb said:**
> redownloaded the binary .bin. got it to run,  did not take in mozilla, rebooted still not working

If you install java from the repositories, getting it to run on mozilla is as simple as running 

sudo apt-get install sun-java5-plugin 
(or sun-java6-plugin in Feisty)

Why do you want to install it by hand?

---

### Post by patrickmcb on 2007-04-12
synaptic??? where is it? sorry I am new to the game....

---

### Post by aysiu on 2007-04-12
> **compmodder26 said:**
> Looks like you are trying to install java, correct?  If so, you can do that from synaptic.  Make sure you have the multiverse repositories enabled and search for "sun" in synaptic.  You should see "sun-java5-jre".  If you are looking for java6 then enable the backports repository.

> **az said:**
> 1.  Use sudo instead of su.  By default the root account is dissabled.  To enable it, you give it a password.  But just use sudo.
2. Install java from the repositories. [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) Listen to az and compmodder26. If you follow those instructions, you'll get Java installed. Forget about your .bin file.

> **steve.horsley said:**
> Following on from what eljalill said, you will probably find 
**gksu nautilus**
very useful. Remember this fiel manager has full rights to traash your whole system, so go carefully. I change the background in mine as a reminder that it's a root-privilege file manager. A very useful tip. More details here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by aysiu on 2007-04-12
Learn how to install applications in general.

**Brief overview and explanation for concepts**:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

**Step-by-step tutorial with screenshots**:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

**Instructions specifically for Java** (which someone already linked to before):
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by aysiu on 2007-04-12
> **patrickmcb said:**
> synaptic??? where is it? sorry I am new to the game....
Read the links I posted above, in the order I posted them.

---

### Post by nicketynick on 2007-04-12
> **LaurelLynn said:**
> I go to the top panel.  Right click and select ¨+Add to Panel¨

Then I Click on ¨Application Launcher¨  then ¨System Tools¨

In there are two items I prize above all others:

[INDENT]File Browser (root)
Terminal (root)
[/INDENT]

They let me ¨sudo -s¨ and ¨gksu nautilus¨ at a single click. :D

Hey LL,
This sounds good, but doesn't work for me??? No "System Tools" is available when I click on "Application Launcher". I'm also running Dapper - what gives?

---

