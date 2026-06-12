---
title: "can't suspend to disk- slackware"
date: 2011-06-15
forum: Any Other OS
---

### Post by daweefolk on 2011-06-15
On my laptop, I can't suspend to disk (hibernate). running "echo -n 'disk'>/sys/power/state" gives me 
"echo: write error: no such device".
I can suspend to ram fine.
Just ask for any other info i didn't give :)

---

### Post by ajgreeny on 2011-06-15
Have you got a swap partition and is it big enough?

---

### Post by daweefolk on 2011-06-15
i originally installed without swap, but created a swap file 1gig at /swapfile, put it in my fstab. it starts fine, is it too small?

---

### Post by u.rusty on 2011-06-15
This helped me when wondering how much space to allocate to the swap partition.

[Swap FAQ]("https://help.ubuntu.com/community/SwapFaq")

While this FAQ is regarding Ubuntu, most of it should apply to almost any Linux.

---

### Post by daweefolk on 2011-06-15
ok my ram is 2g, i have plenty of hdd space so i created a 3G swap file. I still get "write error: no such device" when i try.

---

### Post by Elfy on 2011-06-15
Check the UUID in the resume file /etc/initramfs-tools/conf.d/resume

[https://help.ubuntu.com/community/UsingUUID#Resuming%20from%20Hibernation](https://help.ubuntu.com/community/UsingUUID#Resuming%20from%20Hibernation)

To get the UUID of the swap 

```
sudo blkid
```

Whoops, didn't check the forum - not even sure if slackware has this file ... I know fedora doesn't. I'll leave it here just in case. If it's an issue let me know and I'll delete it.

---

### Post by daweefolk on 2011-06-15
well sudo blkid only showed my main hdd, i wonder if its because my swap is a file. as for the initramfs part, i don't have that in my /etc folder. maybe a slackware thing.

---

### Post by Elfy on 2011-06-15
Probably, without knowing much about slackware, I suspect you'll have more luck hibernate to a partition not a file. Anyway I shall bow out now and come back later to see the replies.

---

### Post by kk0sse54 on 2011-06-15
Have you added "resume=<swap location>" to either lilo, grub, or kernel config?

---

### Post by daweefolk on 2011-06-15
there was already something there, i just added the resume to the end.
append=" vt.default_utf=0 resume=/swapfile"
is that the correct thing to do?

---

### Post by kk0sse54 on 2011-06-15
Yes that was the right thing to do however after digging through some documentation it seems I missed a few things since I only use a dedicated swap partition on my own system.

First off, the resume= parameter needs to point to the partition which contains your swapfile (i.e. /dev/sda1) not the actual file. You then need to add another parameter "resume_offset=<swap file offset>". You can find the swap file offset through the command "filefrag -v <filename>" with the value you're looking for being the first entry under the "physical" column.

Here's the official documentation should you want to reference it [http://www.kernel.org/doc/Documentation/power/swsusp-and-swap-files.txt](http://www.kernel.org/doc/Documentation/power/swsusp-and-swap-files.txt)

---

### Post by daweefolk on 2011-06-15
Wow, this is frustrating. I added the resume_offset bit and still no go. I think I may have to use a livecd to shrink my partition so i can make a swap.
EDIT:
I added a swap partition, edited my append to suit, and got the same error.

---

### Post by tgalati4 on 2011-06-16
I can't help you with your immediate problem as I only have Slack installed on a desktop and I have never used hibernate.  On Ubuntu, hibernate seems to take as long as a cold boot, so I really didn't see the point in using it.  I ran several tests and there appeared to be no benefit to using hibernate versus cold boot.  The only possible reason would be if you had 4 workspaces and you had stuff active in each one and you wanted to preserve that work layout.  Cold boot will normally just give you a blank desktop then you have to load all of the apps that you want to use.  Since you really can only work on one thing at a time (focus issue) I could not see the benefit of using hibernate.  I use sleep all the time and only reboot once every few months.

---

### Post by kk0sse54 on 2011-06-16
Strange, I don't know why swsusp wouldn't be able to find your swap file/partition. Try perhaps posting your lilo.conf and your kernel config if for some super strange unknown reason you don't have CONFIG_HOTPLUG_CPU set which was a common problem several years ago.

---

