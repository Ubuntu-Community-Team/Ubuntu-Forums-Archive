---
title: "how to get java to work as plugin with firefox"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by sthapit on 2007-05-29
hi.  i went to the synaptic package manager and have sun-java6-jre installed.  it works fine on the terminal, but when i go to any website with java, it says missing plugin... any tips on how to enable java with firefox?

---

### Post by starcraft.man on 2007-05-29
> **sthapit said:**
> hi.  i went to the synaptic package manager and have sun-java6-jre installed.  it works fine on the terminal, but when i go to any website with java, it says missing plugin... any tips on how to enable java with firefox?

Uh, you have to install the plugin separately. To get this done easily, you can use two means:

1) Open terminal (apllications >accessories > terminal) and paste this command in.
```

sudo aptitude install sun-java6-plugin sun-java6-fonts
```

Then restart firefox.

2) or if your more comfortable with synaptic and the GUI, push the search button and search for "java6" and then once the list pops up, check off the entries with "fonts" and "plugin" on the end. 

That should do it :).

I included the fonts package too, you'll likely want that if you didn't previously install it. You can omit it though if you wish. Have fun. :D

---

### Post by Redbomber on 2007-05-30
When I run that command, I get "couldn't find any Couldn't find any package whose name or description matched "sun-java6-plugin"

---

### Post by Seisen on 2007-05-30
It should come up that's weird considering they come from multiverse. Try searching in synaptic to see if its in their.

---

### Post by Redbomber on 2007-05-30
No, not there either.  I have just upgraded from Edgy to Feisty by editing my sources.list file.  That all went fine, but could this be the problem?

---

### Post by Seisen on 2007-05-30
It shouldn't be a problem, you can go here and download the two .deb file and then it will pull anymore dependicies you need. 

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=sun&sourceid=mozilla-search]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=feisty&release=all&keywords=sun&sourceid=mozilla-search")

---

### Post by taurus on 2007-05-30
What about

```
sudo aptitude update
sudo aptitude install sun-java6-plugin sun-java6-fonts
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by Redbomber on 2007-05-30
Still no go.  Here is my sources.list.  Hope I posted it correctly.

```
deb http://au.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

```

---

### Post by Seisen on 2007-05-30
Do you get them from the Ubuntu Muliverse repo or the backports repo I don't remember its been that long?

---

### Post by Redbomber on 2007-05-30
Sorry I'm a newb, so I got no idea.  How do I know?

---

### Post by Seisen on 2007-05-30
Add multiverse to your repository list so it will look like that,

```
deb http://au.archive.ubuntu.com/ubuntu/ feisty universe **multiverse**
deb-src http://au.archive.ubuntu.com/ubuntu/ feisty universe **multiverse**

```

then 

```
sudo apt-get update
sudo apt-get install sun-java6-plugin sun-java6-fonts
```

or you can use aptitude whichever one you prefer. Let me know if works.

---

### Post by Redbomber on 2007-05-30
Hey, that's got it!  Thanks a lot.  The support on this forum is great!  :D

---

### Post by Seisen on 2007-05-30
No problem,

---

### Post by amadeus266 on 2007-05-30
I have followed your directions as well and it seems that everything installed correctly, however java still doesnot work in firefox:frown:


EDIT: I solved this problem with the help of this page: [http://plugindoc.mozdev.org/linux.html#Java](http://plugindoc.mozdev.org/linux.html#Java)

---

### Post by YoG%*@ on 2007-05-30
> **amadeus266 said:**
> I have followed your directions as well and it seems that everything installed correctly, however java still doesnot work in firefox:frown:
i think you also have to install sun-java6-jre:
```

sudo aptitude install sun-java6-jre

```
([http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox"))

---

### Post by nobody13 on 2007-06-04
> **starcraft.man said:**
> Uh, you have to install the plugin separately. To get this done easily, you can use two means:

1) Open terminal (apllications >accessories > terminal) and paste this command in.
```

sudo aptitude install sun-java6-plugin sun-java6-fonts
```

Then restart firefox.

2) or if your more comfortable with synaptic and the GUI, push the search button and search for "java6" and then once the list pops up, check off the entries with "fonts" and "plugin" on the end. 

That should do it :).

I included the fonts package too, you'll likely want that if you didn't previously install it. You can omit it though if you wish. Have fun. :D

Thanks worked great!

---

### Post by santy_kushwaha on 2007-06-04
thanks Guys

it worked i was workin on that for 1 week and didn't figure it out thnkx for ur helps guys

---

### Post by freerick on 2007-06-09
ok, in order to install the java packages using the apt package manager, which is the method that was described above, you need to enable to appropriate repository, so the package manager knows where to look for the package. In this case, you have to enable the multiverse repository which includes packages that may have been developed outside of the open-source community and released under a proprietary license. To add the multiverse repositories, add the following at the end of your /etc/apt/sources.list file:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

You can also use the Synapitc Package Manager to add those repositories via the GUI

---

