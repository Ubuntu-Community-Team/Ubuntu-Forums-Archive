---
title: "Regular Data Backups - What's the least I can do?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by muzungu on 2006-06-11
I'm hoping to convert to Ubuntu full-time with a new budget laptop, keeping (for now) a Power Mac for video editing and iTunes. Unfortunately, the laptop I have in mind isn't available with a DVD burner.

I've already read about the 'proper' way to back up an Ubuntu install:

[http://hddsaver.com/content/26/index.html](http://hddsaver.com/content/26/index.html)

But I don't think the resulting file would fit on a CD-R. So...

Would I be safe enough making regular backups of only my home folder for my docs, plus the 'lib' folder for thunderbird email, firefox bookmarks, etc?

Thanks in advance for your advice...

---

### Post by gavagai on 2006-06-11
Well, everyone has their own opinion, but all I back up is my data and configuration files.

You may look into skipping the CD entirely and just mirroring your important stuff on your Mac.  This would also allow you to keep your work/data synchronized across your laptop and desktop.

Ubuntu offers a program called 'unison' to do this.  [http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)  It can synchronize across Mac, Linux, and Windows.  This kind of synchronization allows you to have redundant copies of everything automatically, instead of backups that you have to burn manually.

But yes, it is in my opinion OK to just back up data and config to CD.

---

### Post by aysiu on 2006-06-11
The lib folder doesn't have your Thunderbird email and Firefox bookmarks. Those live in your Home folder as well in hidden folders.

---

### Post by muzungu on 2006-06-11
[QUOTE=aysiu]The lib folder doesn't have your Thunderbird email and Firefox bookmarks. Those live in your Home folder as well in hidden folders.[/QUOTE]

Well, waddaya know... :eek: 

So maybe I can get away with just backup my home folder then?

---

### Post by Gimbo on 2006-06-11
[QUOTE=muzungu]
So maybe I can get away with just backup my home folder then?[/QUOTE]

I don't really know myself, but it seems logical to me that all data and personalised elements of your operating system should be kept together in the /home folder.

---

### Post by Solver on 2006-06-11
By the way, the best location to keep your backup is somewhere else. Another physical hard drive, or better yet, another computer. You can even buy a separate computer (an old used computer, just with a 20 GB HDD, the rest can be really old), network them, and set up your main computer to automatically send backups to the old box weekly.

---

