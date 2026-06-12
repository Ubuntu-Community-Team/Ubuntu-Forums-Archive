---
title: "[SOLVED] Request help with &amp;quot;not on same filesystem&amp;quot; error"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by m9ke on 2007-09-15
Issue:  when ever I try to move a file to the Trash I get the error:  Unable to move to Trash: Not on the same file system

System:  Fiesty, two hard disks.  First disk is a 20GB disk which holds OS; second disk is a 500GB disk (named bigdrive) where I want to store data.

How I messed up my system:
==========================
I could not copy 60GB or so of data on to my Home directory.  Got "not enough storage"  error, leading me to believe the 500GB drive was not accessible to my filesystem.  In addition, I wanted my Home directory on the 500GB drive.

I looked around on the net and found a couple of pages on how to make a second disk Home, and proceeded to do that.

Here is the line for the bigdrive from my fstab *before* I made any changes:
/dev/sdb1 /media/bigdrive ext3 defaults 0 1

Here is the same line for the bigdrive from my fstab *after* the changes
/dev/sdb1 /home ext3 defaults,errors=remount-rw 0 1

Here is what I did to get to the present state I am in:

1. Get root:
   "sudo -s" from within the Terminal.

2.  Ran the following commands from the Terminal:

cp -vax /home /media/bigdrive

umount /dev/sdb1 

cat >> /etc/fstab << HERE 

/dev/sdb1 /home ext3 defaults,errors=remount-rw 0 1 

HERE

mount -a

At this point it got flaky:  Places menu did not open any windows; I closed the Terminal and Applications>Accessories>Terminal would not open a terminal; System>Quit.. would not show Shut Down or Restart.  

It did show Log Out.  Did that, logged back in, and it seemed to work ok.

