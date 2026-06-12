---
title: "cd-rom drive mounting  issues?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by someguyonthestreet on 2007-02-16
Okay so after many trials, i finally installed ubuntu onto my desktop. But now i'm having trouble accessing te files on my dvd drive and cd drive. The dvd is  not mounted and i don't  know hoe to do that. And i can't figure out how to access the files on my cd. When i go to storage media, there's a folder there for \cd0 but i don't understand what to do. I'm new to linux and i've only used windows before. So i suppose i'm learning about computers to begin with.

---

### Post by link141 on 2007-02-16
I've got no idea if this will work, but it's worth a try. You only have one drive, right?
1. put a cd into your drive.
2. open a terminal, (if you hit alt F2, I think a list will pop up and you can open it from that.
3. enter this command:  
```

sudo mount /dev/hdc /media/cdrom0

```
    and enter your password.
4.Check your media folder to see if you cd is mounted 

I give this a 3% chance of actually working (I'm an intermediate user, and don't really know that much :)), but if it does, then that would be cool :).  If it doesn't, then unmount the device with:
```

sudo umount /dev/hdc

```

See what that does, and post any problems that occur.
link141

---

### Post by someguyonthestreet on 2007-02-19
i've reinstalled te operating system. i have a different graphics card, not that tat has anything to do with it. and it works fine now.

---

