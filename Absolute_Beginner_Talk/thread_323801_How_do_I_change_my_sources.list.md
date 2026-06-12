---
title: "How do I change my sources.list?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-12-22
Mind you, I don't want to edit the list... I've already done that with the help of several threads here and at PsychoCats. The problem is that none of it is working, and I think that's because I'm not using /etc/apt/sources.list at all, but rather /etc/apt/sources.list.d/dapper-universe.list. Firstly, then, how do I check to see what my real sources list is, and secondly, how do I change it. Thanks in advance.

---

### Post by macogw on 2006-12-22
did you "sudo aptitude update" after editting the list?  If you don't do that, you can't get stuff from the things you edited.

Looking in my /etc/apt, there's nothing in /etc/apt/sources.list.d I can't be sure that it's the same on Dapper, but I think it should be.

---

### Post by Sef on 2006-12-22
> Firstly, then, how do I check to see what my real sources list is....

```
gksudo gedit /etc/apt/sources.list
```

Copy and paste it here.  It would be easier to explain how to change it if it could be seen.

---

### Post by macogw on 2006-12-22
Sef, that's not what s/he has a problem with.  S/he thinks synaptic is looking somewhere other than /etc/apt/sources.list to find the repos and wants to figure out exactly where Synaptic is looking.

---

### Post by Sef on 2006-12-22
You're right.  I did misread her post.

---

### Post by ricardisimo on 2006-12-22
> **Sef said:**
> You're right.  I did misread her post.

That's "his" post, which leaves still leaves "him" (me) in the dark. To answer macogw's question, I can't do anything involving the repositories. I keep getting the same line over and over:
```
E: Malformed line 4 in source list /etc/apt/sources.list.d/dapper-universe.list (dist parse)
E: The list of sources could not be read.
```
     This problem led me to the PsychCats' pages, after which I successfully edited the entirety of my sources.list to bring it into the Edgy Century, but to no avail. It doesn't matter, because I appear to using that other list, and therefore need to confirm that and then change it.
     Sef, if you still want to see my sources.list I can post it, but it'll look exactly like what you see on this page: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources). I should probably instead paste here the contents of my sources.list.d/dapper-universe.list. Here it goes:
```
# automatically added by gnome-app-install on 2006-09-22 01:59:33.498379
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-updates
```
I'd be willing to do to this list what I've already done to the other, but I'd rather figure out how to reset which list is being used. Thanks again.

---

### Post by ricardisimo on 2006-12-22
I guess I should have probably also mentioned that I'm on Edgy, not Dapper, as was suggested earlier.

---

### Post by ricardisimo on 2006-12-23
I don't want to edit the list... I've already done that with the help of several threads here, at Ubuntu and at PsychoCats. The problem is that none of it is working, and I think that's because I'm not using /etc/apt/sources.list at all, but rather /etc/apt/sources.list.d/dapper-universe.list.
Whenever I try using apt-get or aptitude, I get some version of basically the same response:
```
E: Malformed line 4 in source list /etc/apt/sources.list.d/dapper-universe.list (dist parse)
E: The list of sources could not be read.
```
I've now changed my sources.list to read exactly as is described [here]("http://www.psychocats.net/ubuntu/sources"), but it matters not, because synaptic et al. are looking at dapper-universe.list, which reads thusly:
```
# automatically added by gnome-app-install on 2006-09-22 01:59:33.498379
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ edgy-updates
```
I just now tried to download the deb for automatix2, to see if that would help me out, and gDebi won't even launch:

