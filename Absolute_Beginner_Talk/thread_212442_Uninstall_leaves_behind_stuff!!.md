---
title: "Uninstall leaves behind stuff!!"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-07-09
I thought Linux was NOT like windows when it comes to 
uninstalling stuff.
Let me be more clear.
I have installed some apps (blender, amsn, etc.) and 
then uninstalled them through Sunaptic (yes, marked for 
complete removal). 
But as I was broswing the filesystem I found files as left overs from the 
installations (Both blender and amsn).
Am I doing something wrong or am I right that linux doesn't wipe everything?

---

### Post by aysiu on 2006-07-09
Removing doesn't remove config files necessarily--especially the ones in your home directory.

---

### Post by metaltailz on 2006-07-09
Well I don't know what you have found but when I did stuff like that on my new Xubuntu machine, I would select blender(Yup I use it too) to uninstall and it would do so. But it would leave all the packages that blender needed to run.

I fixed this by using aptitude. It is a command that you run in the terminal to install packages much like Synaptic but not as graphic.

Say you want to install blender again, you use this:

sudo aptitude install blender

That will get all the things that blender needs to run. But should you decide to uninstall it just do this

sudo aptitude remove blender

That will remove blender and everything that was downloaded and installed to make blender work.

---

### Post by aysiu on 2006-07-09
I don't think geokok1981 is talking about dependencies.

But, yes, I also recommend *aptitude*.

You're not the only person this bothers. Read more [here](http://www.ubuntuforums.org/showthread.php?t=160246).

---

### Post by ciscosurfer on 2006-07-09
> **geokok1981 said:**
> I thought Linux was NOT like windows when it comes to 
uninstalling stuff.
Let me be more clear.
I have installed some apps (blender, amsn, etc.) and 
then uninstalled them through Sunaptic (yes, marked for 
complete removal). 
But as I was broswing the filesystem I found files as left overs from the 
installations (Both blender and amsn).
Am I doing something wrong or am I right that linux doesn't wipe everything?

While it's a bit dated, [this thread]("http://www.linuxquestions.org/questions/showthread.php?t=363365") still applies today.  Keep in mind that choosing one package manager over another is basically a matter of personal preference.  All pm's (apt-get, aptitude, synaptic) all have the same capabilities, although some require different switches or filters in order to achieve the same effect.  Each one will resolve dependencies if set up correctly.  I'm mainly a command-line person myself, and tend to use aptitude b/c I like how it functions "right out of the box".  Also important is to remember to choose one pm and stick with it.  Resolving dependencies can become a hassle when you switch back and forth between pm's.  Let me know if I can be of any further assistance! :D

Additional links that may be of interest:
[apt-get vs aptitude]("http://www.ubuntuforums.org/showthread.php?p=1137995")
[an apt-get primer]("http://os.newsforge.com/comments.pl?sid=42537&op=&threshold=0&commentsort=0&mode=thread&tid=2&pid=0")
[debian administration]("http://www.debian-administration.org/polls/24")

---

### Post by geokok1981 on 2006-07-10
I read all the posts suggested to come to this conclusion.
All managers may leave something behind and it is
up to the user to locate orphan packages-libraries and decide if need to be deleted.
Because I ll probably end up messing my machine though I ll stick with synaptic and try to manually delete left overs (for example if
I have amsn and uninstall it I can delete the file .amsn, right??)
Can u tell how to easily locate these files/folders and if there is something I should never delete???

---

### Post by aysiu on 2006-07-10
There is a difference between orphaned packages and residual configuration files.

*aptitude*--if used properly--will not leave behind orphaned *packages*.

All package managers will leave behind residual configuration files, though.

The best way to easily locate something? ```
sudo updatedb
locate amsn
``` Substitute *amsn* with whatever you're looking for. When in doubt, don't delete.

Are you hard up for disk space?

---