No boot problems.  I copied a file over from a USB drive to my new Home directory, to prove I could write to the disk.  It copied over, but could not be moved to the Trash (message it's in a different file system.)  

Also noticed ownership of the new home folder was root not me.  

Changed it to me with 
m9ke@ubuntu:~$ sudo chown -v -R m9ke:m9ke /media/bigdrive/home

Confirmed ownership changed by seeing the locked icon that was on the new home folder was not present any more; and confirming in Properties that ownership has changed from root to me.

Copied about 60GB of data over from a USB disk.

Still get error message when trying to delete log file:  Unable to move to Trash; Not on same filesystem.
Selecting it and doing Shift-delete did delete the file.

Could I get some advice?  Right now I can see two possibilities to fixing this:

1-Format the drives and reinstall Ubuntu.  (All my data is well backed up)  If I take this route, I would like advice on how to make the second drive contain my Home directory.  Or:

2-Fix the "can't move files to the trash issue".  Don't know how to proceed on this one, so can't really decide between Options 1 and 2.

Thoughts?

---

### Post by jamvegan on 2007-09-16
> m9ke@ubuntu:~$ sudo chown -v -R m9ke:m9ke /media/bigdrive/home

I'm confused about what this directory is.  After changing fstab, you should no longer be referring to that drive as /media/bigdrive.  It should just be /home.  Also, /home should be owned by root, but your home directory (/home/m9ke) should be owned by you.

From the steps that you posted, I don't see anywhere that you deleted the old fstab entry for the big drive?  If both the old and new lines are there, you should delete or comment out the old one.  This may be what's causing your different filesystem error.

---

### Post by m9ke on 2007-09-16
Jamvegan, thank you for your reply!

here are the last two lines of my fstab
/dev/sdb1 /media/bigdrive ext3 defaults 0 1
/dev/sdb1 /home ext3 defaults,errors=remount-rw 0 1

You are correct, the "old" line for bigdrive is still there.  I will comment it out, and post back results.

Thanks again,

m9ke

---

### Post by m9ke on 2007-09-16
With that line commented out the last two lines of my fstab look like this:

# /dev/sdb1 /media/bigdrive ext3 defaults 0 1
/dev/sdb1 /home ext3 defaults,errors=remount-rw 0 1

Made this change to my fstab, and bigdrive does not mount at boot up time.

Can you (or anyone) suggest a way to have bigdrive mount at start up, and contain my Home directory?

---

### Post by jamvegan on 2007-09-16
m9ke, you're welcome. :)

The drive should be mounting *as* /home.  What is the output of the following?
```
df -h
```

---

### Post by m9ke on 2007-09-16
Thanks for staying with me jamvegan.  Here is what I get from df -h.  sda is the 20GB drive.  The 500GB drive is sdb, and doesn't seem to appear here.

```
m9ke@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  2.7G   15G  16% /
varrun                379M  104K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  108K  379M   1% /proc/bus/usb
udev                  379M  108K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
m9ke@ubuntu:~$ 
```

Thanks,
m9ke

---

### Post by jamvegan on 2007-09-16
What is the output of this?
```
mount
```

I'm also wondering if changing
```
/dev/sdb1 /home ext3 defaults,errors=remount-rw 0 1
```
to
```
/dev/sdb1 /home ext3 defaults 0 2
```
would fix the problem.  (The way that you have it set now looks like the way that you would mount /.)

---

### Post by m9ke on 2007-09-16
Digging into this a little more.  I decided to uncomment out the line we discussed previously in this thread and compare the results with the above.  To summarize:

Case1:
====
With these two last lines in my fstab:
```
# /dev/sdb1 /media/bigdrive ext3 defaults 0 1
/dev/sdb1 /home ext3 defaults,errors=remount-rw 0 1
```

df -h returns:
```
m9ke@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  2.7G   15G  16% /
varrun                379M  104K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  108K  379M   1% /proc/bus/usb
udev                  379M  108K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
m9ke@ubuntu:~$
```

Case 2
=====
UN-commenting out the first of the last two lines in my fstab and rebooting to show comparison:

With these last two lines in my fstab:
```
/dev/sdb1 /media/bigdrive ext3 defaults 0 1
/dev/sdb1 /home ext3 defaults,errors=remount-rw 0 1
```

df -hreturns:
```
m9ke@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  2.7G   15G  16% /
varrun                379M  104K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  108K  379M   1% /proc/bus/usb
udev                  379M  108K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             459G   74G  363G  17% /media/bigdrive
/dev/sdb1             459G   74G  363G  17% /home
m9ke@ubuntu:~$ 
```

Thoughts?

Thanks,
m9ke

---

### Post by m9ke on 2007-09-16
jamvegan, looks like we posted simultaneously.  I will review your suggestions and post back the results.

Again, thanks!!
m9ke

---

### Post by m9ke on 2007-09-16
Making the last two lines of my fstab:
```
# /dev/sdb1 /media/bigdrive ext3 defaults 0 1
/dev/sdb1 /home ext3 defaults 0 2
```

After rebooting, I got the following:
-Moving the same file I had the problem with before  from a subdir in my Home folder  to the Trash resulted in no error message.  Moving it back from the Trash to the subdir in my home folder resulted in no error messages.

-Output of mount:
```
m9ke@ubuntu:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sdb1 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
m9ke@ubuntu:~$ 
```

-Output of df -h:
```
m9ke@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  2.7G   15G  16% /
varrun                379M  104K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
procbususb            379M  108K  379M   1% /proc/bus/usb
udev                  379M  108K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   33M  346M   9% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             459G   74G  363G  17% /home
m9ke@ubuntu:~$ 
```

Here is what I think this means:
The "Unable to move to Trash...different filesystem" problem is solved.
My sda 1 (20GB disk) is mounting on /
My sdb1 (500GB disk) is mounting on / home
I will be able to boot from sda1 and install apps to it
I will be able to use sdb1 to store data, without touching it even if I reformat the small disk (sda1)

Do you see any problem with the above?  Or any thing else I should look at?

Thanks very much for your help and sticking with this issue, jamvegan!
m9ke

---

### Post by jamvegan on 2007-09-16
Hey, m9ke, happy to help. :-)

