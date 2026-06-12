---
title: "What do all these extentions mean?"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-10
Ok..... so I would like to install TrueCrypt. I've been looking at different programs
and have notice that there are all different ways to install something...

for instance I installed a program earlier that just require I download a .tgz
file. Open it then just run a .sh file inside of it.

Then I downloaded Truecrypt and it's a .tar.gz
When I open the .tar.gz up I find a .deb
Which I assume is debian which is what Ubuntu is
based off of ( Right? )
So what do you do with the deb file now?

What do all these extensions mean? 
I'm pretty sure tar is like a Zip file right?

Could someone explain to me a little about installing programs and these
file extensions.

Also, I'd like to know when I would have to do it from source and
what goes into that.

Also, is /usr/lib like program files in Windows?
I'd like to put all my programs in one place so I
know where they're at.....

Thanks

---

### Post by Steveway on 2007-08-10
$sudo apt-get install truecrypt
Or use Synaptic and search for truecrypt.
Learn to use the Packagemanager first before you got to a site and download a program.

---

### Post by Orbital75 on 2007-08-10
Hi SteveWay, thanks for posting and helping me with my question...
I've used the Add and Remove program under Applications
and it works great but I have noticed that alot of programs
I would like are not in there.  Maybe it's somewhat limited.

I have also tried out the Synaptic Package Manager
and had some success with it. I've search a few times
in there to find dependences. 

With these installation tools, I find it just throwing the
package or program on the computer and not telling me
where it's going.  I'd like to put all my programs in
a folder like Program Files does on Windows. Just to
keep everything neat and easy to find.  

I'd just like to know what all the extensions mean
and  when a program needs dependencies.
It seems the package manager does it all for
me without telling me anything.

I also searched for Truecrypt in Synaptic Package Manager
and it didn't find anything. I have all the boxes checked
Universe, Mutiverse, and Restricted

---

### Post by Steveway on 2007-08-10
If you compile yourself, then it will install itself to several directories.
Configuration files in /etc configuration files wich are user-specific go to a hidden directory in /home/username, binarys go into /usr/bin or sometimes /usr/local/bin, libraries /usr/lib and /usr/local/lib and so on.
Don't bother to change this, it's good like it is.
.tar are packaged files and .gz or .bz mean that it is compressed.
You can learn all those things by using Google.

---

### Post by overdrank on 2007-08-10
> **Orbital75 said:**
> Hi SteveWay, thanks for posting and helping me with my question...
I've used the Add and Remove program under Applications
and it works great but I have noticed that alot of programs
I would like are not in there.  Maybe it's somewhat limited.

I have also tried out the Synaptic Package Manager
and had some success with it. I've search a few times
in there to find dependences. 

With these installation tools, I find it just throwing the
package or program on the computer and not telling me
where it's going.  I'd like to put all my programs in
a folder like Program Files does on Windows. Just to
keep everything neat and easy to find.  

I'd just like to know what all the extensions mean
and  when a program needs dependencies.
It seems the package manager does it all for
me without telling me anything.

I also searched for Truecrypt in Synaptic Package Manager
and it didn't find anything.

Hi maybe this link will help a little
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by Orbital75 on 2007-08-10
> **overdrank said:**
> Hi maybe this link will help a little
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

Wow, what a great link !!!!!  Thank you.

---

### Post by bwtranch on 2007-08-10
Hi Orbital, thanks for making the leap. But, I have to tell you there are some major differences here between windoze and Linux. First of all, you didn't have a place in win where all your "program files" went. It stuck files allover your system that it accessed. What do you think all those .dll files were doing there? All that dir entry was just a script (and you can learn to write one yourself ) that told the OS where to find the files and load them to run the program. 

Think about it, if every program had to have everything that it needed to run, it would take a day to load, another day to run, and you would be out of HDD space in less time than that.

Linux takes a more hands on approach and let's you specify the directories where you want things to go. There are conventions, but you don't have to follow them (but, I recommend that you do, because they are there for a reason). Stick with the Gnome apt (add/remove) until you get a better handle on what I am telling you. It will give you your apps by cat and pretty much take care of you. You can, after that, get a little more adventuresome and read about how to install from source and about proper file management and you may run across some that I have written.

I wish you luck and please don't try to compare this with windoze, because the sheep are without a coat. :)

---

### Post by Orbital75 on 2007-08-10
> **bwtranch said:**
> I have to tell you there are some major differences here between windoze and Linux. First of all, you didn't have a place in win where all your "program files" went. It stuck files allover your system that it accessed. What do you think all those .dll files were doing there? All that dir entry was just a script that told the OS where to find the files and load them to run the program. 

Linux takes a more hands on approach and let's you specify the directories where you want things to go. There are conventions, but you don't have to follow them (but, I recommend that you do, because they are there for a reason). Stick with the Gnome apt (add/remove) until you get a better handle on what I am telling you. It will give you your apps by cat and pretty much take care of you. You can, after that, get a little more adventuresome and read about how to install from source and about proper file management and you may run across some that I have written.

I wish you luck and please don't try to compare this with windoze, because the sheep are without a coat. :)

I see.... I didn't think about .dll files. 
There certain programs that I would like to install that
are not in the add/remove or Synaptic Package Manager.
For example TrueCrypt...... I would just like to know how
to install programs such as this and know where things go.

As you said "There are conventions, but you don't have to follow them (but, I recommend that you do, because they are there for a reason)". 
I can break the OS, I'm using a VM so all I have to do is just reinstall my Snapshot. This VM is for learning so I can ultimately switch and then run 
Win in a VM where it should be in the 1st place.

I've installed a great deal with the add/remove and Synaptic Package Manager.
I just feel like their doing everything for me.  I want to know what's going on
behind the scenes. I want to get my hands dirty ......

---

