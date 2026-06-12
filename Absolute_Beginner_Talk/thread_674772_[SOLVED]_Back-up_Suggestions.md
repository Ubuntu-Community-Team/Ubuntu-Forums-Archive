---
title: "[SOLVED] Back-up Suggestions"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by concerto on 2008-01-22
I just installed**_ Keep_** From add and remove programs.

I'm guessing the best thing to do is to back up all my information on a Separate external hard drive in case my computers hard drive crashes.

If my computer would CRASH and I would have to install Ubuntu from scratch, Is their any special files I should be backing up besides the obvious (spreadsheets, term papers, etc.)

Can you guys think of any that I will regret not backing up?  ...oh, Browser Bookmarks would be a good one to back up also.


Any others?

---

### Post by wolfen69 on 2008-01-22
what you are suggesting is what i do. i keep all valuable files on seperate hard drives.

---

### Post by LaRoza on 2008-01-22
> **concerto said:**
> I just installed**_ Keep_** From add and remove programs.

I'm guessing the best thing to do is to back up all my information on a Separate external hard drive in case my computers hard drive crashes.

If my computer would CRASH and I would have to install Ubuntu from scratch, Is their any special files I should be backing up besides the obvious (spreadsheets, term papers, etc.)

Can you guys think of any that I will regret not backing up?  ...oh, Browser Bookmarks would be a good one to back up also.

Any others?

Open your home directory, press Ctrl + h. Those files and directories that begin with a . are hidden and are used to save your settings.

Note, .Thumbnails and .Trash are not worth copying...

.purple is the Pidgin directory (catchy name). If you were to install Ubuntu, and put a copy of that directory in your home folder, Pidgin would be exactly the same (assuming you have all the plugins that you used).

Most of these settings have descriptive names, and you can easily back them up. Be aware that browser directories usually have the cache also, which you may not want.

(I use Opera, and Opera stores passwords and all Opera configurations in the .opera directory. When I do a fresh install of Opera on another computer (running Linux), I just put my .opera directory in my home directory, and it is exactly the same as the one I copied it from. Make sure you use the same versions...)

Copying the configurations for you settings is a very good thing to do.

---

### Post by twistedtwig on 2008-01-22
I go a step further (this is for my server rather than desktop so you may find it ott)... I backup my important files into seperate folders on the external drive.  But I also backup my entire server into a tar file so i could unzip it and have the whole system back up and running.

I use a bash script to copy the files from my various folders to the hard drive (so I don't forget to copy something).

If you would like any advice on doing this just shout.

---

### Post by hyper_ch on 2008-01-22
The most essential stuff to backup is:

/home  --> all your settings and personal files
/etc  --> computer-wide configuration stuff (e.g. xorg.conf, smb.conf, ....)
/var/www --> webroot if you run apache
/var/lib/mysql --> mysql databases (although here I would use a mysqldump script that safes them as .sql as the actual files could become corrupted if they are being changed while copied. Turning mysql off and copy those files then should be fine).

---

### Post by indytim on 2008-01-22
Here's a summary of my backup strategy.  I admit it's a bit "over-the-top" but I think it gives me enough redundancy for just about any catastrophe.

Background:
I have 4 Linux ops and Win2k installed and operational on my primary HD (160G SATA).  My second HD is devoted to data storage and backup material (320G SATA).  My external is a 320G SATA with one ext3 partition.

Weekly (Saturday mornings):
1.  I do the updates pushed through the repositories.  This is the ONLY time I do updates unless the sky is falling.
2.  I then log into FluxUbuntu and kick off Partimage.  I do a partition image of each ops and /home partitions on my ops hd.  These output files are written to the backup area of my second h/d.
3.  As needed when running a lot of update traffic on my data partitions, I then include them into the backup scheme on #2.
4.  When completed, I run copies of the backups created in #2 & #3 onto the external h/d.
5.  On the 2nd h/d, I keep only the most current backup.  On the external h/d, I keep 3 weeks worth of backups and purge from there.

If I need to restore a particular ops, it usually takes a total of about 3-5 minutes to do a full restore from a either the backup or a previous week's configuration.

Hope this is beneficial.

IndyTim

---

### Post by hyper_ch on 2008-01-22
I do an incremental snapshot-style backup every 6h onto a 500gb disk on my computer. Also once a day I do make an incremental snapshot-style backup to my box at my parents' home. I keep each backup for 90 days. I don't think I will required to have older backups.

Backup process is quite simple and straight forward... only restoring doesn't go as quickly as an image backup like the previous poster does. You'll have to re-setup the system and then just get your "wanted" files back.

---

### Post by kleo skywalker on 2008-01-22
I'm not sure if this is exactly what you're looking for, but I found a fairly easy solution while looking through threads which I've posted [here]("http://ubuntuforums.org/showthread.php?p=4184124#post4184124").
It creates a LiveCD (or DVD, that depends on the size) of your current Ubuntu install. So if your system crashes you can just pop in the disc and click install.

---

