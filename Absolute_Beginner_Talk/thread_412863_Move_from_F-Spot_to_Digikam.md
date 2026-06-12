---
title: "Move from F-Spot to Digikam"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by gunksta on 2007-04-18
I'm experimenting with KDE, again, and I really like what I see in Digikam. But, I have A LOT of work in my tags and organization under F-Spot. I'd like to move my work from F-Spot to Digikam. Problem, I can't find any way to do this.

I've googled, looked here, and looked at the apps. So far, no dice.

If anyone has any ideas, that'd be great. If there's already a known way to do this, it will save me trying to write something.

--andy

---

### Post by yabbadabbadont on 2007-04-18
First off, you should have simply bumped your original thread from last night instead of starting a new one.  Bad gunksta, bad gunksta.  No soup for you.  :D

Second, I know that F-Spot has an option to store the tags directly in the images.  Did you use that?  If not, you might see if it is possible to have it do so, then maybe digikam will pick up the tags automagically.  I'm just guessing.  I just started using digikam myself (yesterday in fact) and I'm interested in what you find out on this.

---

### Post by gunksta on 2007-04-18
> **yabbadabbadont said:**
> First off, you should have simply bumped your original thread from last night instead of starting a new one.  Bad gunksta, bad gunksta.  No soup for you.  :D 

Different forum, Different thread. 
The other thread you are talking about is under Desktop Environments. I thought I might get seen by a different set of eyeballs under this part of the forum. :) 

> **yabbadabbadont said:**
>  Second, I know that F-Spot has an option to store the tags directly in the images.  Did you use that?  If not, you might see if it is possible to have it do so, then maybe digikam will pick up the tags automagically.  I'm just guessing.  I just started using digikam myself (yesterday in fact) and I'm interested in what you find out on this.

Yeah, that option has been set, telling F-Spot to store the tags directly in the photos, but it doesn't seem to actually work/do anything. I've looked at the IPTC and EXIF data with my own eyes and there ain't nothing there at all.

Oddly, a couple of tags survived from a brief flirtation with Google Picasa. I experimentally tagged about 10 photos, and Digikam imported those tags just fine. But, F-Spot didn't actually save anything in the photos.

I'm afraid I may have to write a script to pull the info out of the f-spot db and insert it into the digikam db. I hope someone has already done this. I'm no SQL wizard and I don't know much at all about sqlite.

--andy

---

### Post by knightnet on 2007-04-20
Never used F-Spot I'm afraid but I do know that Picasso does store some of its meta data in the IPTC fields. I'm impresed with digiKam which seems to have good support for IPTC (of which I am a big fan!).

If you do have to write a script, you might want to look at the command line tool exiv2. I've already written a script that renames a folder full of files with default camera names to my preferred format based on the date/time of the photo plus the name & model of the camera.

Hope it does well.
Julian.

---

### Post by gunksta on 2007-04-23
> **knightnet said:**
> Never used F-Spot I'm afraid but I do know that Picasso does store some of its meta data in the IPTC fields. I'm impresed with digiKam which seems to have good support for IPTC (of which I am a big fan!).

Yes, Digikam can definitely see the IPTC data stored by Picassa. I was very impressed by this. It appears that moving back and forth between Picassa ad digikam would be very easy.

> **knightnet said:**
> If you do have to write a script, you might want to look at the command line tool exiv2. I've already written a script that renames a folder full of files with default camera names to my preferred format based on the date/time of the photo plus the name & model of the camera.

Thanks for the tip. Right now I am staring at the f-spot database and trying to make sure I understand it's structure, and to make sure my hand-written queries generate the same results as f-spots.

Next I have to learn how digikam stores it's information.

--andy

---

### Post by knightnet on 2007-04-24
> **gunksta said:**
> Yes, Digikam can definitely see the IPTC data stored by Picassa. I was very impressed by this. It appears that moving back and forth between Picassa ad digikam would be very easy.


Ah, watch out though because I understand that Picassa doesn't store ALL of its information in EXIF/IPTC.

> **gunksta said:**
> 
Thanks for the tip. Right now I am staring at the f-spot database and trying to make sure I understand it's structure, and to make sure my hand-written queries generate the same results as f-spots.

Next I have to learn how digikam stores it's information.

--andy


You will want most stuff in the IPTC fields, these are part of the EXIF data (they are, in effect, an extension though they are treated separately).
This will enable your photos to be independent of the application you are using. Afaik, this is how digiKam stores much of its useful stuff.

Let me know how you get on, I'd be happy to help if I can.

Regards, J.

---

### Post by gunksta on 2007-04-25
OK, I have been learning about the F-Spot and Digikam databases.

Of course, they are very, very different. I'm going to explain what I know, and see if anyone has any ideas on how I can move my info over.

The first challenge is F-Spot uses sqlite2 and Digikam uses sqlite3. I was hoping I could use datakiosk to move the info around, but it can't open sqlite3 databases. Therefore I think I am pretty much relegated to the commandline. Fortunately, sqlite has great documentation.

**_F-Spot Database_**
To save 99% of my info, I really only need to interface with 3  tables.

[INDENT]**Table Name______________Table Columns**
photos______________ id, time, directory_path, name, description, default version
tags______________id, name, category_id, is_category, sort_priority, icon
photo tags______________ photo_id, tag_id[/INDENT]

**_Digikam Database_**
Obviously, I have to move the info into this db.

[INDENT]**Table Name______________Table Columns**
Images______________ id, name, dirid, caption, datetime
Tags ______________id, pid, name, icon, iconkde
ImageTags______________ imageid, tagid[/INDENT]

