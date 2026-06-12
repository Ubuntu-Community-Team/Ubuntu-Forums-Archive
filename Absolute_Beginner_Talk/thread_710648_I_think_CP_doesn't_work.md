---
title: "I think CP doesn't work ??"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by golem3 on 2008-02-28
I need some serious help. I can't tell what's gone wrong. 

So my Ubuntu box has gone sour and it won't boot up. That's no biggie, since I can re-format, but cp isn't working in the command line. Why?

Here's what I did...tell me what went wrong. I want to backup my data in the /home/my_name (everything, including evolution mail files) to a external USB hd (called /media/disk-2)

I logged in command line (Cntl+F1) and then at the command line I 

$ sudo cp -rv /home/my_name -t /media/disk-2/

And some files copy over, other's don't. Most fail. After about two hours of copying, it said the USB disk ran out of space (which is a lot of bull) and then now the original HD in my laptop is "full". About 10 GB of data was transferred, but that's no good when I have around 70GB in my home folder.

Help me to get my files copied out of the original HD. Thanks.

---

### Post by brettg on 2008-02-28
Boot off the live CD, mount both the drives and then copy things over from there.

On a related issue, I consider it beneficial to mount /home to a separate partition. That way if you want to re-install you can just remount your old home partition and you don't need to copy stuff around like you are doing here.

---

### Post by golem3 on 2008-02-28
I didn't know the live CD allows this. Do you mean just go into the live CD as if I was testing Ubuntu out?

I used GParted and copied the entire partition, but that partition doesn't mount.

OH, thanks for the partition idea. The only thing though - how much should I allocate to the OS partition? Obviously I want the most for the home folder

---

### Post by brettg on 2008-02-28
Of course it depends on what you use the machine for etc, but for a general purpose machine I tend to allocate 10-20Gb to / and the rest to /home.

---

