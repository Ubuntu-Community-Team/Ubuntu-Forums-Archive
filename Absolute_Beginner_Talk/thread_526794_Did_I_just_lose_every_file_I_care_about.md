---
title: "Did I just lose every file I care about?"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by neander on 2007-08-15
I cannot believe this...for the first time I wanted to make sure I had all my important notes and data files on ubuntu edgy backed up to cd so I read the help files, which say drag the files you want to back up to the cd/dvd burner dir and then click burn to cd. So I did. The burn to cd dialog was greyed out so I had to close it. I rebooted. Now, it seems that all of my important files were MOVED to the cd/dvd burner folder and are competely GONE! I cannot believe it but they are gone and there is nothing in the trashcan etc.

Someone please tell me how to get my files back. And someone, please explain how what just occurred makes the slightest bit of sense. If the help file paragraph had mentioned that I was going to remove the selected files from disk it's have been just slightly helpful.

I am so disappointed by this.

---

### Post by original_jamingrit on 2007-08-15
I'm not sure, but I think this might help:

[http://ubuntuforums.org/showthread.php?t=229143](http://ubuntuforums.org/showthread.php?t=229143)

---

### Post by Hobo Joe on 2007-08-15
Try installing testdisk. Brace yourself though, becuase it's complex, and will take quite some time. And it may not work.
```

sudo aptitude install testdisk

```

Also, for future reference, it's better to use a program such as gnomeburner for things like this.

---

### Post by steveneddy on 2007-08-15
[HTML]Did I just lose every file I care about?[/HTML]

Probably

---

### Post by neander on 2007-08-15
There is nothing in lost + found, if there was supposed to be some chance that it had backups or stray files.

I just cannot believe this. How could the instructions for using the cd\dvd burner be so incredibly lame? It's just insanely stupid that following the instructions MOVES files from your hdd to cd, if it doesn't blow up. Anyone would have assumed from the instructions that the cd/dvd burner list were pointers to the real files and folders.

My god I had no idea ubuntu could be this dumb. Sorry, but I am really shocked that something this brutal could happen so easily. It's not like I'm using a cutting edge version, this is 6.10.

---

### Post by original_jamingrit on 2007-08-15
This is an odd problem, it shouldn't be *moving* things.  Nothing's even supposed to happen untill the burning process begins.  Were you using the default nautilus burning application?

> **steveneddy said:**
> Probably

+ lame

---

### Post by neander on 2007-08-15
There is an application listed as cd/dvd creator in the nautilus Go menu. I assume it's there by default but possibly I installed it a long time ago and never used it.

What a wake up call to beware of this os. Not, not use it, I don't mean that. But it's way more deadly than windows. I'm a programmer by trade, and I've never had a data loss like this other than perhaps the first month when I was using my xt.

---

### Post by Hobo Joe on 2007-08-15
> **neander said:**
> There is an application listed as cd/dvd creator in the nautilus Go menu. I assume it's there by default but possibly I installed it a long time ago and never used it.

What a wake up call to beware of this os. Not, not use it, I don't mean that. But it's way more deadly than windows. I'm a programmer by trade, and I've never had a data loss like this other than perhaps the first month when I was using my xt.

It's still worth giving testdisk a try. It might not work, but man I'd want to try everything if I lost a bunch of data. Actually, I have before, so I know what you're going through.

---

### Post by neander on 2007-08-15
I installed testdisk, that went well but what do I do with it? It's not listed on any menu. I guess I need to read up on testdisk...what is it, a file recovery tool?

All of you, thanks for trying to help.

---

### Post by Hobo Joe on 2007-08-15
```

testdisk

```
In console. General rule of thumb, if it's not in the menu, try just typing the name of the program in the terminal.

---

### Post by AnRa on 2007-08-15
Try using:
```
locate *file*
``` (where file is one of the missing ones) to make sure that they aren't hidden somewhere.

---

### Post by dasunst3r on 2007-08-15
When I dragged a file to the CD/DVD creator, the file is *not* moved.  How did you put the files in the CD/DVD?  Ctrl+C -> Ctrl+V or Ctrl+X -> Ctrl+V?  If it's the latter, then you may have indeed lost your files.

---

### Post by Cappy on 2007-08-15
What you want to do is open a terminal, maximize it to your full screen and type
```

sudo photorec
```
photorec is installed when you install the testdisk package. photorec will recover lost files. testdisk is for recovering lost partitions.

---

### Post by Hobo Joe on 2007-08-15
> **Cappy said:**
> What you want to do is open a terminal, maximize it to your full screen and type
```

sudo photorec
```
photorec is installed when you install the testdisk package. photorec will recover lost files. testdisk is for recovering lost partitions.

Oops, my mistake.

---

### Post by neander on 2007-08-15
OK, but in this scenario, what option do I go for? Analyze or Advanced/File system utils? I've not lost a partition...this software seems mostly to be about recovering partitions.

---

### Post by michaelzap on 2007-08-15
I don't understand how this happened to you. If I drag files to the burner window in Nautilus they are not moved, and if I then delete them from the burner window the actual files are not affected. That sounds like a very strange and frightening error!

---

### Post by Hobo Joe on 2007-08-16
> **neander said:**
> OK, but in this scenario, what option do I go for? Analyze or Advanced/File system utils? I've not lost a partition...this software seems mostly to be about recovering partitions.

Do what Cappy said and run Photorec instead. Just look around the program, it has a few different options, all of which can be useful.

---

### Post by vexorian on 2007-08-16
It is odd, but I guess that if you wanted to copy the files you should have copied the files.. no need to blame the OS for doing what you asked it to do...

edit : no matter how hard I try, the files don't get lost, are you confident you didn't manually remove them? cause this sounds as ultra unlikely. If not then there should be somewhere, verify if you have gained free space in your partition.

edit: ho to your home, make it show hidden files, look for a .trash folder..

edit II: This is terribly odd, burner:/// does not hold any file but references to it, so it is simply impossible to move files there, please try to recapitulate what happened, it might be helpful to a)know what actually happened. b) report the bug.

---

### Post by neander on 2007-08-16
Here are the precise and simple steps I took.

Try to drag and drop some files to the cd drive, which had a cdrw disk in it. Not surprisingly that didn't work.
Looked in ubuntu help for 'burn to cd'. Found the entry for cd/dvd burner. Followed the cd/dvd burner directions there. That is:

opened the cd/dvd creator folder via Go on Nautilus.
dragged the files and folders I cared about to it.
Clicked the burn to cd button
Dialog opens but is greyed out. Wait a couple minutes and then 'force close' after clicking the red x.
Try again same result
Reboot
Try again, add files back to the 'burn' folder via drag drop.
This time the dialog opens but is not greyed out.
Wait and wait, nothing is being written to cd. Close the dialog. reboot
The files I had moved to the folder are gone from any location I can find.

I'll try that latest suggestion above re recovery

---

### Post by neander on 2007-08-16
Re it's not the os's fault.

The instructions say to copy the files to cd, drag them into the folder. It does not say that by doing so, you will be erasing them from the hdd. I did what it said I should do.

---

### Post by vexorian on 2007-08-16
if anything it would be nautilus' fault, if it was really true...

I tried the same thing and it burned a file to my disk, I tried killing it during the burn process and nothing.

I am thinking that if you really lost your files, it is not because of the burning issues.

tried a "find" over one of the file names?

edit: among some things, killing that cd burner thing is killing nautilus. But besides of that I can't get any idea. Mind you I tried googling and can't find anything like that, so I have to insist, this was caused by something else.

> Clicked the burn to cd button
Dialog opens but is greyed out. Wait a couple minutes and then 'force close' after clicking the red x.
when I click that button, another dialog appears.it is not supposed to burn the CD instantly. perhaps one file was too big to nautilus? I once tried to burn an iso with nautilus but it didn't go well, so I installed brazero and forgot about nautilus for it.

Still, that cannot explain file dissapearance.

...
edit:
Been taking a look to nautilus-cd-burner bugs:

[https://bugs.launchpad.net/nautilus-cd-burner/+bug/57772](https://bugs.launchpad.net/nautilus-cd-burner/+bug/57772) So, you probably moved a lot of files... and it was indexing stuff, the bug here is that it should tell you about it. 

pretty lost on what could have caused those files to get lost, just so we know, what was the location of the files?

---

### Post by neander on 2007-08-16
Whew, I found the files. Maybe it was my ham-handedness with linux after all, or maybe some nautilus bug bit. After I wrote up the process I went through, I remembered something else I'd done. Thinking the cd/dvd creator folder was simply a list of items to be copied, I added some folders to it in order to organize the backup a bit. Had two nautilus windows open so that I could drag and drop easier. At some point I noticed that the two nautilus windows had somehow synch'd to the same folder. I thought that was some quirk of n behavior and went on...later when the write op seemed to fail, the files were missing. They were found in the folder that nautilus had seemed to synch the two windows too, ie one of the folders that was supposed to have been copied.

I do a lot of work with file systems every day and it's rare that I screw something up. However I admit that being off my normal turf, it might all be due to being a klutz on linux. But, I was really wigged when both n windows were found to be pointing at the same dir, it really surprised me, at the time I wondered if n had issues with keeping two diff instances open? 

In any case, I will know to be even more cautious going forward.

Thanks again for your help.

---

### Post by neander on 2007-08-16
anyways, what I wrote above at least touches on where the files went. 

But why they were moved is another question. By dragging to the folder mentioned in the help file they should have been moved, if a normal file system operation, yes. But for the instructions to the built in cd writing software to tell you to drag the files there, and then in moved them...

I have not dared to test that operation again now, but one of you said that it only copied the files.

I don't get what took place. Anyways...glad to have the files back and thanks for your support.

---

### Post by neander on 2007-08-16
Is there actually a 'gnomeburner' package? nautilus cd burner is the closest I could find, and that seems to have been installed already, I think it's the cd/dvd burner that is listed under Go in Nautilus?

---

### Post by angkor on 2007-08-16
```
apt-cache search gnomebaker
gnomebaker - application for CD/DVD creation in the GNOME desktop
```

Or you could try **K3b** if you don't mind installing lots of KDE libraries. It's KDE's burner.

Anyway, glad you've got your data back.

---

### Post by hyper_ch on 2007-08-16
K3B is an excellent burning program.

---

### Post by jvc26 on 2007-08-16
+1 for K3B though I also like Gnomebaker. Glad to hear you got your files back.
Il

---

### Post by shaydee on 2007-08-16
Just a short hint on how to move/copy/link files *within* Nautilus: Use the middle mouse button when you drag&drop. Doing that allows you to clearly specify what you want to do with the files that are selected.
And I'm also glad that you didn't lose your files for good, neander. :)

P.S.: Yes, its "gnomebaker". I use it, too.

---

### Post by vexorian on 2007-08-16
my vote goes for brazero , it is in the repos

---

### Post by tgalati4 on 2007-08-16
After reading through this thread, one gets the impression:

A long-time windows-user gets impatient with a greyed-out box (assuming it's broken) and immediately kills it.

A long-time windows-user feels the system is unstable (because of the above) an immediately reboots it.

A Linux-user would use "top" to see if Nautilus or the cdburner program is still working (probably churning away in the background).

A Linux-user would only reboot as a last resort.  There are many tools and techniques available for probing the situation before rebooting.

So yes, a Windows-user can get burned by killing a process mid-way and then rebooting.

Try dumping a lot of mp3's to a player through USB and then pulling the plug before it's finished.  Nautilus gives the impression that the files are transferred, but they are cached and sent to the background.  The actual transfer could take several minutes.  If you move the files and yank the cord, you could lose those files.  It happens.

So yes you can blame Linux or you can blame Windows conditioning or both.

---

### Post by notwen on 2007-08-16
> **neander said:**
> At some point I noticed that the two nautilus windows had somehow synch'd to the same folder. I thought that was some quirk of n behavior and went on...later when the write op seemed to fail, the files were missing. They were found in the folder that nautilus had seemed to synch the two windows too, ie one of the folders that was supposed to have been copied.

I do a lot of work with file systems every day and it's rare that I screw something up. However I admit that being off my normal turf, it might all be due to being a klutz on linux. But, I was really wigged when both n windows were found to be pointing at the same dir, it really surprised me, at the time I wondered if n had issues with keeping two diff instances open? 

In any case, I will know to be even more cautious going forward.

Thanks again for your help.

If you find yourself working w/ two instances of Nautilus at the same time alot, you may want to look into obtaining [Gnome Commander]("http://www.nongnu.org/gcmd/").  If I'm organizing/moving/removing files I'll find myself using Gnome Commander, I us Nautilus for simple folder navigation nowadays, leave the work to either terminal or Gnome Commander.  Give it a shot, it may prevent this from happening in the future. =]

---

### Post by irish_flu on 2007-08-16
> **neander said:**
> anyways, what I wrote above at least touches on where the files went. 

But why they were moved is another question. By dragging to the folder mentioned in the help file they should have been moved, if a normal file system operation, yes. But for the instructions to the built in cd writing software to tell you to drag the files there, and then in moved them...

I have not dared to test that operation again now, but one of you said that it only copied the files.

I don't get what took place. Anyways...glad to have the files back and thanks for your support.

I'm still not sure exactly what went down either, but good job solving your issue.  It's always tougher to support yourself, especially through the film of frustration when it looks like all your data is gone.

---

