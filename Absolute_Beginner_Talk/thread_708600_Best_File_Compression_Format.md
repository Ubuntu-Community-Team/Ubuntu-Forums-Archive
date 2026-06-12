---
title: "Best File Compression Format?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-26
I have a Folder on an ext3 partition that I use as a Windows Samba Share, so I can share files with multiple Windows clients but serve from Ubuntu...
I am looking for the best way to compress and archive this folder on a regular basis, so I am looking to find the best compression method/format.

I've been using [PeaZip](http://peazip.sourceforge.net/) and the [7z](http://en.wikipedia.org/wiki/7z) compression format, is that my best bet?
Look forward to hearing your suggestions,
Thanks,
-BassKozz

p.s. the folder contains various windows files but mainly MS Office (doc,xls,csv,etc...) files and pdfs.

---

### Post by KhaaL on 2008-02-26
Hi
I don't have any hard data to back this up ATM, but all the comparisions I've seen before has proven 7zip to be superior to the alternatives.

---

### Post by tszanon on 2008-02-26
> **KhaaL said:**
> Hi
I don't have any hard data to back this up ATM, but all the comparisions I've seen before has proven 7zip to be superior to the alternatives.
I second that. I did some personal tests myself and my conclusion was just the same. The only problem is that 7zip needs LOTS of memory when set to maximum compression (more than 1 GB for sure, but I don't know how much memory).

---

### Post by BassKozz on 2008-02-26
Thanks for the input, I'll stick with what I've been using  (PeaZip+7z)
:)

---

### Post by PeterJS on 2008-02-26
Maximum Compression keeps pretty much the definitive list of compression tools ranked by ratio, speed, and a couple of composite weights.

