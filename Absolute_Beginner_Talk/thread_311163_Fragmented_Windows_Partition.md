---
title: "Fragmented Windows Partition"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by AusIV4 on 2006-12-02
For quite a while I've been planning on setting my laptop up to dual boot Ubuntu when I have some extra time. That extra time came this weekend.

This morning I tried to install Edgy. When I ran the installer and tried to repartition that way, it was trying to create a linux partition larger than the free space on my windows partition. Obviously that would create some problems, so I opted not to do that.

I opened up QTParted and tried shrinking my NTFS partition that way. After about 45 minutes it through a confusing error, so I rebooted to to windows, thinking maybe I needed to defragment first.

I fired up the Windows Disk Defragmenter and hit Analyze. It showed that I had group of "unmovable files" about 80% of the way through my partition (which is only about 60% full).

Will repartitioning move those files safely, or do I stand to screw up my partition by repartitioning with those unmovable files where they are?

If necessary I can wait a couple of weeks (until I get home from school to find my Windows Install CD), reinstall windows then install Ubuntu, but I was hoping to get this done this weekend.

Any help?

---

### Post by HokeyFry on 2006-12-02
ooo unmovable files that kinda sucks... i dont know much about the NTFS partition sooo... a reinstall might be ur best bet, but idont really see how a file can be truely "unmovable"

---

### Post by AusIV4 on 2006-12-02
It crossed my mind that the unmovable file might have something to do with the filesystem itself, and reducing the partition might not cause any problems. I may have other problems, however, as when the defragment finished, there were some large sections of contiguous files that were further past the end of where most files stopped than there had been before.

I'll probably just wait until I can get my install CD - it will wind up a cleaner install that way anyway.

---

### Post by smoker on 2006-12-02
hi, try suggestions below before defragging,

go to add/remove, and uninstall any apps you don't need or haven't used for a while,
download a programme called 'ccleaner' (untick the yahoo toolbar when installing), and run the cleaner to get rid of all windows temp/junk/log files.
turn off system restore, to delete all restore points which take up a lot of space (you can turn it back on after defrag)
turn off your pagefile (you can turn this back on after defrag)

turn off any screensaver, running apps, even antivirus, when defragging. you may have to defrag a couple of times to get things in good order.

hope this helps

---

### Post by AusIV4 on 2006-12-02
I had already removed most of the programs on the partition - the only ones remaining were the ones I'd boot to windows for.

However a little bit of searching produced [this page]("http://howtoprimers.com/techtalk/2006/02/moving-the-unmovable-windows-disk-defragmentation-strategies/"). I haven't tried it yet, but I'm hoping that may clear things up for me.

---

### Post by smoker on 2006-12-02
looks like good advice

also, have you backed up essential data, plus you could always remove as much data from the windows partition as you can, and put it back once the resizing has taken place, this will give a better defrag, and also lessen the amount of file moving taking place, less risk.

---

