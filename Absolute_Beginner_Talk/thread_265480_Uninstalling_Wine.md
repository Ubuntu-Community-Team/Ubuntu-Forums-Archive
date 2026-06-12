---
title: "Uninstalling Wine????"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by soutSA on 2006-09-26
I have installed Wine, but being a newbie I have made a couple of mistakes and want to start over. Can you do the uninstall with Synaptic? 
How can you find out where the wine files have been installed? 
What do you need to manually delete?

For future use and uninstall of packages and programs.....what is the easiest why to do this?


Thanks in advance:-k

---

### Post by em3raldxiii on 2006-09-26
The absolute best way (from what I can tell) to install wine (or any application) is to open your command line terminal (applications > accessories > terminal), and type this:

```

sudo aptitude install wine

```

Now since WINE is a kinda special package, the process may be a little different, and it's been a LONG time since I installed it.  It's been installed and I barely use it.  If you want to run Internet Explorer in Linux (for those annoying web pages that "require" it), do a google search for **ies4linux**.

Once you have WINE installed, you shouldn't have to dick with the configuration 'n stuff.

To remove WINE, you can try this:

```

sudo aptitude remove wine

```

Notice that I use **aptitude** instead of **apt-get** ... this is because it handles the uninstall process MUCH better than apt-get (only if you used Aptitude to install it, as far as I know).  Either way, you should be able to use the command-line to remove it effectively.

Ugh ... my head is feeling fuzzy ... time for sleep.  Sorry if I rambled incoherantly, but my vision is swimming .... 'nite :D

---

### Post by soutSA on 2006-09-26
Thanks for the reply...

I still got another question regarding this. Is there a way to see where wine has been installed to ex:

/etc/wine
/home/wine
/boot/wine
/usr/wine

I tried to run the "locate" command to find all the "wine" files:

#locate wine

It gave me a lot of files, mostly in the /usr/lib/wine and /usr/share/wine. Is this and effective why of finding all wine files?

