---
title: "To uninstall any program I desire..."
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Roasted on 2006-08-09
Say I want to uninstall a program. Let's pick uh, how about Wine.

Would I just do this in terminal:

sudo apt-get remove wine

sudo aptitude purge wine

Is that it? Is that all I have to do? Is it the same two commands even if I want to uninstall Azureus or Bitcomet?

---

### Post by hopstah on 2006-08-09
yes, that's it.  but apt-get and aptitude are the same commands.  i'm not sure of the difference between remove and purge though.

the one drawback to this method is that it only removes the package 'wine' or whatever you specify.  i wish there was a way to remove all packages installed with a certain package if their removal won't break any other programs.  does anyone know of a way to do that?

---

### Post by bscbrit on 2006-08-09
Yep, that's one way of doing it.

Or you could do the same thing by using Synaptic and marking the program for removal.

---

### Post by Roasted on 2006-08-09
I thought "remove" removed the actual program, while "purge" deleted all of the files and whatnot associated with that program.

Like, if I were to remove AIM, it would delete AIM, yet my AIM folder would remain with all the other shit. Purge would then get rid of that, etc.

And I thought apt-get and aptitude were the same command, but with purge apt-get didn't work. I tried to sudo apt-get purge azureus and it said something invalid. I tried sudo aptitude purge azureus and it worked.

So do I use purge along with remove for EVERYTHING I want to get rid of? It's basically those 2 commands I gotta remember, period, done?

---

### Post by bscbrit on 2006-08-09
There is no 'apt-get purge' option - see man apt-get for more details.

sudo apt-get remove [packagename]

followed by by one of the 'apt-get clean' options will do what you want.

So the 'something invalid' message was probably referring to the command.  If it doesn't exist, the computer cannot do it!

---

### Post by GuitarHero on 2006-08-09
Using aptitude when install and removing is better because it doesnt leave left over dependecies.  Use it.

---

### Post by Roasted on 2006-08-09
So wait, what the hell is this clean option? I never heard of it.

Should I do:

sudo aptitude clean azureus
sudo apt-get remove azureus
sudo aptitude purge azureus

to FULLY remove azureus and its contents????????????

---

### Post by bscbrit on 2006-08-09
> So wait, what the hell is this clean option? I never heard of it.

Should I do:

sudo aptitude clean azureus
sudo apt-get remove azureus
sudo aptitude purge azureus

to FULLY remove azureus and its contents????????????

Well, the first thing I would suggest is that you start up a terminal or console, and type 'man aptitude', read it, and then type 'man apt-get' and do the same.  Secondly, don't try mixing the two commands.  Decide which one you want to learn to use, and stick with it.  Thirdly, if there is something that you don't understand, then come back with a specific question.  

If you use Synaptic (System -> Administration -> Synaptic Package Manager) if will give you the option to 'Completely remove' a package which does exactly what you want from a GUI.

The 'clean' option allows unwanted packages to be erased from the cache to free up space on the hard drive or to remove unusable packages etc.

---

### Post by Roasted on 2006-08-09
Yeah I know how to use synaptic, but I don't know how to use terminal that well so that's why I'm asking.

I still don't understand why I can't get a more direct answer (no offense). I mean, which commands should I use all the time? I have been using sudo aptitude purge azureus + sudo apt-get remove azureus. And you say that's bad to mix? I just want to know the best commands to use to COMPLETELY uninstall/remove a program so I don't have to come back here again.

---

### Post by UltraMathMan on 2006-08-09
```
sudo apt-get remove --purge *program*
``` will remove the program and all the configuration files associated with it.

