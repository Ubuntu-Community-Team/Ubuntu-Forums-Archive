---
title: "sources.list - commenting/uncommenting repositories"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-10-04
how do you comment/uncoment sources.list, add to it, etc...

---

### Post by aysiu on 2006-10-04
Uncommented: ```
deb http://archive.ubuntu.com/ubuntu dapper main restricted
``` Commented: ```
#deb http://archive.ubuntu.com/ubuntu dapper main restricted
```

---

### Post by n0dl on 2006-10-04
Of course you uncomment and comment using gedit, vim, nano, or some other editor. Also once you uncomment and edit you save it then run sudo apt-get update (and upgrade is recommended) so aptitude sees the new packages available.

---

### Post by aysiu on 2006-10-04
Well, if you're using *aptitude*, wouldn't you do this instead? ```
sudo aptitude update
```

---

### Post by GrimJa on 2006-10-09
I do hope posting a question here isnt a problem, but

I want to understand something;
the sources.lst file contains basically ( I gather) the urls of the websites/servers that ubuntu downloads it's packages from.

But I have backed up the downloaded package files (the cache dir), and want to restore them ( I hear its possible).
Just how do I go about adding my CDRom drive as a ...source:confused:  or whatever.
In short, how do I get ubuntu to look towards my CDROM drive for packages?

Thanks in advance
Grim

---

### Post by bulldog on 2006-10-09
You can add the cd in synaptic fourth tab and second option.[have a dutch version]

---

### Post by GrimJa on 2006-10-09
> **bulldog said:**
> You can add the cd in synaptic fourth tab and second option.[have a dutch version]


So, my in my version (5.something :p) I can use synaptic to enlist the CDROM drive as a location to be examined for packages?

Its that simple?:confused: 

And whats that about a dutch version?

---

### Post by bulldog on 2006-10-09
> **GrimJa said:**
> So, my in my version (5.something :p) I can use synaptic to enlist the CDROM drive as a location to be examined for packages?

Its that simple?:confused: 

And whats that about a dutch version?

In Dapper it can [fourth tab] in Breezy I don't know but I think it could.

Fourth tab is because I have no idea how it's called in your version,I use a Dutch version.

---

### Post by GrimJa on 2006-10-09
> **bulldog said:**
> In Dapper it can [fourth tab] in Breezy I don't know but I think it could.

Fourth tab is because I have no idea how it's called in your version,I use a Dutch version.

I see,
well, thanks for trying to help. But I'm still lost, :p. I dont know just how to get the CD added as a source ](*,)

---

### Post by zappa on 2006-10-09
Via synaptic: 
settings -> repo's
Hit the button that says add cdrom :)

---

### Post by aysiu on 2006-10-09
I don't think you can add a CD-ROM as a repository unless it is properly constructed as a repository (with the appropriate directory structure and list of packages contained within). If it's just a collection of .deb files, I don't think it'll work.

If you want to restore *all* the packages, try going to the "directory" (let's just say it's /media/cdrom) and then installing all the packages: ```
cd /media/cdrom
sudo dpkg -i *.deb
```

---

### Post by GrimJa on 2006-10-09
> **aysiu said:**
> I don't think you can add a CD-ROM as a repository unless it is properly constructed as a repository (with the appropriate directory structure and list of packages contained within). If it's just a collection of .deb files, I don't think it'll work.

If you want to restore *all* the packages, try going to the "directory" (let's just say it's /media/cdrom) and then installing all the packages: ```
cd /media/cdrom
sudo dpkg -i *.deb
```


Well, thanks for that ;)

I dont think I really want to restore all the packages,
(its a PACKED dvd lol), but that could come in handy with a small CD backup I have ;).


But question, when you say "restore" packages do you just mean that the files are going to be copied over to the approprite folders, or that the files will actually be installed , and that I'll see the applications and such when I restart? :confused:

---

### Post by aysiu on 2006-10-09
By *restore,* I mean that you will actually be installing those programs.

---

### Post by Frak on 2006-10-09
synaptics -> edit -> add CD-ROM

---

### Post by GrimJa on 2006-10-10
> **Frak said:**
> synaptics -> edit -> add CD-ROM

In short, that doesnt work.
My brain is really tired now, so I'm not 100% sure, but I think the error message said something  like - failed to add Cd as a repository, maybe this is not a debain disk.

The files are stored in a folder (the only one) on the CD named archives (yes, i backed up that folder).

I have 2 CDs, 1 is a DVD, the other a normal CD, both have their files in that folder.
Synaptic does scan the disk briefly, but it doesnt take it long to tell me Blah.:-k 

