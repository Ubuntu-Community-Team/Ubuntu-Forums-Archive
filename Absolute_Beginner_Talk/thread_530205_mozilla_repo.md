---
title: "mozilla repo?"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by panayk on 2007-08-20
Hello!

Does anybody know a repository for the latest (or near latest) Firefox and Thunderbird versions?

I suppose feisty-proposed has them but is there a way to enable a repo only for specific packages?

---

### Post by kerry_s on 2007-08-20
press alt+f2 type> gksudo firefox
use the firefox help> update to up date it than close it after its done, don't browse with a root firefox. i think its the same for thunderbird.

---

### Post by ukripper on 2007-08-20
Use AUTOMATIX2 which will install swiftfox for you and has thunderbird 2.0 also. Swiftfox is faster version of firefox and contains exactly same plugins and extensions.

You can get automatix2 from following link.
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by hyper_ch on 2007-08-20
Automatix is not recommended.

---

### Post by ukripper on 2007-08-20
> **hyper_ch said:**
> Automatix is not recommended.

Why? It is easier for beginners to instal. I highly recommend automatix for beginners.

---

### Post by hyper_ch on 2007-08-20
Just because something is "easier" it doesn't make it better ;)

Do you think Windows is easier than Linux? Do you think Window is better than Linux?

Automatix has some flaws and it may disrupt your system. It's better to learn from the beginning on how to do thing properly... you know, you can't get rid of bad habits easily.

---

### Post by ukripper on 2007-08-20
> **hyper_ch said:**
> Just because something is "easier" it doesn't make it better ;)

Do you think Windows is easier than Linux? Do you think Window is better than Linux?

Automatix has some flaws and it may disrupt your system. It's better to learn from the beginning on how to do thing properly... you know, you can't get rid of bad habits easily.

i am using linux system since 99 and I am more into linux systems than i ever was with windows. I still recommend automatix2 for beginners there are flaws for many systems even new linux kernel 2.6.22 has flaws but doesn't mean you ignore it. From beginner's point of view it is different story. Automatix makes life easier and I am saying it with experience as i have tested it on my clients whom i support.

---

### Post by hyper_ch on 2007-08-20
well, I've also been using linux sind '99 - actually only as servers but then, doesn't matter much how long one's been using it, right?

You just say you highly recommend but you don't even point out the dangers it poses... Automatix makes things easier... that's true... but it also makes the system easier to break; that should not be forgotten.

---

### Post by panayk on 2007-08-20
I didn't mean to start a flame war :)

> Why? It is easier for beginners to instal. I highly recommend automatix for beginners.
I am not **that** much of a beginner... I think I can manage a web browser :)

> press alt+f2 type> gksudo firefox
Strangely, even if I "sudo firefox", updating is still disabled. Maybe because this is not the official brand?

But the point is that I am really keen on the idea of doing all my updates through a central system.

In Windows, it was very annoying to have applications constantly popping up dialogs requesting to check for updates.

---

### Post by ukripper on 2007-08-20
> **hyper_ch said:**
> well, I've also been using linux sind '99 - actually only as servers but then, doesn't matter much how long one's been using it, right?

You just say you highly recommend but you don't even point out the dangers it poses... Automatix makes things easier... that's true... but it also makes the system easier to break; that should not be forgotten.

point taken, but that is where good part comes in. To learn it after you break it is easier from understanding the whole system before you even step into something new which is quiet daunting for some and there automatix kicks in

---

### Post by kerry_s on 2007-08-20
hey, guys that's enough. suggest it and move on. let the OP decide what they want. no need to argue what is best, when it works it works, when it go's bad i'm blaming you. :lolflag:

---

### Post by ukripper on 2007-08-20
> **kerry_s said:**
> hey, guys that's enough. suggest it and move on. let the OP decide what they want. no need to argue what is best, when it works it works, when it go's bad i'm blaming you. :lolflag:

 Damn man, wasn't me!! Please please dont shoot me..:lolflag:

---

### Post by panayk on 2007-08-20
So, from what I gather after a quick google search, it should be possible to partially enable a repository.

Can someone provide instructions on how to enable a repository for a specific package and its dependencies?

---

### Post by kerry_s on 2007-08-20
> **panayk said:**
> So, from what I gather after a quick google search, it should be possible to partially enable a repository.

Can someone provide instructions on how to enable a repository for a specific package and its dependencies?

did you try the running it as root trick and let firefox update firefox and thunderbird update thunderbird?

it's not a good idea to use other *ubuntu version repos as you might end up in dependency hell, as in this requires this this and this, next thing you know this this and that don't work any more.

but if you just have to go that way, it is exactly the same line as you have now with just a different name.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
to
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) fiesty main restricted universe multiverse
to
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted universe multiverse

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by panayk on 2007-08-20
> did you try the running it as root trick and let firefox update firefox and thunderbird update thunderbird?

Yes, "gksudo firefox" then Help -> Check For Updates which is greyed out.

> it's not a good idea to use other *ubuntu version repos as you might end up in dependency hell, as in this requires this this and this, next thing you know this this and that don't work any more.

I do not want to use the entire repository for e.g. gutsy. I suppose my question is:
"Can I tell synaptic that it is allowed to install the firefox package from gutsy, **and only that**, when updating, **if and only if** it can satisfy its dependencies from the other repos?"

---

### Post by kerry_s on 2007-08-20
> **panayk said:**
> Yes, "gksudo firefox" then Help -> Check For Updates which is greyed out.



I do not want to use the entire repository for e.g. gutsy. I suppose my question is:
"Can I tell synaptic that it is allowed to install the firefox package from gutsy, **and only that**, when updating, **if and only if** it can satisfy its dependencies from the other repos?"

i suppose you can just add the repo, then in synaptic click on firefox>mark for update and see what it wants to do, you can always uninstall it, remove the repo and install the old 1 back.
things like that is why i moved to debian.

Which reminds me, do you have the backports repo turned on? that's for main apps like those.

---

### Post by brennydoogles on 2007-08-20
> **panayk said:**
> Yes, "gksudo firefox" then Help -> Check For Updates which is greyed out.



I do not want to use the entire repository for e.g. gutsy. I suppose my question is:
"Can I tell synaptic that it is allowed to install the firefox package from gutsy, **and only that**, when updating, **if and only if** it can satisfy its dependencies from the other repos?"

It may be easier to browse the repositories for the .debs, or possible to write a bash script which will update the repositories and filter only Mozilla updates. I would see if either you or someone knowledgeable could come up with the bash script.

---

### Post by igknighted on 2007-08-20
+1 to opensuse here, they have a repo specifically for this purpose (keep mozilla products up to date).  Many major apps have them in opensuse (OO.o, KDE/Gnome etc.)

---

### Post by Acglaphotis on 2007-08-20
Why dont you try and use Ubuntuzilla? Its a script to update firefox to the latest version. here is the url: [http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")

---

### Post by panayk on 2007-08-20
> **Acglaphotis said:**
> Why dont you try and use Ubuntuzilla? Its a script to update firefox to the latest version. here is the url: [http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")

I'll give it a try. Thanks!

---

