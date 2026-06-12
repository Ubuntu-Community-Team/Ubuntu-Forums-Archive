---
title: "Prog install problems"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-05-10
I have two progs downloaded to the desktop and no matter what I try I cannot get them to install,

I click on them and the package manager opens them up showing all the bits and pieces. I left click and try to use GDebi I am told the file is either corrupt ar I don't have the right permissions. I have all permissions checked for these progs.

One is a "tar.gz" file and the other is a "zip".

Have tried a couple of commands in Terminal with no joy either. Prolly used the wrong commands as I'm not really up to speed with with this stuff yet.

So what I'm asking is: What do I do to get these and future progs installed and running? Please, step by step if you will. I promise to write it all down for future use.

Many thanks,

Frustratedly yours,

Jon

---

### Post by Bachstelze on 2007-05-10
What programs are you trying to install ? Most often, they're in the Ubuntu repositories and you can install them with apt instead of going through shource compiling.

---

### Post by taurus on 2007-05-10
```
cd ~/Desktop
tar xvzf **filename.tar.gz**
unzip -x **filename.zip**
```

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by starcraft.man on 2007-05-10
Just a suggestion, but maybe ya should have a nice read through ubuntu guide so ya get an understanding of how to install any app with apt-get. Just a note but GDebi is for debian installers, tar.gz and zip are archiving formats. You have to extract them either with above commands, or right click and select "extract here". Try to read up on how things works, will help in the long run :)

---

### Post by kragen on 2007-05-10
It sounds like you've downloaded some source code - you may well find that the programs you want to install are already available via the ubuntu repositories. What the are programs?

If you goto "System > Administration > Synaptic Package Manager", enter your password and try searching for the programs you want, do they appear? If they do, right click on them and just select "Mark for installation", if you get a message to install additional packages, accept that too, then just click on apply and it should do all the hard work for you.

If this doesn't work, then you're going to need to post more info :)

---

### Post by Romin-1 on 2007-05-10
Thanks for the quick responses guys.

I will try the codes you suggested and get back to you.

I must be older than I admit 'cause when I read one of the help pages sometimes I come away more confused than I was to begin with.

Thanks again,

Jon

---

### Post by starcraft.man on 2007-05-10
> **Romin-1 said:**
> Thanks for the quick responses guys.

I will try the codes you suggested and get back to you.

I must be older than I admit 'cause when I read one of the help pages sometimes I come away more confused than I was to begin with.

Thanks again,

Jon

LOL, your never too old, my pops over 65 and hes a windows power user :) Well, maybe not as knowledgeable as me but he knows what hes doing and to modify plenty of things without me around ^^.

Tell us if it works out :)

---

### Post by Romin-1 on 2007-05-10
I aint old; my birth certific is 69 though. Got into 'Puters with Commodore and upgraded to some box from Radio Shack. I've hacked, jacked and stacked XP home, SP2 'till it's held together with rubber bands and duct tape. Also a rabid Firefox fan.

Strange thing; some of the chrome codes I wrote for FF work in Windoze but not in Ubuntu. Gotta tweak them and the user.js scrips.

One of the progs I'm trying to load is "Alltray' which will let you minimize FF and T-Bird to the tray when you click on the "X".

Will get back later with a progress report.

Jon

---

