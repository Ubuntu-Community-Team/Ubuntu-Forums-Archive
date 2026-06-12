---
title: "partition help"
date: 2007-05-21
forum: Apple Intel Users
---

### Post by fumanchu on 2007-05-21
Im currently running feisty on my core duo macbook pro, and everything finally seems to be running ok.  Now I would like to be able to listen to my mp3 files, which are on my osx partition, from ubuntu.  What would be the best way to do this?

---

### Post by ronocdh on 2007-05-21
> **fumanchu said:**
> Im currently running feisty on my core duo macbook pro, and everything finally seems to be running ok.  Now I would like to be able to listen to my mp3 files, which are on my osx partition, from ubuntu.  What would be the best way to do this?
You can mount your OS X partition with the following command:```
sudo mount /dev/sda2 /mnt
```This will mount your main drive in OS X to the folder "mnt" in your root directory in Ubuntu. You may, however, run into permissions errors. I think a cheap way around this is to make sure your Ubuntu and OS X login names are identical.

Please post back with results.

Also, make sure you grab the "xine extra codecs" from Synaptic in order to play MP3s.

---

### Post by fumanchu on 2007-05-21
hmm, im still getting the permission problems after making my login names the same.

---

### Post by fumanchu on 2007-05-21
ok nevermind, i just solved the permission problem, thanks for the help

---

### Post by fumanchu on 2007-05-21
actually, while im here, is there any way to make it so ubuntu automatically mounts sda2 everytime i log in?

---

### Post by benanzo on 2007-05-21
to automatically mount your OS X paritition when you start Ubuntu:

Make a directory for the OS X partition to mount into:
```
sudo mkdir /mnt/osx
```

Open the Filesystem Table (/etc/fstab) for editing as the root user:
```
sudo gedit /etc/fstab
```

Add this line to the end of the file:
```
/dev/sda2 /mnt/osx hfsplus user,defaults 0 0
```

**/dev/sda2** is the name of the OS X partition to mount.
**/mnt/osx** is where you want the partition to mount to.
**hfsplus** is the type of filesystem the partition is (HFS+)
**user,defaults** these are the options to set when mounting the partition.  "user" lets non-root users mount it.
**0 0** don't worry about these (they're used for backing up and filesystem checking)

If you want to be able to write to the OS X disk from Ubuntu you'll need to disable journaling from within OS X and mount the partition as root in Ubuntu.

To disable journaling in OS X:
Open a terminal and type:
```
diskutil disableJournal disk0s2
```

Or use Disk Utility.

---

### Post by fumanchu on 2007-05-21
thanks, that works perfectly

---

### Post by fumanchu on 2007-05-21
oh no!  I changed the ownership of all the folders on the mounted harddrive using:  "sudo chown -R alex /mnt/osx" and I thought itd work since I set my login names to be the same in ubuntu and osx, but now osx wont start at all, how can I fix this?

---

### Post by ronocdh on 2007-05-22
> **fumanchu said:**
> oh no!  I changed the ownership of all the folders on the mounted harddrive using:  "sudo chown -R alex /mnt/osx" and I thought itd work since I set my login names to be the same in ubuntu and osx, but now osx wont start at all, how can I fix this?
Hm, a problem indeed. Well, OS X has a handy little app called Disk Utility that gives the options **Verify Disk Permissions**and **Repair Disk Permissions** for drives. I would try booting up from your OS X installer disc, running Disk Utility, and seeing whether you can fix it that way.

Let us know how it goes.

---

### Post by fumanchu on 2007-05-22
ok, now im atleast able to boot into osx again, but I still don't have permission to get into most folders, and on the ubuntu side im still able to access everything.  How can I switch ownership back to osx, or even better, isnt there a way that I could access the harddrive from both ubuntu and osx?

---

### Post by ronocdh on 2007-05-22
> **fumanchu said:**
> ok, now im atleast able to boot into osx again, but I still don't have permission to get into most folders, and on the ubuntu side im still able to access everything.  How can I switch ownership back to osx, or even better, isnt there a way that I could access the harddrive from both ubuntu and osx?
Benanzo's instructions above are IMO very clear, and yes, they allow you to share files across both partitions. Benanzo did not advise any **chown** procedure that I saw.

What did you do to be able to boot into OS X again?

---

### Post by fumanchu on 2007-05-22
I was able to log back into osx after using the permission repair function on disk utility, and yes, benanzo's instructions were very good, but i still did not have permission to access most of my osx files from ubuntu.  So I tried the chown command, an idea that I found from this thread [http://ubuntuforums.org/showthread.php?t=411966&highlight=hard+drive+mount+permission](http://ubuntuforums.org/showthread.php?t=411966&highlight=hard+drive+mount+permission), and that solved my problem, however, now I have the same permission problems on the osx partition.

---

### Post by fumanchu on 2007-05-22
does anybody know how to fix this?  I think I really messed something up, changing the ownership of my entire hard drive probably wasn't the smartest thing to do :(

---

### Post by ronocdh on 2007-05-22
> **fumanchu said:**
> does anybody know how to fix this?  I think I really messed something up, changing the ownership of my entire hard drive probably wasn't the smartest thing to do :(
Well I don't think this is enough to solve the problem, but perhaps it's a piece of the puzzle: in Ubuntu, I do not have permission to edit my Documents folder on my OS X partition. So to get around this, I did **sudo nautilus**, navigated to the Documents directory (I had mounted the OS X partition previously), and right-clicked to edit the permissions.

The permissions were originally set to "501." I do not know the significance of this figure; perhaps it's just a generic Linux "no-no," but I thought I would share it. Perhaps there's a way you can reinstate that value from Ubuntu and then OS X will treat your partition kindly again.

To be clear, now you are able to log into OS X, but you cannot view your Documents? Is this correct?

---

### Post by fumanchu on 2007-05-23
Thats right, I can log in but I can't view most of my user files.  I seem to have found a crude solution though; by changing the ownerships manually back to my osx user name (when logged into osx) I can access most of my files again.  However, all of my permissions are still really messed up and some things aren't working right.  I wish there were a way to just reset all the ownership changes I made, maybe if I bring it to the apple store they can help me out.

---

### Post by ronocdh on 2007-05-23
> **fumanchu said:**
> Thats right, I can log in but I can't view most of my user files.  I seem to have found a crude solution though; by changing the ownerships manually back to my osx user name (when logged into osx) I can access most of my files again.  However, all of my permissions are still really messed up and some things aren't working right.  I wish there were a way to just reset all the ownership changes I made, maybe if I bring it to the apple store they can help me out.
Very much luck, of course. Please don't forget to post your solution, when you come across it! It would be nice for some people here to have a detailed account of went wrong, first so they can avoid it, and second so they can solve it. ;)

---

### Post by fumanchu on 2007-05-23
There are a bunch of folders that appear on my mounted hard drive that I can't see in osx, is it safe to assume that these and everything in them should be owned by root?

---

### Post by onbongos on 2007-05-23
the 501 is the user id of the first user created by the osx installer

---

### Post by onbongos on 2007-05-23
> **fumanchu said:**
> There are a bunch of folders that appear on my mounted hard drive that I can't see in osx, is it safe to assume that these and everything in them should be owned by root?

it is safe to assume you can ignore them entirely ;)

---

