---
title: "Possible to have /home as My Documents target?"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by bombitmd on 2006-08-22
I'm on XP/Ubuntu dual boot, and can now access files from either OSes.  However, I'm still having permission problems with XP. (Will  try to fix it after this post.)

Since it's proven that I can access and modify [COLOR="Red"]/home[/COLOR] files from XP without any problem, I'm thinking of just creating a single drive for all my personal files.  Ofcourse, I'll be using [COLOR="Red"]/home[/COLOR] as the drive.

My question is:  **[COLOR="Blue"]can I make [COLOR="Red"]/home[/COLOR] as the target directory for My Documents?[/COLOR]**  Will I not encounter any problems, especially with XP permissions?  I still haven't gotten the permissions issue straigheted out just yet.

Related to this, can I just use Partition Magic to convert and merge my FAT32 into my /home partition?  Will I lose files in either directories?

Thanks for all your patience :p

---

### Post by bodhi.zazen on 2006-08-22
Don't know about Windows XP. Likey this is a registry edit?

---

### Post by aysiu on 2006-08-22
/home cannot be FAT32, but you can reformat FAT32 to be Ext3 and add that space on to the end of /home if it's its own partition.

You can also make /home (if you're using [http://www.fs-driver.org](http://www.fs-driver.org)) My Documents in Windows if you delete the My Documents folder and then make a shortcut to /home in C:\Documents and Settings\bombitmd called My Documents and linked to /home

---

### Post by bombitmd on 2006-08-22
> **aysiu said:**
> /home cannot be FAT32, but you can reformat FAT32 to be Ext3 and add that space on to the end of /home if it's its own partition.

The /home I'm referring to is the Linux mounted /home drive, so it's already ext3.

You can also make /home (if you're using [http://www.fs-driver.org](http://www.fs-driver.org)) My Documents in Windows if you delete the My Documents folder and then make a shortcut to /home in C:\Documents and Settings\bombitmd called My Documents and linked to /home

Yes, I'm using that program, which is why I can access /home from XP.  I thought of creating a shortcut to /home, but I wanted to know if I could set it as the target for My Documents. In XP, you can change the target directory of My Documents to anywhere.  My real concern is, if I DO use /home as My Documents target, and assuming there are still permission problems,  will I be able to write onto it if I'm in Linux? What will happen if permission is not allowed?

---

### Post by sonny on 2006-08-22
> **bombitmd said:**
> My question is:  **[COLOR=Blue]can I make [COLOR=Red]/home[/COLOR] as the target directory for My Documents?[/COLOR]**  Will I not encounter any problems, especially with XP permissions?  I still haven't gotten the permissions issue straigheted out just yet.

On windows I think it'll be tricky. But you can always make a shortcut to My Documents in your /home/user directory. I personally think the second is better, because if you make My Documents you /home/user folder then you will have all you user specific configuration files within you actual documents, which will lead to an unorganize folder, if you just make a shortcut to your /home/user folder you will have a "cleaner" folder, and this way you could avoid some of the permission problems.

> **bombitmd said:**
>  Related to this, can I just use Partition Magic to convert and merge my FAT32 into my /home partition?  Will I lose files in either directories?

You WILL LOSE ALL YOUR FILES, I do not recommend you to do this unless you REALLY know what you're doing.

---

### Post by bombitmd on 2006-08-22
Thanks again, sonny.  Yeah, I was starting to feel that targeting /home would be a bit tricky, considering how Windows likes to control everything.  I'll first try short cutting /home, then try to fix this permission problem.  Once I'm sure it's all working out fine, then I'll back up files and merge the the two partitions into one ext3 /home drive.  Thanks again!

---

