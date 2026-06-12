---
title: "/home is full???"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by kaufmannn on 2008-01-12
So... I installed Gusty 64-bit through Wubi, gave it like 15 Gigs to have fun with. I'm finally getting the hang of Ubuntu, though still essentially blindly follow "enter this into terminal to fix that," etc... 

But I have most of the things I want to work, working (aside from flash... but in Gusty 64-bit that supposed to be a nightmare). Now, however, I have come across a whole new beast: my home folder is full. I never even knew this was it's own partition... I knew swap was and I knew from an earlier failed Ubuntu test that I could make a home partition, but with a 15gig install I didn't expect Wubi to screw me like this.

I think it only gave me 2 gigs. WHAT CAN I DO WITH THAT? I would like to access a few more gigs, even just to double it to four. Can I somehow put files (like movies) into areas other than home?

Uh, yeah... that's the gist of my story so far. Any help guys?

---

### Post by iris-n on 2008-01-12
You can put it in other places, indeed, but it isn't recommended. It's easier to keep track (when reinstalling, backup) when they're on a single folder.

Now, i would recommend you using gparted ```
sudo apt-get install gparted
```, to expand your home partition (back it up before!).

Otherwise, you could just create a /movies folder, or whatever. You would have to ```
sudo mkdir /movies
sudo chown <your_name> /movies
```

Hope that helps ^^

---

### Post by hnprashanth on 2008-01-12
Iris,

will gparted work inside ubuntu, or we need to boot that from CD?
i thought we have to boot that.

---

### Post by nowshining on 2008-01-12
when u install ubuntu it actually reservers a few gigs of memory, about 3gb on gutsy. :)

gparted is a partition tool u can then resize and make new paritions, etc.. be careful tho with it. ;)

---

### Post by Partyboi2 on 2008-01-12
> **hnprashanth said:**
> Iris,

will gparted work inside ubuntu, or we need to boot that from CD?
i thought we have to boot that.
The partition you are working  with gparted needs to be unmounted. So using gparted on a live cd is the way to go.

---

### Post by kaufmannn on 2008-01-12
Don't worry folks, I slept on the issue and now in the new light I've figured an even better method to solve my woes. As I mentioned, I'm using a Wubi install of Ubuntu. Meaning I have a working install of Windows (in my case Vista) which still commands most of my harddrive space. Shortly after installing I stumbled across this program which allowed me to read and write on my windows drive. I tested it right away and found I could play movies from the other partition - sweet! So, right before posting this I moved the movie I downloaded with deluge to the vista partition and I think I'm fine now.

I like to download movies, hence I ran out of space... but no longer will that be an issue. 

Thanks for the help, but I found my own way without fooling with partition sizes.

---

### Post by iris-n on 2008-01-12
hnprashanth, 

It depends on where you use it. The partition you're gonna mess with needs to be umount'ed, in this case it was /home, hence it was possible to unmount it without shuting down the system. However, if you're gonna resize the partition on where /boot, /var or other system folders are, you need to boot in the live CD.

---

