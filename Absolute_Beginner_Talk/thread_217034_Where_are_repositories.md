---
title: "Where are repositories?"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by Bios___ on 2006-07-16
Erm yea? 

where are they? 

As much as I am grateful for the help on this forum, and belive me I am, Im having trouble with understand what to do with certain codes.

I was just told to use firesrtarter, which is in the repositories. :confused: 

Where the hell is the repository, or even what is a repository  ? :S :confused:

I mean I dont know where or what its for.


If anyone thinks im a n00b, your right, majorly.

I do apologize for my ignorance, but I've only used Ubuntu for the first time, for a few hours in total.

Oh I forgot, Im using Ubuntu 5.10- if that helps at all.........

---

### Post by deadgobby on 2006-07-16
Here is some info for you and how to enable extra's
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by bluecherry on 2006-07-16
Repositories are basically collections of packages that were prepared for you r linux installation.

An application that can show you what these repositories (or repo's) contain is called "Synaptic" and can be found under "System > Admin > Synaptic".

If you would like to install firestart, you open Synaptic, click on "Search" and type "firestarter".

Synaptic will search all available packages en show you the results. Right-click on the package firestarter and select "Mark for installation". 

To finalize installation klik the "Apply" button.

Synaptic will now install firestarter and any other application (or packages) that you selected.

Synaptic will also perform configuration, install dependencies (packages needed by the package you want to install), etc... This is also the place to be when you want to remove application.

Hope this little intro had it's use ;).

---

### Post by Bios___ on 2006-07-16
Erm, I did that, and nothing came up :S

No firestarter......

---

### Post by mostwanted on 2006-07-16
Take a look at this, explains most things about software installation that can be confusing to a new user:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Bios___ on 2006-07-16
ok that gave me a better idea, but my actual question is where is firestarter?

its not in the repository.

---

### Post by mostwanted on 2006-07-16
Oh, but it is. The guide explains why it might not be readily available, just give it a little time and try to read all the way through. Heck, just read the headings, there is one that says "What if my app isn't available?" or something like that.

---

### Post by UncleTally on 2006-07-16
Hi, I'm a total noob too, and had the same troubles as you.

You have to load Synaptic Package Manager, then choose Settings, Repositories. In the box that appears you need to select each of the channels one by one, click Add and select the component "Community Maintained (Universe) and click Add. You should then find firestarter by searching in the main Synaptic window.

Hope this helps.

UT

---

### Post by wildseven on 2006-07-16
if you are having problems, it could be that your repositories are hashed. 
type this in terminal
```
sudo gedit /etc/apt/sources.list
```
take out the # infront of all the things that start with deb
then save it.
to get firestarter and install type
```
sudo apt-get install firestarter
```
that should install firestarter.

Repositories, think giant archive of things you can get. apt-get is the command to for packages from the repositories. install is the option. other options are remove which is the option to uninstall a package. i will put examples.
/ex
```
sudo apt-get install xmms
```

this installs xmms which is a music player. Lets say you dont like it and want to uninstall. you would type this

```
sudo apt-get remove xmms
```

to search the repositories the command is a little different.
here is an example. Lets say you need libdvdcss (needed to view encrypted DVS's ) and you arent sure of the name. to search you could type

```
 apt-caches search libdvdcss
```

this will bring up all the packages that has libdvdcss in the name or the information. it will tell you what the packages do.

p.s you dont need sudo for apt-cache search.
p.s.s to be honest i dont really like synaptic, i think its faster and easier to do it all from terminal

hope this helps.

---