```
:~$ sudo gdebi-gtk
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

(gdebi-gtk:18104): libglade-WARNING **: Error loading image: Failed to open file '/usr/share/gdebi/gdebi.png': No such file or directory

(gdebi-gtk:18104): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `logo'
Traceback (most recent call last):
  File "/usr/bin/gdebi-gtk", line 33, in ?
    app = GDebi(datadir=data,options=options)
  File "/usr/lib/python2.4/site-packages/GDebi/GDebi.py", line 71, in __init__
    self._cache = MyCache(self.cprogress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 36, in __init__
    self.open(progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 53, in open
    self._cache = apt_pkg.GetCache(progress)
SystemError: E:Malformed line 4 in source list /etc/apt/sources.list.d/dapper-universe.list (dist parse), E:The list of sources could not be read.
```

I should mention that I am on Edgy, and that this whole debacle began with installation problems with Audacious; it wouldn't install properly, and after several tries I finally decided to try to add the Audacious Ubuntu download repository to my software sources dialog.
Now here I am, throwing myself at your gentle mercies. Pity me. I am not an animal. TIA.

---

### Post by ricardisimo on 2006-12-23
I just now tried to download the deb for automatix2, to see if that would help me out, and gDebi won't even launch:

```
:~$ sudo gdebi-gtk
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

(gdebi-gtk:18104): libglade-WARNING **: Error loading image: Failed to open file '/usr/share/gdebi/gdebi.png': No such file or directory

(gdebi-gtk:18104): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `logo'
Traceback (most recent call last):
  File "/usr/bin/gdebi-gtk", line 33, in ?
    app = GDebi(datadir=data,options=options)
  File "/usr/lib/python2.4/site-packages/GDebi/GDebi.py", line 71, in __init__
    self._cache = MyCache(self.cprogress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 36, in __init__
    self.open(progress)
  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 53, in open
    self._cache = apt_pkg.GetCache(progress)
SystemError: E:Malformed line 4 in source list /etc/apt/sources.list.d/dapper-universe.list (dist parse), E:The list of sources could not be read.
```

I'll keep on searching.

---

### Post by Sef on 2006-12-23
> E: Malformed line 4 in source list /etc/apt/sources.list.d/dapper-universe.list (dist parse)

> # automatically added by gnome-app-install on 2006-09-22 01:59:33.498379
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates

Try commenting out line 4.   To comment out a line, but a # before it, like in line one.   Let's see if it works then.

(When you comment out a line, the machine will not read it.)

---

### Post by Sef on 2006-12-23
>  # automatically added by gnome-app-install on 2006-09-22 01:59:33.498379
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates


I see something in line 4: ubuntu/ edgy-updates.  After ubuntu there is a /.   Remove the / and see if the problem clears up.

---

### Post by randiroo76073 on 2006-12-23
Have you tried:  sudo apt-get update ?  Another thing to try is cut/paste contents of /etc/apt/sources.list.d to another folder of your choice, then sudo apt-get update, if it's needed it will be rebuilt.

---

### Post by dbbolton on 2006-12-23
i deleted all of the content in my sources.list file, saved it, and then just checked the repositories i wanted to use in synaptic.

---

### Post by ricardisimo on 2006-12-23
> **Sef said:**
> I see something in line 4: ubuntu/ edgy-updates.  After ubuntu there is a /.   Remove the / and see if the problem clears up.

The slash was fine, or at least it made no difference, so I commented the line out as per your previous suggestion. There are still problems and error messages aplenty, but at least I have ***some*** access to the repositories. What is still unresolved is why I can't use my brand-spanking-new /etc/apt/sources.list. Why is it it that I can copy and paste the King James Bible into that file or even delete it entirely and it would make no difference? It's just bizarre.

---

### Post by macogw on 2006-12-23
I don't get why it's even looking in /etc/apt/sources.list.d/whatever There shouldn't BE anything in that folder to begin with.

---

### Post by Sef on 2006-12-23
> I don't get why it's even looking in /etc/apt/sources.list.d/whatever There shouldn't BE anything in that folder to begin with.

Why is it doing it is the question that I am asking, but I have no answer at this point.  If you have an idea, please post it.   She would like to resolve her problem.

---

### Post by ciscosurfer on 2006-12-23
> **Sef said:**
> Why is it doing it is the question that I am asking, but I have no answer at this point.  If you have an idea, please post it.   She would like to resolve her problem.To everyone:

**According the man page for sources.list**

SOURCES.LIST.D
       The  /etc/apt/sources.list.d  directory   provides   a   way   to   add
       sources.list  entries in seperate files that end with .list. The format
       is the same as for the regular sources.list file.

So, unless you've got different sources listed in the /etc/apt/sources.list.d/dapper-universe.list file (or if you do, you can consolidate those sources into one singular sources.list file if you want).  Otherwise, you can probably just delete that dapper-universe.list file.

The you should update and dist-upgrade. :D

---

### Post by ricardisimo on 2006-12-23
> **ciscosurfer said:**
> To everyone:

**According the man page for sources.list**

SOURCES.LIST.D
       The  /etc/apt/sources.list.d  directory   provides   a   way   to   add
       sources.list  entries in seperate files that end with .list. The format
       is the same as for the regular sources.list file.

So, unless you've got different sources listed in the /etc/apt/sources.list.d/dapper-universe.list file (or if you do, you can consolidate those sources into one singular sources.list file if you want).  Otherwise, you can probably just delete that dapper-universe.list file.

The you should update and dist-upgrade. :D

OK... Please understand that I've got a genuine - and, I think reasonable - fear of the consequences of deleting the only file that seems to be working with regards to accessing repositories. What do I do? Just move it to the trash?

---

### Post by randiroo76073 on 2006-12-23
Cut/paste into folder of choice for backup.  You can always copy/paste back if not satisfactory :D
This keeps you protected & backed up

---

### Post by ricardisimo on 2006-12-23
> **randiroo76073 said:**
> Cut/paste into folder of choice for backup.  You can always copy/paste back if not satisfactory :D
This keeps you protected & backed up

I ran sudo nautilus instead to delete it, but whatever... Amazing. I deleted that list and voila. Everything's fine now. How the hell does that work? Can someone explain to me what just happened? Unfortunately, now I'm back to square one: trying to install Audacious and get my system sounds back. Wish me luck.

---

### Post by missmoondog on 2006-12-23
it worked because you were actually using the correct file. pretty simple.
the rest should be just as simple.

---

### Post by ricardisimo on 2006-12-23
One last question: Can I delete the entire folder /etc/apt/sources.list.d? I only deleted the dapper-universe.list, but if I can get rid of the whole thing that would be fine by me.

---

### Post by ciscosurfer on 2006-12-23
> **ricardisimo said:**
> One last question: Can I delete the entire folder /etc/apt/sources.list.d? I only deleted the dapper-universe.list, but if I can get rid of the whole thing that would be fine by me.We all have sources.list.d directories -- only some of us use it (couldn't tell you who though) to allow for allowing for multiple sources lists.  There's no reason to remove that directory.  It's causing no harm.  If there were certain repositories that were listed in the dapper-universe.list file that were different from what was located in your sources.list, then you can copy those entries over to your regular souces.list, so, the bottom line is that now apt is reading in or parsing only one souces.list to update its package list.  

The point is: if you want or have a need (can't figure out why anyone would really want to do it though) to have separate souces lists, then separating them into multiple lists is one of doing it.  I suppose, let's say, you're a developer or a tester and you have a desire to literally keep testing or development repos separate from your regular repos, then splitting them up would make some sense.  But there's really no reason to do.

Hope that helps.  And I'm glad you've got everything back up and running!  :D

---

### Post by ricardisimo on 2006-12-28
Have there been any system updates in the past few days? I've come to expect that telltale orange dot, and I'm surprised if more than a day goes by without it. So now it's been four days since I thought that I had this problem resolved, and no updates. Here's the expurgated (I'll send the entire thing if anyone wants it) version of what I get when I run apt-get update:
```
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/non-free/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/free/source/Sources.gz  404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/non-free/source/Sources.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```
Thanks for your help.

---

### Post by taurus on 2006-12-28
Looks like that site, [http://packages.freecontrib.org/](http://packages.freecontrib.org/), is either dead or off the net!  Therefore, edit your /etc/fstab and put a # in front of it.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Then, see if there is any updates...

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by ricardisimo on 2006-12-28
> **taurus said:**
> Looks like that site, [http://packages.freecontrib.org/](http://packages.freecontrib.org/), is either dead or off the net!  Therefore, edit your /etc/fstab and put a # in front of it.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Then, see if there is any updates...

```
sudo aptitude update
sudo aptitude upgrade
```

I'm assuming you mean /etc/apt/sources.list, or no?

---

### Post by taurus on 2006-12-28
Yes, the /etc/apt/sources.list, not the /etc/fstab...

---

### Post by ricardisimo on 2006-12-28
Hmmm... I guess it's just that there haven't been any updates. Oh, well... Thanks again.:-D

---

### Post by ciscosurfer on 2006-12-29
> **ricardisimo said:**
> Hmmm... I guess it's just that there haven't been any updates. Oh, well... Thanks again.:-DThe PLF repository for Ubuntu has been shut down.  New maintainers for Ubuntu are supposed to take the reigns soon.  More to follow >> [http://plf.zarb.org/](http://plf.zarb.org/)

Comment out those lines in your sources.list for now or find another repo that satisfies the debs that you need to update from those repos.

---

### Post by ricardisimo on 2006-12-29
> **ciscosurfer said:**
> The PLF repository for Ubuntu has been shut down.  New maintainers for Ubuntu are supposed to take the reigns soon.  More to follow >> [http://plf.zarb.org/](http://plf.zarb.org/)

Comment out those lines in your sources.list for now or find another repo that satisfies the debs that you need to update from those repos.

Any recommendations? Thanks.

---

### Post by ciscosurfer on 2006-12-29
> **ricardisimo said:**
> Any recommendations? Thanks.Which apps are you trying to grab from the old PLF repos?  List them and we can tell you where to get new ones.

---

