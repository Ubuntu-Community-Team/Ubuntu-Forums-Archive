---
title: "Rather urgent help needed"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by fwuffycloud on 2007-06-12
Ok, this could be long, but i am in need of help quite desperately.

What i want to achieve:
   Reinstall windows successfully 
   Create a partition an duel boot between Ubuntu and windows.

First off, due to my own stupidity, whilst installing linux (trying to do this with a tutorial) i did not get a screen asking about sizing the partition, even though in the guide it said this would happen. So i carried on, thinking this screen would come later, and ended up overwriting Windows.

I would of kept Ubuntu but for some reason My mouse kept freezing after about 5 minutes and not work again (and for some bizzare reason i dont think my PC has a ps/2 socket for my mouse extension), then later on my keyboard froze. So i felt i had to re install windows.

I installed windows with the disk i had from Dell, and everything looked ok, apart from the fact that it was very, very slow, even moving a window took up 50% CPU usage. That was definately bad. I was given advice that I needed to format my hard drive or C drive, and then re install Windows. But i do not know how to do this, i get on to the Repair screen from booting up with the Windows disk, but i do not know the command to use to do this (or even if i am supposed to do this).

I know im asking a lot, but could anybody guide me through this Process of reinstalling Windows so it isnt slow, and creating a Partition and Dual boot with Windows and Ubuntu?

(I'm Sorry that this is mainly a windows problem, but I know that you guys are very helpful and that somebody might know) (and i also apologize for any bad spelling or grammar as im using my sisters laptop)

Thankyou,

Cloud

---

### Post by fwuffycloud on 2007-06-12
Please help, i'm not sure what i can do, and i really need my PC back up and running.

---

### Post by starcraft.man on 2007-06-12
Ok, geez ya waited a while...

Lets see. Just to get things started you have System restoration disks from Dell right? Not an actual "Windows Install Disk". Man I hate those things.

Ok, this is what we will do. First of all before editing any partitions do remember that any partition labelled dell and really small is your service partition and you need that to use the disks. DON'T EVER Delete it. Else you'll be stuck....

Now, I dunno what went wrong with the reinstall... Was it only graphical lag/choppy when moving windows/something graphical? If thats the case, I'm gonna assume that the drivers weren't installed properly from the disk and thus the computers rendering. Go to the manufacture site and install your latest Nvidia or ATI drivers.

Try that, if it doesn't work post back and I shall tell ya how to manually delete all the other partitions and reinstall windows.

---

### Post by fwuffycloud on 2007-06-12
Hmm, well the thing is the internet doesnt seem to work either, but that could be due to something else, i'll give it a try, i'll report back when i have tried.

Thanks a lot for replying, was hoping someone would be able to help.

---

### Post by fwuffycloud on 2007-06-12
Oh and in response to your question, yes it does seem to be graphical lag, but i still cant seem to get it to detect my wireless router, even through a cable. Would something be affecting that too?

---

### Post by starcraft.man on 2007-06-12
> **fwuffycloud said:**
> Oh and in response to your question, yes it does seem to be graphical lag, but i still cant seem to get it to detect my wireless router, even through a cable. Would something be affecting that too?

OK, well that is very weird. I'm gonna have to assume that your reinstall from the CDs failed badly. The drivers must not have been reloaded properly at all, I'm pretty sure the Dell disks are supposed to do that.

Here is how to do it manually assuming that you continue to have trouble:

1) Boot into the live CD of Ubuntu and download and install gparted with the following command in terminal:

```
sudo aptitude install gparted
```

Then open it up, either from terminal or the menu under System > Administration.

1a) If you don't have a live CD and want a quick utility to use, download and burn the [URL="http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828"]GParted Live CD.
[/URL]
2) Delete old partition manually.

Here is [documentation on it in general.]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") This [is the index.]("http://gparted.sourceforge.net/documentation.php") Good thing to read up on, partitioning is a very useful skill IMO.

Basically, all you want to do is identify all your partitions and wipe out (right click and delete) the one(s) with Windows and any affiliated ones. The only partitions that should be left are the Dell partition and of course any strictly data Partitions that your using (if you have none thats fine).

3) Put back in your Restore CD from Dell and let it restore the Default system to wherever it usually installs to. I'm pretty sure those imaged disks from dell don't have an option to restore to a particular partition and instead will restore what it expects to. Just do that. I can provide instructions for shrinking and modifying the partition later.

3a) If it does provide the option of choosing where to install (doubtful), then go back to GParted and make a 10 GB (my recommended size for Win XP, Vista needs more if thats your version) partition to install Windows in. Then make another 6 GB partition to install Ubuntu into. You should then have two logical partitions (I make those primary, I assume dell will be a third primary) one should be a small swap drive, probably 512 MB to a 1 GB, the other should be a data drive to use (read the instructions here about[ planning partitions]("http://www.psychocats.net/ubuntu/partitioning"), decide if you want a fat32, ext3 or NTFS partition).

That should do it. If the restore fails again, the disks are damaged or something else more serious is wrong with the system.

Good Luck.

---

### Post by fwuffycloud on 2007-06-12
First of all, thanks for the help, cant believe how smart everyone is on here.

I have a  question,
About the Mouse problem in Ubuntu, do you know anything about this? because creating partitions could be difficult with no mouse, but i'll have to keep restarting and getting quicker at everything.

I'll give it a go now, but my sister will take over soon as i have to go out. (she's older and smarter at these things though so its ok :)

---

### Post by phr0ze on 2007-06-12
Have you been having problems in general with the system prior to trying ubuntu? I ask because after the restore from the Dell Recovery CD the system should be flawless. If you still experience problems after that, I suspect some kind of hardware issue.

---

### Post by fwuffycloud on 2007-06-12
ok, I'm in gparted, i see NTFS, extended (which i assume is dell) and Linux-Swap, o i just delete the NTFS?

---

### Post by fwuffycloud on 2007-06-12
phr0ze: No, my system had been working abolutely fine up until Ubuntu. I really dont know what went wrong with the dell recovery disk (the disk says reinstallation dvd but i assume that means the same thing)

---

