---
title: "[SOLVED] apt-get autoremove messed up everything!"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Giamby986 on 2008-02-28
Hi guys, 
I think I've done something **utterly stupid**...
while correcting dependencies for apt_0.7.9ubuntu12_powerpc.deb
using sudo apt-get install -f i've got a message from apt-autoremove...
I said yes... and in no time he started deleting...like 3 tons of stuff I needed!!!
I don't have the list of stuff he wants to remove BUT:: 
[I]synaptic is gone
aptitude is gone
update manager is gone [no big deal... but...]
a lot of other stuff's gone...[/I]
deb packages won't open the usual way but with archive manager...
I've messed up preeeeetty badly my poor xubuntu... now
is there a way to perform some kind of recovery?
like a clean install from the terminal or some recover using another user...
I don't know...
next time i use autoremove I'll keep my eyes** open**...
Hope someone can help...

::Giamby::

---

### Post by jw5801 on 2008-02-28
Yowza! What were you doing trying to install apt? If you're using apt then it's already there!

Hmm... "apt-get" won't be around anymore will it? Well about all I can think of would be to get the deb for apt (for the architecture you have, is it a powerpc?), extract it using the archive manager, and manually install it's files, then see if you can run apt-get again. It goes in /usr/ so the binaries should go in /usr/bin, the libraries in /usr/lib, etc etc. I'm not sure what the internals of a deb are like but I would assume extracting it should produce a few folders (bin, lib) so take whatever is in these folders and move it to /usr/*the-appropriate-folder*

---

### Post by spamzilla on 2008-02-28
Open terminal and run these commands:

> sudo aptitude update

and then

> sudo aptitude upgrade

Does it list all the files it just removed for installation? If it does install them and be more careful ;)

---

### Post by capink on 2008-02-28
Try running this command:

```
sudo apt-get install ubuntu-minimal ubuntu-standard xubuntu-desktop
```


Edit: If apt-get is removed you have to install it first. Download it from [here]("http://mirrors.kernel.org/ubuntu/pool/main/a/apt/apt_0.7.6ubuntu14_powerpc.deb"). and install it using the command:

```
sudo dpkg -i path/to/apt/package
```

if dpkg is removed I think you have to reinstall Ubuntu.

---

### Post by Giamby986 on 2008-02-28
thanks capink...
I've just done what you've suggested::

> **capink said:**
> Try running this command:

```
sudo apt-get install ubuntu-minimal ubuntu-standard xubuntu-desktop
```



With this result::

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-standard is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-minimal: Depends: apt-utils but it is not going to be installed
                  Depends: aptitude but it is not going to be installed
                  Depends: tasksel but it is not going to be installed
  xubuntu-desktop: Depends: gdebi but it is not going to be installed
                   Depends: gnome-app-install but it is not going to be installed
                   Depends: language-selector but it is not going to be installed
                   Depends: synaptic but it is not going to be installed
                   Depends: update-manager but it is not going to be installed
                   Recommends: apport-gtk but it is not going to be installed
                   Recommends: restricted-manager but it is not going to be installed
                   Recommends: ubufox but it is not going to be installed
                   Recommends: update-notifier but it is not going to be installed
E: Broken packages

