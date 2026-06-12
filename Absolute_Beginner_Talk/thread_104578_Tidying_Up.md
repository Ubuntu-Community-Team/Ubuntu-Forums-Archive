---
title: "Tidying Up"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by Brainless on 2005-12-16
Is there a CCleaner-like program for Linux? :-s

---

### Post by bscbrit on 2005-12-16
I'm not sure what CCleaner does, but you could look for something here:

[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

If that does not help, let me know exactly what CCleaner does, and I will a. let you know whether you need it under linux, and b. try to find an equivalent if you do need it.

If you find an equivalent, it is always worth letting the Admins know so that they can add it to the link that I have given above.

---

### Post by bscbrit on 2005-12-16
OK I have Googled for CCleaner and now understand more about its function.  If you want to install a program to remove spyware and adware - you don't need to.  Open Source software means that the code is scrutinised by many people before it gets to your machine.  It is most unlikely to contain spyware or adware!  That is one of the benefits of Linux!
If you are trying to (ahem!) hide your browsing habits then there is nothing that specifically does this job but it is fairly easy to achieve the same thing using existing ubuntu utilities.  'wipe' will securely delete files and directories so that the data cannot be recovered without huge difficulty - probably not even worth Government agencies' efforts unless they are convinced that you are up to no good!  But you still have to know which files and directories to delete.  That depends on which programs you are using so I cannot provide a simple answer.
One solution would be to browse the web and then use 'find' with the appropriate flags to discover which files have changed while you were online.  That should give you a clue as to what needs deleting.
**I am giving you this information to enable you to protect your privacy - I am not condoning or advocating that you use your computer for any purpose that is illegal!**

---

### Post by Brainless on 2005-12-16
I'm looking for software that'll automatically get rid of junk files. Under Windows, I had a lot of unnecessary files left behind by obsolete software. :smile:

---

### Post by bscbrit on 2005-12-16
I wasn't suggesting anything else!  However, I have not experienced the same problem with linux and I have used several different distros over the last few years.  A useful tip (if you haven't already done something similar) is to create a directory called say 'downloads' and set your browser and other programs to use that, rather than the default desktop.  Then all of the downloaded data is either in that directory or in /tmp, both of which can be easily erased and/or cleaned.  Of course, browsers also keep a record of where they have been etc, but if you are using the default Firefox then there is the option under Edit-Preferences-Privacy to delete that data also.

---

### Post by bscbrit on 2005-12-16
I suppose that junk files from previously installed software could apply equally to linux as windows but I cannot say that I have ever noticed by disk filling up because of it.  The method of using shared libraries that linux uses is far more efficient than the method that windows employs.  Under windows, you might find that a dozen programs each install the same dll, but put it in different locations.  Furthermore, uninstalling the programs is notorious for not removing such items, or for removing records from the registry.  Such problems do not occur in linux, especially if you use  synaptic / apt-get with the appropriate options to remove files.

---

### Post by Brainless on 2005-12-16
[QUOTE=bscbrit]Then all of the downloaded data is either in that directory or in /tmp, both of which can be easily erased and/or cleaned.[/QUOTE]

How do I clean /tmp? :confused:

---

### Post by bscbrit on 2005-12-16
As /tmp is used for quite a few things while you are logged on as a user, you cannot just delete the contents of the directory without creating problems.  But most of the items in that directory are self evident (at least to a certain degree).  You can either simply delete those using either Gnome or from the command line, or use a simple bash script to do the job automatically everytime you log off.  You will probably have to use 'sudo' to give you sufficient privileges to do the job.  Erasing the files will slow down the logging off procedure, perhaps for as much as a few minutes on a slow machine, while it does its job but it will achieve the task.  We complain when computers are slow to boot but being slow to switch off is usually less of a problem.

---

### Post by Mustard on 2005-12-16
[QUOTE=Brainless]How do I clean /tmp? :confused:[/QUOTE]
I have always assumed that tmp is cleaned each time you reboot.  It may even be a 'cron job'.  Cron jobs are regular jobs that linux does in the background at specific times or with specific triggers.

---

