---
title: "Reinstall part of  Feisty"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Rosemere on 2007-07-24
I have not resolved any of the issues I have with Feisty Ubuntu 7.04 so I have this idea.

If I have the disk or can download from the internet, is it possible to just reinstall synaptic Product Manager or Add/Remove from applications. Maybe this would save a lot of time.

---

### Post by deadgobby on 2007-07-24
OK what did you do or what do you want to do? Please by all means go into details.
Gobby

---

### Post by Rosemere on 2007-07-24
Using Ubuntu 7.04. I was trying to install flash player and somehow I have done something incorrect. 
I cannot go into Synaptic Manager by this method of : system administration
synaptic package manager. 
When I do this I get the following error.
E: Type 'deb-sr' is not known on line 5 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

When I go to Add/Remove Applications I get the following message:
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I can get to soft ware sources in Synaptic by right clicking Update Manager on the toolbar and going to preferences. 

I also have another post here which was started because I was missing the less file. Maybe the two problems are tied together

Below is part of source files: I have been told to change deb-sr to dec-scr on line “five”  BUT is that really line 4  on my computer 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) feisty universe restricted main

deb-sr

c [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties



## Major  bug fix updates produced after the final release of the

## distribution.



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.gksu gedit /etc/apt/sources.list

If you can give me some simple directions as to how to repair it would be great.
__________________

---

### Post by Orochi on 2007-07-24
This line:

> **Rosemere said:**
> 
deb-sr

c [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

Should look like this:

```
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ feisty universe restricted #Added by software-properties
```

That is, make it all on one line by deleting the newlines between "-sr" and "c"

---

### Post by Seisen on 2007-07-24
After you follow what Orochi told you make sure that you reload your source list by putting in the terminal or using synaptic

```
sudo apt-get update
```

---

### Post by Rosemere on 2007-07-27
I still haven't resolved how to change the code. I open Terminal and when I have the list files **what or where do I change** so that I have the following .  I really think Linux is a lot more difficult than Windows and I would consider myself no newbie there.

deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

---

### Post by ubuntu27 on 2007-08-15
> **Rosemere said:**
> I still haven't resolved how to change the code. I open Terminal and when I have the list files **what or where do I change** so that I have the following .  I really think Linux is a lot more difficult than Windows and I would consider myself no newbie there.

deb-src [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

You are using Ubuntu (GNOME) right?

so open the Terminal (Applications/Accessories/Terminal)

and write the following:

```
sudo gedit /etc/apt/sources.list
```

Replace

c [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) feisty universe restricted #Added by software-properties

to this:

```
deb-src http://ubuntu.mirrors.tds.net/pub/ubuntu/ feisty universe restricted #Added by software-properties
```


Save it, and close it.

Now type

```
sudo apt-get update
```

---