:(

Obviously all the package listed are the packages erased by autoremove when I get to correct dependencies for apt_0.7.9

I think if I download all the packages listed and install 'em everything should be ok ...right?

Oh and thank you guys for the quick answers!

PS to jw5801
I was trying to install apt_0.7.9 because i need some libraries that apt_0.7.6 hasn't...
that's it :)

---

### Post by igknighted on 2008-02-28
wherever you got the deb for 0.7.9 get all those other packages as well.  They can't install because they _need_ 0.7.6.  What could possibly have been doing that needed you to change the version of apt?  That should never happen.

---

### Post by Giamby986 on 2008-02-28
> **igknighted said:**
> wherever you got the deb for 0.7.9 get all those other packages as well. 
They can't install because they _need_ 0.7.6

Thank you, I've got it now...
I'm working this thing up just now... step by step >.<

> **igknighted said:**
> What could possibly have been doing that needed you to change the version of apt?  That should never happen.

Well... some days ago I got some trouble with gnome-app-install
[and I've also started a thread [::here::]("http://ubuntuforums.org/showthread.php?t=705533")]
so this morning I've tried to install the 0.5.2.4 version...[::the hardy one::]
it ends up it needed some libraries from apt-utils_0.7.9... 
that in the end needs apt_0.7.9 to work... see? Easy!
It can happen lot of times instead...^_^
Then you only need to say Y to apt autoremove in the wrong time... eh
and you got half a nightmare... eh eh :)

---

### Post by Giamby986 on 2008-02-28
...any other suggestions?

---

### Post by ice60 on 2008-02-28
if no one else replies try searching the forum, you should find what you need.
[http://ubuntuforums.org/search.php?searchid=37075963](http://ubuntuforums.org/search.php?searchid=37075963)

---

### Post by jw5801 on 2008-02-28
> **Giamby986 said:**
> Thank you, I've got it now...
I'm working this thing up just now... step by step >.<



Well... some days ago I got some trouble with gnome-app-install
[and I've also started a thread [::here::]("http://ubuntuforums.org/showthread.php?t=705533")]
so this morning I've tried to install the 0.5.2.4 version...[::the hardy one::]
it ends up it needed some libraries from apt-utils_0.7.9... 
that in the end needs apt_0.7.9 to work... see? Easy!
It can happen lot of times instead...^_^
Then you only need to say Y to apt autoremove in the wrong time... eh
and you got half a nightmare... eh eh :)

If you want to use the Hardy version of apt, the easiest thing to do would be to upgrade to Hardy. I'm thinking that your other issue should be solvable without trying to upgrade apt however. Apt is one of those things you shouldn't really try to upgrade, since each version will be dependent on a different version of glibc and libgcc which are libraries that _everything_ else is dependent on. So if apt tries to upgrade glibc and libgcc whilst upgrading itself, it's going to look for upgrades to everything that is directly dependent on them, then, when it can't find any, will tell you autoremove will get rid of redundant packages.

So I personally would be inclined to revert to the Gutsy version of apt and work on gnome-app-install from there. If you download the .deb for your architecture from [here](http://packages.ubuntu.com/gutsy/apt) you should then be able to install it using dpkg.

---

### Post by capink on 2008-02-28
We need to undo any changes you have done to your system. What exactly did you do? How did you install apt_0.7.9? Have you downloaded the package and installed it? Or did you add hardy's repositories to your sources.list?

It seems that some packages that does not belong to your distro is obstructing other packages installation because of dependencies. Please try the following and report back.

1. Open a root subshell

```
sudo -s
```

2. Make an apt_preferences file as follows

```
cat > /etc/apt/preferences << EOF
Package: *
Pin: release v=7.10
Pin-Priority: 1001

EOF
```


3. Run the following commands:

```
apt-get update
```

```
apt-get upgrade
```


This is supposed to downgrade all packages to gutsy's version. If using this method some packages are indeed downgraded, try rerunning the command in my previous post.

---

### Post by Giamby986 on 2008-02-29
Hi guys and thanks capink for the hints!
I've solved everything using apt-get...
I've downgraded from 0.7.9 to 0.7.6 and installed all the package I needed
that were autoremoved... now its all OK :) [I hope]
I thought I can go and put some chunks of hardy into gutsy and so on...
man, that was a good lesson... eheh

Now the last thing to fix [the one I made all this mess for]
is to get gnome-app-install working...
but that's another business I'm talking about [::here::]("http://ubuntuforums.org/showthread.php?t=705533")

This thread here is solved now...
Thanks again everybody!

::Giamby::

---