Will the Apptitude remove wine remove all wine related files or will there still be some files left like in windows?:(  If so, how do I locate these files and can you just go and remove them manualy?

I want to know how to do this and am only using Wine as an example, because I am sitting with the problem at the moment and would like to know for future reference too.

PS: I am only trying to learn more about linux and would really like to know how to keep my system as clean as possible.

Thanks in advance

---

### Post by CatKiller on 2006-09-26
> **soutSA said:**
> I have installed Wine, but being a newbie I have made a couple of mistakes and want to start over. Can you do the uninstall with Synaptic? 
How can you find out where the wine files have been installed? 
What do you need to manually delete?

For future use and uninstall of packages and programs.....what is the easiest why to do this?


Thanks in advance:-k

If it's just a problem with your configuration, or you've messed up the pretend registry in the pretend Windows or whatever, you can just delete the .wine directory in your Home folder (Ctrl-H to see hidden files). All the config files and the pretend C: drive are in there. The next time you run Wine, this directory will be recreated, giving you a fresh install of pretend Windows.

If you really want to remove a package, then by far the best way is with Synaptic/aptitude. It's really not a good idea to just delete some of the files (with the exception of stuff in your Home folder), since that's likely to mess up the packaging system. I suspect that a lot of applications do leave their configurations behind when you remove the packages, but these are (usually) simply in directories like .wine or .scummvm or whatever. These can safely be deleted afterwards if you want to get rid of the configurations as well.

If you're curious about which files a particular package has installed, open up Synaptic, find the package and click on Properties. The installed files are listed as one of the tabs.

---

### Post by em3raldxiii on 2006-09-26
As far as learning how packages and "installed components" are handled by Linux, WINE is not a very good example really.  It's a "special" software package that doesn't do things the way 95% of all other packages do.  However, Catkiller was right about the part where *you do not want to delete files in your filesystem* without a correct removal process.  In Linux, this is due to a vast array of "shared components" and "common resources" (which explains why Linux applications use FAR less disk space than similar Windows apps).  With WINE, first you do the [COLOR="Blue"]aptitude remove[/COLOR] command which will remove all the parts that Linux is aware of (especially if you originally *installed* with aptitude).  Using the Synaptic Package Manager will do much the same thing.  Then you can remove your [COLOR="#0000ff"]/home/USERNAME/.wine[/COLOR] directory.  If you are using a file browser (you know, the normal graphical way of looking at your folders), then as Catkiller says hit [COLOR="#0000ff"]ctrl-h[/COLOR] to view hidden files (any file or folder that starts with a period like **/.wine** is a hidden file).

But like I said, WINE is atypical, so it's not a good example of how Linux handles the installation and removal of normal applications.  From what I can tell (and I am only a few months ahead of you), using the command line [COLOR="#0000ff"]sudo aptitude install <application>[/COLOR] is the most comprehensive way to install and remove programs.  Aptitude is a little program that handles all the complicated interdependencies of Linux applications, so that if/when you decide to remove that application, it correctly removes any dead dependencies.  Other package management systems may not be as effective.  Unfortunately, if you originally installed something with **apt-get** instead, then using **aptitude** to remove it will not benefit you.  I believe it has something to do with aptitude building a little database that keeps track of what is installed where and how to remove it.  

There was a wonderful little article about this somewhere ... I'll find it if I can :D

The end result is that, if correctly handled, aptitude will remove all "residue" of the formerly installed package, thus keeping your system as "clean" as possible.  Keep in mind, though, that Linux does a substantially better job of handling the filesystem in general than Windows, so you should never run into the same problems.

*EDIT:  I just did some interesting reading.  Here are some really cool links for further information.  It appears that the Ubuntu gods are listening to you :D*.

[Aptitude versus Apt-get]("http://www.psychocats.net/ubuntu/aptitude.php")

[Ubuntu development page RE dependency removal tool for Synaptic (already in beta testing)]("https://launchpad.net/distros/ubuntu/+spec/dependency-removal")

[Ubuntu Forum discussion about aptitude versus apt]("http://ubuntuforums.org/showthread.php?t=221176")

[A Beta tool called gtkorphan which apparently scans your system for orphaned dependencies.]("http://www.marzocca.net/linux/gtkorphan.html")

Hope that helps :D
*END EDIT*

---

### Post by CatKiller on 2006-09-26
Thank you. You clarified a lot of things that I didn't explain very well. I'm pleased that Synaptic will be getting funky dependency-removal things too - I'm aware (possibly from your other posts on the subject) that aptitude is better for this than apt-get that I understand Synaptic uses, but I still use Synaptic. It's prettier, easy to browse, and all of the packages that I'd got previously, I'd got through Synaptic. Maybe after Edgy is released I'll start using aptitude. :)

---

### Post by em3raldxiii on 2006-09-26
Hehe, well if Synaptic starts to handle dependencies like Aptitude does (or maybe if all the package managers could play along together nicely), then *I* would start to use Synaptic ;)

This is definitely case-in-point about how the Linux community directly affects the software itself.  You don't see this sort of user-input in *ahem* *OTHER* Operating Systems, hey?

---

### Post by soutSA on 2006-09-27
Thanks for all the advice!!!

Those links help a lot and pointed me in the right direction.

Thanks a million.

---

### Post by em3raldxiii on 2006-09-27
You are more than welcome, my friend!  Like I said, I'm only a couple of months ahead of you on the learning-curve, so I [COLOR="Blue"]really[/COLOR] understand what it's like to be in your position.  One of the things I found most perplexing (and I think most newbie Linux users will agree) is the stark difference in file structure.  I've seen MANY other posts to this effect, but when you first start, the directory tree is frightening.  /etc?  /bin? /var?  What is all this, and how do I know what goes where???  I'm still not entirely sure I know, to be honest, but I have found that in general you can just trust that Linux knows where to put it's stuff and you shouldn't dick around with very much in those folders.  Just the odd xxxxx.conf file, or some such.  It's not like in Windows where you have to know where every single file actually lives.  So many components are shared, and that's probably the very core of the filesystem.

Bla bla bla ... there I go again.  I swear, I just like to see my own typing on the screen.  LOL!

Anyway, keep up the questions and I'll continue to be verbose ;)  Let us know if you discover anything (plus it could help others who view this thread).

---

