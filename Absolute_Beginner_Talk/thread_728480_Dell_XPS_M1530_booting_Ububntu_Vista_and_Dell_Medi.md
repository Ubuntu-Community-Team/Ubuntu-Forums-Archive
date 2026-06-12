---
title: "Dell XPS M1530 booting Ububntu Vista and Dell MediaDirect."
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by spacesearcher on 2008-03-18
I recently ordered the Dell XPS 1530 and I have a few questions hopefully someone can answer.
I want to Dual boot with Vista while keeping the Dell MediaDirect working. I have found this tutorial for the M1330:
[http://www.daryl.mu/2007/12/29/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/](http://www.daryl.mu/2007/12/29/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/)
 
has any one tried doing this the M1330 is very similar to M1530 so it work the same way? Is it safe? and lastly the tutorial uses ext3 for the disk format in step 6.4 should I use that or NTFS instead?

I'm scared of wiping the hard drive on a brand new computer but I also really want this configuration and don't want to have to back everything up if I did it later.

Thanks

---

### Post by gobbles414 on 2008-03-19
> **spacesearcher said:**
> I recently ordered the Dell XPS 1530 and I have a few questions hopefully someone can answer.
I want to Dual boot with Vista while keeping the Dell MediaDirect working. I have found this tutorial for the M1330:
[http://www.daryl.mu/2007/12/29/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/](http://www.daryl.mu/2007/12/29/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/)
 
has any one tried doing this the M1330 is very similar to M1530 so it work the same way? Is it safe? and lastly the tutorial uses ext3 for the disk format in step 6.4 should I use that or NTFS instead?

I'm scared of wiping the hard drive on a brand new computer but I also really want this configuration and don't want to have to back everything up if I did it later.

Thanks

It certainly appears that the guide you've linked is well constructed. Since I don't own a Dell nor would I wish to keep the MediaDirect feature if I did, I can't offer you much first-hand advice. But I do have some general pointers.

There's one part of the guide that's a bit unclear. The procedure requires a real Vista installation disk -- versus a system recovery utility. Did your Dell include a real Vista installation disk? Or, did it come with only a system recovery utility? Luckily, it doesn't really matter with Dells. In my experience, companies like Acer and HP will not send a real Windows installation disk to customers under any circumstances. But Dell should be willing to send a real Vista installation disk to you upon request. Some other tips... Use ext3 instead of NTFS in step 6.4. I doubt that the Ubuntu installer would even allow NTFS -- but I've never tried. After you complete step 1, you may wish to use [GWSCAN]("http://support.gateway.com/support/drivers/search.asp?param=gwscan&st=kw") to "write zeros" to your hard drive. Writing zeros is simply a more thorough way of erasing your hard drive. BTW, I ALWAYS write zeros to the hard drive on a new computer. Even iPods have been known to leave the factory with viruses. You can't be too careful about viruses these days.

I hope that some of these ideas are helpful.

---

### Post by spacesearcher on 2008-03-19
Ok thank you for helping me. When I ordered the computer I called so I could specifically ask if it came with disks and it does. they sent disks for another computer when the hard drive had issues and it came with a dell cd labeled windows XP so I'm assuming vista will be the same. It just changed from in production to shipped so I'm packing up all of my files now (its so nice to reorganize).

 And for the dell media direct I am only going to keep on it if I can see a change in battery usage when watching a dvd. Its not like it takes the computer very long to boot into a real operating system to play it, which is what they advertise. 

thank you

ps I saw somewhere a terminal command to zero the hard drive using ubuntu live cd so thats what I will probably do.

---

### Post by gobbles414 on 2008-03-20
> **spacesearcher said:**
> Ok thank you for helping me. When I ordered the computer I called so I could specifically ask if it came with disks and it does. they sent disks for another computer when the hard drive had issues and it came with a dell cd labeled windows XP so I'm assuming vista will be the same. It just changed from in production to shipped so I'm packing up all of my files now (its so nice to reorganize).

And for the dell media direct I am only going to keep on it if I can see a change in battery usage when watching a dvd. Its not like it takes the computer very long to boot into a real operating system to play it, which is what they advertise. 

thank you

ps I saw somewhere a terminal command to zero the hard drive using ubuntu live cd so thats what I will probably do.

My pleasure... If you have both XP and Vista installation disks, I recommend that you install XP. I've got Vista Ultimate. So I can tell you from experience that XP is much better than Vista for most tasks. Also, I recently tried to write zeros to one of my hard drives using an Ubuntu 7.10 LiveCD. The process got stuck in an endless loop and I had to use GWSCAN instead. But admittedly, I wasn't using the best hardware at the time. So, I'd be interested to learn if you're able to successfully write zeros using your LiveCD.

---

### Post by spacesearcher on 2008-03-20
> **gobbles414 said:**
> My pleasure... If you have both XP and Vista installation disks, I recommend that you install XP. I've got Vista Ultimate. So I can tell you from experience that XP is much better than Vista for most tasks. Also, I recently tried to write zeros to one of my hard drives using an Ubuntu 7.10 LiveCD. The process got stuck in an endless loop and I had to use GWSCAN instead. But admittedly, I wasn't using the best hardware at the time. So, I'd be interested to learn if you're able to successfully write zeros using your LiveCD.

Thats what I have heard that a lot about vista. I'm going to try it anyways and then judge it along with dell media direct. then rearrange to what I think will be most comfortable. I'm just excited to be able to finally permanently install ubutnu!
one other thing I was pondering in my mind while backing up things was. how easy is it to share bookmarks email settings and things between the to OS's using Mozilla? What about music library/files? or just all file redundancy in genral? I'm so used to everything just being in the C: drive I don't know how easy it will be to adjust to installing things in other places.

---

### Post by gobbles414 on 2008-03-20
> **spacesearcher said:**
> Thats what I have heard that a lot about vista. I'm going to try it anyways and then judge it along with dell media direct. then rearrange to what I think will be most comfortable. I'm just excited to be able to finally permanently install ubutnu!
one other thing I was pondering in my mind while backing up things was. how easy is it to share bookmarks email settings and things between the to OS's using Mozilla? What about music library/files? or just all file redundancy in genral? I'm so used to everything just being in the C: drive I don't know how easy it will be to adjust to installing things in other places.

I cannot answer your bookmarks question. But in general, any partition that Windows can read/write is also read/write in Ubuntu 7.10. So you should be able to share files between the two operating systems rather easily.

---

### Post by spacesearcher on 2008-03-21
k thanks I will post if the zeroing thing worked after I do it here should be in a few days hopefully. I think all the other questions I have will be answered once I do it and mess around with it.

---