Looks good!  The only thing you might want to check, since you mentioned something about changing ownership earlier, is the ownership of directories and files.  If you were to run:
```
ls -ld /home
```
the output should look something like:
```
drwxr-xr-x 3 root root 4096 2007-08-04 09:41 /home
```
and the output of:
```
ls -ld /home/m9ke
```
should look something like:
```
drwxr-xr-x 55 m9ke m9ke 4096 2007-09-16 10:53 /home/m9ke
```
Any files within /home/m9ke should be owned by you, too.

---

### Post by m9ke on 2007-09-16
jamvegan, comment noted about changing ownership in your last post. 

Before addressing that, I would like your thoughts on this:

Looking at my filesystem I see some potential problems.  Ie two instances of home and two instances of m9ke.  Rather than trying to describe, I am uploading a screen shot, which is snipped from the whole window in my File Browser.

Should I be concerned about how this is set up?

---

### Post by m9ke on 2007-09-16
jamvegan, following up on your suggestions: 

-ran ls -ld /home
and got:
```
m9ke@ubuntu:~$ ls -ld /home
drwxr-xr-x 5 m9ke m9ke 4096 2007-09-15 19:34 /home
m9ke@ubuntu:~$ 
```

I am noting that you suggest it should look somehting like owner is root not m9ke

Next ran ls -ld /home/m9ke
and got:
```
m9ke@ubuntu:~$ ls -ld /home/m9ke
drwxr-xr-x 19 m9ke m9ke 4096 2007-09-16 11:05 /home/m9ke
m9ke@ubuntu:~$ 
```

This looks more like what you suggested I should expect in your post.

Next I looked at Properties of 5 or 6 files in /home/m9ke and confirmed that I am the owner.

I think this is getting close to resolved, after:

1-I change ownership as you suggested earlier
2-I get educated to either fix or ignore the multiple instances of Home and m9ke as shown in the screenshot in my earlier post.

Thanks,
m9ke

---

### Post by jamvegan on 2007-09-16
Yep.  That's not good.  It looks like /home/home/m9ke is the directory that you copied from your old /home/m9ke.  Here's what I'd suggest doing to fix it.  First, copy the extraneous m9ke directory to save it as a backup, in case there's anything you need there (which I doubt, but best to be safe):
```
cp -r /home/m9ke /home/home/m9ke/m9kebak
```
Next, move the copy of your original home directory to where it should be:
```
mv /home/home/m9ke /home/m9ke
```
You may need to add "sudo" to the front of that, depending on how you currently have ownership/permissions set. Now /home/home should be empty, and you should get rid of it:
```
rmdir /home/home
```
Again, you may need "sudo" in front of that.

Then I would press control-alt-F2 and try logging in as yourself.  If you get no error messages, and end up with your normal terminal prompt, then type "ls" and make sure that you see the files that you expect to see in your home directory.  If everything looks good, exit that terminal, press control-alt-F7 to get back to the GUI, and log out and back in to the gnome session to make sure that works.  If you encounter any errors or weirdness at any point, post them here before logging out, especially if Ubuntu is your only available computer/OS for connecting to the Internet.  You can switch back and forth between the virtual terminal and the GUI with control-alt-F2/control-alt-F7 whether or not you log out of either, incidentally.

---

### Post by m9ke on 2007-09-16
Thanks, jamvegan.  I will follow your suggestions, and post back results.

m9ke

---

### Post by jamvegan on 2007-09-16
As you may have realized, I had not read your last reply about ownership when I posted my last reply.  I'm going to wait to comment on that until after you indicate how cleaning up the directory structure goes, just to try to keep from having two threads going at once here in this one thread. :-)

---

### Post by m9ke on 2007-09-16
Ran the first  three commands you proposed.  None threw errors, and I looked at the results in the file browser quickly to make sure what was happening was expected.  Nothing jumped out at me.

Next did Control-alt-F2 and tried logging in as me.  No error messages.

Ran ls as instructed.   Here I started seeing different results from what I was expecting.  Did not see home directory or its files.  Instead saw "Desktop m9ke"

Did a Control-alt-F7,  got back to the GUI, which had Firefox and a Terminal open when I left it.  Tried sudo lshw in the terminal. It asked my password and produced the expected output. 

So these operations seemed to have worked, except I saw "Desktop m9ke" not the home directory and its files.

