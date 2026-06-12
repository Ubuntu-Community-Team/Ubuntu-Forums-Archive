---
title: "Erasing CD-RWs?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by NotPhil on 2007-02-05
I'm sure I must be missing something obvious. 

I can't see a way to erase a CD-RW with Ubuntu's default apps. When I insert a blank CD it asks if I want to burn a music or data CD, or just ignore it so I can use another tool on the CD, but there's no dialog for CD-RWs with data already on them, and right-clicking on the CD's desktop icon only allows you to open, eject, or copy the CD.

Do I need to download some extra utility to erase a CD-RW, or is there something already installed that I can't find?

---

### Post by Ryan450 on 2007-02-05
take a look at K3B. I believe it comes installed with ubuntu by default, its my favourite burning app in linux. Once you have that up simply go to the tools menu along the top and you'll see an entry that looks like 

erase-cdrw

cant remember exactly what menu as I'm running entirely from my short term memory on this.

---

### Post by ComplexNumber on 2007-02-05
<oops>

---

### Post by ComplexNumber on 2007-02-05
> **NotPhil said:**
> I'm sure I must be missing something obvious. 

I can't see a way to erase a CD-RW with Ubuntu's default apps. When I insert a blank CD it asks if I want to burn a music or data CD, or just ignore it so I can use another tool on the CD, but there's no dialog for CD-RWs with data already on them, and right-clicking on the CD's desktop icon only allows you to open, eject, or copy the CD.

Do I need to download some extra utility to erase a CD-RW, or is there something already installed that I can't find?
you need the right tools installed. install the following together with a frontend such as gnome-baker:
'dvd+rw-tools'
'dvdrtools'

they're primarily for dvd for work with cd-rw too.

---

### Post by pistcivet on 2007-02-05
I have done this in the past from the command line using CDRDAO.
Its in the repos if you don't already have it.
Type man cdrdao , for usage. (I can't remember the exact syntax though)
Its very easy - no TOC file is needed to blank a CDRW.

---

### Post by steve.horsley on 2007-02-05
If you literally just want to erase a CD, then you can use k3b as others have said. If however you are concerned that you wnat to erase a CD in order to record something new, don't worry aout that. The normal CD burnignn program built into nautilus will spot a CD with data on it and ask if you want to erase it or change it for another one.

---

### Post by NotPhil on 2007-02-05
> **steve.horsley said:**
> If you literally just want to erase a CD, then you can use k3b as others have said. If however you are concerned that you wnat to erase a CD in order to record something new, don't worry aout that. The normal CD burnignn program built into nautilus will spot a CD with data on it and ask if you want to erase it or change it for another one.
Thanks,  but it looks like K3B is a KDE application. I don't really want to install and load all those KDE libraries into memory just to erase a CD. And when I drag files to a CD-RW that already has information on it, I'm told that I don't have the permissions for that "folder."

I'll check out GNOMEBaker, but is there any way to add items to the contextual menus that pop up when you right-click on a desktop icon? I was thinking that it might be easier to add some scripts there so you wouldn't have to launch a GUI app, or go to the terminal, just to do simple things like erase a CD-RW.

---

### Post by ComplexNumber on 2007-02-05
> but is there any way to add items to the contextual menus that pop up when you right-click on a desktop icon? I was thinking that it might be easier to add some scripts there so you wouldn't have to launch a GUI app, or go to the terminal, just to do simple things like erase a CD-RW.download nautilus scripts from [here]("http://gnome-look.org/content/show.php?content=39336"), then extract the contents and dump the contents in the .gnome2 directory in your home directory. i could probably modify one of them for you so that it opens the application of your choosing to burn a cd/dvd.

---

### Post by steve.horsley on 2007-02-06
Have you tried launching this command?
**cdrecord blank=fast**

---

### Post by NotPhil on 2007-02-06
> **ComplexNumber said:**
> download nautilus scripts from [here]("http://gnome-look.org/content/show.php?content=39336"), then extract the contents and dump the contents in the .gnome2 directory in your home directory.
Thanks for the link. Here's another [site]("http://applications.linux.com/article.pl?sid=06/05/03/153241&tid=26") about Nautilus scripting that I just found.
> **steve.horsley said:**
> Have you tried launching this command?
**cdrecord blank=fast**
I didn't know about cdrecord, cdrdao, or dvdrtools till this thread. Thanks for the tips.

---

### Post by icehammer on 2007-02-06
try

cdrecord blank=fast
 
OR

cdrecord blank=all


for a minimal or a full blanking session.. its much better than installing all godforsaken softwares..

---

### Post by steve.horsley on 2007-02-06
> **NotPhil said:**
> I didn't know about cdrecord, cdrdao, or dvdrtools till this thread. Thanks for the tips.

FYI, I believe that all the burner GUI programs are merely front ends that get their instructions from you and then put together a command-line to run one of those commands in the background. Many of them even have a window where you can see the text that cdrecord spits out as it works.

---

### Post by mikewhatever on 2007-02-06
Graveman has the option.

---

### Post by famouscoco on 2007-11-27
i want to erase a dvd-rw..but when i follow the rules for cd-rw (trying to write until "erase cd" message comes),the drive ejects the dvd and an error log says that "invalid format"..what should I do??

---

### Post by Sorken on 2007-11-27
This works for me to erase dvd-rw disks
> dvd+rw-format -blank /dev/dvd

---

### Post by stchman on 2007-11-27
> **Ryan450 said:**
> take a look at K3B. I believe it comes installed with ubuntu by default, its my favourite burning app in linux. Once you have that up simply go to the tools menu along the top and you'll see an entry that looks like 

erase-cdrw

cant remember exactly what menu as I'm running entirely from my short term memory on this.

K3B is not installed by default.  To install K3B do the following in a terminal:

```
sudo apt-get -y install k3b libk3b2-mp3
```

Once finished K3B will have an erase CDRW option.

---

### Post by 99bluefoxx on 2007-12-01
so, which command line erases a cd-rw so i can put new data on it?
i would like to know before i burn the first new -rw ive had in a while
btw, im using them strictly for mp3 backup, if that makes a difference

---

### Post by TeaSwigger on 2007-12-01
> **99bluefoxx said:**
> so, which command line erases a cd-rw so i can put new data on it?
i would like to know before i burn the first new -rw ive had in a while
btw, im using them strictly for mp3 backup, if that makes a difference

See icehammer's post up above. The quick erase should do the trick. Makes no difference if you're using it for backing up mp3 files, data is data in this context. All that said, RW's aren't the best medium for backups, especially not if you're needing to store on 'em for long term.

---

### Post by 99bluefoxx on 2007-12-01
kk, ty

---

### Post by 99bluefoxx on 2007-12-07
ok, so i tried the cdrecord blank=all
but this is what came up
```
bluefoxx@azurE-prIDE:~$ cdrecord blank=all
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... giving up.
wodim: No such file or directory.
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
bluefoxx@azurE-prIDE:~$

```i also tried the cdrecord blank=fast
but i got pretty much the same result
i have a cdrw/dvdrom drive and its set to my main, i also have a generic cd drive as the slave drive on the setup
what is going wrong here?

EDIT: i found the problem, i need to un-mount the disk, which meant ejecting it and leaving it in the tray, then running the command. =P

---

### Post by Teknyk on 2007-12-08
cdrecord doesn't appear to be installed on my laptop but cdrdao was and worked fine for me. I didn't even have to install anything else.
just opened a terminal and typed "cdrdao blank" (no quotes) and hit enter.

about 45 seconds and it was done.

And because I am lazy (plus I can't recall half the crap I type) I just created a launcher for it on my desktop.:biggrin:

---

