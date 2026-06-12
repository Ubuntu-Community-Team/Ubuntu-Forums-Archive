---
title: "This is about Ubuntu-GS-Remix 12.04"
date: 2012-12-19
forum: Any Other OS
---

### Post by Rangir on 2012-12-19
This has to be in a new thread, and not on UGR 12.10 one, so I am opening it. First of all I must thank Stinger, ScreamingJ3sus for directing me to it. 

It is a fantastic distro, I can't understand how I missed it. It doesn't have Unity, Ubuntu desktop etc, so nothing of Unity to uninstall, as I had done with Precise and Raring. There is no need for some obscure lib file to be deleted.

Kansasnoob points out that the original developer Jan Hoffmann had stated 
> With Ubuntu GNOME Remix coming together with Ubuntu 12.10, there won't be a new version of **my own remix** anymore

I can say now, after working with it for few hours that Jan doesn't need to isue a new version of his own remix, as it is an LTS one. Kansasnoob had refuted the idea of it being a LTS one, but after looking in the sources.list, I can state that it is a LTS one. It has only this amount of repos included in default,
>  deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main universe restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main universe restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main universe restricted 
but, all other Precise repos can easily be added to that list.

There is also additional repos included, 
> deb [http://ppa.launchpad.net/jan-hoffmann/gnome-shell/ubuntu](http://ppa.launchpad.net/jan-hoffmann/gnome-shell/ubuntu) precise main
deb-src [http://ppa.launchpad.net/jan-hoffmann/gnome-shell/ubuntu](http://ppa.launchpad.net/jan-hoffmann/gnome-shell/ubuntu) precise main 
and, if they are not updated since April, 2012 (Kansasnoob), it doesn't really matter as far as Ubuntu keeps its Precise repos good for and until April 2017.

This is a LTS release, whether or not anyone says so.* It is an automatic LTS release.*

There is nothing Ubuntu could do or say that this not a supported LTS release. ***It is automatically supported until April 2017**!*** Ubuntu cannot delete any applications from the original state as of April 2012; Ubuntu can add files, upgrade files in Precise repos, but cannot delete any. So far, so good for this UGSR 12.04!:D

---

### Post by deadflowr on 2012-12-19
It isn't an LTS because even though the base repos are precise, several of the packages for this release won't be supported long term, much like Lubuntu.
Lubuntu 12.04 shares the same repos, yet it is not LTS.

---

### Post by kansasnoob on 2012-12-19
I'm not the one refuting the fact that it's NOT an LTS, the developer is:

[http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/1/](http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/1/)

> As there are some people asking about the next version based on Ubuntu 12.04: Yes, there will be a new version released shortly after Ubuntu's final release. **[COLOR="Red"]It won't be a LTS version, though, as it contains software from the universe repository that is not supported as long.[/COLOR]**

And the PPA packages have not been updated since April:

[https://launchpad.net/~jan-hoffmann/+archive/gnome-shell](https://launchpad.net/~jan-hoffmann/+archive/gnome-shell)

In fact it says there:

> THIS PROJECT WILL NOT BE CONTINUED.

But it's your machine, do as you wish ;)

---

### Post by Rangir on 2012-12-19
> **deadflowr said:**
> It isn't an LTS because even though the base repos are precise, several of the packages for this release won't be supported long term, much like Lubuntu.
Lubuntu 12.04 shares the same repos, yet it is not LTS.

Could you please tell me, which might be those packages that might not be updated?
There is only 
> deb [http://ppa.launchpad.net/jan-hoffman...e-shell/ubuntu]("http://ppa.launchpad.net/jan-hoffmann/gnome-shell/ubuntu") precise main
deb-src [http://ppa.launchpad.net/jan-hoffman...e-shell/ubuntu]("http://ppa.launchpad.net/jan-hoffmann/gnome-shell/ubuntu") precise mai

This could be blocked by placing # in front of each line, so they won't get updated from that ppa, but all other files would be updated from the Precise repos, all of them as in the Ubuntu Precise iso. I've added them to the sources.list and updated the installation already and upgraded it too, so it is up to date today. 

But still, some of the files might not have got updated and upgraded as you say, so could you please pinpoint them for me? Thanks!

---

### Post by Rangir on 2012-12-19
> **kansasnoob said:**
> I'm not the one refuting the fact that it's NOT an LTS, the developer is:
[http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/1/](http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/1/)
And the PPA packages have not been updated since April:
[https://launchpad.net/~jan-hoffmann/+archive/gnome-shell]("https://launchpad.net/%7Ejan-hoffmann/+archive/gnome-shell")
In fact it says there: THIS PROJECT WILL NOT BE CONTINUED.                      

Dear Kansasnoob, we are mixing two things here; 1) Jan Hoffmann says that he won't continue with the project, meaning he won't make a Quantal one, or a Raring one, or just won't make another distro, 2) that doesn't mean his already released distro won't be automatically updated and upgraded by Apt getting the command sudo apt-get update && sudo apt-get upgrade from the Precise repos.* It will, until 2017! *

Because of* that* fact, it is a LTS distro.

But still, as nothing is permanent, there is no guarantee that Jan Hoffmann might change his mind and make another distro. I really hope, he'd do that, as I find this a very good distro.

> But it's your machine, do as you wish ;)Yes, of course, freedom for everyone to make or break his machine! Oh, it is only a 14GB partition, so the machine would work. :)

---

### Post by Rangir on 2012-12-20
More than 6 hours later from my last post, I achieved quite a success with Jan Hoffmann's UGSR. Sorry Jan, I uninstalled the gnome shell, but the gnome classic works very well. 

Maybe this distro brings me luck, because I achieved something I wanted for a long time.:D

The screenshots would tell the story.

---

### Post by zombifier25 on 2012-12-20
> **Rangir said:**
> More than 6 hours later from my last post, I achieved quite a success with Jan Hoffmann's UGSR. Sorry Jan, I uninstalled the gnome shell, but the gnome classic works very well. 

Maybe this distro brings me luck, because I achieved something I wanted for a long time.:D

The screenshots would tell the story.

May you elaborate on how you get standalone Dash like that?

---

### Post by screaminj3sus on 2012-12-20
> **kansasnoob said:**
> I'm not the one refuting the fact that it's NOT an LTS, the developer is:

[http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/1/](http://ubuntu-gs-remix.sourceforge.net/p/blog/articles/1/)



And the PPA packages have not been updated since April:

[https://launchpad.net/~jan-hoffmann/+archive/gnome-shell](https://launchpad.net/~jan-hoffmann/+archive/gnome-shell)

In fact it says there:



But it's your machine, do as you wish ;)

The packages in that ppa are just a few metapackages, which you don't even really need installed (like the ubuntu-desktop package)

I agree it would be disingenuous to officially call it an LTS, under the hood it is ubuntu 12.04 for the most part, and ubuntu 12.04 will continue to get updates. Its not that much different than installing ubuntu 12.04 and installing gnome-shell.

---

