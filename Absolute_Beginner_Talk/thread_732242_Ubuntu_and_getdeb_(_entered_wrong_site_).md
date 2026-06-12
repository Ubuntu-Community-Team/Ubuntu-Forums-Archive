---
title: "Ubuntu and getdeb ( entered wrong site )"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2008-03-22
Hi, I just installed ubuntu 7.10 and got all the updates for it......
Well, after updating and rebooting I started to customize my
system.... I wanted to go to Getdeb and get some stuff
but instead of typing getdeb.net,,,,,, I typed getdeb.org
and it took me to the wrong site.  The site had 1 advertisement
on it and thats all.... Is this a bad site? Should I be worried it did
something to my system?

---

### Post by scragar on 2008-03-22
I'm guessing it's just one of those bought to try and leech sucess from another site using adverts as a revenue source, avoid it if you can. Same deal with ies4linux.com etc.

and as for it doing anything to your system I would not worry, as long as you didn't download then run any applications your perfectly fine, and if you did then unless you gave it root perms I would not be significantly worried(although I would say to instantly try to find the process and kill it, along with the origionating file etc).

---

### Post by jan quark on 2008-03-22
well it is just a site full with google ads
not very informative, but not very dangerous I guess
not worth a second look I think

getdeb.net is the place you want to go

---

### Post by ugm6hr on 2008-03-22
> **Orbital75 said:**
> Should I be worried it did
something to my system?

No.

If you are particularly concerned about internet security, you can use the Firefox addon NoScript which will limit javascript use on websites you visit.

But unless you enter your administrator password, no websites will be able to cause lasting damage to your system, so it is unlikely you will have problems.

---

### Post by Orbital75 on 2008-03-22
Thank you for your quick responses. I'm sooo new to Ubuntu and Linux, I don't know what can happen... I've been told that Ubuntu is very secure and I shouldn't have to worry about
things like this as I did with Windows..... As far as I know nothing downloaded and I didn't download anything..... 

Now, If I had been installing from the ubuntu repositories and had to enter my password
but closed the repos windows before I went online, would my password still be in affect?
I've heard that it stays active for 15 minutes or something.....?

---

### Post by scragar on 2008-03-22
I'm guessing what your asking, is that if you opened synaptic package manager(and input password when asked), then closed it before downloading anything, if your password would still be in effect?

Where password carry over is somewhat confusing, but the timer is 15 minutes by default. There are a few examples of when and where commands copy over and not, for example:

In a terminal the password need only be entered once of sudo, but every time for gksudo and gksu
If your using 2 different terminals using sudo on the first would not exempt you from passwording the second, same applies to tabs.
gksu remembers that you have entered the password for 15 minutes when launched outside of a terminal, when inside timer lasts only for current terminal session(you type exit, or close the terminal) of 15 minutes, whichever is shorter.

This is not by any means conclusive, and these are only what I observed on dapper, so things may have changed to highten security.
all in all, 3 admin access systems:
**sudo** = command line - remembers being entered for 15 minutes or terminal lifetime, whichever is shorter
**gksudo** = graphical - other gksudo programs will need password entered, since this does not employ the 15 minute timer.
**gksu** = graphical - used for most options by default, remembers itself as entered for 15 mins to save needing to re-enter password when doing lot's of changes.

---

### Post by ugm6hr on 2008-03-22
> **Orbital75 said:**
> Now, If I had been installing from the ubuntu repositories and had to enter my password but closed the repos windows before I went online, would my password still be in affect? I've heard that it stays active for 15 minutes or something.....?

That is strictly true.  "sudo" has a 15 minute logoff time.  It is not recommended you change this time (although I understand this is possible).

If you are concerned, NoScript will ensure nothing runs / downloads withour your express permission.

However, it is unlikely that the occasional use of sudo will be problematic.

---

### Post by Orbital75 on 2008-03-22
Yep.... you guys understood. I was installing some things from the repos
before I went online to some sites such as Gnome-look and getdeb.net

Of course you have to enter your password to get into the repos so 
I'm worried that I still had privileges when I hit that site by accident.
I just install no script but the damage may have already been done.

So, you guys are stating that it is likely that my machine had privileges
when I hit that site because 15 minutes is given to install.

Just want to make sure I understand..... I just installed Ubuntu so
reinstalling this early wouldn't be that big of a deal. It would be a head ache
later on though.....

---

### Post by scragar on 2008-03-22
since firefox isn't launched with root perm's you shouldn't worry, root perm's will only carry over to other applications that are either the children of root applications(like say, synaptic running apt-get) or launched using a root perm's giving command like the 3 I listed earlier.

---

### Post by ugm6hr on 2008-03-23
@OP: I can't see any problems if you didn't click on anything on that getdeb.org website.

@scragar:I don't actually fully understand sudo permissions, but I am interested in this.

As you say, Firefox is not launched with sudo permissions.  However, it can launch sudo tasks if given permission.  For example, if you visit a Flash website, and don't have Flash installed, it will offer to install it for you (asking for your password in the process).

gksudo applications (like Update Manager etc) appear to hold the sudo status open (for 15 minutes, presumably) for any other gksudo programs that are launched.

So presumably it is *theoretically* possible for Firefox to perform admin tasks without your express knowledge....  I appreciate this is extremely unlikely, but was just interested to know how this works.

---

### Post by scragar on 2008-03-23
I'm not completely sure how it work's either, but it looks to be the case that the timer only counts for programs launched from the same source(desktop/menu considered same), for example desktop launchings of synaptic and the users+groups menu would only require the password once, while atempting to launch a .deb install would still ask for the password once you decide to install(works by launching a new task as a child process, adding gksu or gksudo for the password prompt).

another thing I noticed(back on 6.06 atleast) was that gksudo would always ask for the password, even if I entered it previously just a few seconds ago, so perhaphs for people obsessed with security that would be a better choice than gksu as is used by default?

---

