---
title: "installing ubuntu-dektop from command line"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by vinu76jsr on 2007-10-19
my ubuntu gutsy gui accidently get uninstalled by me 
I want to know how to reinstall it
I can access shell 
and please tell e the required repositories

---

### Post by ice60 on 2007-10-19
do you remember what you did to uninstall it? it will be easier to reverse it if you say. if it was something in the terminal you can press the up arrow key to see the last commands you ran.

however, this should install the ubuntu desktop -
sudo aptitude install ubuntu-desktop

---

### Post by staffie2001uk on 2007-10-21
Newby question:  Where do I find the package - ubuntu desktop ? 

I used the command line you specified and it sad it couldn't find the package. 

To elaborate: I have installed the server version and want the GUI for ease of use.  

TIA.

---

### Post by Hobo Joe on 2007-10-21
Well, you'll want to check your repos, which are located in your source.list file, to get to it type:
```

sudo nano /etc/apt/sources.list

```
Make sure that all the repositories are enabled(If they have a '#' in front of them they are disabled), except for the CD ones.

Then once you have done that run the command:
```

sudo aptitude install ubuntu-desktop

```

---

### Post by staffie2001uk on 2007-10-21
I removed the # from in front of all the repositories - pretty much every one had # in front and a line above saying it was commented out because the installer could not verify it. 

Used ^O and then ran the install command.  Same result, no package with that name found. 

Still puzzled.

TIA.

---

### Post by Maestro23 on 2007-10-21
> **staffie2001uk said:**
> I removed the # from in front of all the repositories - pretty much every one had # in front and a line above saying it was commented out because the installer could not verify it. 

Used ^O and then ran the install command.  Same result, no package with that name found. 

Still puzzled.

TIA.

When you finished your edits in nano, you did CTRL+O, then CTRL+X right?

Then do a :

> sudo aptitude update


Then try the package again.

---

### Post by staffie2001uk on 2007-10-21
I had written the edited file out, but I hadn't done the update. 

That appears to have sorted it. 

Thank you very much. 

Col.

---