[http://www.maximumcompression.com/index.html](http://www.maximumcompression.com/index.html)

---

### Post by herbster on 2008-02-27
You mention doing it on a regular basis-- would you like to have it automated, like a scheduled compression once/week or something?

---

### Post by BassKozz on 2008-02-27
> **herbster said:**
> You mention doing it on a regular basis-- would you like to have it automated, like a scheduled compression once/week or something?
Very much so, would you happen to have/know a way to automate this?

---

### Post by hyper_ch on 2008-02-27
> **B/-\ssKozz said:**
> Very much so, would you happen to have/know a way to automate this?

A shell script that runs in a cron job.

---

### Post by herbster on 2008-02-27
> **B/-\ssKozz said:**
> Very much so, would you happen to have/know a way to automate this?

Piece o' cake! So you want to compress a folder, let's say it's /home/yourusername/stuff. Open a text editor and paste:

```
#!/bin/bash
tar cjf package.tbz2 /home/yourusername/stuff
```

Save it as anything, let's say "schedule.sh" and then open a terminal:

```
chmod +x schedule.sh
```

Now in the same terminal:

```
crontab -e
```

I can't remember if Ubuntu defaults to Vi or Nano, I think nano so you should be fine. Paste this line:

```
30 12 * * * ./home/yourusername/schedule.sh
```

This would run the compression every day at 12:30am. Adjust it to the time you want it to run. The 3 asterisks are day, month and day of the week (0-6, with 0 being Sunday). Save and close when you're done. That should do it, though it is very late and I'm falling asleep, so excuse any laziness/errors. I'll help out tomorrow if I messed up.

---

### Post by Giorgio tani on 2008-02-27
> **B/-\ssKozz said:**
> I've been using [PeaZip](http://peazip.sourceforge.net/) and the [7z](http://en.wikipedia.org/wiki/7z) compression format, is that my best bet?
Look forward to hearing your suggestions,

I recently added a short benchmark comparing various archiving formats from PeaZip, WinZip and WinRar [http://peazip.sourceforge.net/peazip-compression-benchmark.html](http://peazip.sourceforge.net/peazip-compression-benchmark.html)
I hope this comparison, although quite basic, may be interesting.

It should be noted however that different compression algorithms behaves differently on various data structures, so performance/compression tradeoff may vary depending on the nature of data to be archived.
Moreover, selecting the right archiving format depends also on other factors i.e. availability of strong encryption, authentication, integrity checks, possibility of data repair using recovery records etc...
And last but not leat important, the archive format should guarantee compatibility, for other users you may need to send the data or for yourself for future use; for that reason I would prefer any Open Source format whose specifications are fully disclosed (so a reader can be implemented in any future scenario) over any closed source one.

---

### Post by BassKozz on 2008-02-27
> **herbster said:**
> Piece o' cake! So you want to compress a folder, let's say it's /home/yourusername/stuff. Open a text editor and paste:

```
#!/bin/bash
tar cjf package.tbz2 /home/yourusername/stuff
```

Save it as anything, let's say "schedule.sh" and then open a terminal:

```
chmod +x schedule.sh
```

Now in the same terminal:

```
crontab -e
```

I can't remember if Ubuntu defaults to Vi or Nano, I think nano so you should be fine. Paste this line:

```
30 12 * * * ./home/yourusername/schedule.sh
```

This would run the compression every day at 12:30am. Adjust it to the time you want it to run. The 3 asterisks are day, month and day of the week (0-6, with 0 being Sunday). Save and close when you're done. That should do it, though it is very late and I'm falling asleep, so excuse any laziness/errors. I'll help out tomorrow if I messed up.
Thanks for the script **herbster** :D,

Two quick questions:
[LIST=1]
[*]I would like to use 7z (ultra compression level) instead of tar to get the maximum compression, how can I change "*tar cjf package.tbz2 /home/yourusername/stuff*" to reflect that?
[*]I would like the archive name to auto append the date at the end of it, so instead of **package.7z**, I'd rather have it read **package-20080227.7z**, any idea's on how that can be done?
[/LIST]

On another (related) note are there any good resources on how to create shell scripts (for dummies/newbs) ;)?
Thanks again,
-BassKozz

> **Giorgio tani said:**
> I recently added a short benchmark comparing various archiving formats from PeaZip, WinZip and WinRar [http://peazip.sourceforge.net/peazip-compression-benchmark.html](http://peazip.sourceforge.net/peazip-compression-benchmark.html)
I hope this comparison, although quite basic, may be interesting.

It should be noted however that different compression algorithms behaves differently on various data structures, so performance/compression tradeoff may vary depending on the nature of data to be archived.
Moreover, selecting the right archiving format depends also on other factors i.e. availability of strong encryption, authentication, integrity checks, possibility of data repair using recovery records etc...
And last but not leat important, the archive format should guarantee compatibility, for other users you may need to send the data or for yourself for future use; for that reason I would prefer any Open Source format whose specifications are fully disclosed (so a reader can be implemented in any future scenario) over any closed source one.
Thanks for the input **Giorgio** :D

---

### Post by herbster on 2008-02-29
> **B/-\ssKozz said:**
> Thanks for the script **herbster** :D,

Two quick questions:
[LIST=1]
[*]I would like to use 7z (ultra compression level) instead of tar to get the maximum compression, how can I change "*tar cjf package.tbz2 /home/yourusername/stuff*" to reflect that?
[*]I would like the archive name to auto append the date at the end of it, so instead of **package.7z**, I'd rather have it read **package-20080227.7z**, any idea's on how that can be done?
[/LIST]


Hang up, are you using 7z to back your home directory? Your root? Straight from the man page of 7z:

```
Backup and limitations
       DO NOT USE the 7-zip format for backup purpose on Linux/Unix because :
        - 7-zip does not store the owner/group of the file.
```

If you want to preserve permissions backing up a home directory, you should be using tar/bzip2. Bzip2 has strong compression.

If you are bent on using 7z, here you go, this would be the script instead of what I posted earlier:

```
#!/bin/bash
7z a backup-$(date +%m%d%y).7zip stufftobackup
```

That would churn out a backup-022908.7zip file.

Then add the cronjob as I indicated and you're done. :D

---

### Post by tszanon on 2008-02-29
You can also TAR everything, and then compress the tar file with 7z.

---

