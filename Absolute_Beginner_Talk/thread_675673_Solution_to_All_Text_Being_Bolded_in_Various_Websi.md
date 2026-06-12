---
title: "Solution to All Text Being Bolded in Various Websites"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by LordKelvan on 2008-01-22
Hi:

I solved a problem today with the way some sites look, and thought I would share it with everyone.  I have seen a few people post this problem, but unfortunately, I cannot find those posts anymore.  I am currently using Ubuntu 7.10 (Gutsy Gibbon) with Firefox 2.0.0.11, although I believe this problem & solution is applicable to other versions of Ubuntu and/or Firefox.

Let me first describe my problem.  I started to notice that in some websites (in my case it was Yahoo! Mail and ubuntuforums.org, but there may be other ones out there) ALL the text was bolded.  I'm not talking about the text that is regularly bolded (like how threads with unread posts are bolded in ubuntuforums.org), I am talking about every piece of text on these sites being bolded.  It was driving me crazy!!!

Today I discovered the root of the problem.  I'll describe why the problem was happening, as I don't think it affects everyone.  I had enabled the Firefox option that says "Allow websites to choose their own fonts, instead of my selections above" (this should be located in the font configuration section of the Firefox preferences).  Now, it turns out that Yahoo! Mail and ubuntuforums.org are using the Tahoma font in various places, and for some reason I only had the **BOLDED TAHOMA FONT** installed, and not the regular Tahoma font.  Thus, any time Tahoma font was being used in websites, Firefox would always use the bolded Tahoma font I had on my system.  

To find out whether this is your problem, you should open up a terminal (Applications->Accessories->Terminal), and run the following commands:

```

sudo updatedb
locate tahoma.ttf
locate tahomabd.ttf

```

This first command updates your database (enter a password if prompted) - it might take a few minutes, so just wait.  The second command tries to find the regular Tahoma font on your system, and it shouldn't list any results.  The third command tries to locate the bolded Tahoma font on your system, and it should list results.

If what I describe above sounds like your situation, I suggest you head over to the following website:
[http://www.howtoforge.com/sharp_fonts_gnome_p2]("http://www.howtoforge.com/sharp_fonts_gnome_p2").    Just follow the instructions at the bottom regarding Tahoma fonts, and the problem should be fixed.

A piece of advice: the very last part of that webpage tells you to enter in the following command:

```
sudo dpkg-reconfigure fontconfig
```

which I feel is overboard, because it configures a bunch of other font things for you.  Instead I would suggest running the following line at the terminal (again enter a password if prompted):

```
sudo fc-cache -f -v
```

That command will refresh your font cache, which means applications should start using your new fonts.  Having said that, ubuntuforums.org didn't quite look perfect even after I did this.  What I ended up doing was logging out and then back in in order to get everything looking right.

One Final Thing:
The webpage I linked to above also includes instructions for a few other things that you can do to make your fonts look better (its actually page 2 of an article, so feel free to browse both page 1 and page 3).  Personally, I found that changing Xorg to use 96 DPI (this is separate from the DPI setting in the Gnome Appearance font configuration dialog) made fonts look sharper for me (or maybe its just my imagination :D).

If anyone needs any further help/clarification on this problem & solution, let me know.

Cheers,
LK

---

