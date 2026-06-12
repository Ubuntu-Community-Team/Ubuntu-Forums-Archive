---
title: "Reading Files on a CD/DVD-ROM without proper permissions"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by meb495 on 2007-01-20
I know there have been several posts citing similar problems but the issue is so straightforward and simple that I know there must be a simple fix if someone knows it and can help me.

I have many burned DVDs with AVI files - burned on OS X and thus, i suppose, have unix-style permissions.  When I burned them I didn't much care about permissions because at the time I wasn't a Linux user.

Now I find that I can easily read (play, copy, etc) files on these DVDs only if the permissions are set to allow people other than the owner to read them - obviously only a few are.

I tried doing a su cp command from the terminal to copy the files onto my hard drive using my own root status.  This neither worked nor produced an error.  Perhaps I did something wrong?

I'm new to Linux and Ubuntu but love Ubuntu so far!!  Please, someone must have a simple way around this problem? 

Thanks,

---

### Post by aysiu on 2007-01-20
I don't know the answer to your question, but I think your thread belongs in this forum and not the HowTo section. Good luck!

---

### Post by an.echte.trilingue on 2007-01-20
This is just a thought:

try adding nosuid to the /ect/fstab file, like this:

Before:
```
/dev/hdc        /media/cdrom0   iso9660,udf     ro,user,noauto  0       0
```


After:
```
/dev/hdc        /media/cdrom0   iso9660,udf     ro,user,noauto,nosuid  0       0
```

Hope it works,

Take care,
-mat

---

### Post by meb495 on 2007-01-21
Thanks aysiu for putting this in the correct forum.  Also thank you Mat for the nosuid suggestion.  Unfortunately it didn't work.  

Perhaps I should just blame Apple for letting me burn a DVD like this with wacky permissions.  

If anyone has any other ideas short of using a Windows box or a Mac to access the files let me know.

Thanks,
Ubuntu Cool

---

### Post by amaroamaral on 2007-02-01
Hello to all!
I have exact same problem, burnded a bunch of files in OS X um CD's, now o cannot opent in my PC UBUNTU 6.10, say "permissions" problems, all files assigned to root!

No solution yet....

---

### Post by meb495 on 2007-02-03
I found an easy fix that worked from someone on the LinuxQuestions forums.  The fix is adding my UID and GID (user ID and group ID) to the dvd-drive entry in my fstab.  This overrides whatever is written on the individual disks and makes me the owner of every file on any disk in the drive.

As you'll see, the following is that portion of my fstab.

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,nosuid,uid=michael,gid=100     0       0

Other options that were suggested included 1) manually adding a UID of 501(the owner of the burned files) to my passwd file and logging in as 501, which i didn't try and 2) copying the files as root from the command line, which I unsuccessfully tried but for all I know I may have done incorrectly because people say it is supposed to work - I'm not sure.

The thread on the linuxquestions forum is at:

