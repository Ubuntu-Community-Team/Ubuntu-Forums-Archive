---
title: "equivalent of frontpage"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by woodart on 2007-05-02
Is there an application that is the equivalent of frontpage for building websites?

Can this app import a frontpage website and convert it?

TIA

---

### Post by viciouslime on 2007-05-02
You could try NVU, it's not quite as beginner friendly as frontpage, but since frontpage just saves in plain html, it will indeed open your existing site. It is available in the repositories.

---

### Post by horace on 2007-05-02
> **woodart said:**
> Is there an application that is the equivalent of frontpage for building websites?
TIA

I don't think there's anything that bad!!  Why not try an html editor like bluefish?

---

### Post by starcraft.man on 2007-05-02
> **woodart said:**
> Is there an application that is the equivalent of frontpage for building websites?

Can this app import a frontpage website and convert it?

TIA

Wow... first time I ever seen someone ask for Frontpage.... I'm in a bit of shock.

There are 3 good ones to look at on Ubuntu, Nvu, Bluefish and Kompozer. From some things I read, NVU was abandoned for Kompozer... not certain about that.

Full list of WYSIWYGs [here.]("http://linuxappfinder.com/tag/WYSIWYG") Except blue fish, dunno why its missing.

---

### Post by igknighted on 2007-05-02
There's also quanta+ which is a KDE app, not quite as user friendly as kompozer/nvu, but i think its the only wysiwyg editor in the repo's

---

### Post by JacobRogers on 2007-05-02
Also I think you can use Open Office to save .html files.

---

### Post by thefoolisme on 2007-05-02
I have used NVU to edit a frontpage site, and it works quite well.  I would recommend trying that one.  I installed it on my work PC to do some editing of a frontpage page I'd started at home.  I was able to download all the info from the web into NVU, make the corrections, and update it, without being near the original files.  Give it a whirl!  :)

---

