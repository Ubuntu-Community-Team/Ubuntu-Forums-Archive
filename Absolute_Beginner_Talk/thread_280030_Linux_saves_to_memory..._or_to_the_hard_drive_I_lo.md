---
title: "Linux saves to memory... or to the hard drive? I lost my work."
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by Celil Rifat on 2006-10-18
Hi, 

I really like Linux and I just switched to ubuntu, and my experience has been very pleasant until yesterda, when I realized I had lost two days worth of work (an hour before it was due!), because of the weird way in which linux saves. 

I was writing a program on my laptop. I saved everything and decided to suspsend my laptop. When I resumed, Linux crashed (or rather I restarted it the crude way, because the screen was black). After restarting I was confronted with the nasty surprise that the last modifications on my prgrams were missing. 

I researched on the issue, and learned that linux does not really save on the HD, but caches stuff in memory. I think this whole caching nonsense in linux defeats the whole purpose of saving once documents. Is there a way to disable it and save all files to HD instantly? 

And why doesn't Ubuntu sync the cache to the hard drive by default before standby?

---

### Post by taurus on 2006-10-18
Not sure exactly what you are talking about?  When you suspended your machine, did you still have that app open?  Also, what filesystem are you using on your Ubuntu?

---

### Post by Mimsy on 2006-10-18
This is probably a dumb qestion, but was the laptop set to "suspend to ram" or "suspend to hard drive"? Mine can do both, and the ram option seems prone to inconvenient crashing so I disabled it.

I realise it's not very comforting right now, but with any luck you can make sure it won't happen again.

/Mimsy

---

### Post by gn2 on 2006-10-18
> **Celil Rifat said:**
> Hi, 

I really like Linux and I just switched to ubuntu, and my experience has been very pleasant until yesterda, when I realized I had lost two days worth of work (an hour before it was due!), because of the weird way in which linux saves. 

I was writing a program on my laptop. I saved everything and decided to suspsend my laptop. When I resumed, Linux crashed (or rather I restarted it the crude way, because the screen was black). After restarting I was confronted with the nasty surprise that the last modifications on my prgrams were missing. 

I researched on the issue, and learned that linux does not really save on the HD, but caches stuff in memory. I think this whole caching nonsense in linux defeats the whole purpose of saving once documents. Is there a way to disable it and save all files to HD instantly? 

And why doesn't Ubuntu sync the cache to the hard drive by default before standby?

User error. Never rely on the machine to "remember" things for you. Always  "Save As" before Suspend or Standby. Applies equally to Windows.

---

### Post by IYY on 2006-10-18
I'm confused... You clicked on the save button and it still wasn't saved on the disk?

---

### Post by Cartwheels4amile on 2006-10-18
Sounds like you used "standby" instead of "hibernate." In my experience, you should ALWAYS save your work before you put your computer to sleep. You can never be too safe with important data.

---

### Post by Celil Rifat on 2006-10-18
> **taurus said:**
> Not sure exactly what you are talking about?  When you suspended your machine, did you still have that app open?  Also, what filesystem are you using on your Ubuntu?

I was saving it to my vfat partition. 

I actually did save my work and programs multiple times. I had compiled them as well. It all looked as everythign was taking place on the HD, when in fact it was happening asynchronously in the laptops ram, without being comitted to the harddrive. 

When you press save, you expect your data to be saved to the hard drive. But it turns out that in Linux you have to type the "sync"command to synchronize the cache in the RAM and the HD. So in case of a sudden crash, you may loose valuable data, you thought was saved. 

I will mount all my drives in SYNC mode from now on, in order to guard against such nasty surprises. When you save something you expect it to be saved, the ASYNC default saving method that Linux uses defeats the whole idea of saving.

---

### Post by d3v1ant_0n3 on 2006-10-18
When I click 'save' or 'save as' in an app, the file gets saved to the hard disk...This is default behaviour AFAIK:-?

---

