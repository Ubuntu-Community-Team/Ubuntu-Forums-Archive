---
title: "explain this command?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by emnaki on 2008-04-12
(cd /mnt/img ; tar -cf - *) | (cd /mnt/usb ; tar -xvf -)
Can someone explain the above command to me? Especially I would like to understand what the '-' means and what  the '*' means in the above context. Also how does the brackets work?

---

### Post by mordantae on 2008-04-12
> (cd /mnt/img ; tar -cf - *) | (cd /mnt/usb ; tar -xvf -)
Can someone explain the above command to me? Especially I would like to understand what the '-' means and what the '*' means in the above context. Also how does the brackets work?

well i'm relatively new to this but i as far as i can see...

cd means change directory, what follows (/mnt/img) is referring to the directory that you're changing to [/mnt/img would usually have a mounted device/filesystem inside] .

the ; is to allow you to process two separate commands after one another 

tar is usually used for backing up files or opening .tar files (called tarballs i believe)

the -c option means create
the -f option means to use archive file or device (have a look at the man pages and they usually answer your questions...just type: man tar   in this case and you'll have access to the entire tar command manual page.)

from what i gather the - means the default stream of input 

the * is a wildcard....usually referring to 'any string or character' ....

now that's all in parenthesis, meaning it will be worked out separately, and the output of all the commands mentioned so far will be

Note : this is a pipe :) --->   | 

| <-- piped (using that symbol over there) meaning the output/result of that command will be passed on to what's going on on the other side...
which is basically the same thing but a different /mnt point is being referred to and -xvf means to verbosely extract the specified .tar file



im not suggesting you should take my word for this *watch me hang a large disclaimer notice on my forehead* since i'm still pretty much new to this as i only started using linux at all about 4 months ago...but a word of advice is to READ man(ual) pages when you dont know what something does and good on ya for asking around here...thats a very good way to learn..i found this community superbly helpful...

im not entirely sure what the command means exactly...but as far as i can gather its making a tarball out of everything it finds in /mnt/img and un-tarring it (sort of like extracting it) into your pendrive? ie. /mnt/usb ???

hope this helps...

:)

---

### Post by waynep on 2008-04-12
(cd /mnt/img ; tar -cf - *) | (cd /mnt/usb ; tar -xvf -)

ok . . . The | in the middle is the pipe character. The results of things to the left of the | will be fed to the thing on the right of the |.

(cd /mnt/img ; tar -cf - *) - This changes the current dir to /mnt/img. It then tars up (c create f specifies file) everything in the dir (* means everything) and sends the resulting output of tar through the pipe. The later "-" in the "tar -cf - *" as the file specification means standard out.

 (cd /mnt/usb ; tar -xvf -) - The part accepts from standard in, the tar ball from the other tar command.  This changes the dir to /mnt/usb then untars stuff from standard in to the current directory. 

In a nutshell, this will move all the files in /mnt/img to /mnt/usb. BTW: tar will traverse subdirectories. 

Another way to do this . . . 

cd /mnt/img ; find . -print | cpio -pvmud  /mnt/usb

-wayne

---

