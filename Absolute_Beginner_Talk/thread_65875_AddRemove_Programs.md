---
title: "Add/Remove Programs"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-09-15
I try to access Add/Remove and it jsut hangs there?

any ideas how to sort that?

--
sophtpaw

---

### Post by orev on 2005-09-15
synaptic?

try:  (I assume you do this though..)

sudo apt-get update

sudo apt-get upgrade

I notice that some little niggles are worked out on upgrade....


???

Good luck..

---

### Post by grj on 2005-09-15
Try going to a terminal window and type

sudo apt-get install bible -s (or any other app you do not have)
when prompted for a password, enter your current user password

If you get errors there is something wrong with apt, if not it is something else and you can use apt at the command line until you get it fixed.

---

### Post by Irony on 2005-09-15
Perhaps something to do with Smeg or python-xdg? From my notes;

Smeg has some problems. Remove Smeg via Synaptic.
Also find;
python-xdg
Then;
Package > Force version
Install (downgrade) the old Ubuntu version to 0.9-1 and all will be well.

---

### Post by sophtpaw on 2005-09-15
[QUOTE=orev]synaptic?

try:  (I assume you do this though..)

sudo apt-get update

sudo apt-get upgrade

I notice that some little niggles are worked out on upgrade....


???

Good luck..[/QUOTE]

yeah, nice try Orev,

unfortunately nothing as simple  :roll: 

--
sophtpaw

---

### Post by sophtpaw on 2005-09-15
[QUOTE=Irony]Perhaps something to do with Smeg or python-xdg? From my notes;

Smeg has some problems. Remove Smeg via Synaptic.
Also find;
python-xdg
Then;
Package > Force version
Install (downgrade) the old Ubuntu version to 0.9-1 and all will be well.[/QUOTE]

hmm...do not want to downgrade.
Add/Remove Packages is not vital afterall. just nice to have things working. I can get what i need from Synaptic, in this case it was Epiphany. Which i had tried initially to get from Add/Remove which is when i noticed that it wasn't working. 

--
sophtpaw

---

### Post by sophtpaw on 2005-09-15
[QUOTE=grj]Try going to a terminal window and type

sudo apt-get install bible -s (or any other app you do not have)
when prompted for a password, enter your current user password

If you get errors there is something wrong with apt, if not it is something else and you can use apt at the command line until you get it fixed.[/QUOTE]


I can confirm that there is not problem with apt-get or Synaptic. Now how are you suggesting i use apt-get to fix Add/Remove Packages?

--
sophtpaw

---

### Post by jeffreyvergara.NET on 2005-09-17
I also have this problem only after I made a full system update (ubuntu update manager)

---

### Post by mustang on 2005-09-18
I also have this problem and have no idea how to fix it...

---

### Post by UbuWu on 2005-09-19
[QUOTE=sophtpaw]I try to access Add/Remove and it jsut hangs there?
[/QUOTE]

Are you running breezy? Is it fully up to date with all updates?

---

### Post by sophtpaw on 2005-09-19
[QUOTE=UbuWu]Are you running breezy? Is it fully up to date with all updates?[/QUOTE]

Sorry, one should always specify:

Hoary/Ubuntu

yes, everything is upgraded and updated

--

sophtpaw

---

### Post by UbuWu on 2005-09-19
On hoary the add/remove programs is buggy and not very useful. This is one of the things that will be greatly improved in breezy. For hoary, I'd suggest using synaptic.

If you want to see what it will look like see here: [http://shots.osdir.com/slideshows/slideshow.php?release=430&slide=24](http://shots.osdir.com/slideshows/slideshow.php?release=430&slide=24)

---

### Post by sophtpaw on 2005-09-19
[QUOTE=UbuWu]On hoary the add/remove programs is buggy and not very useful. This is one of the things that will be greatly improved in breezy. For hoary, I'd suggest using synaptic.

If you want to see what it will look like see here: [http://shots.osdir.com/slideshows/slideshow.php?release=430&slide=24](http://shots.osdir.com/slideshows/slideshow.php?release=430&slide=24)[/QUOTE]


Kool and thorough selection of screenshots. I'll practice patience and wait for the full version of Breezy to be released. In the meantime i agree that Synaptic replaces add/remove programs well enough

thx again


--
sophtpaw

---

### Post by TristanMike on 2005-09-19
The problem lies with the python-xdg package, if you find it via synapic you can "Force Original Hoary Version", this will solve it, however, you will constantly have the package wanting to update itself, so in turn you'll constantly have the "update" icon in the taskbar, furthermore, you will have to continually make sure that you don't update it when you update everything else.

Of course, you could go [ here](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871) and apply the fix, but why would you want to do that?

 :razz:  :)

EDIT: I didn't notice my first "fix" had already been mentiond, oops, shoulda fully read.  8-[

---

### Post by redmoon on 2005-09-24
Can someone please tell me how exactly i install that patch?

Cheers.

---

