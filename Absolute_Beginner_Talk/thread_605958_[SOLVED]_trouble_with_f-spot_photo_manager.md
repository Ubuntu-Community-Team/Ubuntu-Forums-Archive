---
title: "[SOLVED] trouble with f-spot photo manager"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by jryprt on 2007-11-07
Hi I downloaded some pictures from a CD to f-spot I loaded 2 sets (same pic) by mistake , so I tryed to delete
them & I was left with the date of pictures & at the bottom of window stills shows 1853 photos how do I get rid
of them (date of pictures & at the bottom of window stills shows 1853 photos)
here is a screenshoot

wrong screenshot

---

### Post by jryprt on 2007-11-07
> **jryprt said:**
> Hi I downloaded some pictures from a CD to f-spot I loaded 2 sets (same pic) by mistake , so I tryed to delete
them & I was left with the date of pictures & at the bottom of window stills shows 1853 photos how do I get rid
of them (date of pictures & at the bottom of window stills shows 1853 photos)
here is a screenshoot

wrong screenshot


here the right one

---

### Post by Daveth on 2007-11-07
this error holds through reboot of your pc then? 

What about deleting all the new photos and re-loading- with a view to clearing out F-Spot's database. Might be something in here as well

[http://f-spot.org/User_Guide/Organize#Edit](http://f-spot.org/User_Guide/Organize#Edit)

---

### Post by jryprt on 2007-11-08
> **Daveth said:**
> this error holds through reboot of your pc then? 

What about deleting all the new photos and re-loading- with a view to clearing out F-Spot's database. Might be something in here as well

[http://f-spot.org/User_Guide/Organize#Edit](http://f-spot.org/User_Guide/Organize#Edit)

Yes after reboot its still there , I tried re downloading photos & deleting them again now over 3000 dates & at the bottom it said over 3000 photos still there but the photos are gone

---

### Post by Daveth on 2007-11-08
um, as that link notes you could

"Expert Tip: F-Spot uses a database stored at ~/.gnome2/f-spot/photos.db. Note, to access it, use the sqlite3 command. "

looks like the database is loathe to free records, or F-spot to take any notice of it and to keep on displaying phantom data. Might be worth trawling some other linux distos for F-Spot posts, if you can find nothing here.

---

### Post by Seq on 2007-11-08
I assume you deleted the files directly, and not via F-spot? If you right-click in F-Spot, there should be two items: "Remove from Catalogue" and "Delete from Drive". Those options are what you are looking for.

What happens when you import photos is that F-Spot parses information from the EXIF data (Dates, etc) and stores it in it's catalogue (an SQLite database mentioned by Daveth). When you delete files directly, F-Spot still has the catalogue information, so you get what happened to you. This makes sense, as F-Spot really does not know if the photos were deleted, or if they were part of a network file share or removable media that is no longer connected.

---

### Post by jryprt on 2007-11-08
> **Daveth said:**
> um, as that link notes you could

"Expert Tip: F-Spot uses a database stored at ~/.gnome2/f-spot/photos.db. Note, to access it, use the sqlite3 command. "

looks like the database is loathe to free records, or F-spot to take any notice of it and to keep on displaying phantom data. Might be worth trawling some other linux distos for F-Spot posts, if you can find nothing here.

I tried to get to the file but can not find it , when I tried the sqlite3 command look at screenshot
should I download sqlite3

---

### Post by jryprt on 2007-11-08
[QUOTE=Seq;3731765]I assume you deleted the files directly, and not via F-spot? If you right-click in F-Spot, there should be two items: "Remove from Catalogue" and "Delete from Drive". Those options are what you are looking for.

What happens when you import photos is that F-Spot parses information from the EXIF data (Dates, etc) and stores it in it's catalogue (an SQLite database mentioned by Daveth). When you delete files directly, F-Spot still has the catalogue information, so you get what happened to you. This makes sense, as F-Spot really does not know if the photos were deleted, or if they were part of a network file share or removable media that is no longer connected.[/QUOTE

Here how I tried deleted them , edit > select all > edit > Delete from Drive & I tried Remove from Catalogue
also . I tried removing f-spot thur synaptic reboot then installed f-spot & its still there

---

### Post by cubeist on 2007-11-08
Do you have other pictures in f-spot you want to keep?  if so, export them first!!, then go into your /.gnome2/fspot folder and try deleting the database... then relaunch f-spot and add your photos... 

edit -  I have never tried this... but in theory, f-spot will just create a new database if it cannot find the old one.

---

### Post by jryprt on 2007-11-08
> **cubeist said:**
> Do you have other pictures in f-spot you want to keep?  if so, export them first!!, then go into your /.gnome2/fspot folder and try deleting the database... then relaunch f-spot and add your photos... 

edit -  I have never tried this... but in theory, f-spot will just create a new database if it cannot find the old one.

How do I get to  /.gnome2/fspot folder I have looked around & do not see it .

---

### Post by cubeist on 2007-11-08
ah! it's hidden... anything with a dot in front of the name is hidden from plain sight... in your nautilus browser, go to view  and select show hidden files (shift h).

---

### Post by jryprt on 2007-11-08
> **cubeist said:**
> Do you have other pictures in f-spot you want to keep?  if so, export them first!!, then go into your /.gnome2/fspot folder and try deleting the database... then relaunch f-spot and add your photos... 

edit -  I have never tried this... but in theory, f-spot will just create a new database if it cannot find the old one.

Ok I found /.gnome2/fspot folder It will not open I need permissions( screenshot )  how do I 
get permissions

---

### Post by jryprt on 2007-11-08
> **jryprt said:**
> Ok I found /.gnome2/fspot folder It will not open I need permissions( screenshot )  how do I 
get permissions

I used sudo nautilus & open root folder then open /.gnome2 there is not a folder for f-spot (screenshot)

---

### Post by cubeist on 2007-11-08
Thats really interesting, have you tried reinstalling the app from synaptic?  Also, perhaps the folder is located elsewhere... I am not sure where though, perhaps others can chime in on this... I will have to ponder it for a while...

---

### Post by Seq on 2007-11-08
> **jryprt said:**
> I used sudo nautilus & open root folder then open /.gnome2 there is not a folder for f-spot (screenshot)

You want /home/USERNAME/.gnome2 , not /root/.gnome2

---

### Post by cubeist on 2007-11-08
Yes, thankyou Seq.  my earlier post was a typo. I meant ~/.gnome2/fspot ... I forgot the tilde

---

### Post by jryprt on 2007-11-09
> **Seq said:**
> You want /home/USERNAME/.gnome2 , not /root/.gnome2

Thanks Seq  & cubeist  It cleared the date & # at the bottom .
I sudo nautilus then /home/USERNAME/.gnome2 
had to click on show hidden files & the file photo. db I sent to the trash 
I open f-spot all is OK opened /home/USERNAME/.gnome2 again & a new photo.db is there

Thanks again Jerry

---

