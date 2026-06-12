---
title: "Ipod/Installing stuff in general"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by SilverDragon on 2007-01-10
Okay this seems like a really simple question for someone how knows how to use Linux.

If I was going to install gtkpod, I would just go to the website, download it to my desktop(or wherever else), go to the terminal and type 

sudo apt-get install gtkpod

right?

Or am I just really to used to Windows and not transitioning well:-D 

When I try that I get this error:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gtkpod

I have a feeling there's a simple solution to this :-D 

I was referring to this link: [http://www.ubuntuforums.org/showthread.php?t=103071](http://www.ubuntuforums.org/showthread.php?t=103071)
to get information

---

### Post by kj1h234lkj1234 on 2007-01-10
That is the correct command, however, you need to enable the extra software repositories.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

By default, Ubuntu only uses a few repositories, but there are many more you can enable.

You can also go to System -> Administration -> Software Sources and check all the boxes instead.

---

### Post by jml on 2007-01-10
There is a much easier way to install the application you want.  The reason your first try was not successful was because Ubuntu does not look for applications to install on the desktop.  What you should do is to use either the add/remove program application or, (my favorite,) Synaptic.  These applications will not only download the application you want, but also check for and handle any dependancy issues (other programs or libraries needed,) and do the actual installation.  In the long run it will save you a whole lot of hurt.  You can install a package manually using the dpkg command, but it does not check for dependancies, and it does not  register the application with the package management software which can cause a lot of problems in the future.  Hope this helps.

Joe

---

### Post by meng on 2007-01-10
Also, if you are using Dapper (6.06) as your profile suggests, then you may consider using aptitude instead of apt-get. It has a very similar functionality and syntax, e.g.:
sudo aptitude install <name of package>
but it has smarter UNINSTALLING capabilities that will remove unneeded software if you change your mind.
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
explains the differences between aptitude and apt-get
[www.psychocats.net/ubuntu](www.psychocats.net/ubuntu)

---

### Post by SilverDragon on 2007-01-10
@kj1h234lkj1234

Thanks I followed the link and got it to install correctly

@jml

From what you said, it seems using the dpkg command is not as good as using the add/remove program application or Synaptic, but would using:

sudo apt-get install <name of package>

result in the same thing as dpkg? Eh I'm not really sure what the dpkg command does.

And "it does not register the application with the package management software"
Would the package manangement software be the add/remove program application or Synaptic or something else?

@meng

I will check out those links tomorrow :-)


Apparently I'm just starting to use Linux, but I think I'm liking it ;-)

---

### Post by NeoLithium on 2007-01-10
dkpg installs a .deb file; basically when you run apt-get install (or aptitude install- which is what I prefer) it handles that for you; downloads and installs.  Apt-get and aptitude check for any dependencies which might be missing; but dpkg doesn't, it's basically expecting you to be ready to install it.

---

### Post by SilverDragon on 2007-01-11
Well one thing I'm not sure about is when I try to install amarok and I use

sudo apt-get install amarok

it seems to be working.

But when I use:

sudo aptitude install amarok 

it comes up to what looks similar in the terminal, but when it asks me to put in my installation CD(something like Debian i386 cd) and I hit enter, it just ends up closing on me without installing anything, but it works when I use the apt-get command?

---

