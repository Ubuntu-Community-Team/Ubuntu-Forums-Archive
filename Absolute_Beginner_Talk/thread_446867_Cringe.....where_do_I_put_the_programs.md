---
title: "Cringe.....where do I put the programs?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by rubix64 on 2007-05-17
O.K. all ego aside I have a question... where do I put the programs? What I mean is I'm trying to do as much work in terminal as possible and some apps downloaded from sourceforge and other places are saved to my desktop, at which point I unpack them in my ~username dir and run the .sh file to start the prog( i.e. google earth, Jin chess GUI, savage-game)

So where are these files REALLY designed to go under the linux filesystem?

"sudo cp /usr/local/google-earth/googleearth.desktop /usr/share/applications" #was a script i found to place GE4 in the Applications>Internet dropdown in GNOME.

....so #1 where should the packages that I dl go to (when doing this from command line)
& #2 what is the appropriate script to place this programs within the Applications menu?


Thanks so much in advance!

rube

---

### Post by dfreer on 2007-05-17
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

This might help you out.

---

### Post by revealer on 2007-05-17
well if you know the name of the program just run the which command in a command line
for example if you want to know where the beryl manager is installed then type:
which beryl-manager
and it will give you something like:
/usr/bin/beryl-manager

---

### Post by aysiu on 2007-05-17
[This](http://ubuntuforums.org/showpost.php?p=1138374&postcount=24) will help you get Google Earth installed.

Google Earth is a special case.

Usually you can find and install programs using the repositories. Read more here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by az on 2007-05-17
> **rubix64 said:**
> 
So where are these files REALLY designed to go under the linux filesystem?

"sudo cp /usr/local/google-earth/googleearth.desktop /usr/share/applications" #was a script i found to place GE4 in the Applications>Internet dropdown in GNOME.

....so #1 where should the packages that I dl go to (when doing this from command line)
& #2 what is the appropriate script to place this programs within the Applications menu?


Thanks so much in advance!

rube

Well, if you get them from the repositories, then you shouldn't have to worry about that.  The problem with installing applications from upstream "by hand" is that you have to update them or remove them by hand as well.  Since linux is a compatible on the source code level, installing binary apps from third-party sites is not always going to work - and you may end up borking your system.  Apps that you compile from source will also need to be maintained by hand.  And their installation to your system folders may not be friendly, either.

That being said, the best place for such third-party apps is you own home drive.  That way, you don't risk overwriting a file that is owned by a package that is part of the packag manager.

---

