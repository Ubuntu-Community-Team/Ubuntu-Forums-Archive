---
title: "Looking for good photo manager"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2007-10-28
With my wife and I both being photographers, we have alot of pictures. On my computer alone, I have about 6,000, not to mention the 20GB on an external HD. Because of the sheer mass of pictures, it can be very difficult to locate the picture I am looking for unless I know exactly when it was taken. I am now looking for a photo manager that will allow for certain features:

Better Photo Management than F-spot:
     After importing  pictures into F-spot, you are left with all of your photos strewn about in paths such as /media/pictures/images/Photos/2005/08/13/img.jpg which seems great.... until you need to find something without F-spot around to help. What I would be looking for would be similar, but with the ability to customize pathnames, and also filenames.

Boolean Searches:
     As I have recently begun the unbelievably tedious process of Tagging all photos, I would love to have a way to search Tags to find whatever pictures I need. F-spot is able to filter tags (which is helpful) but I would like a more powerful search if Possible. For Example: My name is Brendon and My wife's name is Angela. At our wedding is a great picture of a friend of ours. I want to be able to look at all pictures from our wedding that are NOT tagged Brendon or Angela, which would cut down the number of results by a huge amount.

The ability to import my Tags from F-spot:
     So that all of my tagging has not been in vain.

If anyone knows of a photo manager that can do these things, or a way to extend F-Spot to make it more suitable to my needs, I would love your feedback. Thanks for your time!!!!

---

### Post by Frak on 2007-10-28
You may want to try DigiKam

```
sudo aptitude install digikam
```

---

### Post by Pumalite on 2007-10-28
Or this:
[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

---

### Post by n3tfury on 2007-10-28
i'll put in a vote for picasa.  digiKam is good, but kde...meh.

---

### Post by Frak on 2007-10-28
> **n3tfury said:**
> i'll put in a vote for picasa.  digiKam is good, but kde...meh.
KDE may be meh, but K apps are some of the best.

I'll put in another vote for Picasa.

---

### Post by brennydoogles on 2007-10-28
> **Frak said:**
> You may want to try DigiKam

```
sudo aptitude install digikam
```

Will Digikam allow Boolean Searches?

---

### Post by Frak on 2007-10-28
> **brennydoogles said:**
> Will Digikam allow Boolean Searches?
Not sure, I'm not a photographer, collector, etc. for photo's. You may just want to install it, try it, and see what you think. Picasa is a good choice also.

---

### Post by bayvista on 2007-11-04
Picasa  is great, but I cannot access my photos on my XP Desktop with Picasa  on Ubuntu. I have to copy them to Ubuntu first which is painful.

---

### Post by ruru on 2007-11-04
I have just uninstalled f-spot which, although it looks better than Gthumb, has issues with memory (2000 photos used 4GB RAM + 12 GB swap and locked the machine up for over an hour before I killed it - I gave it second chances too, but the same). 

Now trying digikam which looks good (although I'm a non-KDE user) - Gthumb is just a little too basic.

Problem is that f-spot has stripped my entire collection of its exif data so I will have to reload from backup...

---

### Post by brennydoogles on 2007-11-04
> **ruru said:**
> I have just uninstalled f-spot which, although it looks better than Gthumb, has issues with memory (2000 photos used 4GB RAM + 12 GB swap and locked the machine up for over an hour before I killed it - I gave it second chances too, but the same). 

Now trying digikam which looks good (although I'm a non-KDE user) - Gthumb is just a little too basic.

Problem is that f-spot has stripped my entire collection of its exif data so I will have to reload from backup...

I personally have not been impressed with Digikam. It has a few features which are nice ( like the feature to help you find duplicate photos... very nice) but overall I have found the GUI and menu interfaces to be somewhat less than useful for my needs. I may try Picasa again, but I don't like that it installs in wine (and looks ugly while doing it), and I can't seem to find a way to get it to integrate well with nautilus, and more specifically the GIMP. If I remember correctly, I think it was the inability to directly open my photos for editing (other than Picasa's color tweaking which is pretty good) in the GIMP that got me last time. Since I am studying Information Technology with a concentration in Web Design, I am always using the GIMP to edit my photos for use as banners or background images, and I also use the GIMP's color picker all the time to create color schemes from the colors in a particular photo. Anyone had any luck with integration?

---

### Post by bayvista on 2007-11-05
Solved the Picasa problem with Network Drives. Just mount the share following the many examples in the Forums and bingo!! I can now access My Pictures on my Windows server using Picasa on my Ubuntu Notebook.

---

### Post by steve_waters on 2007-12-26
Did end up settling on a photo manager other than F-Spot in the end?

Sitting similar position to yourself at the moment.

Thanks,
Steve

---

### Post by steve_waters on 2007-12-27
You can do, well if I read the help manual correctly, boolean searches in f-spot:

2.2.3.&#8195;Type-to-find

 There is also a type-to-find entry. Press / to open it. It cannot be used at the same time as the find bar. You can type queries such as "TagA and (TagB or (TagC and TagD))". At any point, if F-Spot recognizes what you've typed as a valid query, it will update your search. The not operator is not yet supported.

Only downside is the "not" operator not being supported yet, but the yet makes me think it is coming.

Steve

---

### Post by sailor2001 on 2007-12-27
> **brennydoogles said:**
> I personally have not been impressed with Digikam. It has a few features which are nice ( like the feature to help you find duplicate photos... very nice) but overall I have found the GUI and menu interfaces to be somewhat less than useful for my needs. I may try Picasa again, but I don't like that it installs in wine (and looks ugly while doing it), and I can't seem to find a way to get it to integrate well with nautilus, and more specifically the GIMP. If I remember correctly, I think it was the inability to directly open my photos for editing (other than Picasa's color tweaking which is pretty good) in the GIMP that got me last time. Since I am studying Information Technology with a concentration in Web Design, I am always using the GIMP to edit my photos for use as banners or background images, and I also use the GIMP's color picker all the time to create color schemes from the colors in a particular photo. Anyone had any luck with integration?

picasa is in the repositories............no need for wine

---

### Post by Laibcoms on 2007-12-27
I use Picasa for linux as released by Google.  Picasa Linux is using a modified version of Wine, Google didn't bother re-coding it natively for GNU/Linux.

It works fine... I read though Google is still thinking if they will post the source-code though, they are thinking no one will need it... hehe... :p

1 vote for Picasa Linux!

---

### Post by GSF1200S on 2007-12-27
After looking at it, I cast my vote for picasso as well- thats a nice piece of software..

I dont care for how the Linux port has such Windows like dialogs, but the functions work awesome...

---

### Post by rplantz on 2008-01-06
> **sailor2001 said:**
> picasa is in the repositories............no need for wine

I don't see it there, but I'm running 64-bit. Is it only available in 32-bit?

---

### Post by Frak on 2008-01-06
> **sailor2001 said:**
> picasa is in the repositories............no need for wine
It installs Wine right next to it.

---

