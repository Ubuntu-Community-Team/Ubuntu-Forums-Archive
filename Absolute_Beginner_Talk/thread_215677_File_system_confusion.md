---
title: "File system confusion"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2006-07-14
I am stil a bit confused regarding the layout of linux's file system. 

I have read that /opt is a good place to put add-on programs so I initially thought that this would be a good place to put my geronimo server for development. But, I can only put things in this directory as super user. Which leads me to think that I should use my /home/me diretory for this sort of thing so I am not constatly using sudo or I don't have to change permissions on something that I should probably leave alone right?

Also, when using the synaptic package manager to install new programs why doesnt' it tell you were thigns are going? In Windows (sorry to use that word here) it tells you the dir it's going to be installed, but ubuntu or linux in general just put's it where ever when using the managers anyway. 

Thanks for the help!

---

### Post by Brunellus on 2006-07-14
Ubuntu tends to put packages from Synaptic into /usr as I recall.  Exact placement isn't important, as the package also tells the package manager where all the files are.  If you like, this is better than Windows, which makes it incumbent upon you, the user, to remember/know where all files/libraries/registry entries are located...

you can, in fact, put programs into your home directory.  In fact, if the program won't be made available to all users on the computer, it's probably a good idea to do so.  I understand that that's how it used to be, back in the day.

---

### Post by cjnkns on 2006-07-14
ok thanks..

If I put all the new progrmas.. such as geronimo in my home directory then if I create a new user accoutn i wouldn't be able to access that particular server (unless I install it for the new user also) is there a dir or somwhere that is considered an alternative or a standard way to do something like this?

---

### Post by kripkenstein on 2006-07-14
You can find out where programs are installed, by doing 'properties' in Synaptic, then 'installed files'. This will show you all of the installed files for that package (much better than Windows, I hope you agree :) ).

Generally you shouldn't need this, though. You can run commands by their name in a shell, or in the GUI. Leave it to the package managers to decide where to install things, you don't need to know such details.

If you have a program that *isn't* from a package, then you need to decide where to put it, of course. If only you will use it, then home is a reasonable choice.

---

### Post by cjnkns on 2006-07-14
/home directory it is! Thanks for all the help...

---