---

### Post by jamvegan on 2007-09-16
Do you have another way to access the Internet?  It sounds like things are mostly okay, and you should be able to log out of the gnome session and log back in (and, in fact, not doing so could potentially start to produce some weirdness), but I'm hesitant to ask you to do so if you have no other way to get back here.  Could you post another screenshot like you did before, showing how things are now?

---

### Post by m9ke on 2007-09-16
Hi jamvegan,

Yes, I have another box next to me, and it will connect to the net.

And yes, I am working on another screen shot now.

FWIW, all the data on my Ubuntu box is backed up.  One avenue I was considering to fix this problem was a complete format-reinstall. 

So it's all good.  Will post screen shot in a few minutes, as soon as I finish it.

Thanks again!!
m9ke

---

### Post by m9ke on 2007-09-16
Here is another screen shot.  One thing I notice right away is that I have two m9ke directories, and Desktop seems to be in kind of a weird spot.

The backup you suggested I make does not appear because I confirmed it was empty and then deleted it.

Thanks,
m9ke

---

### Post by m9ke on 2007-09-16
Here is a better screenshot, showing that both Desktop directories are empty.

It looks like I am going to have to step away from the computer for a couple of hours.  I will check back then.

jamvegan, thanks for sticking with me on this so far.  Please let me know what you think.  It seems to me we are making progress, but maybe not quite there yet!

Cheers,
m9ke

---

### Post by jamvegan on 2007-09-16
Oops!  That was my fault.  This command:
```
mv /home/home/m9ke /home/m9ke
```
would have done what I intended it to do if there wasn't already a /home/m9ke directory, but since there was, it placed the other directory in that directory instead of replacing the directory.

These commands:
```
mv /home/m9ke/m9ke/.* /home/m9ke/m9ke/* /home/m9ke/
rmdir /home/m9ke/m9ke
```
should get everything as it should be. ("/home/m9ke/m9ke/.*" catches all hidden files and directories, and "/home/m9ke/m9ke/*" catches all normal files and directories.)  You should see two messages, about not being able to move . and .. because they are busy.  That's fine.  You don't want to move them, anyway.

I'm going to be away from the computer for a while, too, but I'll check back later this afternoon or evening.

---

