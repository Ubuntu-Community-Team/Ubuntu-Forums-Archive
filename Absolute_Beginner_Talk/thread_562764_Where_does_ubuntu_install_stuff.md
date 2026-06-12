---
title: "Where does ubuntu install stuff?"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Innomen on 2007-09-29
Day 1 newb, expect a lot of me.

installed pidgin via the whole ...

wget [http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb](http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb)

sudo dpkg -i pidgin_2.0.0beta7devel.vicox-1_i386.deb

...thing

it shows up in the synaptic manager but not in the Internet menu where it's supposed to, and i have setting from windows pidgin i'd like to copy over, something i don't even know can be done but before i ask people how to do that i'd like to try it myself

... but for the life of me i cant work the search thingy (does it look everywhere by default? i see no place to specify), and therefor cant find where that command installed pidgin. when i click search and just type in pidgin i get the folder where i copied over the windows install. "pidgin portable"

Pardon me if that laughable, but hey what are newbs for :P

So to sum up my question is, how does search work, can i make it be more specific, and where are applications typically installed. is there a "program files" equivalent?

thank you for your time.

---

### Post by snake444 on 2007-09-29
i dont know about pidgin but most of apps are installed to your home folder
/home/user/.NameOfApp/
you can see hiden folders (that starts with .) by pressing ctrl+h

and you didnt need to install the program from wget and dkpg you can open Add\remove programs and search there the pidgin or the needed program

---

### Post by Daveth on 2007-09-29
same error I made!  See this for a similar and correct answer

[http://ubuntuforums.org/showthread.php?t=512489](http://ubuntuforums.org/showthread.php?t=512489)

Thanks to Nekiruhs for putting us straight .

---

### Post by por100pre1 on 2007-09-29
> **Innomen said:**
> Day 1 newb, expect a lot of me.

installed pidgin via the whole ...

wget [http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb](http://vicox.net/ubuntu/pidgin_2.0.0beta7devel.vicox-1_i386.deb)

sudo dpkg -i pidgin_2.0.0beta7devel.vicox-1_i386.deb

...thing

it shows up in the synaptic manager but not in the Internet menu where it's supposed to, and i have setting from windows pidgin i'd like to copy over, something i don't even know can be done but before i ask people how to do that i'd like to try it myself

... but for the life of me i cant work the search thingy (does it look everywhere by default? i see no place to specify), and therefor cant find where that command installed pidgin. when i click search and just type in pidgin i get the folder where i copied over the windows install. "pidgin portable"

Pardon me if that laughable, but hey what are newbs for :P

So to sum up my question is, how does search work, can i make it be more specific, and where are applications typically installed. is there a "program files" equivalent?

thank you for your time.

Whoever made that package should have kept that in mind.
First, lets verify that pidgin can run by typing pidgin. Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
which pidgin
```

if you get something like this: /usr/bin/pidgin pidgin is fine. Open Main Menu

```
alacarte
```

click internet at left, then click new element. Now you can make a new launcher the command to use is pidgin .

---

### Post by Innomen on 2007-09-29
Ahhh neato, thanky that made it all sparkly. I even managed to get my settings across, of course I cheated and used google.

what was confusing is the app is named pidgin but the settings are still stored in .gaim. Kinda confusing, but i'll muddle through, i'm done with closed source. 

i'll try not to gush at how mindbogglingly awesome this is so far.

Thank you for the data. :)

Edit: did i mention you all rock? Yes, yes i just did.

---

### Post by por100pre1 on 2007-09-29
> **Innomen said:**
> Ahhh neato, thanky that made it all sparkly. I even managed to get my settings across, of course I cheated and used google.

what was confusing is the app is named pidgin but the settings are still stored in .gaim. Kinda confusing, but i'll muddle through, i'm done with closed source. 

i'll try not to gush at how mindbogglingly awesome this is so far.

Thank you for the data. :)

Edit: did i mention you all rock? Yes, yes i just did.

Gaim is now called Pidgin, the developers changed the name because AOL was giving them headaches with the AIM name rights. The package seems to look for old Gaim settings. Glad to know the issue is solved.

Please mark your thread as solved. [Here's]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") how.

---

### Post by Dr Small on 2007-09-29
The .NameOfApp folders in your Home Folder, are for configuration files only, not where the application installs to.

Dr Small

---

### Post by crimesaucer on 2007-09-29
> **Daveth said:**
> same error I made!  See this for a similar and correct answer

[http://ubuntuforums.org/showthread.php?t=512489](http://ubuntuforums.org/showthread.php?t=512489)

Thanks to Nekiruhs for putting us straight .

Just to add this... most programs are installed into your /usr/bin

and some programs are installed into the /opt file... like Swiftfox, or wicd, and even my Thunderbird 2.

... and the config files are hidden in your /home/user/."hidden_config_file" or easier written as ~/."hidden_config_files"

---