Anyone have another way? :|

(bear in mind that i've backed up the "Archives" folder, on both CDs)

Please Help

---

### Post by aysiu on 2006-10-10
As I tried to explain earlier, in order to add a CD as a repository, the CD has to have the proper structure and list of packages. It has to be *created* as a repository.

If it's just a list of *.deb* files, that's not enough.

---

### Post by GrimJa on 2006-10-10
Forgive me, I guess I overlooked that a bit.

But I now understand what you're saying.

Somehow I though just backing up the archives folder would facillitate all that, but I guess that was nothing but an assumption.

So tell me, what can I do to get these files installed.

BTW, I didnt try that dpkg command you were telling me about :o.

But I most certainly will tonight. I hope it works.
Call it unfounded negativity, but something in the back of my head is just telling me it wont :|
But I'll try anyhow.

---

### Post by CatKiller on 2006-10-10
> **GrimJa said:**
> So tell me, what can I do to get these files installed.

If you've got a big list of .debs, then you can install the particular .deb using [these instructions]("http://monkeyblog.org/ubuntu/installing/#deb"). You may have some trouble with dependencies and the like - if the package you want to install depends on packages that are already in that directory, you'll have to install them all with the one command. [The Ubuntu package search]("http://packages.ubuntu.com/") facility may help you with finding out the names of programs and how they tie into the packages you have.

---

### Post by GrimJa on 2006-10-10
Thank you very much for you links Catkiller. I really appreciate them, and though I dont have regular internet access, I think they'll help.

And thanks to everyone else also, I'll tell you how it goes tomorrow. Going home to try tonight ;)

---

### Post by GrimJa on 2006-10-12
Ok.. so In short.

EVERYTHING tried was a complete failure.

I tried restoring everything from the DVD. That screwed me because it was for ubunto 6, and I have 5.

So.. I reinstalled, thinking i would use the disk that I had personally backed up, I did try, but it never worked out;
after the packages were finished going on, nautilus crashed.
When I restarted nautilus, the machine crashed sometime afterwards (GDM) and the kernel would not show (F4,F5, none).
But the system was still up, because even though I couldnt see the kernel... I logged out and did a halt command.

I dont know what caused all this. After all, this is the very same system that I had got those (all of them) packages from. The only thing that changed, was my AGP card, and I think that may have something to do with it.

The other thing I'm considering as one possibly reason for te machine mucking after the restore.. is that I used the defaults for some lan+USB configurations that popped up, during restore.
I just pressed enter for most, because I didnt understand what they all were referring to.


I guess what I really need, is some way to restore individual packages.

P.S, for the short time that GDM comes up and doesnt crash, I can run amarok, and all the other apps I restores.

But in any case... Does ANYONE know how I can get what I backed up restored correctly?

---

### Post by bulldog on 2006-10-12
I think you have to install your original OS where you made the backup with.

Then you can reinstall your backups.

Shouldn't know another manner.

---

### Post by moore.bryan on 2006-10-12
> **GrimJa said:**
> Just how do I go about adding my CDRom drive as a ...source:confused:  or whatever.
In short, how do I get ubuntu to look towards my CDROM drive for packages?

*try ```
sudo apt-cdrom add cdrom
```*

---

### Post by aysiu on 2006-10-12
Do you need that last *cdrom*?

I think this works: ```
sudo apt-cdrom add
```

---

### Post by moore.bryan on 2006-10-12
[I]aysiu...
frankly, i don't know... :-)  i had issues with a reinstall before and that was the code someone gave me.  i was interested and i just checked the debian man page for apt and low and behold you're absolutely right... just apt-cdrom add.  thanks!
[/I]

---

### Post by GrimJa on 2006-10-13
> **aysiu said:**
> 
I think this works: ```
sudo apt-cdrom add
```
About this ^ 


Doesnt this ;
[QUOTE=aysiu;1597000]I don't think you can add a CD-ROM as a repository unless it is properly constructed as a repository (with the appropriate directory structure and list of packages contained within). If it's just a collection of .deb files, I don't think it'll work.QUOTE] Still apply?:???: 

Because in that case.. then I'd be back to square one.

As I was explaining, the package restoring didnt work out too well at all. Nautillus crashed after I restored the packages, and I have a good feeling that that has somethign to do with the fact that I had an AGP card using in my last system.

Lat night i tried doing things manually, copying over the packages manually, but the dependencies were far too complicated. 
What I'll try doing is copying over the files, but not over-writing the ones i have in my cache dir.
Then trying to install.

Sound feasible?

---

