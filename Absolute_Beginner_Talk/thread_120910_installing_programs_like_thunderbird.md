---
title: "installing programs like thunderbird"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by mbmack on 2006-01-23
hi, I just got my ubuntu cd in the mail and installed on my old laptop.  I was surprised that its working lol.  other than my sound not working im happy.  but i want to install thunderbird that i just downloaded (i dont like evolution).  I dont have a clue as to how.  I extracted it and its in a folder on my desktop but there is no setup. i assume i need some kind of installer. thanks in advance for your help. Oh and another thing, it runs slower than win 98.

---

### Post by aysiu on 2006-01-23
Go to Applications > Accessories > Terminal and type these commands: ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
```

If you prefer to do it graphically, go to System > Administration > Synaptic Package Manager, click **Reload**, and then search for Thunderbird and right-click it, mark it for installation, then click **Apply**.

---

### Post by mbmack on 2006-01-23
didnt work and this is what i got.

mark@ubuntulaptop:~$ sudo apt-get update
Reading package lists... Done
mark@ubuntulaptop:~$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree... Done
Package mozilla-thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-thunderbird has no installation candidate
mark@ubuntulaptop:~$

---

### Post by mbmack on 2006-01-23
I guess it has something to do with where the downloaded programs are.  It has been extracted and its on my desk top.

---

### Post by aysiu on 2006-01-24
Your *sudo apt-get update* didn't pop up anything. It should have a long list, like this: ```
sudo apt-get update
Password:
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:5 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:6 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Get:7 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 59.4kB in 1s (32.3kB/s)
Reading package lists... Done
``` Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by mbmack on 2006-01-24
what you saw was it. I didnt get any of that.

> mark@ubuntulaptop:~$ sudo apt-get update
Reading package lists... Done
mark@ubuntulaptop:~$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree... Done
Package mozilla-thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-thunderbird has no installation candidate
mark@ubuntulaptop:~$

---

### Post by AndyCooll on 2006-01-24
Aysiu is indicating that your sources.list might be empty, hence the reason you're not getting the long list he displayed. As he requested, please post the output of this command:

```
cat /etc/apt/sources.list
```

Thanks
:cool:

---

### Post by Mustard on 2006-01-24
[QUOTE=mbmack]I guess it has something to do with where the downloaded programs are.  It has been extracted and its on my desk top.[/QUOTE]

The way that Aysiu is showing you is the proper way to install Thunderbird using the online repository of over 17,000 packages, ready to install, that Ubuntu has at its disposal.  The method you are using of installing Thunderbird is not really necessary and the two methods are unrelated.

What you need to do is to fix your sources.list, which for some reason is not as it should be by default.  To analyse the problem we really need to see your sources.list from the /etc/apt/ directory.  Using the above command will do that for us.

---

### Post by mbmack on 2006-01-24
sorry it took so long i had to work. Here is what it says.

mark@ubuntulaptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
mark@ubuntulaptop:~$

---

### Post by noumaan on 2006-01-24
I am also facing exactly the same problem when I tried to install thunderbird using apt-get via terminal.

---

### Post by aysiu on 2006-01-24
Believe it or not, your sources.list (though long) is almost entirely empty.

The only repository in there is your installer CD.

Every # is called a "comment out."
If you look carefully, you'll notice almost every single repository has a # in front of it, meaning that it's not being read.

To get up-to-date repositories, see the first link of my signature.

Or... just remove all the # signs from the lines that look like web addresses.

**P.S.** Out of curiosity, how did you end up with that sources.list? That's not the default.

---

### Post by mbmack on 2006-01-24
well to be quite honest being that this is the beginner forum, im not sure that i even know what a source list is or even a repository for that matter. lol all I know is i want to install thunderbird on my computer and they said to type that stuff in the terminal.  So why the source list and not just download and install?  Anyway I'll try to make it work I'll go and try to get the up-to-date repositories like you suggested.  Thanks for your help.

---

### Post by mbmack on 2006-01-24
ok I got the up-to-date repositories and as soon as i did I had a bunch of updates to install.  Thanks for your help, i think i can figure it out now (with the help of the links in your sig).  The only problem now is trying to get my sound to work and speed it up.  I'm open to suggestions. lol.  It still works better than i thought it would and i am using my old laptop (amd k6II 266).  If it works this good on here it should do better on my newer desktops.

---

### Post by Mustard on 2006-01-24
[QUOTE=noumaan]I am also facing exactly the same problem when I tried to install thunderbird using apt-get via terminal.[/QUOTE]

I would suggest you likewise check our sources.list.  Click on the link in Aysiu's signature and follow the instructions on how to set up the extra repositories (multiverse and universe).

---

### Post by mbmack on 2006-01-24
ok it's installed thanks.

---

### Post by aysiu on 2006-01-24
[QUOTE=mbmack]well to be quite honest being that this is the beginner forum, im not sure that i even know what a source list is or even a repository for that matter. lol all I know is i want to install thunderbird on my computer and they said to type that stuff in the terminal.  So why the source list and not just download and install?[/QUOTE] Well, the *second* link of my signature explains everything, but I'll give you a quick and dirty.

1. Installing from repositories is a lot easier. With one command in the terminal or a few clicks in Synaptic, I can download *and* install the application (or several applications).

2. The repositories are easier to search, as you can search by description and/or name, and all the results are software that's easily installable.

3. The repositories help you keep *all* your installed programs up-to-date (well... security-wise, anyway).

4. The repositories are a trusted source.

---

### Post by mbmack on 2006-01-24
thanks, i appreciate the explanation and i also appreciate your patience.  I'm learning slowly but surely lol

---

