---
title: "really beginner. i mean REALLY beginner"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by worstofboston on 2006-07-23
I want to apologize in advance for taking up space with this.

I used windows, even developed aps in windows, for a dozen years.

This Linux isnt intuitive to me. I have to unlearn everything. I am happy to, its just not easy.

Can anyone reccomend a site for me to learn very basic stuff? Like how to move around in the directories, how to install programs, what different extensions mean (like is a .bin the same as a .exe?) and stuff like that? I dont want to bother everyone here with ridiculous quesitons I can answer myself, but all the beginners guides I have seen seem to take it for granted that you know this stuff.

Or maybe I am just antsy. I got into Linux so I could use content management systems, and I cant even figure out how to RUN php or if it is installed... never mind how to use it.

For instance, I downloaded LimeWire and have no idea how to install it. I have a .bin sitting on my desktop. There are so many management tools and so many aps to do so many things - I am lost in it. 

Thanks a lot, and I apologize. 

JD

---

### Post by Jagot on 2006-07-23
Here's a great site which explains how to install pretty much anything:

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

There are also some Ubuntu specific guides here which you may wish to have a look through:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

This is a good guide to the command line which may be of use to you:

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by worstofboston on 2006-07-23
I appreciate it very much. 

I wont come back until I read them all! 

JD

---

### Post by Bad Hair on 2006-07-23
don't feel like the lone ranger. you're not the only one that has to try to relearn everything you thought you knew. the previous reply had some good options for a overview of Ubuntu & Linux. you might also want to see if your community has a local linux users group that can assist you. example: San Antonio has a local Linux users group and they are more than happy to assist anyone trying to convert. if you live in a town of any decent size there's probably one there too. good luck and don't give up, it's difficult not to think in terms of windows but it can be done!!

---

### Post by adam.tropics on 2006-07-23
..Also, if you don't mind downloading some more, I would reccomend Frostwire over Limewire, as it has no 'reminders' to upgrade constantly thrown at you, no ads, is open source, comes in an Ubuntu .deb package (easy to install for you) and is almost the same as Limewire. It is gonna be the one to go with as Limwire are toying with DRM at the moment.Yuk! You can get it [here.]("http://www.frostwire.com/")

---

### Post by woedend on 2006-07-23
[www.ubuntuguide.org](www.ubuntuguide.org)
[http://stanton-finley.net/fedora_core_5_installation_notes.html](http://stanton-finley.net/fedora_core_5_installation_notes.html) (NOTE: THIS IS NOT UBUNTU!! But it is good for learning some things).

most importantly, this site.  Use the search button...theres TONS of info.  Can't find it - Fire away your questions in the absolute beginner forum...

---

### Post by worstofboston on 2006-07-23
I managed to install FrostWire... the .deb made it easy. Now it wont run when I select it off my menu, but I probably have to reboot. Maybe not... thank you for that tip.

JD

---

### Post by Jagot on 2006-07-23
You may need to install Sun's Java first:

[https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956](https://help.ubuntu.com/community/Java#head-f4267cc37a197ccf46397cc58ff0944838741956)

---

### Post by adam.tropics on 2006-07-23
I would check you have sun-java5-jre installed. Frostwire and for that matter Limewire, don't play nicely with users without java!

edit: snap!

---

### Post by worstofboston on 2006-07-23
It is not available in any software channel, might not support my system architecture.

Doex ctrl-c not copy in Linux? Ctrl-V paste?

This is a windows thing, eh?

---

### Post by Jagot on 2006-07-23
If you're talking about Java, it is available in the multiverse repository.  See here to enable it:

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

ctrl+c and ctrl+v work fine in Ubuntu, however, in the command line you need to add shift to both of those, so shift+ctrl+c to copy.

---

### Post by jimmygoon on 2006-07-23
> **worstofboston said:**
> It is not available in any software channel, might not support my system architecture.

Doex ctrl-c not copy in Linux? Ctrl-V paste?

This is a windows thing, eh?

It doesn't work in gnome-terminal but it should work everywhere else. The clipboard is contained within the program though so if you copy and paste something from firefox and then **close firefox** and then try to paste it in Text Editor... it won't exist and you will have the illusion of not being able to paste. If you ask me, it is one of, if not THE most annoying things about GNOME

---

### Post by worstofboston on 2006-07-23
Whenever I update my respositories, it freezes on file 9 of 10. Wont let me update. Just sits there indefinately.

I need to read up on this stuff. Its one thing after another.

Thank you.

---

### Post by Jagot on 2006-07-23
If you're using the US mirrors for the repositories there appear to be some problems with them at the moment - I'd suggest waiting an hour or two and trying it again.

---

### Post by T700 on 2006-07-23
For an easy and safe way to install Java, codecs, and quite a few other useful things, check out Automatix (see the link in my sig).  By the way,  you can learn an amazing amount by following the links in signatures.  Welcome aboard!

Paul

---

### Post by benduenga on 2006-07-23
I am new to linux also ... about 3 months.  I really liked the 

[www.linuxcommand.org](www.linuxcommand.org) 

as a beginner language learner.

---

### Post by worstofboston on 2006-07-23
Installing FrostWire... I got Java installed okay. Dont know how, really... but I did. Was cool that it worked. 

Now I removed FrostWire and reinstalled it, hoping that it would take with Java5 installed properly. 

It doesnt do anything. It is there, in my menu, but it just sits there and when I select it I dont even get what I would normally call an hourglass. Normally I would be able to check my processes and if it is trying to run, but I dont know how. 

Its okay. I appreciate everyone's help. I think I am trying to take bigger steps than I should now. Like I said, I am just antsy.

JD

---

### Post by adam.tropics on 2006-07-23
Try running frostwire from a terminal, and see what errors it gives you. Open a terminal, type 
```
frostwire
```
and then hit enter.

---

### Post by adam.tropics on 2006-07-23
I suspect what you need to do, is open a terminal, do
```

sudo update-alternatives --config java

```
select Sun's java, then try running frostwire again.

---

### Post by woedend on 2006-07-23
last time i installed frostwire i had to change some kind of config file to unix...dont know if its still necessary.

---

### Post by adam.tropics on 2006-07-23
> **woedend said:**
> last time i installed frostwire i had to change some kind of config file to unix...dont know if its still necessary.

Yeah, I remember that, someone mis-packaged (<--wonder what the correct expression is!) it. Just checked the new one and it's fine. About time too, took long enough!

---

### Post by Hotwhlz85 on 2006-07-23
I completely agree with the poster who said use automatix to install Frostwire.  I had struggled with installing that and Azureus.  I'd get them installed and they never worked, even when I knew I had java installed correctly.  I found a thread where automatix was mentioned.  Uninstalled both Frostwire and Azureus and then did the automatix install.  Both programs worked as soon as I fired them up.  Not only that but automatix includes a ton on other cool apps and the Debian start menu which is much more user friendly.

---

### Post by Omnios on 2006-07-23
There are a lot of command line references in my signature ranging from cheet sheet like pages up to command line bash scripting

---

### Post by worstofboston on 2006-07-23
> **adam.tropics said:**
> I suspect what you need to do, is open a terminal, do
```

sudo update-alternatives --config java

```
select Sun's java, then try running frostwire again.

This worked beautifully. I would never have known that code at this stage. Hopefully I can pick up on this stuff.

Thank you everyone.

---

### Post by adam.tropics on 2006-07-24
you're welcome. The command line stuff you will pick up pretty quickly as you go along. Especially if you like to tinker!

---

