---
title: "F-spot and Shotwell messing up image order"
date: 2012-07-03
forum: Any Other OS
---

### Post by hanspb on 2012-07-03
Hi,
I'll try here since I do not get any response in the Linux Mint Forums. I have just upgraded a laptop previously running Mint 11 (Gnome) to Mint 13 (Cinnamon) with a complete reinstall. When I did the backup I forgot the F-Spot database, but that should not be a problem since all tags are stored within the image files, so only the tag thumbnails should be affected.

Anyway, after the Images folder was restored and I imported all the images again, the order the images were displayed in was all messed up. In the timeline, they were placed some in 1930 and 31, and the rest from 2001 to 2029. So it seems to have read the day and mistaken it for the last two digits of the year! All files contain correct dates from the last two or three years, and the files are stored in a Year-Month-Day folder hierarchy.

To get around this problem I tried Shotwell, but the same thing happened there. And the strange thing is, when I import new images from the camera, they appear correctly.

Any ideas?

---

### Post by eric-yorba on 2012-07-03
Seems like something messed up the metadata in your photos.  You can confirm this fairly easily; in Shotwell, select a photo that demonstrates the problem by single-clicking it.  Then look at the info pane (lower left of the window) and see what it says for the date.

So if that is the issue, it's not going to be too easy to fix.  You'll need to either manually adjust the dates, or find some software that can batch edit the dates based on your folder hierarchy.

---

### Post by hanspb on 2012-07-04
Thank you for your reply. The date in each image is correct.

---

### Post by Perfect Storm on 2012-07-04
Moved to Other OS/Distro Talk.

---

### Post by eric-yorba on 2012-07-05
hanspb, could you either attach an image that has this issue, or send one to me (eric "at" yorba.org) so we could take a look at it?  Since it's an ordering issue, two or more photos would be best.

I don't think we've ever seen this issue before, and I wonder if there's something unusual about the metadata in these photos that's tripping up Shotwell.  We won't know for certain until we have a photo or two to examine.

Thanks!

---

### Post by hanspb on 2012-07-05
Yes, I can do that tomorrow evening, as I don't have access to that computer today.

---

### Post by hanspb on 2012-07-07
Here is a link to a zip-file with 3 images that have this problem. I have also made a screenshot of the info pane in F-spot for each image.

[https://www.dropbox.com/s/7vv8a06z49ivyud/date-order-problem.zip](https://www.dropbox.com/s/7vv8a06z49ivyud/date-order-problem.zip)

It seems the file size was well over the limit for attachments, so I put it in my Dropbox. Hope that is ok.

Hans Petter

---

### Post by eric-yorba on 2012-07-09
So yes, the metadata in the file corresponds to what F-spot is showing.  If you install the command line utility "exif", you can see the following results for each file:

Date and Time (Origi|2001:01:11 03:57:52
Date and Time (Origi|2017:05:11 02:29:28
Date and Time (Origi|2017:06:11 04:57:05

To be clear, this confirms that both F-Spot and Shotwell are displaying the dates within the files correctly.

Something must have messed up the dates on your files; since the metadata indicates that F-Spot has modified these files, that's one possible culprit.

That said, I have some good news for you -- the correct dates ARE still there!  There's more than one "date" field in these files; the one that F-Spot and Shotwell both read from is the "original" timestamp.

If you open up the files in exif, you'll see two other timestamps that (I assume) are correct.  For example, here's what's in SDC13361.JPG:

Date and Time       |2011:06:05 15:42:05
Date and Time (Origi|2017:05:11 02:29:28
Date and Time (Digit|2011:05:17 02:29:28

Unfortunately, I don't know of any simple automated way to fix these timestamps.  Presumably this could be scripted in Bash, Python, etc. if you're up for such a task.

---

