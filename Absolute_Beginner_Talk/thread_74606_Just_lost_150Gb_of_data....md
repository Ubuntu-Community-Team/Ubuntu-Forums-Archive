---
title: "Just lost 150Gb of data..."
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by Reejoc on 2005-10-12
Installed ubuntu and copied about 150Gb of stuff from another drive into the home directory.

Then decided to format the now empty 150Gb drive because it was still NTFS and ubuntu can't write to NTFS. Select RieserFS as the format, then it asks for a path...the hell?...I just want to format the thing. Figure it's some strange linux 'mount point' affair and select /home

Formats...

Now nothing in ubuntu works (errors about /home/username not being found)...and no sign of the contents of my home directory.

Back to Windows!

---

### Post by patrick295767 on 2005-10-12
[QUOTE=Reejoc]Installed ubuntu and copied about 150Gb of stuff from another drive into the home directory.

Then decided to format the now empty 150Gb drive because it was still NTFS and ubuntu can't write to NTFS. Select RieserFS as the format, then it asks for a path...the hell?...I just want to format the thing. Figure it's some strange linux 'mount point' affair and select /home

Formats...

Now nothing in ubuntu works (errors about /home/username not being found)...and no sign of the contents of my home directory.

Back to Windows![/QUOTE]

For me, noo return to windows, Linux is sooo great and powerful ... :-) :-)

([http://www.ubuntuforums.org/showthread.php?t=64557](http://www.ubuntuforums.org/showthread.php?t=64557))

---

### Post by Havoc on 2005-10-12
Yup.Most problems happen in Linux because of user error.Well, your error was 150 GB in weight.

Have a nice day! ;)

---

### Post by Wolki on 2005-10-12
[QUOTE=Reejoc]Then decided to format the now empty 150Gb drive because it was still NTFS and ubuntu can't write to NTFS. Select RieserFS as the format, then it asks for a path...the hell?...I just want to format the thing. Figure it's some strange linux 'mount point' affair and select /home

Formats...

Now nothing in ubuntu works (errors about /home/username not being found)...and no sign of the contents of my home directory.[/QUOTE]

Hm, how exactly did you format the drive?

Maybe you formatted the wrong drive, maybe you formatted the right one and changed your /home to the newly formatted drive. If it's the last one, your data is still there, but you have to point your fstab to the right partition again. No luck if you really formatted your home partition though...

---

### Post by raublekick on 2005-10-12
It sounds like Ubuntu might just be confused about where /home is actually located since now there are two. I'd suggest reformatting the drive, but seeting the mount point to something like /backup or /media or something, anything that isn't used already in Ubuntu. 

I had some trouble before with stuff like this, it's a pain in the butt to fix but your data should be there.

---

### Post by Reejoc on 2005-10-13
[QUOTE=raublekick]It sounds like Ubuntu might just be confused about where /home is actually located since now there are two. I'd suggest reformatting the drive, but seeting the mount point to something like /backup or /media or something, anything that isn't used already in Ubuntu. 

I had some trouble before with stuff like this, it's a pain in the butt to fix but your data should be there.[/QUOTE]
You guys were right, the data is still there, it's just I couldn't see it because /home was messed up.

All sorted now.

---

### Post by patrick295767 on 2005-10-13
[QUOTE=Reejoc]You guys were right, the data is still there, it's just I couldn't see it because /home was messed up.

All sorted now.[/QUOTE]


You see linux is damn nice !! No data Loss !!

---

