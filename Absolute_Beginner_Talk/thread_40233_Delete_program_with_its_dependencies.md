---
title: "Delete program with its dependencies"
date: 2005-06-08
forum: Absolute Beginner Talk
---

### Post by BerryB on 2005-06-08
Hello,

I was configuring my system, I tried some programs that seemed fun, like gDesklets. Now some of them aren't what I supposed they where, so I want to delete them. I installed like so: apt-get install gdesklets. With this install came a whole bunch of dependencies, and since probably no other program will need these, I like them to be removed also. So basicly the system just checking if the installed program has dependencies which can be removed. Now this seems to be a problem, I can't find how to do this... If its possible, can someone tell me how to do so? apt-get remove gdesklets only deletes gdesklets itself, not all those for me useless dependencies (I'm trying to hold my disk space taken as low as possible)

---

### Post by shof2k on 2005-06-08
The easiest way for us newbies is to run synaptic, and select complete removal. That should get rid of the lot.

---

### Post by jdong on 2005-06-08
First, use Synaptic to install deborphan.

Open up a Terminal, and type in **deborphan -nz**. This lists all libraries on your system that are not Required:, Suggested:, or Recommended by any other package on your system.

**NOTE**: Cautiously use this tool. Just because no .deb package depends on a library doesn't mean that nothing on your system needs it! Keep a list (or mental note) of packages that you've removed with deborphan, just in case something goes wrong in the future.


**TIP:** To mass-delete everything deborphan finds, use **deborphan -n | xargs dpkg --remove**. Again, USE CAUTIOUSLY.

---

### Post by ruben_b on 2005-06-08
thanks, i didn't knew that.

but what's about packages allready remove but not with this option?

---

### Post by jdong on 2005-06-08
It's ok. Deborphan is just an informative tool. It goes through all the **libraries** (not programs, that'd be pointless!) in your system and finds the ones that aren't used by any other .deb package installed on your system.

If you remove a program, many of its libraries are orphaned (not needed by anything anymore). Deborphan is specifically for finding these.

---

### Post by ruben_b on 2005-06-08
could you tell us how to use this tool?

---

### Post by BerryB on 2005-06-08
GREAT :smile: Exactly what I'm looking for! So I can just apt-get remove gdesklets, and then remove the dependencies by looking at them with deborphan and delete the libraries with apt-get?

BTW, what is the program 'xargs' and 'synaptic' ?

---

### Post by ruben_b on 2005-06-08
i found it. it should work this way:

sudo apt-get remove $(deborphan)

---

### Post by BerryB on 2005-06-09
Ok, great!

> NOTE: Cautiously use this tool. Just because no .deb package depends on a library doesn't mean that nothing on your system needs it! Keep a list (or mental note) of packages that you've removed with deborphan, just in case something goes wrong in the future. 
Ok, so even if I didn't remove anything there will be some orphanded libraries? Or will those be only there if I compiled something myself, or installed something in another way then by apt-get???

---

### Post by BerryB on 2005-06-09
ok, I deleted the programs with their dependencies  ;-)  But when I was browsing the /usr/share directory, I there are still directories of the deleted programs left... Can I just rm them?

---

### Post by jobezone on 2005-06-10
[QUOTE=BerryB]ok, I deleted the programs with their dependencies  ;-)  But when I was browsing the /usr/share directory, I there are still directories of the deleted programs left... Can I just rm them?[/QUOTE]
 You can delete them yes, or you could have "purged" the packages when removing them? I don't remember the command, but in synaptic it's the option just below remove, called completely remove (or simillar).

Also, to everybody wanting to use deborphan, try it in Synaptic. Go to filters, and create a new filter called Orphan. On the right pane, only activate the deborphan checkbox. Save, and voila, you've got a filter for orphaned packages....

---

### Post by BerryB on 2005-06-10
[QUOTE=jobezone]You can delete them yes, or you could have "purged" the packages when removing them? I don't remember the command, but in synaptic it's the option just below remove, called completely remove (or simillar).[/QUOTE]
Is this only possible with programs you're going to remove, or also with programs you've already removed?

---

### Post by jdong on 2005-06-10
[QUOTE=BerryB]ok, I deleted the programs with their dependencies  ;-)  But when I was browsing the /usr/share directory, I there are still directories of the deleted programs left... Can I just rm them?[/QUOTE]

Umm, unless you REALLY need them to be gone, I don't recommend it. It's generally not a smart idea to mess around by hand in /usr/share, which the dpkg package manager expects full control over.


Next time, PURGE if you want to remove everything.


BTW, the remnants probably occupy a very insignificant amount of space anyway. I wouldn't worry.

---

### Post by BerryB on 2005-06-10
all right, thnx anyway :smile:

---

