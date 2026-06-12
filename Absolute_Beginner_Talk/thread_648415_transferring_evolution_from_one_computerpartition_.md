---
title: "transferring evolution from one computer/partition to another"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2007-12-23
Hi all,

Over the last two days I had been trying to shift my EVOLUTION (mail client) data and settings from one computer to another. There does not seem to be one simple HOWTO for this. Searching on the Evolution website (the FAQs) and then experimenting a little, I figured this out. I thought of sharing this with others for benefit of others who want to do the same thing in the future.

****************************************************************
SHIFTING EVOLUTION FROM ONE COMPUTER/PARTITION TO ANOTHER
****************************************************************

ON THE OLD COMPUTER:

1. We need to back up all the data relating to Evolution. To do so first close evolution and then in a terminal type: ```
evolution --force-shutdown
```

2. Then type: ```
gconftool-2 --shutdown
```

3. Then type: ```
tar -cvzf $HOME/evolution-backup.tar.gz $HOME/.evolution $HOME/.gconf/apps/evolution $HOME/.gnome2_private/Evolution
``` 
(This creates the archives of all the evolution data in the file called "evolution-backup.tar.gz" and this file is located in $HOME.)

4. Then type: ```
gconftool-2 --dump /apps/evolution > some-file.xml
``` (This stores your evolution settings in the file called "some-file.xml")

5. Copy the archive file on a media by typing: ```
cp $HOME/evolution-backup.tar.gz /media/IOMEGA/
``` 
(This assumes that the path to the media you are using is /media/IOMEGA; change this accordingly).

6. Copy the settings file on a media by typing: ```
cp $HOME/some-file.xml /media/IOMEGA/
``` 
(This againg assumes that the path to the media you are using is /media/IOMEGA; change this accordingly).

Now, move to the new computer/partition.

ON THE NEW COMPUTER/PARTITION

0. DO NOT OPEN EVOLUTION.

1. Connect the media, open a terminal and copy the archive file from the media to the home directory: ```
cp /media/IOMEGA/evolution-backup.tar.gz $HOME/
``` 

2. Copy the settings file to the home directory: ```
cp /media/IOMEGA/some-file.xml $HOME/
```

3. Navigate to the home directory: ```
cd ~

```

4. Unpack the archive: ```
tar -xvzf evolution-backup.tar.gz

```

5. Make sure Gconf is shut down: ```
gconftool-2 --shutdown
```

6. Load the settings: ```
gconftool-2 --load some-file.xml
```

7. Navigate to the evolution directory: ```
cd $HOME/.evolution
```

8. Log in as root: ```
sudo su
```

9. Change directory permissions recursively: ```
chmod -R 755 *
```

10. Now close terminal and open EVOLUTION and everything should be there!

---

### Post by wheredidrealitygo on 2007-12-23
Evolution has a GUI method of doing this too. Go to "file", then "backup settings" and it will make the evolution.tar.gz.

Then copy this tar file, and then on the other computer, click "restore settings" from the other computer in the file menu as well.

---

### Post by aam-aadmi on 2007-12-23
I am still having problems accessing evolution in the new computer. Basically permission issues are not being resolved. When I try to change the permissions of directories in ~/.evolution I get into another problem: some folders are not being opened because it cannot be "locked"!

So I will try the GUI method and see if that works.

---

### Post by aam-aadmi on 2007-12-24
The GUI method also did not work. So I went for a fresh install of Ubuntu on the new computer. Then when I started Evolution for the first time, I asked it to use the backed-up data (in the archived form) that I had saved from the old computer. That way, it worked.

---

### Post by wheredidrealitygo on 2007-12-24
It's good to have both the GUI and CLI methods of doing things, different people like doing it different ways.

Is it possible to mark the thread as solved?

Thanks for following through on your results. Glad to hear it worked out :)

---

