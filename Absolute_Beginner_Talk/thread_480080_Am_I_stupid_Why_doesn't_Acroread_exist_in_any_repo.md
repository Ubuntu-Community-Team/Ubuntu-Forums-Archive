---
title: "Am I stupid? Why doesn't Acroread exist in any repository?"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-06-21
First of all. I Know I installed a bunch of repos  correctly (except for maybe one because I get an error message about a missing public key). The only place on the web that told me the addresses of repositories was some guy called Trevino or Tr3vino. do a google on Feisty Repositories and he'll come up. So I install them after receiving advice to download "acroread" but after doing so (and I got a load of updates from all the new repos so I know they work), I can't find the darn thing. Look: there needs to be a nice, easy LIST of repos one can add. Have I missed it somewhere? How can I get acroread- and no, I don't want anything else. I want acroread.

help me out!

---

### Post by FleetAdmiral74 on 2007-06-21
Do you specifically know that this program should be in the ubuntu repositories, or are you just expecting it to be in there?

---

### Post by NeoLithium on 2007-06-21
Acroread is available in the ubuntu multiverse repositories :)

Oh, as well, the repository list you seek, is at [http://www.ubuntuguide.org](http://www.ubuntuguide.org)  A nice set for whatever version of Ubuntu you may be running.

---

### Post by moonliter on 2007-06-21
Just copy and paste this in terminal then hit enter.It will install acrobat reader for you if you enable it in repositories:


```
sudo aptitude install acroread
```

---

### Post by HotShotDJ on 2007-06-21
> **Protagonistics said:**
>  How can I get acroread- and no, I don't want anything else. I want acroread.First, no, your not stupid.  However, it is bad practice to just add repositories.  You could end up with some serious problems like that.  The [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories, however, provide a great set of add-ons, including acroread, googleearth, as well as many of the multimedia codecs you may need or want.  Be sure to follow the instructions on the page I linked to very carefully.

---

### Post by Protagonistics on 2007-06-21
Yes, I was told that it existed by an Ubuntu user in another post. he only said to make sure "all my repos were on" time for a PM...

---

### Post by NeoLithium on 2007-06-21
Yeah, it is in the repositories. A good, safe guide to adding the extra repositories is right here, that you can follow; which will allow the installation of a great deal of programs:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

If you're not using Feisty, just check the top part of the page for other versions of Ubuntu and follow those pages instead.

---

### Post by Protagonistics on 2007-06-21
Now THIS is what I was looking for!

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Thanks for the help, objective acquired.

---

### Post by girishv on 2007-06-21
When he said,
ALL THE REPOSITORIES ON
he meant, to uncomment the repos which are already there in the list, not to add additional repos

Girish

---

### Post by Anicka on 2007-06-21
I cannot find it either and I know I had it installed in Edgy, but when I updated to Feisty, Acroread disappeared. "aptitude search acroread" gives absolutely nothing and I have all the ubuntu-repos enabled.

---

### Post by PartisanEntity on 2007-06-21
I got it from the Medibuntu repo, it used to be in the Edgy repo but I too could not find in the Feisty repos.

Also make sure to install the acroread-plugins which allow you to fill in PDF forms that are designed to allow user input.

---

