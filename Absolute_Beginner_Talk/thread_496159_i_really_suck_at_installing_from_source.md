---
title: "i really suck at installing from source"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by dracomordag on 2007-07-08
so just for the hell of testing it out, i try to download and install [OnTV](http://johan.svedberg.com/projects/coding/ontv/). i get the .tar.gz, and according to the [readme](http://svn.gnome.org/viewcvs/ontv/trunk/README?view=markup), it's as simple as >   1. ./configure --prefix=/usr
    2. make
    3. make install (as root)
    4. Restart bonobo-activation-server
       (killall bonobo-activation-server; killall gnome-panel)
so ./configure --prefix=/usr goes fine, but as soon as i type "make" i get > david@office-desktop:~/Desktop/ontv-2.6.0$ make
make: *** No targets specified and no makefile found.  Stop.

i've failed to install so many programs from source, that i've since just about given up. I couldn't get deluge to install, i can't get sunbird to install... the list goes on.

what the hell is wrong with me, and how can i fix it?

---

### Post by taurus on 2007-07-08
Can you post the complete output when you run the first command from a terminal?

```
./configure --prefix=/usr
```

---

### Post by felicity on 2007-07-08
I'm not sure why it isn't working for you, but there are .debs for ontv at [this link]("http://mirror.linux.org.mt/mirror/ubuntu/pool/universe/o/ontv/")

Deluge now has ubuntu debs on their site for 0.5.2.  (though I was able to get it installed from source OK)

If it makes you feel any better, I couldn't get sunbird installed from source either.

---

### Post by eternalsword on 2007-07-08
Just the basics, but I have to ask, have you installed build-essential via synaptic or apt?  If not, you won't be able to compile anything and would explain your troubles.

---

### Post by Anonii on 2007-07-08
> **eternalsword said:**
> Just the basics, but I have to ask, have you installed build-essential via synaptic or apt?  If not, you won't be able to compile anything and would explain your troubles.
He would get a related message (not beeing able to find the make package etc.). He doesn't, so the problem doesn't lie there.

I guess that the ./configure wasn't succesfull, and as taurus said, the output will show if that's the case.

---

### Post by dracomordag on 2007-07-08
turns out my pythons arent fully updated and i dont have pygobject

i'll update them, and that should solve the issue

EDIT: problem solved. now the issue is that it's not in my programs list... its not anywhere. any thoughts? i'll check the OnTV site

---

### Post by Anonii on 2007-07-08
> **dracomordag said:**
> turns out my pythons arent fully updated and i dont have pygobject

i'll update them, and that should solve the issue

EDIT: problem solved. now the issue is that it's not in my programs list... its not anywhere. any thoughts? i'll check the OnTV site
That's normal. Building from source will not create a desktop entry for you. You will either have to create it, using an application like alacarte, or just run it from the terminal (Even tho I don't know the application, I think that **ontv** on the terminal would do it.).

---

### Post by dracomordag on 2007-07-09
are you telling me that there is no way to add a program to the menu bar?

btw, with OnTV, its placed in the panel, so no worries.

---

### Post by dorath on 2007-07-09
You can add things to the menu via System --> Preferences --> Main Menu.

Select menu you wish the item to appear under (left side), then click New Item (upper left side).

---

### Post by ramjet_1953 on 2007-07-09
Don't forget, when "rolling your own" you almost certainly also need the development packages, as well as the regular package for an application.

eg libassa3.4-0  AND libassa3.4-0-dev

Regards,
Roger 8)

---

### Post by godd4242 on 2007-07-12
> **ramjet_1953 said:**
> Don't forget, when "rolling your own" you almost certainly also need the development packages, as well as the regular package for an application.

eg libassa3.4-0  AND libassa3.4-0-dev

Regards,
Roger 8)

That has to be the most intensely awesome expression for installing from source I've ever heard in my life

Kickass

---

### Post by deadlikeoscar on 2007-07-13
My professor used that term for compiling a kernel as well. 

Don't forget that Subversion can be a good way to install programs as well.

---

