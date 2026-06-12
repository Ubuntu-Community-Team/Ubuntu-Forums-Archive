---
title: "recover file after rm 'ing it"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-02-22
i havn't deleted anything yet, but was reading about recovery and thought i better prepare myself for that awful day when i accidently rm something by accident!

so is there an easy way to recover data deleted through the rm command? any software?

---

### Post by george29 on 2007-02-22
read this article..

[http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss](http://servers.linux.com/article.pl?sid=06/08/21/1558230&from=rss)

not sure if this is completely the sort of thing you want but can probably do the job...

---

### Post by PetePete on 2007-02-22
yeh ive already read that.

looking for more of a GTK+2 style program... or similar.. not a recovery program intended for a whole disk failure... just 1 file.

---

### Post by Ben Sprinkle on 2007-02-22
It's something to do with inodes. I heard if you have a process running that is still refrencing to it, that it's possible to recover it.

For instance:
You have a terminal open and you rm it, that terminal process, if still refrencing to it, may be recoverable. But I got no idea how to recover it lol.

---

### Post by PetePete on 2007-02-22
so why is it more difficult than in windows?
windows i accidently delete something, i run a number of recovery programs, and it gives me a list of recoverable data and i just click what i want..... why not linux so easy?

---

### Post by Ben Sprinkle on 2007-02-22
I have no idea, my reccomendation is not to 'accidently delete it' in the first place. This shouldn't happen in the terminal, so always delete in nautilus so you can recover it in the trash.

---

### Post by jvc26 on 2007-02-22
It might be a good idea not to delete with such abandon that ones get accidentally deleted. You can get them back from trash if you just rightclick delete them, but it tends not to be a good idea to just wipe :)
Il

---

### Post by george29 on 2007-02-22
got all the following links from searching google with ' linux recover deleted files'

[http://www.ists.dartmouth.edu/classroom/file-recovery.v0.81.php](http://www.ists.dartmouth.edu/classroom/file-recovery.v0.81.php)

[http://e2undel.sourceforge.net/recovery-howto.html](http://e2undel.sourceforge.net/recovery-howto.html)

[http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html](http://www.cyberciti.biz/tips/linuxunix-recover-deleted-files.html)

[http://www.cyberciti.biz/tips/linux-recover-deleted-files-with-lsof-command.html](http://www.cyberciti.biz/tips/linux-recover-deleted-files-with-lsof-command.html)

[http://recover.sourceforge.net/linux/](http://recover.sourceforge.net/linux/)

[http://www.faqs.org/docs/Linux-mini/Ext2fs-Undeletion.html](http://www.faqs.org/docs/Linux-mini/Ext2fs-Undeletion.html)

And got the quote below from this web faq.
[http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

Q: How can I recover (undelete) deleted files from my ext3 partition?
Actually, you can't! This is what one of the developers, Andreas Dilger, said about it:

In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to "grep" for parts of your files that have been deleted and hope for the best.


[http://www.stellarinfo.com/linux-data-recovery.htm](http://www.stellarinfo.com/linux-data-recovery.htm)  commercial software

---

### Post by PetePete on 2007-02-22
thanks george

---

### Post by Tomosaur on 2007-02-22
Wait wait wait. This is simple. Just write a script which only moves things to the ~/.Trash folder, and then make rm point to it, like this:
Put this in a text file in your home directory and name it 'rm' (not rm.txt, just rm):
```

#!/bin/bash
mv $@ $HOME/.Trash

```

Back up the 'real' rm:
```

sudo mv /usr/bin/rm /usr/bin/rmBACKUP

```

Now, you can either move your script to /usr/bin, or you can just link to it.

TO MOVE IT:
```

sudo mv ~/rm /usr/bin/rm
sudo chmod +x /usr/bin/rm

```

TO LINK IT:
```

chmod +x ~/rm
sudo ln -s ~/rm /usr/bin/rm

```

Obviously, you can modify this to do other stuff, but that's basically it. Alternatively, you can just modify the real rm.

This should work just fine. You could alternatively try making an alias for rm and putting it in your ~/.bashrc file. Test the script out on a few test files before you commit to replacing rm with it.

---

### Post by Ben Sprinkle on 2007-02-22
Not a bad idea. ^^
But the real recovering from inodes I got no idea.

---

### Post by Tomosaur on 2007-02-22
Made a little mistake. The $1 in the script should be $@.

---

### Post by Ben Sprinkle on 2007-02-22
I might actually do this, thanks man.

---

### Post by PetePete on 2007-02-22
good idea, but how do you delete the file from trash? would you have to run the real rm... so something like: realrm files2delete

---

### Post by Ben Sprinkle on 2007-02-22
Right click the trash icon > empty.

---

### Post by Tomosaur on 2007-02-22
No problem. Remember that the 'real' rm has all kinds of features like recursion and whatever, but you can emulate that in the script. The one I posted just features a 'delete' function (which moves stuff to .Trash rather than deleting), so if you want to extend it, be prepared to put in a little time.

---

### Post by Tomosaur on 2007-02-22
> **PetePete said:**
> good idea, but how do you delete the file from trash? would you have to run the real rm... so something like: realrm files2delete

Naming the script 'rm' was realy just a suggestion. You could just as easily call it 'del' (like on Windows), and keep the proper rm. That way, you could always delete things with 'del', then 'rm' the ones you know you definately don't want to keep.

---

