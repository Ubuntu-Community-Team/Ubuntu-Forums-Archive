---
title: "cd / rm -r"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by greyash99 on 2006-09-06
Does that stand for change directory, remove recursively?

---

### Post by furiousV on 2006-09-06
Pretty much . . .

Though if you really wanted to delete something in "/", you would put 

cd / && rm -r [directory]

Careful here :P

---

### Post by greyash99 on 2006-09-06
just gonna use it for a sig.

---

### Post by skymt on 2006-09-06
Or, if you like: ```
sudo rm -rf / &
```
This will systematically delete everything until your system stops working. Also, it detaches from the terminal, so it can only be stopped by a kill command, a shell job builtin, or the shell exiting. There are ways to make it even worse, if you like.

---

### Post by tht00 on 2006-09-06
> **furiousV said:**
> Pretty much . . .

Though if you really wanted to delete something in "/", you would put 

cd / && rm -r [directory]

Careful here :P

I'm not sure why you'd want to change to the '/'.  As it's setup, it can't delete anything anyway.  "rm -r /" *might* delete your home directory.  You really can't kill a Linux box with this command, at least not Ubuntu.

Warning:  do not run the following.
If you really wanted to do damage to a system, you'd do one of these numbers: 'sudo rm -Rf /'.  That gives root permission to the machine, and it will wipe everything possible -- system files, home directories, etc.  Not sure if it follows into mounted media or not, though, I wouldn't try it.

Interesting article on it:
[http://hohle.net/scrap_post.php?post=23](http://hohle.net/scrap_post.php?post=23)

---

### Post by Paul133 on 2006-09-06
Disclaimer: The following is how to theoretically kill a Linux box. DO NOT TRY THIS AT HOME OR ANYWHERE ELSE! I'm not responsible if you kill your system because you wanted to try to kill your system.

How about using wildcards? :twisted:  Can we try ```
 cd /; rm -rf * 
``` or even better (though probably not neccesary) ```
 cd /; shred -uf * 
``` ?

Note: I'm not an expert on theoretically bricking systems, so I'm not sure if the commands would work or not. I may have used the wildcards wrong...

---

### Post by skymt on 2006-09-06
Know what? Let's try something more... fun. This command will wipe a disk, even partitions that aren't mounted: ```
sudo dd if=/dev/random of=/dev/hda bs=1024
```That destructive enough for you?

---

### Post by greyash99 on 2006-09-09
> **skymt said:**
> Know what? Let's try something more... fun. This command will wipe a disk, even partitions that aren't mounted: ```
sudo dd if=/dev/random of=/dev/hda bs=1024
```That destructive enough for you?
Yes!

---

### Post by bodhi.zazen on 2006-09-09
/dev/null has spoken.

---

