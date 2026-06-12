---
title: "Unable to install ANYTHING"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by say592 on 2007-12-23
I have successfully installed Ubuntu, but when I go to install drivers or any other thing, it wont allow me to.

Everything says its incompatible with my processor, because it is not i386. I know this isnt the case though, because I have an Intel Pentium processor. 

Im trying to install the nVidia drivers, so it is pretty important to be able to get them working.

---

### Post by as0l0 on 2007-12-24
i barely remember having this problem when i first installed, but i think the solution was to change the sources for updates.  i believe i changed it from Australia to Main Site.

---

### Post by forestpixie on 2007-12-24
have your sources been commented out - if you didn't have a working net connection when you installed they would have been disabled

edit your sources.list

```
gksudo gedit /etc/apt/sources.list
```

Edit - oops

---

### Post by autocrosser on 2007-12-24
Goto Menu>Add/Remove Applications--start the app & search for Nvidia. Make sure that you "Show all available applications"

You will most likely be told you need to allow extra repositories--do so.

Another way to open things up is: Menu>System>Administration>Software Sources
You will be asked for a password (yours) & in the first window---check all the boxes--download from the main server & close. You will be told it needs to update sources--do so.

Then goto Synaptic (same sub-menu area) & search for Nvidia. You should now be able to D/L the drivers you need.

---

### Post by hyper_ch on 2007-12-24
what are you trying to install?

---

### Post by forestpixie on 2007-12-24
> Im trying to install the nVidia drivers, so it is pretty important to be able to get them working.this I believe :)

---

### Post by hyper_ch on 2007-12-24
where did you get that from?

nVidia should be installed through the restricted driver maanger...

---

### Post by forestpixie on 2007-12-24
the first post - and yes so it should :)

I think it's one of those  - "ubuntu installed without a working net connection and all the repos get commented out in the sources" - threads

---

### Post by autocrosser on 2007-12-24
That is what it sounded like to me also.......

---

### Post by hyper_ch on 2007-12-24
> **forestpixie said:**
> the first post - and yes so it should :)

I guess it's still too early in the morning for me ;) my apologies

---

### Post by forestpixie on 2007-12-24
still to early here as well, been up for 2 hours - woken with a plaintiff cry of - 'is it xmas yet dad'- grrrr

that's successfully made the day longer than it needed to be :)

---

### Post by autocrosser on 2007-12-24
Yes--tis' about 12 here--I just wandered away from Hardy-land (all is well there--no broken software to have fun with :(  )--So I thought to lend a hand  ;)

---

### Post by as0l0 on 2007-12-24
> **forestpixie said:**
> the first post - and yes so it should :)

I think it's one of those  - "ubuntu installed without a working net connection and all the repos get commented out in the sources" - threads

so the error is 'your machine isn't an x86"?  someone might want to look at that one :/

---

### Post by forestpixie on 2007-12-24
yea probably so - but a quick search would have pointed in the right direction as well I thiink :)

---

### Post by say592 on 2007-12-24
Ok, I think I got it. I had to enable some boxes in the software sources.

Im downloading the drivers right now, Ill let you guys know if there are any more problems.

---

### Post by forestpixie on 2007-12-24
my bad - there's a typo :oops:

sort one thing first then we can look at the graphics card issue 

do this in a terminal and paste the output

```
cat /etc/apt/sources.list
```

---

