---
title: "[SOLVED] KTorrent ... how to?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by R@inm@n on 2008-03-01
I am using KTorrent as my downloader app for torrents.  I have also used Azureus, Bit torrent, and Deluge.

I find that for me, KTorrent is the best because it is fast and doesn't use as much memory/CPU as Deluge...etc..

Anyways, the ongoing problem I always have with KTorrent is that it "grows" or gets larger as I click on it and use it during downloading.... until it takes over my whole desktop. I can't get it to go back to the original size because no matter what I try, it just stays big.  I can't shrink it back down by dragging from a corner, because I can't see the corner!!!. 

 I've had this same problem with it in the past, and was helped by several members on here, but can't remember what I was told to do.

I have deleted this app many times and re-downloaded it again in an effort to get it to start fresh in it's original size, but every time I install it again, it comes back the same very large size.

So then, my questions:   How do I un-install this KTorrent so that when I re-install it again it comes back to it's original small, manageable size?

 Or .......  how can I get it to shrink to the original proportions that it was when I originally installed it without deleting it and starting over?

 
 I want to continue using KTorrent as my primary torrent handler, as apart from the size issues, it works very well for me.


 Any advice please?


  Thanks,





    R.

---

### Post by Crumpets and Jam on 2008-03-01
Hang on a second. Your saying that the window 'inflates' until it dominates your entire screen?

---

### Post by wolfen69 on 2008-03-01
this sounds like gnome/x issue and not the fault of ktorrent. for future reference, to completely remove something do : sudo apt-get remove --purge program_name

---

### Post by Sn3ipen on 2008-03-01
This sounds like a problem with x, Compiz Fusion or Gnome. This wont probably help you allot but you can allways hold "Alt and click on the mousoe click" to drag the windows so you can rezize it.

---

### Post by Oldsoldier2003 on 2008-03-01
> **wolfen69 said:**
> this sounds like gnome/x issue and not the fault of ktorrent. for future reference, to completely remove something do : sudo apt-get remove --purge program_name
 man apt-get:

purge
           purge is identical to remove except that packages are removed and
           purged.


so you can just type sudo apt-get purge <package>

also remove doesn't remove the application settings, purge is supposed to do it ( though i'm sure somewhere there is an app that breaks the rule)

---

### Post by TheWizzard on 2008-03-01
in general you'd use gnome apps in gnome and kde apps in kde.

---

### Post by Oldsoldier2003 on 2008-03-01
> **TheWizzard said:**
> in general you'd use gnome apps in gnome and kde apps in kde.
True but there are KDE apps that are far superior to their gnome counterparts, K3b for instance.

---

### Post by R@inm@n on 2008-03-01
> **Crumpets and Jam said:**
> Hang on a second. Your saying that the window 'inflates' until it dominates your entire screen?


  Yes, gradually, as I use KTorrent.  I dragged the window [Ktorrent] to the size I want it so I can work easily with the app, then after a few uses, it gradually gets larger until clicking on any part of it just makes it worse... bigger.

Eventually, it gets so large that I can no longer get to the corner to drag it and make it smaller. 

 

  R.

---

### Post by R@inm@n on 2008-03-01
> **Oldsoldier2003 said:**
> man apt-get:

purge
           purge is identical to remove except that packages are removed and
           purged.


so you can just type sudo apt-get purge <package>

also remove doesn't remove the application settings, purge is supposed to do it ( though i'm sure somewhere there is an app that breaks the rule)



Ok i'll try this.


  R.

---

### Post by R@inm@n on 2008-03-01
> **Oldsoldier2003 said:**
> man apt-get:

purge
           purge is identical to remove except that packages are removed and
           purged.


so you can just type sudo apt-get purge <package>

also remove doesn't remove the application settings, purge is supposed to do it ( though i'm sure somewhere there is an app that breaks the rule)


I tried this...the result:   "Couldn't find KTorrent"



    R.

---

### Post by Oldsoldier2003 on 2008-03-01
> **R@inm@n said:**
> I tried this...the result:   "Couldn't find KTorrent"



    R.
Already uninstalled perhaps?

---

### Post by R@inm@n on 2008-03-01
> **Oldsoldier2003 said:**
> Already uninstalled perhaps?


Nope, it's not already uninstalled.

 
 R.

---

### Post by R@inm@n on 2008-03-01
looks like i have you all stumped?


  Me too...  :confused:



   R.

---

### Post by R@inm@n on 2008-03-01
I removed KTorrent [again] using add/remove programs.

I couldn't get the "purge" command to do anything.


 I did succeed in getting the window down to a slightly smaller size by reducing it sideways, but I could not  get it to reduce it's size lengthways....so I wasn't able to get it to work properly after all.

When I remove KTorrent using "add/remove" there are other libs associated with this app that also get removed with KTorrent.  However, the OS must retain a memory of the last settings of the removed app because it is still in the base OS somewhere.

Can I access this and completely remove all traces of KTorrent, or is this something a n00b like me can't manage?

As I said, "purge" didn't even find the app called KTorrent.

The command "sudo apt-get purge KTorrent" does not work.


 Anyone else got any ideas please?



  Thanks,




    R.

---

### Post by TheWizzard on 2008-03-02
> **R@inm@n said:**
> 
As I said, "purge" didn't even find the app called KTorrent.

The command "sudo apt-get purge KTorrent" does not work.



try without capitals

---

### Post by R@inm@n on 2008-03-02
> **TheWizzard said:**
> try without capitals


You sir, are a genius.   :)


Thank you, that worked. i was able to erase KTorrent and all it's libs.


 Now, i'll try re-installing again to see if it goes back to it's original size.


  R.

---

### Post by R@inm@n on 2008-03-02
Well ..... after erasing KTorrent and it's associated packages,  I re-downloaded and installed it again.

 Still the same problem. It was huge, covered my whole desktop.  :confused:


 Ah well, that's it, I give up.  I'll just have to use another torrent downloader.  it's a pity, because KTorrent is faster than anything else i've tried.

 Thanks to everyone for the help.


   R.

---

### Post by TheWizzard on 2008-03-03
> **R@inm@n said:**
> Well ..... after erasing KTorrent and it's associated packages,  I re-downloaded and installed it again.

 Still the same problem. It was huge, covered my whole desktop.  :confused:


 Ah well, that's it, I give up.  I'll just have to use another torrent downloader.  it's a pity, because KTorrent is faster than anything else i've tried.

 Thanks to everyone for the help.


   R.

[http://www.google.nl/search?q=command+line+torrent](http://www.google.nl/search?q=command+line+torrent)

---

### Post by forestpixie on 2008-03-03
try deleting the hidden ktorrent folder and reinstalling

it's in 

/home/yourname/.kde/share/apps

---

### Post by R@inm@n on 2008-03-03
> **forestpixie said:**
> try deleting the hidden ktorrent folder and reinstalling

it's in 

/home/yourname/.kde/share/apps


You did it...:)

That was what was missing...now I have deleted ALL of the old KTorrent libs and packages, etc...

I re-installed KTorrent and it's acting very civilised for me again... :)

Thank you all for the great help ... especially TheWizzard and Forestpixie.



 R.

---