```
sudo apt-get clean
``` removes the package associated with the program when it was downloaded to the cache (basically if you uninstall WINE and decide you want to reinstall it and you haven't cleaned the cache you won't need to redownload it (it's already stored on your computer). The clean command removes the package which would otherwise remain on your computer.

```
sudo apt-get autoclean
``` removes superceded pakages. Say you upgraded WINE five times, there are packages for all five versions in the cache. Autoclean removes the four oldest versions while leaving the latest one.

-Hope this helps :)

---

### Post by bscbrit on 2006-08-09
It doesn't matter which you use - its a personal preference.  So, at the command line, type

man apt-get     or
man aptitude

and read how that each variant works.  It will tell you exactly what it does although it they are not the easiest of documents to read.  If you still have a problem understanding what it is trying to say (and we all do - its not just you!) then come back and ask for clarification of that specific point.  

Nobody can learn how to do things in Ubuntu on your behalf.  The best that one can ever wish for is a pointer in the right direction and perhaps the solution to a particular problem.  

Linux is sufficiently different from Windows that we all go back to the bottom of the expertise ladder when we start to use it.  The 'man' pages (and there is one for almost every command that you have on your system) can be useful in telling you what a command does, its various flags and options and where to find related items.

sudo apt-get remove azureus
sudo apt-get clean all

will remove the software from your computer.  It will not remove configuration files.  They are (probably) in /etc under the heading azureus.  If this directory or config file exists, remove it also.

Aptitude will have a very similar set of commands but not exactly the same.  For example, it has 'purge' (which apt-get has as a flagged option).  Purge does just what you want in that it also removes the configuration files.

[EDIT]  The previous post covered it before me!

---

### Post by Roasted on 2006-08-09
Probably a dumb question but I assume 

sudo apt-get remove --purge azureus is a combination of

sudo apt-get remove azureus
+
sudo apt-get purge azureus

Is the combination command used for convenience, or is there another reason for it?

---

### Post by UltraMathMan on 2006-08-09
I don't think apt has a purge option, the --purge is a flag for the apt command, so I don't believe apt-get purge *program* would work.

---

### Post by Roasted on 2006-08-09
You're right, it was aptitude.

Sooooo now I'm lost again. Why would "purge" be in the apt-get line that was posted above with remove?

"Sudo apt-get remove --purge azureus"

How does that differ from sudo apt-get remove azureus?

---

### Post by bscbrit on 2006-08-09
> 
sudo apt-get remove azureus
sudo apt-get clean all

will remove the software from your computer. It will not remove configuration files. They are (probably) in /etc under the heading azureus. If this directory or config file exists, remove it also.


Thats all you have to do!

---

### Post by UltraMathMan on 2006-08-09
> **Roasted said:**
> You're right, it was aptitude.

Sooooo now I'm lost again. Why would "purge" be in the apt-get line that was posted above with remove?

"Sudo apt-get remove --purge azureus"

How does that differ from sudo apt-get remove azureus?

sudo apt-get remove azureus removes azureus but leaves behind any configuration files generated by it while the --purge flag removes those as well.

---

### Post by Roasted on 2006-08-09
I see. So I'm under the impression there's two ways I can do this...

either


sudo apt-get remove --purge azureus : to remove all of the config files + the actual program

or

sudo apt-get remove azureus
sudo apt-get cleanall : to get rid of azureus the program plus cleanall, which acts in the same way purge does.

Right? :-k

---

### Post by UltraMathMan on 2006-08-09
Almost ;) 

sudo apt-get remove --purge azureus : to remove all of the config files + the actual program

sudo apt-get remove azureus : to remove program only

sudo apt-get clean : to remove all packages in the cache (ie the file downloaded from which the program is installed)

sudo apt-get autoclean : to remove all packages in the cache, of each program, except the most recent version.

---

### Post by Roasted on 2006-08-09
OKAY! thanks for that clarification...

So in the end, if I use 

sudo apt-get remove --purge azureus

Then I DO NOT need to use

sudo apt-get remove azureus

Cause the first command I posted with the purge line ALSO removes the program. Right? WOOOOOOOO

---

### Post by UltraMathMan on 2006-08-09
Right :D

---

### Post by Roasted on 2006-08-09
K, question. I installed wine. For some reason the installation that I followed on winehq took about 2.5 hours and it wasn't even done yet. I exited it and decided to ditch wine and try out cedega. I did sudo apt-get remove --purge wine, sudo aptitude remove wine, sudo aptitude purge wine, I tried everything I could think of.

Yet when I search for "wine" I find 160 files. :confused:

---

### Post by Roasted on 2006-08-09
hi

---

### Post by UltraMathMan on 2006-08-09
hmm, not really sure why that is...what command sequence are you using to search for it?

---

### Post by bscbrit on 2006-08-10
> **Roasted said:**
> K, question. I installed wine. For some reason the installation that I followed on winehq took about 2.5 hours and it wasn't even done yet. I exited it and decided to ditch wine and try out cedega. I did sudo apt-get remove --purge wine, sudo aptitude remove wine, sudo aptitude purge wine, I tried everything I could think of.

Yet when I search for "wine" I find 160 files. :confused:

If you are searching using Synaptic then, depending on your selected options, it will search both filenames and file descriptions.  Many descriptions could contain the string 'wine' without necessarily having to have 'wine' installed.

If you are searching from the command line then we will need the answer to UltramMathMan's question.

---

### Post by Roasted on 2006-08-10
I'm searching from places - search.

---

### Post by bscbrit on 2006-08-10
OK, which folder(s) are you searching in?  In which folder are files being found?

