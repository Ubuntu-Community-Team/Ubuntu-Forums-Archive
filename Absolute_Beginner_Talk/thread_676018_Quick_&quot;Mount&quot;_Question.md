---
title: "Quick &quot;Mount&quot; Question"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Aysah on 2008-01-23
I'm starting to understand the general concept of mount, especially after through hours of fiddling with my array which finally works and a question came to mind...

**[SIZE="3"]What I'm trying to do ultimately...[/SIZE]**
Now that I have the new partition (mb0), I want to move /home to it.  Alot of the tutorials that I have seen online in regards to moving the /home directory usually move it onto a fresh partition and dedicate the whole partition to it; I don't want that.  In my new partition I've set up different folders, categorized the way I see fit, and now I just want one more folder called "home" and have that be the default home.

**[SIZE="3"]Quick Qustion...[/SIZE]**
If I want to create a new folder called "home" in my new partition (mb0) can I just do the following to mount home to that specific folder?  #-o

```

# mkdir /mnt/home
# mount -t ext3 /dev/md0/home /mnt/home
# rsync -aS /home/* /mnt/home

```

---

### Post by bcrom on 2008-01-23
This should work.  Be advised that rsync only backs up files.  Your original home will still exist.  If you have no need for incremental backups try just a straight 'cp -R' command.

---

### Post by mikewhatever on 2008-01-23
That would create a new directory and mount it under /mnt/home, but would not move your present home directory. If all you want is a backup for /home, it looks ok.

---

### Post by Aysah on 2008-01-23
> **bcrom said:**
> This should work.  Be advised that rsync only backs up files.  Your original home will still exist.  If you have no need for incremental backups try just a straight 'cp -R' command.

I didn't know that actually...  hmmm well being that I just want to move it then I'll use 'cp -R'.  Now I've seen 'cp -A' before but what does the '-R' do??

---

### Post by Aysah on 2008-01-23
> **mikewhatever said:**
> That would create a new directory and mount it under /mnt/home, but would not move your present home directory. If all you want is a backup for /home, it looks ok.

well I was reading through this [http://ubuntuforums.org/showthread.php?t=46866]("http://ubuntuforums.org/showthread.php?t=46866") and I wanted to make sure that 'mount' doesn't only pertain to whole partitions.  Being that it doesn't, I intend on following the directions there with slight modifications that pertain to my setup.

---

### Post by hyper_ch on 2008-01-23
what are you exactely trying to do?

---

### Post by Aysah on 2008-01-23
> **hyper_ch said:**
> what are you exactely trying to do?

i'm moving /home to a folder in my secondary partition which is an array. i just didnt want /home to be my whole array; only a folder **within** the array..


But i think i get it now...

Thanks again everyone for your help!!  =)

---

### Post by cubeist on 2008-01-23
If you are unsure of what a command does in the terminal you should always view the manual pages (man command) in the terminal.  For example, cp -R copies nested folders recursively which should be fine, but other commands with the -R option can destroy your system.  You should always know the effect of a command before you try it!

---

### Post by Aysah on 2008-01-23
:(  issues on this whole procedure...  starting to get icky...

again i would like to note that I'm following this guide... 
[http://ubuntuforums.org/showthread.php?t=46866]("http://ubuntuforums.org/showthread.php?t=46866")

**am I not allowed to use a folder to mount??  am i only limited to using whole partitions?**

everything else in the guide i did and I was able to move the original home folder to 'homeOLD' and even copy out the old one onto my array.  So in my array, which is mounted as (/media/citadel), I have a folder now that says home and has a copy of all my stuff in it.  How do i use '/media/citadel/home' as my new home?  I thought all I had to do was put it in FSTAB and run 'mount -a'..

maybe this isn't a valid line in FSTAB??
```
/dev/mb0/home /home ext3 defaults,errors=remount-ro 0 1
```


If this is becoming a mess I would gladly just restart the process again but I have no idea how to get that one folder from my second drive to be my new home folder... -sighs-  :confused:  I reeeeeallly could use some help right now..

---

### Post by Aysah on 2008-01-23
NEVER MIND...

Talk about complete newb..  I kept reading that friggin thread and forgot im not actually using a whole partition so there is no need for all that FSTAB stuff..  I moved everything over already to my array and /home is completely empty..

i just needed to simply do

```
ln -s /media/citadel/home /home
```

...done   =)  ...happy and rejoicing!!  :guitar:

---

