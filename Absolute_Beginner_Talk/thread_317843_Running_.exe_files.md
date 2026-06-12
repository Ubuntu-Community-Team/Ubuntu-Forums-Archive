---
title: "Running .exe files"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2006-12-13
Can Ubuntu run .exe files? If it can, how?

---

### Post by ciscosurfer on 2006-12-13
You can install [Wine]("http://www.winehq.com/") or [Crossover Linux]("http://www.codeweavers.com/").

---

### Post by _simon_ on 2006-12-13
or Cedega.

It however does not mean that you will be able to actually use the program though.

What is the .exe?

---

### Post by maxamillion on 2006-12-13
neither application will have a 100% success rate with running .exe files though, it has been a long hard struggle to emulate the monstrosity that is windows and the war is still not yet won.

/me

---

### Post by peterj on 2006-12-13
I had that approach for a little while as well, you'll find that theres an equivalent (usually superior) to almost anything built for windows.

---

### Post by wersdaluv on 2006-12-13
The .exe file that I am trying to run is a windows vista readiness test program from dell

---

### Post by ciscosurfer on 2006-12-13
> **wersdaluv said:**
> The .exe file that I am trying to run is a windows vista readiness test program from dellWhile that program probably probes your hardware setup, it most likely will be relying on a current Windows setup to be fully utilized.  Wine, Crossover Office, and Cedega will probably not be able to help in this regard. 

But then again, I could be wrong! :KS

---

### Post by tuxsg on 2007-01-12
Man, if you want to run that software, it means you are planing using vista.

I can tell you the best way to see what can do vista on your machine definetly is installing it.

I tested using this software under winxp and it gives me a base subscore of 4.2, but when I installed it, I only obtain a real 2.4 base subsocre, and its by my ati Xpress 200m!.

Now I have WinVista Ultimate, WinXP and Kubuntu since I'm working as OS expert and I have to be up-to date and ready for every need of my customers.

But vista really bl0w5!!! Believe me, it cannot be compared to ubuntu + xgl + beryl!!! and it is a monster eating my laptop resources!!! I cannot play prince of persia on it, I will do a try on my linux usin wine or cedega or crossover, I will tell you later.

Just be aware of backup your partitions before install vista, because the beta versions would delete all your partition table.

The best way I guess is in a linux installed on a logical volumes (like hda5,hda6, etc) make the extra partition(s) giving the ntfs partition typ (Vista wont let you install over a fat32) and update your grub. Then backup your linux partition with something like acronis TrueImage (I know exists other opensource software to do it, but this is really easy and you can boot with a CD or USB key), install vista, rezise the partittion to have free space and restore your linux partition.

Since the logical volumes doesn't changes its names it should be easy for you  reinstall your grub over the MBR booting from the ubuntu live cd or dvd installation, just don't forget to add the new entry for your vista os.

But believe me, unless you have a really reason for do it (ok gaming is a REALLY reason ;) Windows vista is just a waste of HD space. (It weights around 14GB once installed!!!).

The real thing is the test program under wine* will not tell you anything, and not be useful.

Regards.

Tuxsg

---

### Post by ciscosurfer on 2007-01-12
> **wersdaluv said:**
> The .exe file that I am trying to run is a windows vista readiness test program from dellThe inference from Microsoft is that if you will already be running a version of Windows on your computer to test out the Windows Vista Upgrade Advisor.  It is unlikely you will be able to run that .exe with any success under Ubuntu using any of the aforementioned choices.  Plus, even if you can get it working, the results will not be what you expect as the Upgrade Advisor relies heavily on actually having a working Windows environment. (Granted, it is desinged to probe your hardware, but having a working Windows layer is quite desireable, if not necessary).

That said, if you want to see if you computer can take the load-bearing weight of the new Vista OS, then you should [look here]("https://www.microsoft.com/windowsvista/getready/systemrequirements.mspx") and then compare these (absolute) minimum requirements with your own system specs by using a program such as [Belarc]("http://www.belarc.com/free_download.html").

---

### Post by beamo on 2007-01-12
I installed vista beta rc2 and found it to be pretty darn good. Much better than XP and, in my 4 month+ experience, 100% bug free. I have a recently own-built comp that got a 5.0 rating so my experience may be atypical. However, after using Ubuntu, I'll never go back to Windows, though I dual boot in order to play civ4 on occasion. Other than that, I have no need for it.

---

