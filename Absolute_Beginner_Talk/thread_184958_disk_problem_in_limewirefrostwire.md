---
title: "disk problem in limewire/frostwire"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by Culito on 2006-05-30
I currently have a hard disk set aside for music only.  it is /media/music, FAT32.  All permissions are enabled.  The line in fstab for that drive is:

/dev/hda1 /media/music vfat iocharset=utf8,umask=000 0 0

When I try to configure limewire or frostwire to use that drive for storage, it just says that it's an invalid folder for saving files.

Any ideas?  Would it just be easier to format that drive as ext3?

Thanks in advance,
C

Oh, another thing, I can't log in as su in terminal.  I know I'm using the right password, as I can use it to do other things, but "su" just won't let me!

??

Yes, I'm a noobie.

---

### Post by ProjectGod on 2006-05-30
if su won't let you in...

try resetting the password for it

**sudo passwd root**

type YOUR password ... then type the NEW SUPER USER / ROOTS password... retype for confirmation.

----------------------------------------------

i think it better and easier to have an ext3 partition. unless you wish to have a dual booting system where the operating system (windows) wishes to utilise the music partition also.

:-D

---

### Post by catlett on 2006-05-30
Ubuntu uses sudo by default [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) You can enable a root password by the above post but that is the wiki about sudo.
Fat32 shouldn't be a problem. I have a 40gb fat32 external drive that I download torrents to, although I use bittorrent. Try browsing to the folder in a root nautilus and right clicking to get a menu and then hit on properties<permissions. Make sure all the boxes are checked off. ```
gksudo nautilus
```Other than that I don't know what it could be. Doesn't really make sense. 
If you let it choose a default folder where does it make it?

---

### Post by Culito on 2006-05-30
I changed my password sucessfully, but here's what it says in terminal when I type "sudo nautilus":
(nautilus:12526): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Nautilus opens shortly afterward, and all the /media/music folder permission boxes are checked.  If I try to check any of the special boxes below, it says "Couldn't change permissions".
The default folder for limewire is /home/cully/shared.

I dunno.

---

### Post by solarwind on 2006-05-30
you can get "ext3ifs" installable filesystem driver for windows. Ext3 is much better than any crap filesystsem M$ puts out. Get the "ext3ifs" driver for windows and format your music drive with ext3. You can see your ext3 drives in windows just as if they were windows drives.

---

### Post by Culito on 2006-05-30
Whoops...I figgered it out.  I checked the permissions for the "/music" folder, but that is in the "/media" folder which I didn't check.
And I am in no need for any Windows crap so I'll probably reformat that drive soon.

And I'll probably come up with a whole new set of problems.
-C

---

### Post by catlett on 2006-05-30
That warning always comes up when you run a gui application from the terminal instead of from the menu.
Edit: that's all that's needed from me you have it figured out.

---

