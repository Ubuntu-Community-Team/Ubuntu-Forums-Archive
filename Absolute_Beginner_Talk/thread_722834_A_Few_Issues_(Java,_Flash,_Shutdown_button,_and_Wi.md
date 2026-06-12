---
title: "A Few Issues (Java, Flash, Shutdown button, and Wine)"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Airforcefalco on 2008-03-12
Alright well lets start. I followed that one thread on what to do to install flash and i repeated it going to the troubleshooting portion and it worked but if I would go to another window the flash player would go away. Also it doesn't work every time either.

Next I can't get Java to work and i tried installing the packages but nothing happened.

When i hit my shutdown button it seems to take a minute or two before it even pops up on my screen and then during that time the mouse will move but i can not click on anything.

Lastly is there any good tutorial out there on how to use Wine? I would like to use E-Sword (i know there is a Gnome sword but i like e-sword's setup better), play AVP2 and maybe some other games.

Thank you again for all your help!

---

### Post by Airforcefalco on 2008-03-12
I can has help please?

---

### Post by Airforcefalco on 2008-03-12
Basically i need flash for my college classes online I would appreciate the help and i apologize for the lolcatz comment :-D

---

### Post by Airforcefalco on 2008-03-12
also while i am thinking of it can someone please show me the command line that changes to my desktop? For some reason cd desktop doesnt work.

Thanks again!

---

### Post by Airforcefalco on 2008-03-13
Also something else is that my desktop seems to forget what the last image i put as a wallpaper was. Also for some reason it changed the resolution when i first started my computer this morning.

Thanks again.

---

### Post by jan quark on 2008-03-13
_navigating to desktop:_

```
cd /Desktop
```

_flash:_
either
[http://laiconic.quotaless.com/tutorial3.html](http://laiconic.quotaless.com/tutorial3.html)
or
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

_java:_
```

sudo apt-get instal sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by forrestcupp on 2008-03-13
[Here](http://frankscorner.org/index.php?p=e-sword) is a good guide to get e-sword working with wine.  It's pretty easy.

About the Flash thing.  I don't know how you installed it.  If you didn't do this, open Synaptic, go to Settings->Repositories.  Then click the Updates tab and check the boxes next to 'Proposed updates' and 'Unsupported updates.'  Then close the repositories window and click the reload button.  Then you can search for flashplugin-nonfree and it should be one that works good.

About Java, which package did you install?  The correct one to install is sun-java6-plugin.  That one will install all of the necessary files.  It's kind of confusing because there are some packages in there that seem right, but they don't work.  sun-java6-plugin is the one you want.  You may have to restart your browser for it to work.

Edit:
Somebody beat me to it.  You should do the --purge remove of Flash, then follow my directions to set up the extra repositories for a newer version than what is in the default repos.

---

### Post by Airforcefalco on 2008-03-15
How do i purge remove the program?

---

### Post by Mjölner on 2008-03-15
Here are some pages that have helped me on my journey so far...

[Stuff I've learned about Wine]("http://gaming.gwos.org/doku.php/wine:winestuff") for getting my head around Wine.

and

[linuxcommand.org]("http://www.linuxcommand.org/") for the terminal,

I believe 
[PHP]sudo aptitude purge <program name>[/PHP]          
or
[PHP]sudo aptitude remove <program name>[/PHP]    
will purge for you.

---

### Post by cometa2k7 on 2008-03-15
I have that shutdown problem, it's annoying.

It works sensibly sometimes and gives me the options to "suspend" and to "hibernate". I don't get these options when it takes a while.

**[SIZE="5"]PLEASE HELP!!![/SIZE]**

---

