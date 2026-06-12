---
title: "Importing Music"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by sdrawkcab on 2007-05-31
I've been dreading the inevitable since I've put Ubuntu on a different Hard Drive. 

I would like to move my music collection (about 20GB) to Ubuntu but using a 1GB flash drive would be a real pain. Plus it's all sort of organized in windows.

Oh, one other variable...A lot of my music has very esoteric file names (no it's not stolen!) and it would be a SERIOUS pain to have to rename everything in a music player, any solutions to these problems?

---

### Post by steve-shinn on 2007-05-31
Where does the 20gb of music currently reside/stored ??

---

### Post by sdrawkcab on 2007-05-31
It's just stored in "My Music" on Windows. I guess when I said it's kinda organized it was a little misleading by making it look like I put it in a super special area. Sorry :)

---

### Post by aysiu on 2007-05-31
> **sdrawkcab said:**
> It's just stored in "My Music" on Windows. I guess when I said it's kinda organized it was a little misleading by making it look like I put it in a super special area. Sorry :)
On the same computer?

---

### Post by steve-shinn on 2007-05-31
And is Ubuntu installed on the same hard drive as Windows? or another hard drive ?

---

### Post by kernel tom on 2007-05-31
the easiest way to get your music would be if you had a 3.5" hd to usb connector cable... and if you dont have one and u work with multiple hard drives i'd suggest picking one up

If you are just trying to move ur files, you can copy them from your NTFS hard drive to wherever u'd like on ur Ubuntu hard drive

another option is doing it over the network in your house

EDIT::: after you get your music onto ur Ubuntu drive, I highly suggest letting amarok sort it, it does a great job, and if your music is sorted already amarok will have no problem finding all of it... It also has an advanced tag editor that will auto-complete a majority of ur missing tags

---

### Post by sdrawkcab on 2007-06-01
I installed Ubuntu onto my new external Hard Drive and the music is on my laptops normal drive. I tried searching for it in the laptops hard drive (I can see that Ubuntu notices it), but when I click on the laptop hard drive I don't recognize any of the directories that appear. Is there a certain folder in here that I need to click, or am I just missing something really obvious?

Maybe a quick simple walkthrough would do the trick.

---

### Post by teknosexual on 2007-06-02
> **sdrawkcab said:**
> I installed Ubuntu onto my new external Hard Drive and the music is on my laptops normal drive. I tried searching for it in the laptops hard drive (I can see that Ubuntu notices it), but when I click on the laptop hard drive I don't recognize any of the directories that appear. Is there a certain folder in here that I need to click, or am I just missing something really obvious?

Maybe a quick simple walkthrough would do the trick.

You're probably seeing the folders which Windows normally hides. Look for Documents and Settings > YourUserName > My Documents > My Music.

---

### Post by wataboutbob on 2007-06-02
you can always point to the location of your music folder in Rythmbox music player or Amarok music player and ubuntu should happily play it from there. Really no need to duplicate data for different OSes.

---

### Post by sdrawkcab on 2007-06-02
Well, I don't see **anything** that's familiar. I know what most of the hidden folders look like and all. It actually looks like stuff that Ubuntu uses judging by some of the file names. Do I maybe have to make a network with my windows drive?

I can probably get a screenshot if needed.

I tried making the Music folder shared, but no luck. I'm not getting it.

---

### Post by sdrawkcab on 2007-06-02
Ok, so this drive that you see **is** my laptop drive. I opened the properties to confirm this myself.

[IMG]http://i45.photobucket.com/albums/f95/gaypirate/Drive.png[/IMG]


Now this one is what I see when I open the contents of my laptops internal drive...

[IMG]http://i45.photobucket.com/albums/f95/gaypirate/Drivecontents.png[/IMG]


I checked all of the folders in the latter picture and nothing familiar shows up. I think I'm missing something pretty basic here, any help?

---

### Post by nonewmsgs on 2007-06-02
mate that's a linux / (base directory)
now you have windows and linux in different drives.  you have to mount the windows drive.  automatix has a checkbox option to automatically do that, but im sure some of the veterans can tell you the "real way".

---

### Post by sdrawkcab on 2007-06-03
I figured that that was a Linux setup that I was seeing. But this is why it confuses me. When I look at the Properties of "John's hard drive" which is my laptops hard drive without linux on it, it shows me the linux directories. I did mount it, but nothing different happened...Linux is not on this drive, but it apparently looks like it's storing stuff on it? I installed Ubuntu on my external hard drive using the Live CD, so I don't know if something weird happened or what.

I'm pretty confused...

---

### Post by wataboutbob on 2007-06-03
How about if you just go to Places > Computer > Filesystem > Media

Do you recognise any of the partitions mounted there?

---

### Post by sdrawkcab on 2007-06-10
Ok, I figured out that I'm not having any problems with the Hard Drive, so that's good. But I'm still wondering if there's a way for me to directly put my music from the internal drive onto the external drive. I'm guessing I would have to have both Windows on the hd0 running along with Linux on the external to be able to transfer.

Oh, the reason that I want to do this is because I am going to build a PC relatively soon, and I'm building a Linux desktop on the external drive (The external drive is actually an internal drive in a housing case) for later.

---