### Post by m9ke on 2007-09-16
Ran ```
mv /home/m9ke/m9ke/.* /home/m9ke/m9ke/* /home/m9ke/
```
It returned:
```
m9ke@ubuntu:~$ mv /home/m9ke/m9ke/.* /home/m9ke/m9ke/* /home/m9ke/
mv: cannot move `/home/m9ke/m9ke/.' to `/home/m9ke/.': Device or resource busy
mv: cannot move `/home/m9ke/m9ke/..' to `/home/m9ke/..': Device or resource busy
mv: cannot move `/home/m9ke/m9ke/.config' to a subdirectory of itself, `/home/m9ke/.config'
mv: cannot move `/home/m9ke/m9ke/.fontconfig' to a subdirectory of itself, `/home/m9ke/.fontconfig'
mv: cannot move `/home/m9ke/m9ke/.gconf' to a subdirectory of itself, `/home/m9ke/.gconf'
mv: cannot move `/home/m9ke/m9ke/.gconfd' to a subdirectory of itself, `/home/m9ke/.gconfd'
mv: cannot move `/home/m9ke/m9ke/.gnome' to a subdirectory of itself, `/home/m9ke/.gnome'
mv: cannot move `/home/m9ke/m9ke/.gnome2' to a subdirectory of itself, `/home/m9ke/.gnome2'
mv: cannot move `/home/m9ke/m9ke/.gstreamer-0.10' to a subdirectory of itself, `/home/m9ke/.gstreamer-0.10'
mv: cannot move `/home/m9ke/m9ke/.metacity' to a subdirectory of itself, `/home/m9ke/.metacity'
mv: cannot move `/home/m9ke/m9ke/.mozilla' to a subdirectory of itself, `/home/m9ke/.mozilla'
mv: cannot move `/home/m9ke/m9ke/.nautilus' to a subdirectory of itself, `/home/m9ke/.nautilus'
mv: cannot move `/home/m9ke/m9ke/.thumbnails' to a subdirectory of itself, `/home/m9ke/.thumbnails'
m9ke@ubuntu:~$ 
```
I see the two busy errors you mentioned, but there might be more errors here than anticipated (i.e., the "subdirectory of itself" msgs).

I am a mite reluctant to run the second command suggested 
```
rmdir /home/m9ke/m9ke
``` until we are sure the additional errors above are expected.
Cheers,
m9ke

---

### Post by m9ke on 2007-09-16
More interesting behavior:

Chose System>Quit...
And the choices I got were Log Out, Lock Screen, Switch User, Hibernate, or Cancel.  I.e., I did not see Shutdown or Restart.

This happened once before; and it went away until now after I logged out and logged back in as me.  I will try that.  If my system gets hosed, I will check back here on a different box.

Cheers,
m9ke

---

### Post by m9ke on 2007-09-16
I logged out as described above and was able to log back in as me with no problem.  Restart and Shutdown choices are back on the Quit dialog too.

---

### Post by jamvegan on 2007-09-16
I'm really not sure what that "subdirectory of itself" stuff is about, but all those directories that could not be moved are configuration stuff that should be automatically regenerated if needed, I believe.  You could run:
```
ls -a /home/m9ke/
```
To see if they are there where they ought to be.  Did everything else get moved to /home/m9ke?

As for rmdir, it's a very safe command to run, because it will only remove a directory if it's empty.  It also won't hurt anything to leave the extra m9ke directory around as long as you want while you make sure everything's working.  Just don't put anything in it, because it is a redundant directory that you probably want to get rid of at some point.

---

### Post by m9ke on 2007-09-16
Ran 
```
m9ke@ubuntu:~$ rmdir /home/m9ke/m9ke
```
Got
```
rmdir: /home/m9ke/m9ke: Directory not empty
```

Then
```
m9ke@ubuntu:~$ ls -a /home/m9ke/m9ke
```
Got
```
m9ke@ubuntu:~$ ls -a /home/m9ke/m9ke
.            .gconf   .gstreamer-0.10  .thumbnails
..           .gconfd  .metacity
.config      .gnome   .mozilla
.fontconfig  .gnome2  .nautilus
m9ke@ubuntu:~$ 
```

So rmdir didn't remove /home/m9ke/m9ke because it isn't empty.  The contents look like conf files that could be safely deleted.

What do you think?

---

### Post by m9ke on 2007-09-16
I have confirmed that each and every of the conf files in 
```
/home/m9ke/m9ke
```

is also present in 
```
 /home/m9ke/
```
I think the next step is to delete
```
/home/m9ke/m9ke
```

I propose that I do a 
 rm -r /home/m9ke/m9ke
on that duplicate directory.

What to you think?

---

### Post by jamvegan on 2007-09-16
If everything is working fine, including your Firefox bookmarks (which is the only thing I see in that list of configurations that you're likely to have changed, yourself), then yes, I'd say remove away!

---

### Post by m9ke on 2007-09-16
Removal completed!  The duplicate m9ke directory is gone!  Interesting you mention Firefox:  there were a bunch of write-protected Firefox (and Foxmarks) files I had to delete individually, but Firefox, all bookmarks, and Foxmarks are working fine.

You had also mentioned I should change ownership of /home from me to root.
Would the command below work, or can you recommend a better command?

```
m9ke@ubuntu:~$ sudo chown -v -R root  /home
```

Also, because you recommended this change, I assume that the ownership I assign to /home won't be inherited by subdirectories contained there, which I should own.  Correct?

Thanks,

m9ke

---

### Post by jamvegan on 2007-09-17
Actually, if you used the chown command with -R it *would* change all of the subdirectories.  This will change just the /home directory:
```
sudo chown root: /home
```

Glad everything's working! :-)

---

### Post by m9ke on 2007-09-17
jamvegan, thanks very much for sticking with me on this issue.  I have learned a lot from your suggestions!

 I will use the command you suggest to finish this up.  

Have a great week,
m9ke

---

