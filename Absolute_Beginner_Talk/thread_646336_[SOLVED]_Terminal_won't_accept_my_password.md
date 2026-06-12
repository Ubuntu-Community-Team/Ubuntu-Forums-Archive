---
title: "[SOLVED] Terminal won't accept my password"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Carnivorum on 2007-12-21
Bs'd

I want to install Java, and after I type su in the terminal, he asks me for my password,

Then I type my password, but he constantly tells me:  Authentication failure

What am I doing wrong?

---

### Post by nowshining on 2007-12-21
u need a username after su

su root

however u can do

sudo ur command

or to get to root quicker try this trick

sudo /bin/bash

input ur password

---

### Post by chewearn on 2007-12-21
Sorry, nevermind

---

### Post by Carnivorum on 2007-12-21
> **nowshining said:**
> u need a username after su

su root

however u can do

sudo ur command

or to get to root quicker try this trick

sudo /bin/bash

input ur password

Bs'd

Thanks for your help, I appreciate it.


Eliyahu

---

### Post by nowshining on 2007-12-21
ur welcome Carnivorum

---

### Post by Carnivorum on 2007-12-21
Bs'd

I'm trying to install Java with the example on this page:  [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

This is written there:  

 To install the Linux (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

When I do step 3, he tells me:   No such file or directory
How do I make one, or which directory would be a good alternative?


Eliyahu

---

### Post by nowshining on 2007-12-21
okay go to ur folder, right click and create folder, rename it to whatever u want,

k then once at root issue

cd /home/<ur username>/the folder u created


then once there

issue the command to install it,

then in advance so u don't ask later

when asking to insert the link to the mozilla folder

cd /home/ur username/.mozilla/plugins

also in the insert symbolic link u'll have to change it a bit and not copy and paste but change the name to the java folder they put in as an example to ur folder...but do that once u cd into the plugins folder.

to see hidden files

in a nautilus windows press ctrl+h

to re-hide - do the same

in linux hidden files are the ones with a dot as the first letter/symble in their name.

---

### Post by Carnivorum on 2007-12-21
> **nowshining said:**
> okay go to ur folder, right click and create folder, rename it to whatever u want,

Bs'd

Thanks for your help, but I'm a total Linux and Ubuntu illiterate, I installed it a couple of days ago, and don't know nothing.

I don't know how to go to my folder and create a new one.

Can you help me with that one?

Eliyahu  

> 

k then once at root issue

cd /home/<ur username>/the folder u created


then once there

issue the command to install it,

then in advance so u don't ask later

when asking to insert the link to the mozilla folder

cd /home/ur username/.mozilla/plugins

also in the insert symbolic link u'll have to change it a bit and not copy and paste but change the name to the java folder they put in as an example to ur folder...but do that once u cd into the plugins folder.

to see hidden files

in a nautilus windows press ctrl+h

to re-hide - do the same

in linux hidden files are the ones with a dot as the first letter/symble in their name.

---

### Post by nowshining on 2007-12-21
places - home

create a new folder, example scenerio: 


place/home: nowshining

name: javafirefox

put the java bin file into that folder

right-click - select properties - check mark executable and click apply permissions if shown, if not click close.

open up the terminal

issue

sudo /bin/bash

enter ur pw

root@home: cd /home/nowshining/javafirefox

sh (name of java file)

u'll see a license, press enter until u see a line asking if u want to accept - don't worry if u go to far down, just type the letter y and hit enter

let it install

then when asked to go to the plugins folder

issue 

cd .mozilla

cd plugins

and insert the link there, changing the main java folder example (top) for ur folder such as javafirefox

---

### Post by chewearn on 2007-12-21
> **Carnivorum said:**
> Bs'd

Thanks for your help, but I'm a total Linux and Ubuntu illiterate, I installed it a couple of days ago, and don't know nothing.

I don't know how to go to my folder and create a new one.

Can you help me with that one?

Eliyahu

Ok, I thought you are a BSD guru trying to compile java from source.:confused:  That's why I delete my earlier post, which are irrelevant in that case.

But, since you say you are new to ubuntu, then please follow this link:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Carnivorum on 2007-12-28
Bs'd

It's all a bit heavy for me, but I got one step further.   On this page [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)
I got now one step further.  I managed to make a folder, called Java, but when I do step 4: 

	   
To install the Linux (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6u2-linux-i586.bin

There things go wrong.  When I type in the above command, I get the following message:  

chmod: cannot access `jre-6u2-linux-i586.bin': No such file or directory

Now what?

Thanks in advance for the help.


Eliyahu

---

### Post by aysiu on 2007-12-28
> **Carnivorum said:**
> Bs'd

I want to install Java, and after I type su in the terminal, he asks me for my password,

Then I type my password, but he constantly tells me:  Authentication failure

What am I doing wrong?
Try this:
[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

---

### Post by Carnivorum on 2007-12-29
> **aysiu said:**
> Try this:
[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)


Bs'd

That page tells me to go to a page where I'll get a pop-up which will ask me for Java.

But the problem is, I don't get those pop-ups.

And Xboard, a chess client for Linux, works with me.   Can it be that I have Java already?

How can I check that?

The problem is, that when I want to start Frostwire, it won't start, and it tells me that's because I don't have Java.


Eliyahu

---

### Post by meindian523 on 2007-12-29
Try 

```
chmod a+x jre[TAB]
```
It will give you available options,and therefore you won't have any problems with typos......

---

### Post by Carnivorum on 2007-12-29
> **meindian523 said:**
> Try 

```
chmod a+x jre[TAB]
```
It will give you available options,and therefore you won't have any problems with typos......

Bs'd

After that command I get the following message:   

chmod: cannot access `jre[TAB]': No such file or directory


Eliyahu

---

### Post by meindian523 on 2007-12-29
You sure you are in the directory where you copied the Java installation files?

---

### Post by Fixman on 2007-12-29
su asks for the root password, so you can create one or write

```
 sudo -i 
```

Instead of su

---

### Post by meindian523 on 2007-12-29
or as an alternative,you might want to download the rpm and convert it into a deb file using alien,which will lead to a simple double-click,entering of password and installed!

To convert the rpm into deb file,you will need alien
```

sudo apt-get install alien
```

---

### Post by Carnivorum on 2007-12-31
Bs'd

Hello friends!

When I start frostwire with the terminal, I get the following message:  

eliyahu@eliyahu-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
eliyahu@eliyahu-desktop:~$ 

Is here an easy and quick solution for?  Like something I can download from the synaptic package manager or something?

Thanks in advance.


Eliyahu

---

### Post by meindian523 on 2007-12-31
yup,you can search for sun-java5-jre in Synaptic and install from there.Make sure you have universe and multiverse repos enabled.

---

### Post by Carnivorum on 2007-12-31
> **meindian523 said:**
> yup,you can search for sun-java5-jre in Synaptic and install from there.Make sure you have universe and multiverse repos enabled.

Bs'd


It works! 

Thanks a lot.


Eliyahu

---