---

### Post by Roasted on 2006-08-10
My home folder, which is just my name "Jason." 

I'm seeing files anything from wine.xpm, wineconsole, wine text documents, etc. 160 files worth.

---

### Post by bscbrit on 2006-08-10
Did you install wine to your home directory?  Or might you have accidentally unpacked a zip or tar file there?  I think that you can safely delete them -they shouldn't be there.

---

### Post by tokenwizard on 2007-09-09
> **UltraMathMan said:**
> ```
sudo apt-get remove --purge *program*
``` will remove the program and all the configuration files associated with it.

```
sudo apt-get clean
``` removes the package associated with the program when it was downloaded to the cache (basically if you uninstall WINE and decide you want to reinstall it and you haven't cleaned the cache you won't need to redownload it (it's already stored on your computer). The clean command removes the package which would otherwise remain on your computer.

```
sudo apt-get autoclean
``` removes superceded pakages. Say you upgraded WINE five times, there are packages for all five versions in the cache. Autoclean removes the four oldest versions while leaving the latest one.

-Hope this helps :)

Ok, Here's something interesting for you...
I am trying to completely get rid of Wine and start over. I went into Synaptic and marked if for "Complete Removal" and it completed. Then, just to be safe, I went into terminal and ran "sudo apt-get remove --purge wine" (which of course came back and said wine was not installed). I then ran apt-get clean and apt-get auto clean. 

Everything seems good, right? Well, I go into my home folder and tell it to show hidden files, and I STILL have a .wine folder there with all the program files I had installed with Wine.  But hey, at least all the entries for Wine have been removed from the Gnome Panel menus!

Is there anywhere else that Wine places config files or information? I guess I will need to delete that .wine folder from my home menu as well as any other instances of wine config files places elsewhere in the filesystem.

---

### Post by count_zero on 2007-09-11
Sorry to piggyback on someone else's question, but:
I've been trying to install GTKPod and/or Thinliquidfilm for a couple of days, including various libraries. I've always downloaded the files to desktop and unpacked them there (which might explain why none of the libs were seen!) then moved them to the recycle bin when it didn't work, so as far as I can tell they're off the system.
However, last night I tried GTKPod (or liquidfilm, I can't remember, it was late...) again and tried doing a 'make' which seemed to do something, but I had shut down before it had finished (for girlfriend reasons).
My questions are:
[INDENT]Is there likely to be any residual data from the incomplete 'make' and how do I get rid of it.[/INDENT]
                             
[INDENT]Can I use the search function to find any bits that I've incorrectly installed outside of Add/Remove or SPM (I'm on my work windows system at the moment so can't check this), or would  the How-to at: 

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

be a better way of dealing with this?[/INDENT]

---

### Post by UltraMathMan on 2007-09-11
@tokenwizard: try ```
locate wine
``` to search for any other instances.

@count_zero: gtkpod is available through the repositories, Ubuntu has a package management system to install progams for you so that you don't have to hunt down dependencies. to install it do ```
sudo apt-get install gtkpod
``` or find it in System->Administration->Synaptic Package Manager.

-Hope this helps :)

---

### Post by asmoore82 on 2007-09-11
> **Roasted said:**
> K, question. I installed wine. For some reason the installation that I followed on winehq took about 2.5 hours and it wasn't even done yet. I exited it and decided to ditch wine and try out cedega. I did sudo apt-get remove --purge wine, sudo aptitude remove wine, sudo aptitude purge wine, I tried everything I could think of.

Yet when I search for "wine" I find 160 files. :confused:

the quick search "locate" and "slocate" functions depend on a database that is only updated
every 24 hours. the command that does this update is **updatedb** and is part of a standard cronjob ...
```
~$ cat /etc/cron.daily/slocate 
#! /bin/sh

if [ -x /usr/bin/slocate ]
then
        if [ -f /etc/updatedb.conf ]
        then
                /usr/bin/updatedb
        else
                /usr/bin/updatedb -f proc
        fi
        chown root.slocate /var/lib/slocate/slocate.db
fi
```

"locate" and "slocate" are pretty much useless **in the short-term** and
I would assume that the GUI search is using them on the back end.

the only things you have to really be concerned with are
**purge**-ing packages and **autoclean**-ing once in a while.

And, just to melt-down your brain, most packages that you run and later remove
will still leave behind hidden "dotfiles" in your home directory; this is not a bug.
Ususually I/we don't even think about them, but in the case of WINE, it houses the
entire fake C: drive and can grow rather large, you can remove it like so...
```
~$ /bin/rm -rf ~/.wine
```

---

