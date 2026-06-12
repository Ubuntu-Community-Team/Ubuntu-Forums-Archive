---
title: "Install New &amp; Updated Sun OfficeStar &amp; Skype"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by K7KEV on 2007-03-27
Newbie I am.  This is regarding the adding and updating of program packages.
1.  I note on the Mozilla web site that there is a new ubuntu-related update of Firefox.  The Firefox 1.5 that comes with Ubuntu appears to be superceeded by Firefox 2.0.  The Firefox web shows this Linux upgrade.  After I download it to my desktop, that's where it sits.  I can't get Adept or Synaptic to grab it and install it. 
2.  Same with Skype.
3.  Same with Sun StarOffice 10, that I paid for.

Now that I've kicked XP almost out of my life, I need a hug.  Well, at least an encouraging word.

Keith

---

### Post by scrooge_74 on 2007-03-27
For firefox 2.0 you can use the one inside Ubuntu 6.10.  If the file from the Mozilla Web site you can use the options inside synaptic to install it.  If you have to compile from source follow the instructions.  I still have F 1.5 in a laptop running great, it still gets update under Dapper 6.06

For Skype you only need to add the repository that shows in the [Skype website]("http://www.skype.com/download/skype/linux/repositories.html"), once you add it to your list of repositories you can just tell synaptic to download and install is just as easy as that.

With StarOffice it is been a while since I used it, I am quite happy using Open Office, if SO is a deb package is the same deal using synaptic

---

### Post by K7KEV on 2007-03-27
Much appreciated.  

I guess this means that programs written for other versions of Linux are not easily (if at all) integrated into Ubuntu.    

Now I'm off to figure out how to add a repository. . . .

Thanks again-- Keith

---

### Post by scrooge_74 on 2007-03-28
You can add the repository from inside synaptic or you can make changes to a file call sources.list inside the directory /etc/apt

but you have to be confortable editing files by hand so you better do it from inside synaptic.

You cant installed programs compiled for other distributions, because every flavor of Linux works a little different, when there are no binary files for your particular system then you have to compile from source to get files for your system.

Luckly Debian and Ubuntu have lots of programs already in the repositories

---