Unfortunately, neither db uses the photos actual name as it's internal id. I understand why this is done this way, but it doesn't make my life any easier. Because they index the files in a different way, digikam id # is different from f-spot's id #. This complicates my life.

I can easily query the f-spot db to give me a list of photos (actual file name or internal id #) in each tag. I would like to import these lists into digikam's db. I can see how to do this by hand, but I'm not sure how I can script this to happen. If anyone has any ideas, I would love to hear them.

--andy

---

### Post by gunksta on 2007-04-25
Oops, I forgot to include the pull the data-out part! I have something like 100 tags in f-spot. Their names don't matter. They are numbered 1 - 100. If I want a list of ALL photos tagged with tag #2 I can use:

```
SELECT "photo_tags0"."tag_id" , "tags3"."name" , "photos1"."name"
FROM"photo_tags" "photo_tags0" INNER JOIN "photos" "photos1" 
ON ("photos1"."id"="photo_tags0"."photo_id") INNER JOIN "tags" "tags3"
 ON ("tags3"."id"="photo_tags0"."tag_id") , "photo_tags" "photo_tags2"
WHERE (("photo_tags0"."tag_id" =1))
```

This returns a list of every photo in the database associated with that tag. Since this also returns the actual file name, I can (in theory) insert it into digikam, since I can query the digikam3.db file to find that filename and give me the associated digikam id#.

But, if I do this one at a time, it would probably be faster to just retag all the photos in digikam. I need to figure out how to automate this.

---

### Post by knightnet on 2007-04-26
How about querying the data to a text file (in CSV format or something similar) in file name order. Then use a shell script to walk through the list reading each line into variables.

Using the exiv2 in the script, pass is the filename and appropriate data to put into the EXIF/IPTC fields.

You then have all the relavent data stored in the image files and digitKam will read this when you create a new album with the pictures.

Don't forget to make a copy of your pictures before starting!!

Regards, J.

---

### Post by gunksta on 2007-04-27
That's one heck of a good idea. I will do just that this weekend. Then, I can walk through my photos and correct any mistakes that may happen because of matching names.

exiv2 looks like a truly useful little tool.

Thanks!

--andy

---

### Post by knightnet on 2007-04-30
> **gunksta said:**
> That's one heck of a good idea. I will do just that this weekend. Then, I can walk through my photos and correct any mistakes that may happen because of matching names.

exiv2 looks like a truly useful little tool.

Thanks!

--andy

:) No problem, glad I could suggest something. Let us know how you get on.

J.

---

### Post by gunksta on 2007-04-30
> **knightnet said:**
> :) No problem, glad I could suggest something. Let us know how you get on.

J.

After carefully looking at all of my options, I did use exiv2 to facilitate my transition to digikam. I am happy to say it worked FLAWLESSLY. The few problems I have encountered were of my own making. Looking back on the process, I could have done a few things differently and saved myself some serious headaches.

I now have 99% of the tags I had in F-Spot working in Digikam, thanks to exiv2 and Digikam's IPTC support.

I really appreciate the help members like knigtnet gave me. I'm going to sit down and write a complete HOW-TO for others who may be interested in doing this in the future. I will of course, link to this thread so credit will go where it should.

--andy

My

---

### Post by yabbadabbadont on 2007-04-30
> **gunksta said:**
> After carefully looking at all of my options, I did use exiv2 to facilitate my transition to digikam. I am happy to say it worked FLAWLESSLY. The few problems I have encountered were of my own making. Looking back on the process, I could have done a few things differently and saved myself some serious headaches.

I now have 99% of the tags I had in F-Spot working in Digikam, thanks to exiv2 and Digikam's IPTC support.

I really appreciate the help members like knigtnet gave me. I'm going to sit down and write a complete HOW-TO for others who may be interested in doing this in the future. I will of course, link to this thread so credit will go where it should.

--andy

My

I, for one, look forward to reading it.  Thank you for giving back.

---

### Post by knightnet on 2007-04-30
> **gunksta said:**
> After carefully looking at all of my options, I did use exiv2 to facilitate my transition to digikam. I am happy to say it worked FLAWLESSLY. The few problems I have encountered were of my own making. Looking back on the process, I could have done a few things differently and saved myself some serious headaches.

I now have 99% of the tags I had in F-Spot working in Digikam, thanks to exiv2 and Digikam's IPTC support.

I really appreciate the help members like knigtnet gave me. I'm going to sit down and write a complete HOW-TO for others who may be interested in doing this in the future. I will of course, link to this thread so credit will go where it should.

--andy

My


Glad it worked out for you. I look forward to bookmarking the how-to.
It's amazing how many people overlook the power of the scripting abilities of Linux and related technologies and it is often a fairly simple way to get things done once you've got past the feeling of being overwhelmed!

At work I often now find myself combining the abilities of spreadsheets with web-based back-ends using SQL and PHP mainly. So much easier than struggling just with a spreadsheet or access database!

Regards, J.

---

### Post by zeltak on 2008-02-27
Hi

Any chance the reverse could work? im trying to migrate from digikam to f-spot? would love to get some of you experience working for me

thx again

Zeltak

---

### Post by MGStreak on 2008-03-28
> **gunksta said:**
> I really appreciate the help members like knigtnet gave me. I'm going to sit down and write a complete HOW-TO for others who may be interested in doing this in the future. I will of course, link to this thread so credit will go where it should.


I am desperately attempting to accomplish this migration myself... and upon discovering your post, grew excited for the "HOW-TO" you described.  Then I saw the date on the post, and realized that it was almost a year old.  I can't find this how-to, and I was wondering if you could help me out?

That being said, if anyone else has any solutions for migrating from F-spot to Digikam, I'm all ears.

Thanks in advance!

---

