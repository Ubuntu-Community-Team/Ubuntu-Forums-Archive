---
title: "Adding third party software"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Jet8225 on 2007-12-16
Okay, I opened the software sources and and clicked on the third party software tab. Clicked on the add button to try to install http//:packages.ubuntu.org but it wouldn't let me click "add source". Help with this, please.

---

### Post by overdrank on 2007-12-16
> **Jet8225 said:**
> Okay, I opened the software sources and and clicked on the third party software tab. Clicked on the add button to try to install http//:packages.ubuntu.org but it wouldn't let me click "add source". Help with this, please.

Hi and are you following a guide?

---

### Post by Jet8225 on 2007-12-16
Yes, I was reading this one: 
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by overdrank on 2007-12-16
> **Jet8225 said:**
> Yes, I was reading this one: 
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Ok and there are a lot of good links on that page. But what guide are you using try to edit and add repos to your system.

---

### Post by rune0077 on 2007-12-16
You need to put "deb" in front of the address. So the correct format is:

*deb <http address of software repo>*

This should make the "Add Source" clickable.

---

### Post by Jet8225 on 2007-12-16
I added the deb but it still doesn't let me.

---

### Post by rune0077 on 2007-12-16
That's weird. Post the repo you want to add, and I'll try adding it to mine, that way we can see if it's just your system that's screwed up, or if it's the repo's fault.

---

### Post by Jet8225 on 2007-12-16
with deb it would be 'deb [http://packages.ubuntu.org](http://packages.ubuntu.org)'

---

### Post by rune0077 on 2007-12-16
Try adding /gutsy in the end of it.

So: deb [http://packages.ubuntu.org/gutsy](http://packages.ubuntu.org/gutsy)

that should do the trick.

---

### Post by Jet8225 on 2007-12-16
I get an error when I close it, and if I put deb [http://packages.ubuntu.org/gusty](http://packages.ubuntu.org/gusty) it didn't let me but it did if I put deb http packages.ubuntu.org/ gutsy and when I closed it it says there was an error

---

### Post by philinux on 2007-12-16
edit

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

---

### Post by Jet8225 on 2007-12-16
I'm sorry, but I put the wrong link, instead of .org it's .com. But I still keep getting the same error when I close the window.

---

### Post by Achetar on 2007-12-16
Execute the following command in the Terminal:
```

sudo synaptic

```
Then enter your password.
Open the Settings menu and click Repositories. Now add the repo (dont forget the deb part of it!)

---

### Post by rune0077 on 2007-12-16
Nah, turns out mine won't load either. Adding / gutsy main loads in additional packages apparently, but then gives me an error that the repos can't be contacted or some such. Either the repos you are trying to add a no longer active, or you've got the wrong adress for them. Maybe try and google the repos name, see if something comes up.

---

### Post by Jet8225 on 2007-12-16
> **rune0077 said:**
> Nah, turns out mine won't load either. Adding / gutsy main loads in additional packages apparently, but then gives me an error that the repos can't be contacted or some such. Either the repos you are trying to add a no longer active, or you've got the wrong adress for them. Maybe try and google the repos name, see if something comes up.

It's a website I've entered many times. It's practically the way I install everything.... [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

### Post by rune0077 on 2007-12-16
Oh, isn't that a list of the software in the packages that already shipped with Ubuntu? I just checked out some of the software from the site, and I was able to install it through Synaptic. 

In software sources, make sure you have both the main, universe and multiverse repos selected, then search for anything on that site in Synaptic (System > Administration > Synaptic Package Manager) and it should be available already.

---

### Post by Jet8225 on 2007-12-16
I'm still getting the same errors, and I got the Main, Universe and multiverse selected. Some of the packages in that site are in synaptic but everytime I try to download one of those it depends on one that isn't in synaptic, and when I try to do it with apt-get or aptitude it's very rare that it works. It always says something about the package not found.

---

### Post by rune0077 on 2007-12-16
That's very weird. To the best of my knowledge, nothing from those repos should depend on anything not included with them (I may be wrong in this, but I'm pretty sure). Sounds like there's something messed up with your software sources somewhere.

---

### Post by Jet8225 on 2007-12-16
maybe, but I guess I'll just go to the website and install everything I need from there.

---

### Post by thelatinist on 2007-12-16
Post the output of
```

cat /etc/apt/sources.lst
```

---

### Post by Jet8225 on 2007-12-17
```
jesus@jesus-laptop:~$ cat /etc/apt/sources.lst
cat: /etc/apt/sources.lst: No such file or directory
```

Was that supposed to happen?

---

### Post by philinux on 2007-12-17
cat /etc/apt/sources.list

---

### Post by thelatinist on 2007-12-17
> **Jet8225 said:**
> It's a website I've entered many times. It's practically the way I install everything.... [http://packages.ubuntu.com](http://packages.ubuntu.com).

[http://packages.ubuntu.com/](http://packages.ubuntu.com/) is NOT a repository, so it is no wonder you haven't been able to add it to your sources.lst   The page you are looking at just provides information about all the packages that are available in the repositories.  

I'm sorry, but I think you don't quite understand software installation in Ubuntu.  In Ubuntu you don't need to download packages from a website.  Ubuntu has "package management" software which automatically finds and downloads software from what are called repositories...servers specifically dedicated to sending you packages.If you want to install something, just do the following:

```

sudo apt-get update
sudo apt-get install *package-name*
```

where package name is the name of the package you wish to install.

If you prefer a graphical way of installing, software is also available through Applications > Add/Remove... or by going to System > Administration > Synaptic Package Manager.  Search for the software you want to install, and it will find it.  Check the boxes to add the software and click Apply.

---

### Post by Jet8225 on 2007-12-19
I know I can install it that way but most of the times it says that I couldn't install it.

---

### Post by rune0077 on 2007-12-19
Reading through some of the other threads around here, this might actually be a firewall problem. If you have Firestarter installed, try turning it off while you do the downloading. If you don't have it installed, feel free to ignore this post.

---

### Post by Jet8225 on 2007-12-19
I don't have a firewall installed, but it's okay. If aptitude doesn't work I know where to get them.

---

### Post by thelatinist on 2007-12-19
> **Jet8225 said:**
> I know I can install it that way but most of the times it says that I couldn't install it.

What error message do you get?  That seems to be the real issue we should be working on.

---

