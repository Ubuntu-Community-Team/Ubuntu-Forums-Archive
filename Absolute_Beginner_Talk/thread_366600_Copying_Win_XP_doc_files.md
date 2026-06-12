---
title: "Copying Win XP doc files"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by bruceb on 2007-02-21
I'm totally new to Ubuntu - really like what I've seen so far. However, I've got a problem with a Win XP crash & so using Ubuntu 6.10 on bootable CD to try & access or copy some of My Documents files that I don't want to loose. When I boot my PC with Ubuntu CD & go into Places where I thought I would get access to My Docs files I can't find them - can anyone tell me how to see these files so that I can copy them onto CD or USB mem stick to back them up?

---

### Post by hardyn on 2007-02-21
hda i am assuming....

/documents and settings/$username/my documents

if i am WAY of base please explain futher.

---

### Post by bruceb on 2007-02-21
Thanks, I'd read about hda before, but haven't a clue how to set this from Places - can you provide some really simple one step instructions? - I'm quite simple!! Also I'm only using Ubuntu from CD boot so hopefully can do all this? Thanks  Bruce

---

### Post by hardyn on 2007-02-21
i have never run the live CD, but ill see what i can do,,,

does the live cd show an hda icon on your desktop? is it automounting your windows parition?
if yes, it should be some clicking around.

if its not... you will have to create a mount point, a directory. that is a portal to the other patition.  i don't have experience with the live disk but will give it a whirl.

the mounpoint can pretty much be created anywhere.

open the command shell...

mkdir /windows
mount /dev/hda /windows  - you may have to add switches depending on the type of filesystem you are using for your windows parition... this will be available in the 'man' pages.

man mount

once the device is mounted, it will appear on the desktop. or if not, it will can be accessed by changing directory to it using your mountpoint using nautilus is probably the easiest.

find /windows, double click.
then your windows partion should appear the same as it did in windows.

go find your files and copy them back to the desktop or something.

now you have to get them on to your flashdisk, ipod, external drive or whatever.... this devices should be automounted as soon as you plug them im.

there is lots of info on this forum... if i have messed something up, im sure this question has been asked before, it might just be a question of finding the right search terms.

good luck.

---

### Post by bruceb on 2007-02-21
Thanks for the details really great - firstly no hda icon on desktop!! And next, I don't know how to open shell command. Hope you can help complete novice ....... Bruce

---

### Post by fjf314 on 2007-02-21
To open the shell you just go to Applications > Accessories > Terminal

Once you have the terminal open, you can enter in the commands hardyn gave you.

---

### Post by hardyn on 2007-02-21
i goofed too...

you are going to want to mount 'hda1'

sorry about that.

---

### Post by goodbyewindows on 2007-02-21
I'm having a related problem. I have mounted hda1 (My NTFS windows partition), but it's read only. How do I change permissions? Running Nautilus with gksudo doesnt work. Does anyone have a list of those permission (chmod) codes?

---

### Post by fjf314 on 2007-02-21
Typically, Ubuntu cannot write to NTFS partitions, so running change mode commands won't do you any good.  There is a way to allow you to write to NTFS partitions, but it's more complicated so I will let someone who has experience tell you because I have never actually done it myself.

---

### Post by bruceb on 2007-02-21
Thanks - I've created Windows & now when I do next line I'm getting a message of mount: only root can do that - what does this mean?? Ta --- Bruce

---

### Post by fjf314 on 2007-02-21
You need to be logged in as root or a "super user" in order to be able to issue the commands.  Before you start any of them type in:

```
sudo -s
```

Enter in your password and your prompt at the terminal should be prefaced by the word "root".  Now you should have access to do what you need.

---

### Post by louieb on 2007-02-21
The Ubuntu Live CD is not the best one to copy stuff off your hard drive. For the simple reason that its doesn't automatically mount the hard drive partitions. 
Two that I use for that purpose are Knoppix and Puppy. 
Puppy is my favorite it only about a 50-100 meg download. 
One you load up Puppy there is an icon labeled drives. Click on it and it lists all your drives. Click on mount and it opens up the file manager showing the files on the drive.

Knoppix places an icon on the desk-top for each partition on your drive. Its got a full tool kit but its also close to a 700 meg download.

---

### Post by louieb on 2007-02-21
> **bruceb said:**
> Thanks - I've created Windows & now when I do next line I'm getting a message of mount: only root can do that - what does this mean?? Ta --- Bruce
Prefix you mount command with sudo.
or someone said to enter sudo -s its ```
sudo -su 
```
Root is superman he can do anything including deleting every thing on the hard drive. When you are superman your prompt changes from a $ to a #.
any way this is what I would do

```
sudo mkdir /mnt/ahdp
sudo mount -t ntfs  /dev/hda1  /mnt/ahdp
gksudo nautilus
```

Use the file browser to go to /mnt/ahdp and your windows file should be there.

---

### Post by fjf314 on 2007-02-21
> **louieb said:**
> or someone said to enter sudo -s its ```
sudo -su 
```

Oops, I never realized this.  Someone told me about sudo -s, so that's what I have been using.  What is the difference?

---

### Post by hardyn on 2007-02-21
this is right out of the man pages:

 -u  The -u (user) option causes sudo to run the specified command as a
           user other than root.  To specify a uid instead of a username, use
           #uid.  Note that if the targetpw Defaults option is set (see sudo&#8208;
           ers(5)) it is not possible to run commands with a uid not listed in
           the password database.


and yes, i realize that i should have specified the use of sudo; i do take that for granted sometimes.

---

### Post by fjf314 on 2007-02-21
You would think that from using Solaris and now Linux that I would remember to check the man pages first...  Thanks for the info.

---

### Post by louieb on 2007-02-21
The difference is I typed before I checked. You are correct it is sudo -s. I just tried both  I thought -su would alter the $PATH variable, but all it did was give a message to please use single character options only.   Other than that they both did the same thing.:oops:

---

### Post by bruceb on 2007-02-22
Ok thanks for help so far - I'm going to try Knoppix or Puppy to see if these are simpler for me to use. Do appreciate the comments & help so far, will be back later ........Bruce

---

### Post by Ben Sprinkle on 2007-02-22
> **bruceb said:**
> Thanks, I'd read about hda before, but haven't a clue how to set this from Places - can you provide some really simple one step instructions? - I'm quite simple!! Also I'm only using Ubuntu from CD boot so hopefully can do all this? Thanks  Bruce

In /media.

---

### Post by bruceb on 2007-02-23
Knoppix is great - it's so simple to use, loads really easily & simple to copy files from Win XP onto usb stick - thanks all for help - may consider changing to Linux in future - ta Bruce

---

