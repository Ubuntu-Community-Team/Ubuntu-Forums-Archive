---
title: "Backing up files, need to limit tar.gz size"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-06-26
Hello, I am attempting to backup all of my photos (about 10 gigs on this computer), and I would like to make a few tar.gz archives and put them onto data dvds. The problem i am running into is figuring out the optimal amount to put into the archive so that it fits onto a 4.7 Gig dvd without wasting space. I also have them organized by directory, so if there is an automated way to do this I would need it not to split up individual directories. Any Ideas?? Just as a recap, I need to split up about 10 Gigs of photos into tar.gz's, at approx. 4.7 gigs each to the nearest directory. Thanks for the help!!

---

### Post by brennydoogles on 2007-06-27
*polite bump*

---

### Post by Cypher on 2007-06-27
There is a way of doing it within TAR but it would be probably easier to just great a large tarball and have it split into seperate files and then concat them back together later on.

The other option is to actively go and archive just a subset of files to make them fit on one DVD. Anyway, you could start with this
```

tar -jcvf archive.tar.bz2 <file-list>

```
This will create the huge archive.tar.bz2, you split it with
```

nohup nice split --line-bytes=4300m archive.tar.bz2 archive_ &

```
This will get you "archive_aa", "archive_ab", "archive_ac" and so on..

Later on, when you want to re-create the bug tarball you'd use
```

nohup nice cat archive_a* > archive.tar.bz2 &

```

You should probably leave the "nohup" and "nice" commands to allow it not to bring your computer to it's knees when it's trying to split and concat multi-gig files..

---

### Post by strider1551 on 2007-06-27
Cypher - just out of personal curiosity, the split archives wouldn't be viable by themselves, right?  I assume if he tried to open "archive_aa" with the archive manager, it wouldn't be a valid archive?

---

### Post by Cypher on 2007-06-27
> **strider1551 said:**
> Cypher - just out of personal curiosity, the split archives wouldn't be viable by themselves, right?  I assume if he tried to open "archive_aa" with the archive manager, it wouldn't be a valid archive?
You are right sir. The intermediate files that SPLIT generates would all be invalid archives and would only make sense as a whole when all the pieces are concatenated together. 

I think that would be true of any "incremental" or "multi-volume" archives where one missing piece would break the whole thing. That's why the safer solution is to create self-standing archives with a subset of files. This is a lot more time consuming, but gets rid of the fear of losing a DVD or something..

---

### Post by strider1551 on 2007-06-27
> That's why the safer solution is to create self-standing archives with a subset of files. This is a lot more time consuming, but gets rid of the fear of losing a DVD or something..

I think the time consuming part could be mitigated.  I don't think it would be too hard to whip up a python script to do the job.

---

### Post by brennydoogles on 2007-06-27
> **strider1551 said:**
> I think the time consuming part could be mitigated.  I don't think it would be too hard to whip up a python script to do the job.

If you are feeling up to it I would be appreciative!! My wife and i just lost almost 80 Gigs of pictures, so we are backing up what we have left. Thank you guys for your help!!

---

### Post by stchman on 2007-06-27
> **brennydoogles said:**
> If you are feeling up to it I would be appreciative!! My wife and i just lost almost 80 Gigs of pictures, so we are backing up what we have left. Thank you guys for your help!!

80G worth of pictures?!!!!!!!!!!!!!

That is a lot.

My recommendation is that since you ahve 10G of ipics jus split them up into 1/3 pieces.  You won't need to .tar or .zip then as pics are already compressed.

You could also get an external hdd.  The 250GB ones are pretty cheap.

---

### Post by brennydoogles on 2007-06-27
> **stchman said:**
> 80G worth of pictures?!!!!!!!!!!!!!

That is a lot.

My recommendation is that since you ahve 10G of ipics jus split them up into 1/3 pieces.  You won't need to .tar or .zip then as pics are already compressed.

You could also get an external hdd.  The 250GB ones are pretty cheap.

The external harddrive was what killed us. We had been backing up our pictures on it for several years, and in the course of a month had to wipe my wife's computer (windows= yearly re-installation), and my motherboard crashed, so I had to get a new computer. When we went to access the pictures after that, they were gone. The hard drive has been clicking, so we are going to have a professional recovery done on it, but we have to wait until we have $1500 to spare so we can get our life back (we are both photographers). Thanks for all of the help guys!!!

---

### Post by strider1551 on 2007-06-27
> If you are feeling up to it I would be appreciative!!

I'll try my hand at it.  With any luck I can have something ready tomorrow, or maybe a few days.

---

### Post by strider1551 on 2007-06-28
Alrighty then.  My script should be attached with instructions included.  It's not as polished as a finished project, but it does everything it needs to.  I tested it out on some of my own directories, but nothing on the size that you're using.  Let me know how it works out.

---

### Post by brennydoogles on 2007-06-28
> **strider1551 said:**
> Alrighty then.  My script should be attached with instructions included.  It's not as polished as a finished project, but it does everything it needs to.  I tested it out on some of my own directories, but nothing on the size that you're using.  Let me know how it works out.

Wow. You are my hero. This is why I love the Ubuntu community. I will try it out, and if there are any problems I will let you know. Thank you so much for all of the help you guys have been giving me. You're all awesome!

---

### Post by brennydoogles on 2007-06-28
It works wonderfully.... Thank you!!!

---