### Post by bscbrit on 2005-12-16
Mustard, I have also read that but I have also found that some files seem to have survived several reboots, even when the computer as been left running for several days between each one.  Perhaps I am just paranoid...

---

### Post by wylfing on 2005-12-16
[QUOTE=Brainless]I'm looking for software that'll automatically get rid of junk files. Under Windows, I had a lot of unnecessary files left behind by obsolete software. :smile:[/QUOTE]

1. What makes you think Ubuntu has the same problem? Ubuntu is not Windows.
2. What exactly do you mean by "obsolete" software? If you mean "uninstalled" then you don't have to worry as long as you are using Synaptic or apt-get to manage your installed applications. (Use Mark for Complete Removal to get rid of all the files.)
3. What exactly do you mean by "unnecessary" files? How do you know they're unnecessary?
4. Don't start "cleaning up" /tmp or /var or you'll break your system.

---

### Post by Georgie-o on 2006-05-07
In Windows (which I dislike and am not defending) I have seen a program called "R-Wipe and Clean."  This software deletes all traces of deleted files permanently using DoD 3 or 7 pass write-overs.  Let's say I'm not a secret agent or anything, but just want to know that files are acutally deleted.  Any program to do this?


ps-  bscbrit "Mustard"?!?!

---

### Post by xyz on 2006-05-07
I'm not sure...but would this be what you're looking for:
[http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan](http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan)

Good spring cleaning!

---

### Post by Mustard on 2006-05-07
[QUOTE=Georgie-o]In Windows (which I dislike and am not defending) I have seen a program called "R-Wipe and Clean."  This software deletes all traces of deleted files permanently using DoD 3 or 7 pass write-overs.  Let's say I'm not a secret agent or anything, but just want to know that files are acutally deleted.  Any program to do this?


ps-  bscbrit "Mustard"?!?![/QUOTE]

There is a program called wipe (available in the repositories).  This will securely wipe files.  It works from the command line.  I set it up to work with a nautilus script so I can right click on the files and delete them that way.

I was reading over the forum for the dban nuke application for wiping an entire hard drive and its got some interesting information on the intricacies of securely deleting information from hard drives.  With a journalised filesystem like ext3, its a  difficult thing to remove all traces of a file.

---

### Post by Georgie-o on 2006-05-07
Thanks for the reply.  From the description in synaptic that is exactly what I'm looking for.  I read his manual to see if i can figure it out.

It took me a while to figure out that "Mustard" is your name...

---

### Post by Georgie-o on 2006-05-07
I reviewed the documentation.  You noted that you did a setup to make it do a secure wipe with a right click.  Is this something you could describe?  Also. what folder would you wipe to permanently clear your browser history?

Thanks

---

### Post by ComplexNumber on 2006-05-07
[quote=Brainless]Is there a CCleaner-like program for Linux? :-s[/quote] there's a KDE program called kleansweep [here]("http://www.kde-apps.org/content/show.php?content=28631"). its a program that clears out junk files from one's system. i don't know of any gnome equivelent because i've not looked for one. maybe KDE needs it whilst gnome doesn't ;)
make sure you install the Qt and KDE libraries beforehand.

---

### Post by altonbr on 2007-07-29
> **Mustard said:**
> There is a program called wipe (available in the repositories).  This will securely wipe files.  It works from the command line.  I set it up to work with a nautilus script so I can right click on the files and delete them that way.

I was reading over the forum for the dban nuke application for wiping an entire hard drive and its got some interesting information on the intricacies of securely deleting information from hard drives.  With a journalised filesystem like ext3, its a  difficult thing to remove all traces of a file.

I like to use 'secure-delete' personally. It has a binary called 'srm' which is acts just as 'rm' but uses the DoD secure delete algorithm.

So on the topic, there is a Launchpad spec trying to add secure delete by default to Ubuntu (which I agree with). If you're interested, or if you know how to script (like you did Mustard), can you please take a look?

[https://blueprints.launchpad.net/ubuntu/+spec/gnome-secure-trash](https://blueprints.launchpad.net/ubuntu/+spec/gnome-secure-trash)

---