[http://www.linuxquestions.org/questions/showthread.php?p=2614856&posted=1#post2614856](http://www.linuxquestions.org/questions/showthread.php?p=2614856&posted=1#post2614856)

---

### Post by lambesk on 2007-02-27
I just wanted to say thanks to meb495.  I was having trouble with my CD-Rom drive and I couldn't figure out what to do to get it so that I could browse my CD's that I burned from within Windows.  Adding my uid and the cdrom gid got it so that I can finally use those CD's without sudoing up.  Thanks again!  :)

---

### Post by jesushero on 2007-12-29
I am having this problem with some DVD's burned on Mac OsX. I tried all the proposed solutions but they did not work. When I insert specific DVD's, I can see the folders with an X on them and I can not list the files or access them in any way. The permissions set the owner as 501. I edited the fstab in several different ways, but the problem remained the same. 

What needs to be done is the permissions of files on Cd's and DVD's to be overridden, and replaced with the permissions given to the users by the system administrator. Since DVD's and CD's are meant to be used with many different systems, it is no use sticking to permissions given to files on them. This only adds to incompatibility, from which Linux already suffers a lot. From what I understand, Os X has a way of writing DVD's and CD's with weird permissions that make them normally unusable to Linux users. Apparently they will not bother making their operating system compatible with linux, so let's find a way around this! 

It also happens to movie DVD's that are burned on Os X. When I insert the movie DVD, the DVD player starts and tries to play it but returns a permission error. 

What is EXTREMELY strange about this is that it has started happening with some DVD's that I had previously accessed with no problem on the same Linux machine, with absolutely no hardware or software changes. 

The syslog says that the DVD has been mounted as readonly. Why is that?

```
Dec 30 03:31:40 Levendis kernel: [  619.403894] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'i knew them', timestamp 2007/10/12 16:38 (1000)
Dec 30 03:33:09 Levendis kernel: [  707.983013] UDF-fs: Partition marked readonly; forcing readonly mount
```

What could have caused a partition that was not normally mounted as readonly to suddently start mounting as such?

---

### Post by wirelessmonkey on 2007-12-30
What application are you using to burn these DVD/CDs?  I run several macs with tiger and leopard, and several ubuntu boxes, and don't see this problem.  Perhaps I can replicate it and help you a bit.


WM

---

### Post by jesushero on 2008-01-01
Thank you wirelessmonkey. Some of the DVD's were burned using the standard Os X cd/dvd burner application. Some others were burned using Nikon digital camera capture software, that also burns photographs on Cd's. It was the software that comes with Nikon D-50, forgot the name though. Unfortunately the Mac I had used to do this is in another country now, so I can't repeat the procedure or examine it more.

However what I find totally puzzling is the fact that I have watched a certain movie dvd several times on this computer, before it suddently became unreadable. All of the discs mentioned work perfectly on Windows XP machines (tried them yesterday at a friends place). I really also think that I have accessed one of the discs with the pictures in the past. 

Nothing has changed in my fstab file, I experimented with loads of options and they didn't work so I changed it back to the default.

Is there a straightforward way of changing the permissions of files on CD/DVD discs that I'm missing here? Like a way of mounting the udf or iso partition while chown-ing everything to the current user??

---

### Post by thelatinist on 2008-01-02
**jesushero:**  DVD-Roms *should* be mounted as read-only because they are _R_ead _O_nly _M_emory.  You can't write to them.

Has anyone tried adding umask222 to the fstab?

```
/dev/hdc   /media/cdrom0   iso9660,udf   ro,user,noauto,umask=222   0   0
```

---

### Post by jesushero on 2008-01-02
**thelatinist:** I just tried that and it returned an invalid mount option. It totally refused to mount the drive this way. Also, yes, I confused the read-only mode with permissions... So nothing useful in the logs then...

By the way, yesterday night I tried to access the files as root and it works. Root is (thank-god-allmighty) above user 501. So I am guessing that the user who posted that this did not work for him, probably did something wrong or has a different problem.

So this means I can copy the contents of DVD's on to my hard drive. But I do not want to do that because it's too many DVD's in total. It will be about 30GB!! Also I am not thrilled about the idea of running my DVD player as root!!! 

Any ideas about overriding the permissions as root? Like a way of assigning user 501 to be owned by any other user? Like a symbolic link? Of course, since it is a DVD the permissions of the files can't be changed by sudoing chown.

---

### Post by thelatinist on 2008-01-02
> **jesushero said:**
> **thelatinist:** I just tried that and it returned an invalid mount option. It totally refused to mount the drive this way.

Are these iso9660 disks?  I was assuming they were UDF.  If so, then use the following option instead of umask=222:

```
mode=0555
```

---

### Post by jesushero on 2008-01-02
The one I've just tried is indeed UDF. The owner had been somehow changed from 501 to -1. What do these numbers represent?

BUT, mode=0555 WORKED!!! Thanks a million!! With that on my fstab the owner is set to root but I can copy the files and list them without sudoing. PERFECT! Hope it works on all of them!

If some work one way (mode=0555) and some work the other way (unmask=222) is there a way to use an OR statement in there?

By the way, could you also let me know what these do (so I can totally understand what I have changed)??

Thanks again thelatinist!!!

---

### Post by thelatinist on 2008-01-02
> **jesushero said:**
> By the way, could you also let me know what these do (so I can totally understand what I have changed)??

Glad it works.  To explain, both of these override the file permissions on the CD.  The way user modes work under *nix, permissions are set by a three-digit number. The first digit represents the permissions for owner, the second for group, and the third for other.  The digits are determined as follows: Execute = 1, Write = 2, Read = 4.  If you want to set more than one permission, you add these numbers together to get the correct digit.  Thus:

Execute = 1
Write = 2
Execute + Write = 1 + 2 = 3
Read = 4
Execute + Read = 1 + 4 = 5
Write + Read = 2 + 4 = 6
Execute + Read + Write = 1 + 2 + 4 = 7

When using the mode option you are setting who should have permissions for all files. You have to add a 0 before the three-digit mode.  Therefore mode=0555 grants read and execute permissions to user, group, and other.  Since it is read-only, you don't need write permissions.

When using the umask option, you are setting who should NOT have permissions (anything not specifically denied is allowed).  Since nobody needs write, you use 222.  You do not add 0 before a umask value.

Please note that the mode is umask (_u_ser file creation mode _mask_), not unmask.

---

### Post by jesushero on 2008-01-02
Thanks a lot thelatinist! I got the picture, didn't know about the 3 digit system and was always wondering. Thanks!

---

### Post by thelatinist on 2008-01-02
You are very welcome.  Don't forget to mark the thread solved using Thread Tools so we don't keep coming back to it. ;-)

---

### Post by jesushero on 2008-01-02
I am not the one who started the thread. I'll send a message to the one who started it. Thanks.

---

