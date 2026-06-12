---
title: "Help with mp3 files"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Endow on 2006-06-21
I just installed Ubuntu LTS and for some reason I can't listen to .mp3 files.I can listen to my cd's when I place them in the drive and I can hear .ogg files but even after installing JuK (which I wouldn't really need since I had Rhytmbox already;but since I couldn't get it to work) I can't listen to any of my .mp3's.

This is strange considering the last time I tried Ubuntu (Breezy Badger) I had successfully listened to mp3 files.


So anyone have a clue?
I'm running on AMD64 (and I got the amd64 version of LTS).
Thanks in advance  :D 

PS:New here :)

---

### Post by Jagot on 2006-06-21
[https://help.ubuntu.com/community/RestrictedFormats#head-e18f2d510b1efe975368b818b5aa3ae2b2eee5c8](https://help.ubuntu.com/community/RestrictedFormats#head-e18f2d510b1efe975368b818b5aa3ae2b2eee5c8)

---

### Post by Endow on 2006-06-21
How exactly do I install a specific package?

Ps:Can you also tell me how am I supposed to open .pdf files while surfing online?

---

### Post by bluenova on 2006-06-21
If you are new to Ubuntu, I would suggest taking a look at easy Ubuntu for installing all the restricted stuff. Basically Ubuntu only comes with pure open source software, so things like mp3 codecs, windows fonts and NVIDIA drivers cannot come with Ubuntu and need to be installed separately. This is done very easily by using easy Ubuntu, but you will need to make sure that it's legal to install all of these things, for instance a lot of it cannot be installed if you are in the USA.


[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

---

### Post by Ashish Meena on 2006-06-21
You may also visit 

[http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by fer5437 on 2006-06-21
Go to wiki Ubuntu search for resticted format.

---

### Post by Jagot on 2006-06-21
[QUOTE=fer5437]Go to wiki Ubuntu search for resticted format.[/QUOTE]

That is the link I have already posted.  Everything is explained there.

---

### Post by Endow on 2006-06-21
Bluenova : that seems to have worked.Thanks :)

Still how can I get a sound/music preview by hovering (sp?) my mouse over the file's icon like I used to?

---

### Post by Jagot on 2006-06-21
Well, if easyubuntu hasn't sorted it out for you, audo previewing is the the link I've already posted.

---

### Post by Jucato on 2006-06-21
If you still haven't found a solution, take a look again at the wiki: [https://help.ubuntu.com/community/RestrictedFormats#head-dd75cf9cf440f1782515e6df311684e6f981b4e4](https://help.ubuntu.com/community/RestrictedFormats#head-dd75cf9cf440f1782515e6df311684e6f981b4e4)
There's a section there about Audio Previews in Ubuntu.

---

### Post by Endow on 2006-06-21
Well I haven't found a solution yet but I reckon you guys have given me enough material.


Some other questions I have right now :

-embeded (sp?) linux pdf app for firefox?
-is there a amd64 dapper version of macromedia flash?How can I get it?
-what about Java runtime ??


Thanks for all the help so far guys:-)

---

### Post by Nikusan on 2006-06-21
> Well I haven't found a solution yet but I reckon you guys have given me enough material.


For mp3 install this package: gstreamer0.10-plugins-ugly
For the preview in nautilus install this package: mpg321
For instructions on installing packages see the link in my sig.

> 
-embeded (sp?) linux pdf app for firefox?

Install these packages: acroread mozilla-acroread

> 
-is there a amd64 dapper version of macromedia flash?How can I get it?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Scroll down to "Flash for AMD64 and PPC".

> 
-what about Java runtime ??

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Jucato on 2006-06-21
1. PDF for firefox: I think you have to look at the firefox page for that

2. unfortunately, a AMD64 version  of the flashplugin-nonfree package is not available. But there's still a way to get flash. Here's a link how to do that: [https://help.ubuntu.com/community/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://help.ubuntu.com/community/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)

3. Java for AMD64: again, some more specific instructions for your architecture: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I'm not sure if there are AMD64-compatible versions of Automatix or EasyUbuntu available. If they do, you might find it easier using these tools.

---

### Post by Endow on 2006-06-21
Just so I get this straight.When you guys tell me to install a given package : how exactly am I supposed to do that?

Should I do a search for that application in the add/remove application?I mean it has a limited number of apps but why is it accessing the net all the time?

Also when some page says I should install a package ...sometimes I don't see a download link.Does that mean Ubuntu already has that app?Then how come I can't find that package when i do a search in the add/remove app??


Oh and lastly (I realize these questions and their answers are all interconnected but) is there a command for the terminal for installing a package located in a specific directory?


Thanks again guys.Cool to see such an active and helpful community.Especially considering most of these questions are probably asked over and over again. :-)

---

### Post by 3rdalbum on 2006-06-21
To install those packages, you should use the Synaptic Package Manager program (not Add/Remove Applications).

Remember to enable the Universe and Multiverse repositories, otherwise you might have trouble with some packages:

[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096")

---

### Post by Jucato on 2006-06-21
[QUOTE=Endow]Just so I get this straight.When you guys tell me to install a given package : how exactly am I supposed to do that?

Should I do a search for that application in the add/remove application?I mean it has a limited number of apps but why is it accessing the net all the time?

Also when some page says I should install a package ...sometimes I don't see a download link.Does that mean Ubuntu already has that app?Then how come I can't find that package when i do a search in the add/remove app??


Oh and lastly (I realize these questions and their answers are all interconnected but) is there a command for the terminal for installing a package located in a specific directory?


Thanks again guys.Cool to see such an active and helpful community.Especially considering most of these questions are probably asked over and over again. :-)[/QUOTE]

When the wiki says that you download a package, it usually means (unless otherwise stated) that you open up the Synaptic package manager and look for this package, mark it for installation, and hit Apply. 

The Add/Remove Programs application is basically a fancy version of the Synaptic package manager. However, it has some limitations, as far as I know. What these two both have in common is that when you try to install something, it downloads the requested packages from the repositories (sort of a database of available packages, applications, libraries, etc) and automatically installs them. And yes, they do connect to the internet because the stuff that you want installed is only found online.

The w32codecs, though, is a totally different matter. Due to some legal/philosophical issues, Ubuntu does not include it in its repositories. So you have to manually download and install it. The instructions are on the wiki page.

Here's a very newbie friendly guide to installing software in Ubuntu made by our very own forum member aysiu: [http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php)
Take note, though, that although it's meant for beginners, it focuses/teaches you on the command line. If you want a more graphical approach, the Ubuntu Desktop Guide could help you. The offline version is found on the Help program (not sure what it's called in Ubuntu). An online version also exists at [http://help.ubuntu.com](http://help.ubuntu.com) or the specific section you might be interested is in [https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/ubuntu/desktopguide/C/add-applications.html)

Hope that helps.

---

### Post by Endow on 2006-06-21
So I've been reading some stuff...namely [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)


Thing is the three repositories that are recommended for me to enable on that page are featured in my Software Properties...why?

What should be my criteria when choosing which repositories to enable?


I don't want to mess things up ....

---

### Post by Jucato on 2006-06-21
>  Thing is the three repositories that are recommended for me to enable on that page are featured in my Software Properties
I don't seem to understand what you mean.

>  What should be my criteria when choosing which repositories to enable?
The most basic criteria is that you have to enable the repository where the package you want to install is located. For example, the Java and Flash packages are found in the Non-free (Multiverse) components, so you have to enable that.

>  I don't want to mess things up ....
If you stick to the repositories that are provided by Ubuntu (all repositories that have "ubuntu.com" and "dapper" or "dapper-*something* in them) is practically safe. So you don't have to worry. However, different components have different levels of support.

To learn more about the different components (main, restricted, universe, multiverse) look at this page: [http://www.ubuntu.com/ubuntu/components](http://www.ubuntu.com/ubuntu/components)

(more reading for you :D)

---

### Post by Endow on 2006-06-21
I'm suposed to enable universe and multiverse.Does that means I have to enable every repository that are either universe or multiverse?

(if you scorrll down on that page I posted you'll see what are the 3 repositories I'm talking about...)

---

### Post by Jucato on 2006-06-21
[QUOTE=Endow]I'm suposed to enable universe and multiverse.Does that means I have to enable every repository that are either universe or multiverse?[/QUOTE]
That depends. It all depends on where the package you want to install is located. But generally, if you don't have any ideological/philosophical issues with installing non-free (in the Free/Open Source Software definition of the term) packages like Java, Flash, etc., it's fine to just enable universe and multiverse always. 

Sometimes, a repository already contains the universe or multiverse component and you just have to enable that repository. Sometimes, you have to add the universe/multiverse component to an already existing/active repository (by putting a check mark on the appropriate component). It's on a case to case basis. I hope I'm making sense. :D

> (if you scorrll down on that page I posted you'll see what are the 3 repositories I'm talking about...)

Still can't see what you mean. If you could quote the text, maybe I'll realized how blind I am. :D

---

### Post by Endow on 2006-06-22
Wow man :mrgreen: 

[https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=activate-repos.png](https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=activate-repos.png)

That's the thing.Oh sso multiverse/universe is sort of a library needed by different repositories?I dind't get that... :P

---

### Post by Jucato on 2006-06-22
You can think of the different components (main, restricted, universe, multiverse) as different directories within the repositories, each containing different packages, depending on where the packages would fall under the criteria set by Ubuntu (in the link I also gave). 

About the three you mentioned (at last I see them :D), they are 3 different repositories, all of which have the universe and multiverse components enabled/added. The first one, Ubuntu 6.06 LTS (binary) is the primary Ubuntu repository. The second one is the Updates repository, which contains newer versions of some packages or additional packages that are introduced after Ubuntu 6.06 was released. The third one is the Security Updates repository, where, as you would probably guess, future security updates are placed.

When you enable the universe or multiverse component of a repository (Ubuntu, Updates, or security updates), you are basically gaining access to the packages within those components/sections of the repository.

Well, I hope that explains things a bit.

---

