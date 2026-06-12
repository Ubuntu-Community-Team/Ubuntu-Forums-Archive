---
title: "I accidentally deleted some files from an NTFS Hard Drive - Can I Recover?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2007-02-25
Hello all!

I accidentally deleted all my ".php" files from my NTFS Hard Drive...
Is there a way to recover them?

I performed a "[color=blue]rm *.php /var/www[/color]"...
I wanted to perform a "[color=blue]rm /var/www/*.php[/color]"... ](*,)

Unfortunately, I performed this from the Terminal...!!!

Please help!!!

Thanks

---

### Post by haricharan on 2007-02-25
check this out.. [http://www.ntfs-3g.org/support.html#diskspace]("http://www.ntfs-3g.org/support.html#diskspace")
hope this wud solve it!!
the files deleted from ntfs-3g wud goto a hidden folder named .Trash-<username> in the root of that partition.....

---

### Post by john_spiral on 2007-02-25
Try using [PhotoRec]("http://www.cgsecurity.org/photorec.html") to recover your lost files. Don't boot from the ntfs drive until you have recovered the deleted files.

see my below howto:

[http://www.ubuntuforums.org/showthread.php?t=338451](http://www.ubuntuforums.org/showthread.php?t=338451)

---

### Post by dvarsam on 2007-02-25
[QUOTE=haricharan]check this out.. [http://www.ntfs-3g.org/support.html#diskspace]("http://www.ntfs-3g.org/support.html#diskspace")
hope this wud solve it!!
the files deleted from ntfs-3g would goto a hidden folder named [color=blue].Trash-<username>[/color] in the root of that partition.....[/QUOTE]

I have already checked that!
When you delete files with your mouse, _indeed_, they are sent in that hidden Trash folder.
But when you delete files from the Terminal, they don't go to the Trash can.
And it does NOT matter if those files were lying on an NTFS Partition or a Ext3 Partition...

I would have used the mouse to move those files, but when Ubuntu locks the /var/www/ folder, I am only left with the option of using Terminal commands...
I am coding in .php & every now & then I drop files into the /var/www folder to check the output of the code...
Then I delete the /var/www/ contents & drop some new files in...
By mistake, instead of deleting the /var/www/ folder contents, I deleted my source files & lost everything!!!

Thanks.

---

### Post by steve.horsley on 2007-02-25
I don't know how to undelete NTFS files, but I'm sure there are live rescue CDs out there that can do this. Fortunately, you only deleted the files in the current directory - you didn't do it recursively, which may limit the damage.

For the future, you can use nautilus with full root privilege with this command:
**gksu nautilus**
which wil allow you to trash your system graphically instead of having to use the command line to trash it. ;) I always change the background of my root nautilus to red, to remind me of the danger.

---

### Post by szaka on 2007-02-25
Use ntfsundelete from the ntfsprogs package. If you didn't make modifications to the NTFS partition then it must be able to recover your files. It's very important NOT to make ANY modifications to NTFS because the deleted files can be overwritten forever in that case. Recover everything (the name of the files will be lost) then rename them to their original names.

---

### Post by haricharan on 2007-02-25
> **dvarsam said:**
> I have already checked that!
When you delete files with your mouse, _indeed_, they are sent in that hidden Trash folder.
But when you delete files from the Terminal, they don't go to the Trash can.
And it does NOT matter if those files were lying on an NTFS Partition or a Ext3 Partition...

oh i didnt know that...sorry abt that...lemme see if i could find something else...

---

### Post by ScruffyShandy on 2007-06-14
> **haricharan said:**
> 
the files deleted from ntfs-3g wud goto a hidden folder named .Trash-<username> in the root of that partition.....

Cheers mush, this has just saved me having stupidly deleted every tune I'd ever written.  I spent a frantic 10 minutes then, telling you...........

---