### Post by matt_risi on 2006-10-18
Yikes, sorry to hear about that man. I had a similar experience, I was typing in lecture and it crashed, so I reboot and it could only recover like half of my document. I was super pissed. Expect many more kinks and annoyances like that. I hate to say it, but on my computers I've found Windows to be more stable than ubuntu.

---

### Post by Celil Rifat on 2006-10-18
> **d3v1ant_0n3 said:**
> When I click 'save' or 'save as' in an app, the file gets saved to the hard disk...This is default behaviour AFAIK:-?

I am no expert, but as far as I understand the file does not get saved until you unmount the drive or until you shut down your laptop or computer. A similar think happens when you save to a USB device, and plug it out to realize that there is nothing on it. 

You just get the "illusion" that things are saved. In fact they are saved much later, and may never be saved in case of a crash.

---

### Post by Sef on 2006-10-18
> I was typing in lecture and it crashed, so I reboot and it could only recover like half of my document.

I've had similar experiences with that on Windows.  On Ubuntu, the document almost always comes back up intact.

---

### Post by Tux Aubrey on 2006-10-18
Eh?

> ...as far as I understand the file does not get saved until you unmount the drive or until you shut down your laptop or computer.

My laptop has now been "up" for more than two weeks without a reboot.  Does that mean that all the work I have done since the last boot is really being held in my 512Mb of RAM?  I doubt it!

This is a very disturbing thread.  Can an expert please give us the real answer here or tell us all how to work around this with a"sync" over-ride?

---

### Post by Mimsy on 2006-10-18
> **Celil Rifat said:**
> A similar think happens when you save to a USB device, and plug it out to realize that there is nothing on it. 

My USB drive must be mutated then. It saves to the drive every time I uses it, so I always save a version of the document on the computer I'm working on, and save the final version to the USB drive,since my USB drive is slow.

I'm not sure I even understand what your problem is. Your computer only saves to the harddrive when you close down an application, but not until then? :confused: 

/Mimsy

---

### Post by Celil Rifat on 2006-10-18
> **Mimsy said:**
> My USB drive must be mutated then. It saves to the drive every time I uses it, so I always save a version of the document on the computer I'm working on, and save the final version to the USB drive,since my USB drive is slow.

I'm not sure I even understand what your problem is. Your computer only saves to the harddrive when you close down an application, but not until then? :confused: 

/Mimsy


To be honest the USB drive thing happened to me under Fedora Core, it may be the case that Ubuntu loads USB devices with the sync option by default, unlike harddrives which are loaded with async option, meaning saving does not occur instantaneously.  

I had not rebooted by laptop for the past two days, and during the crash all data for the last two days was gone despite the fact that I had saved it multiple times, despite the fact that I had editted my programs and resaved, despite the fact that I had compiled them, despite the fact that I had actually run those programs. It was just all gone as if it never existed, and was never saved.

---

### Post by po0f on 2006-10-18
> **Tux Aubrey said:**
> This is a very disturbing thread.  Can an expert please give us the real answer here or tell us all how to work around this with a"sync" over-ride?

I'm not an expert, but this is what I know.  Hard disk spinning is bad for your drive's health and longevity.  If your HD actually saved something everytime it was requested of it, you would notice a lot more spinning and flashing, and eventually, a shorter life span for your drive.  Not only are you writing to the drive, but so are background processes.  Just look at the amount of log data in /var/log/messages.

The way around this is for the OS to cache all write requests until it has a sizeable chunk to write all at once, reducing writing to the hard disk.  In the case of Celil Rifat, the drive wasn't synced/caches flushed/whatever.  A failed suspend/resume killed his data.

Regarding USB drives:  they are usually mounted with the "sync" option, since most USB thumb drives are of the solid state variety, meaning no spinning parts that wear and tear.  When you save a file to a USB thumb drive, it gets written immediately.  You can still pull the stick out a little early and have corrupted data on the stick, so wait a while after the activity indicator is done flashing before pulling it out.

