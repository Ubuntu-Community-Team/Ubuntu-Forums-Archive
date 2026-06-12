---
title: "Question about Super-user stuff"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Hesthrim on 2007-10-15
Greetings and Salutations!  I'm a (very) new linux user, so I'm sure I'm missing some of the basics, but..

I'm trying to install ATi graphics drivers (official, from the site) for a Radeon 9600XT gpu, but every time I go to install it I'm told I have to be a super-user.  There's only one login on this (brand new) install of Ubuntu, but I'm guessing this is some kind of admin priviledge level I have to activate manually..?

After some research, I found the 'su' command for the terminal, but this command asks me for a password.  I tried nothing, and 'su', and 'password', but they were all incorrect.  So my question is, on a fresh install of Ubuntu with no other user accounts, how do I enable super-user status so I can install the ATi drivers?

Thanks a ton for reading (and hopefully posting)!!

Hesthrim

---

### Post by Siph0n on 2007-10-15
try su and the password u created for your one account :)

---

### Post by twiceasworn on 2007-10-15
In ubuntu to do anything that changes your system you must invoke sudo.  This gives you super-user privileges for 15 mins at a time.  To do this you just put sudo before whatever command you are giving.  For example:

```
sudo ./configure --with-whatever
```

or 
```

sudo rm -rf mydirectory/ 
```

to get to a root prompt you can do a 
```

sudo -i 
```

Basically put sudo before any command that will change your system, even moving files and deleting them.  Pretty much if you ever get a 'you must be super-user to do this...' type of error, putting sudo in front of the command will usually fix it.

---

### Post by Hesthrim on 2007-10-19
That's great info, thanks!

Will this work if I'm not entering commands via Terminal, but clicking around in the GUI?  The ATi driver package is a self-installer, and I've got the icon on my ... is it still called the desktop in Linux?  Anyways, the desktop-type area. So if I use the sudo command in the terminal, and then click on the icon for the ATi drivers, will it work?

I'll try it when I'm home tonight and see either way, I guess.  Thanks again!

---

### Post by mlentink on 2007-10-19
> **Hesthrim said:**
> Will this work if I'm not entering commands via Terminal, but clicking around in the GUI?  The ATi driver package is a self-installer, and I've got the icon on my ... is it still called the desktop in Linux?  Anyways, the desktop-type area. So if I use the sudo command in the terminal, and then click on the icon for the ATi drivers, will it work?

I'm afraid it's a bit more specific than that. But what you could do it you wanted to do file manipulations for some time, is start up a file-manager session as 'super user' (that's  essentially what 'sudo' means: as Super User DO...):
```
sudo nautilus
```
but quite frankly, I'd personally just run the relevant app by typing it's name in terminal, preceded with 'sudo'.

---

### Post by Hesthrim on 2007-10-19
Ok..

Feel free to answer this with a thread link, or info or whatever, but I've actually looked around and can't find an answer to this (too) simple question.  

Is there  a place/link/site/book that can give me the basics of using the Terminal or command line interface in Linux? Obviously (and I did try it, just for kicks) DOS style commands won't work, in the same way that you can't code in C++ with OOT syntax. 

So I need to learn the basics of entering commands in Linux.  I mean, the really really basic basics, like file tree system and philosophy, changing directories, running executables (except they're not executables in Linux, are they?)  and other really simple stuff. 

I want to help myself and not rely on the forums for every niggling little issue I have, but I need the resources.. any suggestions?  I'll condition this by saying I've checked all the "New to Linux?" type threads, here and elsewhere on the net, and while there are many useful HOWTO type threads, I haven't found any that tell me the absolute basics of using commands in linux.


And as soon as I figure out how to launch the self installer from the command line, I'll give that a try. Thanks again for your continued help.

---

### Post by mlentink on 2007-10-19
linuxcommand.org

Go for it!

---

### Post by Hesthrim on 2007-10-19
Holy crap, that's EXACTLY what I'm looking for!!  This site should be a link on a Sticky thread.. every new Linux user should be made aware of its existence!

Seriously, this is perfect. Thanks so much!

---

### Post by aysiu on 2007-10-19
> **mlentink said:**
> I'm afraid it's a bit more specific than that. But what you could do it you wanted to do file manipulations for some time, is start up a file-manager session as 'super user' (that's  essentially what 'sudo' means: as Super User DO...):
```
sudo nautilus
```
but quite frankly, I'd personally just run the relevant app by typing it's name in terminal, preceded with 'sudo'. Or, better yet, ```
gksudo nautilus
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by mlentink on 2007-10-19
Hesthrim,[B][I]

trust Aysiu[/I][/B]. Never failed me...

---