### Post by panthertd175 on 2008-05-12
I have had a similar problem with wine.  I am still new to Ubuntu after just switching from xp.  My first attempt at using wine was to install iTunes.  The installation was unsuccessful and stopped part way through, after installing seemingly more files for Quicktime than iTunes.  When I tried to uninstall what had been installed of Quicktime, it said Quicktime has been successfully installed (not uninstalled), but it still didn't work. Stupidly I tried to delete any iTunes/Quicktime files in the pseudo c: drive.  (This often works in windows).  This ended up just messing up the wine application.  With the wine application installed, I can't browse the c:\ from the menu nor can I use it to install any other programs.  After uninstalling wine, running the sudo aptitude remove wine command succesfully and deleting the .wine files in my home folder, my problem still isn't solved. When I reinstall wine the missing directories are not replaced. Also, when wine is removed there is still in the applications menu a "wine" folder, with a subfolder "programs" where Bonjour (I'm not sure what that is), "Quicktime" and Apple software update are located.   Again, I am a new user so the more detail the better, but I just want to at least first restore wine to a working order.  Any help would be appreciated.

---

### Post by Victormd on 2008-05-12
Ok, to the removal process...
I'm not sure if you noticed but this is from 2006... :)
I'm going to go with the apt-get approach here.
in the terminal, type
```
sudo apt-get purge wine
sudo apt-get autoremove
```
then,
```
sudo rm -r /home/USERNAME/.wine
```
**[COLOR="Red"]REPLACE USERNAME WITH YOUR LOGIN AND BE VERY CAREFULL, YOU HAVE TO INCLUDE /HOME/USERNAME/.WINE, OTHERWISE THIS COMMAND CAN DELETE YOUR ENTIRE SYSTEM[/COLOR]**
Ok, this will remove wine. You will notice that it might still be showing under the Applications menu, don't worry, that's a dead link that can be removed in the end if necessary.
Now, to assure that you have the latest version, copy and paste these commands to the terminal:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```
These codes are taken from the [WINE website]("http://www.winehq.org/site/download-deb")
Now, to reinstall:
```
sudo apt-get update
sudo apt-get install wine
```
This should reinstall wine properly.
To remove the menu entries under Applications, go to SYSTEM>PREFERENCES>MAIN MENU and you will be able to browse and remove the links there...

Let me know how this goes

---

### Post by inportb on 2008-05-12
> **panthertd175 said:**
> I have had a similar problem with wine.  I am still new to Ubuntu after just switching from xp.  My first attempt at using wine was to install iTunes.  The installation was unsuccessful and stopped part way through, after installing seemingly more files for Quicktime than iTunes.  When I tried to uninstall what had been installed of Quicktime, it said Quicktime has been successfully installed (not uninstalled), but it still didn't work. Stupidly I tried to delete any iTunes/Quicktime files in the pseudo c: drive.  (This often works in windows).  This ended up just messing up the wine application.  With the wine application installed, I can't browse the c:\ from the menu nor can I use it to install any other programs.  After uninstalling wine, running the sudo aptitude remove wine command succesfully and deleting the .wine files in my home folder, my problem still isn't solved. When I reinstall wine the missing directories are not replaced. Also, when wine is removed there is still in the applications menu a "wine" folder, with a subfolder "programs" where Bonjour (I'm not sure what that is), "Quicktime" and Apple software update are located.   Again, I am a new user so the more detail the better, but I just want to at least first restore wine to a working order.  Any help would be appreciated.

So... you've removed ~/.wine . Have you also removed ~/.local/share/applications/wine ?

---

### Post by panthertd175 on 2008-05-12
Haha yes I did realize this was from 2006, but it seemed to be exactly the problem I had.  Removing ~/.local/share/applications/wine did just the trick.  Thanks a lot.

---

### Post by inportb on 2008-05-12
Nice that it worked for you too. I was having headaches with my M$ Office setup until I found this other wine directory.

---

### Post by Victormd on 2008-05-13
Don't forget to mark the post as solved... :)

---

### Post by RequinB4 on 2008-05-14
For future reference, if your problem is based on a wine program, you may not have to re-install wine at all - the real problem is in your .wine directory, where the registry and all the windows program files go.  Before uninstalling, you may want to fix by renamine .wine to .wine.backup and running:

```

wineprefixcreate

```

This will give you a brand spanking new virtual C drive and wine config files.

---

### Post by inportb on 2008-05-14
> **RequinB4 said:**
> For future reference, if your problem is based on a wine program, you may not have to re-install wine at all - the real problem is in your .wine directory, where the registry and all the windows program files go.  Before uninstalling, you may want to fix by renamine .wine to .wine.backup and running:

```

wineprefixcreate

```

This will give you a brand spanking new virtual C drive and wine config files.

True. Or you can run any program through Wine and have the directory automatically generated =P

---

