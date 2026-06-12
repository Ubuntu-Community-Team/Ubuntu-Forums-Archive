---
title: "reFIT disappeared. More Problems."
date: 2008-05-07
forum: Apple Hardware Users
---

### Post by Hellsadvocate on 2008-05-07
I've got a ton of problems on my hands now. I triple boot to OSX, Vista and Ubuntu through reFIT, just recently I decided to change the entire permissions for my Mac partition in OSX so ubuntu could access it. I did it for the main hard drive and subsequently applied it to all enclosed folders. (Read and write permission for everyone). Restart, and Refit is gone, restart again and OSX won't load and holding down ALT just shows windows and mac. 

OSX won't load anymore, and just keeps getting stuck at the main boot screen, doing single user mode now and fsck shows an invalid leaf tree error, as well as some other errors. 

Now i repair some mac's and when I see these typical errors, that means the HD is gone and reformatting or Disk Warrior is the only way to go. What just happened?

edit: just noticed this: ```
http://problemstosolve.com/os-x/permissions-error-snafu-causes-leopard-not-to-boot-solved/
```

Why the f*ck would that happen if you're only editing permissions? Will OSX start panicing if the permissions are by default, what it expects or something? Running fsck in single user mode is giving me a clusterf*ck of errors. Great.

---

### Post by russo.mic on 2008-05-08
First of all, there is absolutely no need to swear in these forums.  It won't get you any bonus points.  You might be frustrated, but keep in mind your own actions led you here.I know the website automatically edits them out, but most of us are older than 13 and know what your saying.  Please, in the future...thanks.

2nd of all, you can't just start changing permissions for the entire filesystem.  I'm pretty sure it wouldn't get you anywhere anyway.  

Boot up from your OS X disc, open up the disk utility from whatever menu it's in (I forget now), select the partition OS X is on and repair your permissions.  That should get you starting again.  OS X is a complex beast and has it's own permissions setup for various reasons and is probably not something to be tinkering with as far as from root goes.  Have all the fun you want in your home folder, however.

Next, if you want read/write access, turn journaling OFF in disk utility.  I believe that will allow you read/write access, however, journaling is a good idea.  your kinda throwing caution to the wind doing that. 

It's also possible you've hosed your OS X partition and might have to reinstall.  If verifying and repair of pemissions doesn't work, I don't know what to tell you.   

Russo.

---

### Post by Brightbelt on 2008-05-08
Your situation sounds complex and I know this is probably Not an issue for you...but I mention it just in case, because it happened to me and caused similar problems...

Make sure you have No external devices attached to your computer: this goes for hard drives and iPods and everything in between.

I get so used to Mac's trouble-free enviroment (former PC-er here) that I forget simple logic. My symptoms were similar - rEFit wouldn't load, and the MAC OSX boot would get stuck... It wasn't as bad as yours sounds.

Good Luck,...Frank B.

---

### Post by cyberdork33 on 2008-05-08
> **russo.mic said:**
> 2nd of all, you can't just start changing permissions for the entire filesystem.  I'm pretty sure it wouldn't get you anywhere anyway.
Yep, that is bad, bad.

---

### Post by Mr. Pink on 2008-05-08
Something similar happened to me when I was trying to constantly mount the OS X partition.  I ended up having to reformat everything (after luckily being able to pull my files off through Ubuntu).  The best advice after you get your system up and running again is keep an extra ntfs+ partition solely for sharing files between mac and linux and don't mount the Mac partition with all of the core OS X files.

---

### Post by russo.mic on 2008-05-09
> **Mr. Pink said:**
> Something similar happened to me when I was trying to constantly mount the OS X partition.  I ended up having to reformat everything (after luckily being able to pull my files off through Ubuntu).  The best advice after you get your system up and running again is keep an extra ntfs+ partition solely for sharing files between mac and linux and don't mount the Mac partition with all of the core OS X files.

I wouldn't recommend ntfs for this purpose.  it suffers from the same problems as mac extended!  It's closed source, and the drivers written to read/write from it aren't as reliable as you'd like.  

Make a transfer partition and format it FAT32 or something.

Russo

---