### Post by aysiu on 2007-05-02
[https://help.ubuntu.com/community/Kompozer](https://help.ubuntu.com/community/Kompozer)

---

### Post by PartisanEntity on 2007-05-02
[Here is a thread]("http://ubuntuforums.org/showthread.php?t=417484") I started on the same issue.

IMO at the moment Nvu/Kompozer is the best web creation and editing application in Linux that comes close in functionality to the likes of Frontpage and Dreamweaver. (Note: Nvu is abandoned now, Kompozer is the updated version of Nvu).

I was using Kompzer until today when it crashed on me and would not launch anymore, I have gone back to using Nvu even though it is abandoned (there is a .deb file on their website which works in Feisty even though it is for Ubuntu 5.04).

---

### Post by Killtown on 2007-05-18
Can't fund Nvu in my Synatic Mgr.  Is it still listed?

---

### Post by Rui Pais on 2007-05-18
> **aysiu said:**
> [https://help.ubuntu.com/community/Kompozer](https://help.ubuntu.com/community/Kompozer)
or for easiness a pre-build package:
[http://www.getdeb.net/search.php?keywords=kompozer](http://www.getdeb.net/search.php?keywords=kompozer)

---

### Post by Killtown on 2007-05-18
I just downloaded Bluefish and Nvu.  They don't seem to be able to draw lines, circles, arrows, etc like FrontPage can.  Is there a webpage building on Ubuntu that does, or did I miss this feature in Bluefish and Nvu?

---

### Post by PartisanEntity on 2007-05-18
> **Killtown said:**
> I just downloaded Bluefish and Nvu.  They don't seem to be able to draw lines, circles, arrows, etc like FrontPage can.  Is there a webpage building on Ubuntu that does, or did I miss this feature in Bluefish and Nvu?

Note sure if Nvu has that, IMO none of the editors I have seen and used so far is as developed as Dreamweaver or Frontpage, but it also depends on your needs of course, they *may* be sufficient.

---

### Post by Killtown on 2007-05-18
> **PartisanEntity said:**
> Note sure if Nvu has that, IMO none of the editors I have seen and used so far is as developed as Dreamweaver or Frontpage, but it also depends on your needs of course, they *may* be sufficient.
Darn.  I liked FP cause it was simple and was easy to draw arrows, circles, etc.   Dream was too complicated.  

Guess I'll have to do drawing in Gimp.


Btw, where can we post suggestions to add certain features to linux software?

---

### Post by esoterica on 2007-05-18
> 
Wow... first time I ever seen someone ask for Frontpage.... I'm in a bit of shock.


Well, just be happy that they are at least looking for an alternative to FrontPage and not instead asking how do I run Frontpage in Linux!

I've been looking through the WYSIWYG type HTML editors for Linux myself just out of curiosity because web development is what I do for a living. I haven't been impressed at all by any of them, of course I'm not too impressed by any of them that run in Windows either. I personally do all my web page work with a text editor and gimp. I also think just learning how to code XHTML and CSS yourself in a text editor is a whole lot easier then trying to learn how to use any of the supposedly "simple" page creation programs out there.

The biggest problem your going to have is if your already using FrontPage then that means you also have FrontPage Extensions installed on your web server (whether your aware of that or not) in order for FrontPage to actually work. If you try to upload or alter the HTML files or anything else on your web server with anything but FrontPage your going to break your FrontPage extensions and they will have to be reinstalled again on the web server in order to work again. Much of the content and security in the pages FrontPage creates for your web site depends on these extensions to be installed and working on the web server in order to actually work when your visitors come to your web site.

Microsoft has stopped supporting FrontPage entirely so you can't even get updates or anything else for it anymore, certainly making it a good time for you to break away from it and seek out alternatives. Their new Expressions Web is a real mess, better than FrontPage, but still a real mess none the less, it also requires ASP.NET in order to work on your web server, though I hear rumors a PHP version is in the works to be released soon.

I think what probably serves as the best alternative to what your looking for that people are using, and I so hate to even suggest them because I hate them so badly, is something like WordPress or Joomla. Do a Google search, I don't even want to give them the satisfaction of a link in my post.

Be warned though, running either Joomla or WordPress on your web server will also leave you open to more security problems than I'd ever want to deal with (which is why I hate them so badly). If you monitor the security vulnerability reports at all that get published each week those two (and similar) are always listed with new vulnerabilities being discovered and exposed every single week. That makes for a handful too stay on top of if you don't want your web site regularly exploited and hacked. Not to mention the vulnerabilities they expose you to that don't even have fixes published for in a timely manor.

The script kiddies love these types of programs running on web servers, that's evident enough by looking at the log files of any public web server and you can see them constantly scanning web servers looking for signs of these specific applications probably more so than anything else.

My own absolute favorite Program for doing all my web development work is this program...

[http://www.editplus.com/](http://www.editplus.com/)

I've been searching hi and low looking for a Linux text editor that's even 1/2 of that program and everything it does. I haven't found anything even close to it yet, so I can't live without it and find myself still doing my web development work on my Windows box even though I set this Linux box up with the specific intention of using it for my work instead. The text editors I see so far for Linux just don't compare and that program has me so spoiled that I can't live without it.

---

### Post by derred on 2007-05-18
> Also I think you can use Open Office to save .html files.
Open Office 2.2 has save as html and export as xhtml builtin so that allong with Bluefish should cover it.

---

### Post by Killtown on 2007-05-21
Installing KompoZer didn't work for me:

> kompozer/kompozer
kompozer/defaults.ini
c@c-desktop:~$ sudo ln -s /opt/kompozer/kompozer /usr/bin/kompozer 
Password:
c@c-desktop:~$ kompozer
bash: kompozer: command not found


Here's how I downloaded it:

[https://help.ubuntu.com/community/Kompozer](https://help.ubuntu.com/community/Kompozer)

---

### Post by Rui Pais on 2007-05-21
> **Killtown said:**
> Installing KompoZer didn't work for me:


Here's how I downloaded it:

[https://help.ubuntu.com/community/Kompozer](https://help.ubuntu.com/community/Kompozer)
that is too complicated and since you do things by hand will be harder to clean if you decide to uninstall.

See my post [#11]("http://ubuntuforums.org/showpost.php?p=2676534&postcount=11") for an easy deb package.

---

### Post by Killtown on 2007-05-21
> **Rui Pais said:**
> that is too complicated and since you do things by hand will be harder to clean if you decide to uninstall.

See my post [#11]("http://ubuntuforums.org/showpost.php?p=2676534&postcount=11") for an easy deb package.
Ah nice, thanks!  It worked.

So is Kompozer just the new Nvu?

---

### Post by Rui Pais on 2007-05-21
> **Killtown said:**
> Ah nice, thanks!  It worked.
great :)

> So is Kompozer just the new Nvu?
i think nobody knows exactly. 
Originally it was just a fork on NVU for bug fixes and experiments with new features, 'till NVU releases a new version... but then NVU seems to stop to be developed although that is never assumed. On it's site the only thing that is update are the dates on bottom of pages (right now says "Copyright. © 2003-2007") but on Download page you got:
> Latest version of Nvu:
Nvu 1.0 - Released June 28th, 2005

But i don't know if kompozer people are developing or just maintained of the old code...

---