---

### Post by Peter41az on 2006-10-18
I must be the luckiest guy in the world then lol. Half the time, i dont even shut laptop down> i get in a hurry, and just hold down the power button. (i dont care if i crash it, its fun putting it all back and i have everything backed up 3 ways to sunday anyway). My point is, i have NEVER lost a single file. 
im watching this thread quite intently.

---

### Post by emarkay on 2006-10-18
*"...as far as I understand the file does not get saved until you unmount the drive or until you shut down your laptop or computer."*

OK now who's the jet fuel genius that said this?  When I click "SAVE" or "SAVE AS" the data gets written to the HDU. **It's there - I can see it in File Manager!**

There is no way some ninconpoop would have desigend a system to do otherwise, and have the file manager show fake data!  [-( 

Seriously, this is NOT true in UBUNTU, correct?:-k   

If NOT, would someone please show me some validated proof that there is NO actual writing to the HDU when I request it via a save command??

---

### Post by Celil Rifat on 2006-10-18
> **Celil Rifat said:**
> Seriously, this is NOT true in UBUNTU, correct?:-k   

If NOT, would someone please show me some validated proof that there is NO actual writing to the HDU when I request it via a save command??

It is very easy to show. Try to save something and check if the HDD LED goes off.

---

### Post by aysiu on 2006-10-18
The original title made this look like a complaint thread, but I think it's turning into more of a support thread, so I've retitled it appropriately.

---

### Post by gn2 on 2006-10-19
> **Celil Rifat said:**
> It is very easy to show. Try to save something and check if the HDD LED goes off.

On my laptop any time I press "save" the hard drive LED comes on, showing the data being written to the disc.

The LED shows read/write activity, not whether it's spinning or not.

In answer to poOf, (another poster on this thread)
The hard drive spins whether or not it's being written to/read from unless you set it to power down after a period of inactivity.

.

---

### Post by slimdog360 on 2006-10-19
perhaps something like this should be put onto lauchpad. I never knew linux acted in this way and agree that it shouldn't, assuming that its true;).

---

### Post by caravel on 2006-10-19
Don't sync and async only apply to networked drives and removable storage, such as floppy drives and USB flash drives?? Sync writes directly to the network drive wheras async writes to a cache, then commits the data when you unmount the drive, AFAIK anyway.  I don't think any of this applies to the partitions your OS is installed on, that would be... insane. :-k

---

### Post by mercurysquad on 2006-10-19
Guys come on. This is simply not true that Ubuntu only caches in RAM until you shut down.

What *does* happen is that temporarily, just a little bit of data is held in RAM and written out periodically. This is mainly for a speed advantage, and it happens on Windows also. Now the thing is that suspending a laptop on Ubuntu is tricky.. it works most of the time but might not work otherwise. It seems you didn't save your data just before suspending. It his highly unlikely that your saved data will not be written to disk before suspend/hibernate.

So yeah.. user error mixed with some bad luck. Next time save your data, close the software and then shut down or suspend. DONT rely on having your data intact after resuming.

Also, if the screen is blank after resuming, try typing your password and hitting Enter anyway. It works ;)

As for the "sync" command ... there is no need for such nonsense (how inconvenient would that be, wouldn't it?). As I said it was just bad luck and user error that somehow the buffered data was not written to the hard drive, _if you are sure you saved your work before suspending._

---

### Post by maaronB on 2006-10-19
> **Celil Rifat said:**
> Hi, 

I really like Linux and I just switched to ubuntu, and my experience has been very pleasant until yesterda, when I realized I had lost two days worth of work (an hour before it was due!), because of the weird way in which linux saves. 

I was writing a program on my laptop. I saved everything and decided to suspsend my laptop. When I resumed, Linux crashed (or rather I restarted it the crude way, because the screen was black). After restarting I was confronted with the nasty surprise that the last modifications on my prgrams were missing. 

I researched on the issue, and learned that linux does not really save on the HD, but caches stuff in memory. I think this whole caching nonsense in linux defeats the whole purpose of saving once documents. Is there a way to disable it and save all files to HD instantly? 

And why doesn't Ubuntu sync the cache to the hard drive by default before standby?

It sounds like you had some sort of problem, but it was not because of memory buffering.  You are correct that things will often be saved to memory, but this is a limitation imposed by the nature of the hardware, and will be found on every major OS; Linux, Mac, or Windows.  But you are talking about a timespan of AT MOST 30 seconds, not two days.  Also any major event, such as a shutdown or suspend should cause the buffer to flush to the hardrive (again as others have noted sometimes suspend type problems will cause problems).
  


So I really don't think you lost the info because of the memory buffering.
But I would like to help you figure out what the problem is.  

Did you recieve any errors when you woke your computer up?  
Are you sure you have been saving everything where you think you have been saving it? Have you tried doing a search on your computer using Beagle or the locate command?

For those that are interested more info can be read at:
[http://howtos.linux.com/guides/sag/buffer-cache.shtml](http://howtos.linux.com/guides/sag/buffer-cache.shtml)

---

### Post by Celil Rifat on 2006-10-19
> **maaronB said:**
> It sounds like you had some sort of problem, but it was not because of memory buffering.  You are correct that things will often be saved to memory, but this is a limitation imposed by the nature of the hardware, and will be found on every major OS; Linux, Mac, or Windows.  But you are talking about a timespan of AT MOST 30 seconds, not two days.  Also any major event, such as a shutdown or suspend should cause the buffer to flush to the hardrive (again as others have noted sometimes suspend type problems will cause problems).

I think the 30 sec limit is only if the update daemon (described in your link) is running. How can I check if that is the case?
> 
The sync command flushes  the buffer, i.e., forces all unwritten data to be written to disk, and can be used when one wants to be sure that everything is safely written. In traditional UNIX systems, there is a program called update running in the background which does a sync every 30 seconds, so it is usually not necessary to use sync.

There is no /sbin/update file on my laptop.
  

> 
So I really don't think you lost the info because of the memory buffering.
But I would like to help you figure out what the problem is.  

Thank you. I appreciate it. 

> 
Did you recieve any errors when you woke your computer up?  
Are you sure you have been saving everything where you think you have been saving it? Have you tried doing a search on your computer using Beagle or the locate command?

I woke up the laptop, and the screen was black, so I just powered it down, as i was certain everything was saved so I had nothing to loose. 

I had saved everything in a directory, and I could see it through ls, cat and all the commands I have been running on the java programs. Linux never indicated that those files were not there. The files are missing the modifications for the last 2 days. 

This happens to me for the first time ever.

---

### Post by Mimsy on 2006-10-19
> **mercurysquad said:**
> Guys come on. This is simply not true that Ubuntu only caches in RAM until you shut down.

...because no one would be stupid enough to design an OS that way?

With Linux that argument makes sense and holds water. It wouldn't surprise me the least to see that as a power-saving feature in vista for laptops though... :rolleyes: 

> **mercurysquad said:**
> Also, if the screen is blank after resuming, try typing your password and hitting Enter anyway. It works ;)

I didn't know that. I will definitely try this next time the blank screen happens. Thanks!

/Mimsy

---

### Post by emarkay on 2006-10-19
***So we've confirmed that Ubuntu acts just like windows or DOS, or any other program, and that this is a fact here in Ubuntu:***

When you hit "SAVE", it SAVES the CURRENT data to wherever it was originally read from, and if you hit "SAVE AS", it SAVES the CURRENT data to wherever you specify, presuming it's a valid location for the CURRENT data to be written to.

Nothing is cached or lost or synched, or whatever (for the purposes of arguments), for after you have SAVED your data, it exists as it was, at the moment you SAVED it, on a non-volatile (permanent) media, (presuming the media it is SAVED to is fault-free).

Correct?

---

