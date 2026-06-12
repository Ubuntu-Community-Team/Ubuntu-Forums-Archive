---
title: "Installing a *.bz2 file. How?"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by Mugzilla on 2005-06-08
Apologies are contained at the end of the post...

Ubuntu Hoary Hedgehog installed as only OS on a P3 800. All components/drivers work. 

I have downloaded MPlayer-1.0pre7.tar.bz2 (I want to play DVDs), a skin, and the codecs.

I figured out how to use the archive manager and "Unzip" (?) it. I made a folder called MPLAYER on my desktop.

I figured out that there is this thing called terminal. I typed:

**sudo apt-get install mplayer-1.0pre7.tar.bz2** 

Terminal tells me the following:

**Reading package lists...Done** 
**Building dependency trees...done** 
**E: Couldn't find package** 
**matt@ubuntul:~$** 


I have this feeling this is a simple fix, but I am stuck.







Noob apology:

Folks, I looked high and low.  I googled "Install Linux software terminal" to no avail. I want to learn Linux, but feel as though there is a NOOB GAP in linux. (I can only find SUPER basic info or developer level stuff.) Please go easy on me.

---

### Post by bored2k on 2005-06-08
1-The apt command can only be used for files from the repositories. 
2-BZ2 is a compressed archive. Extract it with the command tar xjf file.bz2
3-You will have a VERY hard time installing that file. Use this method:
[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)
4- [http://ubuntuguide.org/#dvdplayback](http://ubuntuguide.org/#dvdplayback)

---

### Post by Mugzilla on 2005-06-08
What alternative to this installation style would you recommend? 

Is there another program you would recommend?

It sounds as though this is not the "Ubuntu" way to install something...

---

### Post by bored2k on 2005-06-08
[QUOTE=Mugzilla]What alternative to this installation style would you recommend? 

Is there another program you would recommend?

It sounds as though this is not the "Ubuntu" way to install something...[/QUOTE]
 Read step 3 of my 1st post.

---

### Post by Mugzilla on 2005-06-09
I have updated the sources.list as stated in the repositories. (I removed the # signs as in the example...)

When I run sudo apt-get install w32codecs

matt@ubuntu1:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package w32codecs




(In other words, I am stuck on step 3...)



Once again, THANK YOU for your time. If requested, I will repeatedly bash a wiffle ball bat against my head...

---

### Post by bored2k on 2005-06-09
Ok type sudo gedit /etc/apt/sources.list
Remove everything and replace with this:
> deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse

Then do sudo apt-get update

---

### Post by tread on 2005-06-09
>  I will repeatedly bash a wiffle ball bat against my head 
That would be fun, make a video so I can see it :)

Did you run:
sudo apt-get update 

after adding the repositories? Do that and then do:
sudo ap-get install whatever-package-it-was.

Hope that helps!

---

### Post by tread on 2005-06-09
Edit: crossposted: bored2k beat me to it!

Edit: damn! need to sleep .. meant to edit the above post, not add another. 
And since I hate deleting posts (messes up stuff, esp. if someone sees this and replies, then I deleted so that post is left hanging and so on and so forth :)) I shall let this post stand.

---

### Post by bored2k on 2005-06-09
[QUOTE=tread]Did you run:
sudo apt-get update [/QUOTE]
That is wrong.

---

### Post by bored2k on 2005-06-09
[QUOTE=tread]Edit: crossposted: bored2k beat me to it!

Edit: damn! need to sleep .. meant to edit the above post, not add another. 
And since I hate deleting posts (messes up stuff, esp. if someone sees this and replies, then I deleted so that post is left hanging and so on and so forth :)) I shall let this post stand.[/QUOTE]
 You are thinking things way too much. Good night ;)

---

### Post by Mugzilla on 2005-06-09
[QUOTE=bored2k]Ok type sudo gedit /etc/apt/sources.list
Remove everything and replace with this:

Then do sudo apt-get update[/QUOTE]
 I did the "sudo apt-get update" 

I did **NOT** replace all of the sources.list with
[B]deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
[/B]


I left it the way it was.

Then, I did the "sudo apt-get install w32codecs"

That update line did the trick! I am well on my way!

---

### Post by bored2k on 2005-06-09
[QUOTE=Mugzilla]
I did **NOT** replace all of the sources.list
I left it the way it was.[/QUOTE]
Hey you ask for suggestions, we give you suggestions, but it's still your machina. 

Glad to know something worked.

---

### Post by Mugzilla on 2005-06-09
([TOTALNOOBMODE] So, when I added the "deb" lines to the sources.list , did it:

-Tell Ubuntu WHERE to download the software from, then go fetch them from those places?
- Or did it use the packages that I downloaded earlier?

[/TOTALNOOBMODE]

---

### Post by metallikop on 2005-06-09
[QUOTE=Mugzilla]([TOTALNOOBMODE] So, when I added the "deb" lines to the sources.list , did it:

-Tell Ubuntu WHERE to download the software from, then go fetch them from those places?
- Or did it use the packages that I downloaded earlier?

[/TOTALNOOBMODE][/QUOTE]

When you added the lines to your sources.list and did a sudo apt-get update, you refreshed the list of packages that Ubuntu knows about to include the new lines.  Then when you did an apt-get install PACKAGENAME it downloaded the package from the source in one of the deb lines, it did not use the files that you downloaded.

---

