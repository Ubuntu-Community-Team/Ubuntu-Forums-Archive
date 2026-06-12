---
title: "fix broken packages"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by Wim Sturkenboom on 2007-07-19
Trying to install free codecs using easyubuntu. Get the message that I must fix broken packages first. When I use synaptic to fix, it does not mark any packages (so I can't apply changes).

From easyubuntu.in:
> installing package(s) gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse, gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad, libxine-extracodecs, libxine-main1, faad, sox, lame, ffmpeg, mjpegtools, vorbis-tools, libxvidcore4

Have been reading a bit here, but not sure how to proceed
[http://ubuntuforums.org/showthread.php?t=392590](http://ubuntuforums.org/showthread.php?t=392590)
[http://ubuntuforums.org/showthread.php?t=376105](http://ubuntuforums.org/showthread.php?t=376105)
[http://ubuntuforums.org/showthread.php?t=278896](http://ubuntuforums.org/showthread.php?t=278896)
[http://ubuntuforums.org/showthread.php?t=278908](http://ubuntuforums.org/showthread.php?t=278908)
[http://ubuntuforums.org/showthread.php?t=176423](http://ubuntuforums.org/showthread.php?t=176423)

One of them suggests to manually edit /var/lib/dpkg/status. Searching for one of the names from the quote above (e.g. ugly, I do not find it as a package, but only as e.g. recommended). Am I supposed to remove that single 'word' or what?

[B]The main question:
[/B]How does one fix broken packages, a general approach that will work 99.99% of the time.

Some further comments:
1)
I will stick with 6.06 LTS, so please don't advise to upgrade.
2)
I installed the codecs before using easyubuntu on another system without these problems (approx 6 months ago). Only difference between then an now might be that I installed flash plugin for firefox this time directly from adobe, something that did not work 6 month ago and what was the primary reason that I installed easyubuntu then. Oh, and there were a lot more (security) updates before I installed easyubuntu
3)
Advising to use automatix defeats the point, I want to know how to fix broken packages in general.
4)
Going to try automatix now

---

### Post by Seisen on 2007-07-19
You can go into synaptic, click on edit then select fix broken packages. If that doesn't fix your problem let us know.

---

### Post by Wim Sturkenboom on 2007-07-19
The third sentence of my post states that that does not work.

---

### Post by Seisen on 2007-07-19
It doesn't mark any packages when you use that method.

---

### Post by Wim Sturkenboom on 2007-07-19
From the synaptic help:
> 
Choose Edit &#8594; Fix Broken Packages from the menu.

Apply the **marked** changes to actually fix the packages:
   Click on **Apply** in the toolbar.	
   Choose Edit &#8594; Apply Marked Changes from the menu.
   Press the key combination Ctrl+E.

You will be asked for confirmation. Check the summarized changes that will be applied. 

To continue with the actual repair confirm the changes click on Apply

During the processing of the changes you will see a progressbar. Wait until
the changes have been applied. This can take some time depending on the number
of changes. Afterwards you will be returned to the main window.Regardless if they are supposed to be marked (acoording to help) or not, apply is grayed out. And it immediately states in the status bar that the problem was solved (can't remember the exact wording).

---

### Post by Wim Sturkenboom on 2007-07-21
Bump

---

### Post by Majorix on 2007-07-21
Tried uninstalling and then reinstalling from the TERMINAL?

```
sudo apt-get remove package_name
sudo apt-get install the_package_removed_in_previous_step
```

---

### Post by Wim Sturkenboom on 2007-07-22
Did not try that as I don't know what the 'broken' packages are? Is it the ones from easybuntu.in as mentioned in the opening post?

---

### Post by coolen on 2007-07-22
```
sudo apt-get install -f
```

Attempts to fix broken packages. This will usually work.

---

