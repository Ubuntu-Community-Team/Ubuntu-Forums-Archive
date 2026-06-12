---
title: "Trying to stick with Ubuntu"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by le_renouveau on 2008-03-10
Hi,

I have tried installing Linux for years, without really ever liking it or sticking with it. I installed Gutsy this weekend (second try for Ubuntu) and got almost everything resolved in a weekend (thanks to this forum and ubuntuguide.org). I have now made the switch (no windows partition) I hope I never have to install Windows again except in VMWare. However I still have some issues, and would like your help, comments, suggestions. I thank you in advance.

1- What happened to easy music management (iTunes). I love Amarok, music even seems to sound better with it. However, I'm still stuck with m4a files that VLC can read but not Amarok (I decided to delete my .wmv files and just rerip my CDs). Also, I can't figure out how to simply launch all my songs on a random play list, I always have to select an artist/album.

2- My disks are at 500/750G occupied. They are also NTFS. I figured out the hidden .Trash this weekend, but I'd really love to be able to just empty the trash bin without having to go to hidden directories. Also, is it possible to convert a drive from NTFS to ext3 without losing the data?

3- Is there a way to create links in my home directory that, for example sends the "Documents" folder to somewhere else on the drive? I hate having to go through the whole tree to get to my other drives.

That's all I can think about for now, thanks for your input.

---

### Post by Dr Small on 2008-03-10
As for #3, this would be called system links. An example of how to create one from the command line would be:
```
ln -s ~/Documents /path/to/documents/directory
```

That should make a directory in your home folder, and when you open it, it would take you to the actual path. You can probably do this in your file manager, by right clicking on the directory and making a link.

Dr Small

---

### Post by Inxsible on 2008-03-10
2) No you cannot change a filesystem without losing the data on it. You can however, transfer the data to another drive, change the filesystem and then put the data back on it.

Also, if you use Shift + Del instead of just delete, it will not go in the .Trash folder and will simply be deleted from the drive. You need to be careful with this however, since you can mistakenly delete something that you may not want to.

---

### Post by smurphy_it on 2008-03-10
Glad to see you are sticking with it.  I dumped windows awhile back and have no intentions of ever having it on my latop (not even a virtual session).

#1 - You should try some of the other music managers.  There are a ton of them out there.  I use rhythmbox myself, and it sychs with my Ipod shuffle no problem.  There are a couple of others I tried, just can't remember their names.... Suggest doing a search for multimedia players or something like that in your pacakage manager of choice.

#2 - I don't know much about converting to the different file systems.  There is an option for sure so that files are deleted and don't go to the trash can.  Can't check where it is w/o a linux os (which is not available here at the moment).  I'm thinking, system, preferences, Login but can't be sure.

#3 - Easiest way to do this is to open up the file manager, navigate to where you want to go and drag the icon to the left hand side (in nautilus I believe).  It basically just bookmarks it.
Kubuntu or another file manager would be different and you would probably have to create a symblic link instead.

---

### Post by sourcemorph on 2008-03-10
1) try exaile or rhythymbox.. they r great music library/player tools.. u can get almost everything u want.. 
 
download all the gstreamer plugins through synaptic for playing the propreitory format songs.. 

linux in general n ubuntu in particular r great.. im sure u'll love the shift from windows.

---

### Post by le_renouveau on 2008-03-10
Thanks for your answers, will try them out tonight. (At work on Windows right now and it's starting to feel restrictive)

Too bad about converting the file system.

Is it safe to use NTFS with ntfs3G?
Will there be data corruption or anything like that?
Do I lose any functionality by using NTFS instead of ext3?

Trash Bin: What I meant to ask about the .Trash is:
Can you make the files in .Trash of NTFS drives appear in the Ubuntu Trash bin?

Thanks

---

### Post by sayakb on 2008-03-10
Check your /home/username/.Trash folder for the files. If you accessed them as root, check the /root/.Trash folder.

---

### Post by Inxsible on 2008-03-10
> **le_renouveau said:**
> Thanks for your answers, will try them out tonight. (At work on Windows right now and it's starting to feel restrictive)

Too bad about converting the file system.

Is it safe to use NTFS with ntfs3G?
Will there be data corruption or anything like that?
Do I lose any functionality by using NTFS instead of ext3?

Trash Bin: What I meant to ask about the .Trash is:
Can you make the files in .Trash of NTFS drives appear in the Ubuntu Trash bin?

Thanksntfs-3g is pretty safe to use. Its been tried and tested. The only functionality that you might lose when converting from NTFS to ext3 is that if it is an external drive and you take it to your friends/relatives house to connect to their computer, you will have to install the fs-driver to be able to see yoiur ext3 drive on their windows computers.

---

### Post by neurostu on 2008-03-10
I have an NTFS partition that stores my music and pictures. I keep it ntfs so that when I am required to use windows I still have access to the files.

I have written to the NTFS partition several times from Ubuntu and have never had any problems with corruption.

---

### Post by le_renouveau on 2008-03-10
Good to know there is not any problem using an NTFS partition. I guess I'll stick with that.

---

### Post by le_renouveau on 2008-04-12
Wow, it's been a month and I'm still loving Ubuntu!

Another question: I'm looking for a little program that can keep track of my tv shows for me. My wife is using [http://www.apple.com/downloads/dashboard/movie_tv/tvforecast.html](http://www.apple.com/downloads/dashboard/movie_tv/tvforecast.html) on her mac and it works pretty well.

Any suggestions?

Thanks in advance,

le_renouveau

---

