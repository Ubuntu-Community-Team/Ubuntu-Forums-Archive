---
title: "Wine Error: Newb Assault"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by Deten on 2008-02-23
sudo apt-get remove wine
E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list


How can I fix this... im following the instructions to install the latest wine version according to this page

[http://ubuntuforums.org/showthread.php?t=624644](http://ubuntuforums.org/showthread.php?t=624644)

but I cannot remove the current version due to this error.

Thanks

---

### Post by Deten on 2008-02-23
Im not sure what im doing but I read somewhere to post this... ? 

cat /etc/apt/sources.list.d/winehq.list

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<html>
 <head>
  <title>Index of /apt/sources.list.d</title>
 </head>
 <body>
<h1>Index of /apt/sources.list.d</h1>
<table><tr><th><img src="/icons/blank.gif" alt="[ICO]"></th><th><a href="?C=N;O=D">Name</a></th><th><a href="?C=M;O=A">Last modified</a></th><th><a href="?C=S;O=A">Size</a></th><th><a href="?C=D;O=A">Description</a></th></tr><tr><th colspan="5"><hr></th></tr>
<tr><td valign="top"><img src="/icons/back.gif" alt="[DIR]"></td><td><a href="/apt/">Parent Directory</a></td><td>&nbsp;</td><td align="right">  - </td></tr>
<tr><td valign="top"><img src="/icons/unknown.gif" alt="[   ]"></td><td><a href="dapper.list">dapper.list</a></td><td align="right">18-Jan-2007 22:17  </td><td align="right">151 </td></tr>
<tr><td valign="top"><img src="/icons/unknown.gif" alt="[   ]"></td><td><a href="edgy.list">edgy.list</a></td><td align="right">18-Jan-2007 22:17  </td><td align="right">139 </td></tr>
<tr><td valign="top"><img src="/icons/unknown.gif" alt="[   ]"></td><td><a href="etch.list">etch.list</a></td><td align="right">26-May-2007 21:49  </td><td align="right">160 </td></tr>
<tr><td valign="top"><img src="/icons/unknown.gif" alt="[   ]"></td><td><a href="feisty.list">feisty.list</a></td><td align="right">26-May-2007 21:47  </td><td align="right">181 </td></tr>
<tr><td valign="top"><img src="/icons/unknown.gif" alt="[   ]"></td><td><a href="gutsy.list">gutsy.list</a></td><td align="right">17-Oct-2007 00:21  </td><td align="right">181 </td></tr>
<tr><th colspan="5"><hr></th></tr>
</table>
<address>Apache/2.2.3 (Debian) PHP/5.2.0-8+etch10 Server at wine.budgetdedicated.com Port 80</address>
</body></html>

---

### Post by jrusso2 on 2008-02-23
Thats really confusing it looks like html. Your only supposed to add one of the lines depending on your distro.  If your running gutsy the line should look like this

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

But I don't think you need to do that unless you want the most current wine.

I think you just needed to enable the multiverse  repository in synpatic repository

I am on another distro atm so I can't check my sources.lst

---

### Post by Deten on 2008-02-23
> **jrusso2 said:**
> Thats really confusing it looks like html.
Im not sure what your asking, im not too savvy with linux/ubuntu

---

### Post by JoshuaRL on 2008-02-23
Yeah, not sure what that is.  Can you go into either Add/Remove or Synaptic to remove Wine?  Might be easier than through the terminal.

---

### Post by Deten on 2008-02-23
> **JoshuaRL said:**
> Yeah, not sure what that is.  Can you go into either Add/Remove or Synaptic to remove Wine?  Might be easier than through the terminal.
When I try to add-remove I get this error...

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

sudo apt-get update gives me the same error as above

---

### Post by JoshuaRL on 2008-02-23
Okay, try:
```

sudo dpkg --reconfigure -a
sudo apt-get install -f

```

And if that doesn't work go into System->Administration->Synaptic Package Manager.  Go to the filters and look for the "Broken" filter.  Reinstall anything on there, and see if update and upgrade works.

---

### Post by Deten on 2008-02-23
> **JoshuaRL said:**
> Okay, try:
```

sudo dpkg --reconfigure -a
sudo apt-get install -f

```

And if that doesn't work go into System->Administration->Synaptic Package Manager.  Go to the filters and look for the "Broken" filter.  Reinstall anything on there, and see if update and upgrade works.
[B]stephen@stephen-laptop:~$ sudo dpkg --reconfigure -a
[sudo] password for stephen:
dpkg: unknown option --reconfigure
[/B]
Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

**stephen@stephen-laptop:~$ sudo apt-get install -f**

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.

-----------
You sure that command is right? 

Going to the Synaptic Package Manager gives me the same error as the first post.

---

### Post by JoshuaRL on 2008-02-23
Okay, sorry:
```

sudo dpkg--reconfigure -a

```

As far as the sources list, please post this:
```

gksu gedit /etc/apt/sources.list

```

---

### Post by Deten on 2008-02-23
stephen@stephen-laptop:~$ sudo dpkg--reconfigure -a
[sudo] password for stephen:
sudo: dpkg--reconfigure: command not found
stephen@stephen-laptop:~$ sudo dpkg--reconfigure -a
sudo: dpkg--reconfigure: command not found

Not sure what to do about that... but heres the second one, though if you look at my first post the error was in the winehq.list

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by warbird on 2008-02-23
should be "dpkg reconfigure", no dashes

edit: and the interesting part isnt in sources.list, its in
/etc/apt/sources.list.d/winehq.list    -- thats where the error lies.

---

### Post by Deten on 2008-02-23
i threw that command into google and it came back with 

sudo dpkg-reconfigure -a

only 1 dash, that command ran and its in the midst of doing its work... ill update after.

---

### Post by Deten on 2008-02-23
This is doing alot of stuff, and im kinda freaked out a little...

what exactly is this doing to my computer haha

---

### Post by JoshuaRL on 2008-02-23
It's okay, that command is supposed to help the debian package tool "dpkg" to fix itself if anything goes wrong.

If it's doing anything, then that's a good sign things are getting fixed.

---

### Post by Deten on 2008-02-23
Yeah its like completely resetting everything, i dont even know what im doing I just hit enter for defaults

---

### Post by JoshuaRL on 2008-02-23
Sounds good to me man.  Unless you know what you're doing, leave anything like this to the defaults.

---

### Post by Deten on 2008-02-23
You would think an error in winehq.list would not require an entire reset of debian package tool... i guess i'll trust your judgement

---

### Post by JoshuaRL on 2008-02-23
I believe both dpkg and apt run off of the sources.list, so if something like that was messed up and especially if an install of a package was interrupted than it could goof up dpkg.

---

### Post by Deten on 2008-02-23
Yeah whatever this is, is not the best move... its still going, resetting everything... hell it even wants me to specify what hp printer I have... I HAVE NONE?! so I would suggest giving a disclaimer when you throw out that suggestion to use that command because its very invasive.

Regardless, ill post if it worked when its done.

---

### Post by Deten on 2008-02-23
Same error, this did not fix the problem.

---

### Post by Deten on 2008-02-24
I just saved all my important files to an external drive and formatted/reinstalled ubuntu... such a shame but i guess some problems are pretty damn complicated.

---