### Post by bren on 2007-06-28
the other way to do this (back up large amounts of data into 4.7GB chunks) is to use partimage to create .iso files of a particular data partition where your data is.

you can ask it to split the .iso files into anysize chunks you want.

i was under the impression (but have not tried it yet) that each of the .iso chunks it creates IS restorable on its own but thinking about it this seems unlikely.    would be interesting to know that for sure .... maybe I should check!  

therefore it seems that I should investigate this script as well
thanks guys

bren

---

### Post by xfile087 on 2007-06-28
> **strider1551 said:**
> Alrighty then.  My script should be attached with instructions included.  It's not as polished as a finished project, but it does everything it needs to.  I tested it out on some of my own directories, but nothing on the size that you're using.  Let me know how it works out.

WOW that's amazing and very useful for me so I can backup my home folder!!!

---

### Post by bren on 2007-06-28
hi strider

thank you for this script - i tested and it worked great for a small backup - just need to test it on a big chunk of data

bren

---

### Post by strider1551 on 2007-06-28
I'm glad the script seems to be helpful for people.  I've been polishing it up here and there and adding some documentation (so I know what it was years from now).  Seriously, though, I'm thinking about tossing it on sourceforge and adding support for other archive formats.

---

### Post by brennydoogles on 2007-06-28
> **strider1551 said:**
> I'm glad the script seems to be helpful for people.  I've been polishing it up here and there and adding some documentation (so I know what it was years from now).  Seriously, though, I'm thinking about tossing it on sourceforge and adding support for other archive formats.

When you get a more final version of the program, I would love to have a copy of it. Maybe this program could be expanded for use as a way to back up a home folder. As a random thought... What would I have to do to use this on my windows partition??

---

### Post by strider1551 on 2007-06-28
Assuming it gets on sourceforge, I'll post a note here.  Sourceforge will let you monitor packages to get an email when there are new versions (actually, sourceforge let's you do a ton of stuff).

> As a random thought... What would I have to do to use this on my windows partition?

Install python on the Windows partition (grab it [here]("http://www.python.org/download/") ).  At present, you would have to place the script in the folder you want to archive, then run it as normal from the windows terminal (start > run > cmd, I believe; move to that directory and run "python tarLimit --max-gigabyte=4.7")  Let me know if that doesn't work; I'm rushing to get in bed to wake up at 4a for work.

That being said, I haven't done it myself.  Everything in the script is generic enough when handling paths, so I can't think of anything that would prevent it from being portable.

> Maybe this program could be expanded for use as a way to back up a home folder.
Well, it could do it now.  Just run the script from the home folder.  Individual files are included as well as directories and hidden files.  I assume you're think of something more, though...

---

### Post by bren on 2007-06-28
hi strider

i hope you do get it to sourceforge.... thanks for your efforts

I found one bug when doing a tarLimit of  two large folders which sit in parent folder docs
1st one is music = 7GB
2nd one is misc stuff = 9GB

I set tarLimit going in their directory but it failed saying both are too big to fit into 4.7GB
the files in each dir are pretty small so i guess what i really want is for tarLimit to look recursively down the file tree if it fails on size to see if there is a smaller chunk that could be added.
otherwise i have to drop down the tree myself manually and then collect up all the .gz at the end...

one other option that would be nice is ability to specify destination dir for tar files
and i guess it would be pretty easy to generate tarLimit.log with a list of the path/filenames that have been tar'd

not expecting you to dedicate further efforts
just letting you know how it runs in practice....
who else knows python! (not me although have looked at the code a little)

ciao
bren


bren

---

### Post by brennydoogles on 2007-06-28
> **bren said:**
> hi strider

i hope you do get it to sourceforge.... thanks for your efforts

I found one bug when doing a tarLimit of  two large folders which sit in parent folder docs
1st one is music = 7GB
2nd one is misc stuff = 9GB

I set tarLimit going in their directory but it failed saying both are too big to fit into 4.7GB
the files in each dir are pretty small so i guess what i really want is for tarLimit to look recursively down the file tree if it fails on size to see if there is a smaller chunk that could be added.
otherwise i have to drop down the tree myself manually and then collect up all the .gz at the end...

one other option that would be nice is ability to specify destination dir for tar files
and i guess it would be pretty easy to generate tarLimit.log with a list of the path/filenames that have been tar'd

not expecting you to dedicate further efforts
just letting you know how it runs in practice....
who else knows python! (not me although have looked at the code a little)

ciao
bren


bren

I had a similar issue with the folders being too large, but what I did was run the program from inside those folders, and it had the same effect for me. This program works wonderfully for what I needed. If this ends up on sourceforge, I will do anything I can to get it out there and improve it (even though I suck at programming). Thanks!!!

---

### Post by strider1551 on 2007-06-29
The project got approved for sourceforge.

[Main Page]("http://sourceforge.net/projects/tarlimit/")
[Forums]("http://sourceforge.net/forum/?group_id=199919")
[Trackers]("http://sourceforge.net/tracker/?group_id=199919")

There is a new version posted.  It doesn't change/add any functionality (besides a man page).  It does however, have much better written code.  I have added some of the requests as well as some of my personal thoughts to the tracker.

Out of respect for the Ubuntu forums, I request continued discussion of tarLimit move to the forums and trackers of sourceforge.

---

### Post by Paul820 on 2007-07-19
Just like to say thanks for the script, i have just used it to make a backup of my home folder. Works great. :)

---