### Post by geokok1981 on 2006-07-10
Well, no not really. 
Just used from windows to clean everything that was left behind
in program files and registry.
But I guess left overs aren't good for Linux either, right?
If these files don't slow the system in some way though I wouldn't
really care.

---

### Post by aysiu on 2006-07-10
I don't know that everything *does* get cleaned out from the registry in Windows. I think it depends on the uninstaller.exe and how it's written.

Certainly, Windows uninstalls leave a lot of .dll libraries behind, and when they don't, you often get cryptic dialogues about, "Do you want to remove cdsan543nkld.dll? No programs appear to be using it, but its removal may cause certain programs to not work" or something like that. I've always left the .dll files in there.

Certainly configuration files do not slow down your system at all--only programs and services do.

Still, the ability to remove config files easily (should you wish to do so) should be available. As it is now, they must be removed manually.

Personally, I like having the config files around. That way, if I ever choose to reinstall the application again, all my settings will still be there.

I'd highly encourage you to use *aptitude*, though--the installed libraries and dependencies certainly take up a lot more space than a text configuration file.

---

### Post by Brunellus on 2006-07-10
> **aysiu said:**
> I don't know that everything *does* get cleaned out from the registry in Windows. I think it depends on the uninstaller.exe and how it's written.

Certainly, Windows uninstalls leave a lot of .dll libraries behind, and when they don't, you often get cryptic dialogues about, "Do you want to remove cdsan543nkld.dll? No programs appear to be using it, but its removal may cause certain programs to not work" or something like that. I've always left the .dll files in there.

Certainly configuration files do not slow down your system at all--only programs and services do.

Still, the ability to remove config files easily (should you wish to do so) should be available. As it is now, they must be removed manually.

Personally, I like having the config files around. That way, if I ever choose to reinstall the application again, all my settings will still be there.

I'd highly encourage you to use *aptitude*, though--the installed libraries and dependencies certainly take up a lot more space than a text configuration file.
I always thought that 

apt-get --purge revmove packagename

would also delete all its config files.

---

### Post by aysiu on 2006-07-10
> **Brunellus said:**
> I always thought that 

apt-get --purge revmove packagename

would also delete all its config files. Maybe it does. I don't know. geokok1981, can you confirm whether or not that command works?

Also, is that supposed to delete all configuration files or just the default ones in /etc? In other words, does it get rid of the hidden folders in the home directory, too?

---

### Post by geokok1981 on 2006-07-10
I can try but I guess I shouldn't I have
installed something with apt-get first to uninstall it with it
afterwards?(based on what u said before).
Also, maybe I am not the best candidate since I am only a 10 days 
Ubuntu user. Perhaps someone more experienced will be able to locate left overs for sure...

---

### Post by aysiu on 2006-07-10
Well, there are two things at issue here:
1. Dependent packages
2. Configuration files

The whole *apt-get* v. *aptitude* issue has to do with removing lingering dependencies.

What Brunellus is saying is that the purge command will remove the residual configuration files.

---

### Post by geokok1981 on 2006-07-11
Ok...I did locate amsn and found some files (default installation with synaptic not apt-get).
I checked them and they were all very small.
Since u say they don't slow the system I ll leave them and 
stick with synaptic (seems the easiest thing to do right now).
One last question though:
If I want to delete a config file where can I find it usually?
Is it always a hiddend file in home folder (ie .amsn??)

---

### Post by aysiu on 2006-07-11
> **geokok1981 said:**
> Ok...I did locate amsn and found some files (default installation with synaptic not apt-get).
I checked them and they were all very small.
Since u say they don't slow the system I ll leave them and 
stick with synaptic (seems the easiest thing to do right now).
One last question though:
If I want to delete a config file where can I find it usually?
Is it always a hiddend file in home folder (ie .amsn??)
Well, there are two kinds of configuration files.

One kind usually lives in the /etc folder and has the default configurations.

The other kind usually lives in your /home folder as a hidden folder/file, and it has your specific user preferences.

---

