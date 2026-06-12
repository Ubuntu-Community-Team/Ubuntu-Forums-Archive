---
title: "hmm, major partition problem"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-09-14
Well, here's the story: I was resizing several of my partitions with the GParted Live CD. After it finished, it said there were 4 "warnings" and then when it went back to the partition screen it showed that there was still 7MB of unallocated space. It shouldn't have been there, so I assume that was the problem.

Anyway, I resized them again to use up that space, but this time it stopped completely with an error. Only, now when it went back to the partition screen, it showed the entire HD as unallocated space! I assumed this meant the HD had been wiped, but I was able to restart and load Windows as normal. My Windows partition now reflects the new size, so no trouble there I guess. But when I tried to boot into Ubuntu, that didn't work, and my shared partition is no longer available either, so I can only guess that all my other partitions were erased.

No big deal, really, but when I reboot with the GParted Live CD, it still shows the entire HD as "unallocated", so there's no way for me to simply delete those partitions officially and reclaim that space.

What do I do at this point? There are about 8GB of space that I don't have access to now.

Thanks,
John

---

### Post by theredcross on 2006-09-14
some of the specific errors you're getting would be nice, don't have a clue what's going on without them. Maybe a list of your partition tables would be good as well.

---

### Post by JohnJSal on 2006-09-14
Well, I saved the details of the second error, but it looks like it was saved on a Linux partition (/root), which of course is probably gone now.

---

### Post by nalmeth on 2006-09-14
The entire drive can't be unallocated if windows is still there.

Do you have multiple harddrives? You can select different HD's at the top right of gparted.

Do you have an ubuntu CD? If you do, try it, and load up gparted from there to see if there is a difference.

---

### Post by JohnJSal on 2006-09-14
I have a single 60GB HD and it is/was divided this way:

Windows    20GB
/          10GB
/home       1GB
shared      25GB
swap        1GB

I then resized it so that the / directory would be 7GB and the other three would all be 512MB, putting the remaining ~25GB back to Windows. This worked the first time except that it still left 7MB free. So I tried it again and the second time got the error.

I have tried rerunning the GParted Live CD, and I have also used the Ubuntu Live CD, and every time I run the partitioner it shows this:

unallocated    55GB

That is my entire hard drive. Obviously it's not correct, since Windows seems to be unharmed from the process. I have no doubt that the other partitions were destroyed because 1) Ubuntu won't boot, and 2) my shared drive is no longer present.

So I don't know what's happening with that extra 8GB of space, but I'd like to do something with it. It's just that, as things are now with GParted, it is detecting my entire HD as unallocated space.

---

### Post by nalmeth on 2006-09-14
Was grub erased too? If not, when grub loads hit ESC and try loading the Recovery Mode.

Was your ubuntu partition close to full before you shrunk it?

I hope you backup your data :-\"

You might want to try a different partitioning tool, like diskdrake, which is on the PClinuxOS liveCD.

---

### Post by egoldtech on 2006-09-14
try this amazing tool for this guys : Boot it .:
I have used more than 500 times, I think is the best one ..
[http://www.terabyteunlimited.com/](http://www.terabyteunlimited.com/)

good luck

---

### Post by JohnJSal on 2006-09-15
No, the Ubuntu partition wasn't full. I don't know if the GRUB was erased, how do I tell? It still boots to the screen where I can choose whether I want Ubuntu or Windows. What would Recovery Mode accomplish though? I still need to partition, but I can't.

And I'd rather not pay for Boot It, especially if I don't know it will work given my current situation. GParted doesn't detect my partitions, why would this one?

---

### Post by nalmeth on 2006-09-15
Yes, that is GRUB

Recovery mode should leave you with a shell, but while booting it should detect any filesystem errors, and possibly fix them. 

If you can get to the command prompt, enter this command:
sudo fdisk -l

Post that output

(it's a lowercase L not an I or 1 :) )

---

### Post by JohnJSal on 2006-09-15
Ok, I'll have to wait til I get home and try this. When I tried to boot into Ubuntu, it did take me to a prompt, but it was a little different than normal. There were error messages on the screen about the filesystem being corrupted, so I didn't know if this was still a regular Linux prompt. But if I get back there, I will try this command.

---

