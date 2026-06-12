---
title: "Second hard drive in Ubuntu (slave), how to send files to it?"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by danr on 2006-05-04
Hello everyone,

I added a 2GB slave hard drive to the computer I have Ubuntu installed on, just to see if I could make it work. And to my surprise it does actually work! And it shows up in “Disks” as 1.83GB free space.
I formatted it so it would have the right file system on it for the OS to use and then I “activated” it. I didn’t know what to tell it to do as far as the “Format type” and the “access path” so I left it set as the default settings of “Extended 2” and “/boot” it listed for them from the start. As far as I can tell its fine the way it is but I’m not sure! lol

Anyway my question is how do I save anything to it?
I made a drawing on it and I wanted to save it to that drive so I would know how.
I can see anyway of doing so as I look around in it though.

Well, that and is there anything wrong with the settings I used when I formatted it.

Any other info you’d like to share about the different settings and such would be great also!

Thank you for your help and guidance,

---

### Post by juicybananahead on 2006-05-04
Have you mounted the drive? If you don't know what I mean, just post the results of the following commands into the forum.
```
cat /etc/fstab 
```
```
cat /etc/mtab 
```

---

### Post by danr on 2006-05-05
Hi juicybannahead,

Lol, No I don’t know what you mean, but when I made those entries and then I typed “mount drive” and it says,
Can’t find drive in /etc/fstab or /etc/mtab.

I don’t have the computer on line now but I can put it on line if you need to see the results of the commands.

Thank you for the assistance, Dan

---

### Post by cptjaben on 2006-05-05
here's a guide that includes information on mounting harddrives, it may be of some help but i'm sure someone else can give you a more specific answer:

[http://ubuntuguide.org/]("http://ubuntuguide.org/")

---

### Post by Belathor on 2006-05-05
Hey! I had this problem 2 days ago! I needed to mount a 20GB hard drive to my file system. Have a look at this thread and see if it helps. I was working in Xubuntu at the time, but I did everything in the terminal so hopefully it will be of help! :D 

[http://ubuntuforums.org/showthread.php?t=169520]("http://ubuntuforums.org/showthread.php?t=169520")

---

### Post by catlett on 2006-05-05
[http://www.faqs.org/docs/lnag/lnag_drives.html](http://www.faqs.org/docs/lnag/lnag_drives.html)
Here's another good guide. Your drive might not be mounted. It needs to be mounted for linux to know it is there.
To mount you have to make a place for it. So we'll first make a spot for the drive. I put things in /media.That's where you'll see the default places for floppy and cdrom drives. So open the terminal and type ```
sudo mkdir /media/second
``` You can put anything you want for the name. I used second for the example (second hard drive).
Now you have to mount it.  If you made it Ext3 this is the command (if you used fat 32 use vfat where I put Ext3). This command will have extra commands to make the drive read and writable to users and not just root. (complicated way to say you can write to it without doing anything special) ```
sudo mount -t ext3 -o user,rw,exec,umask=000 /dev/hdb1 /media/second
```
That will mount the drive and make it accessable. The only part I'm not sure about is hdb1. That is how your second hard drive wil be listed. My issue is if the 1 is needed. I never had to mount a drive with only 1 partition. You might only have to write hdb. Hopefully someone will post. I don't think it will be an issue because the drive is technically hdb1 even if there are no other partitions. (sorry if I'm confusing you. /dev/hdb1 means...device-dev...hard drive-hd...second hard drive-b...first partition on second hard drive-1...so you're communicating to linux where this place is, it is on the device hard drive which is the second hard drive in the system and the first partition of that hard drive.../dev/hdb1. This is my question. Does it have to be declared the 1st partition if there is only one?)

---

### Post by danr on 2006-05-05
Hi Belathor thanks for the link,

Well I tried to follow the directions you followed, lol  but it gets to the point were it wants to know if I want to change the name of it and I select “no” and it stays there. How did you get past that point?
Everything looks good until I get to that point and then it all ends, it will not let me exit or save. 

Cptjaben, thank you for your link to, I’ll be checking it out also.

Dan

---

### Post by Belathor on 2006-05-06
I am not really sure where you stopped but I will try my best to sum up what I did.

1.) find out if the drive is in the file system by typing 'df' in the terminal.

2.) Assuming it isn't, you need to find the partition on the hard drive that you created. Do this by typing 'sudo fdisk -l /dev/[hard drive name]' If you just formatted it, there should only be one partition on the drive.

3.) Now type in 'sudo nano /etc/fstab'. This shows you all of the partitions mounted on the file system. Copy the layout of one of your already mounted partitions (trying to put the text under the headings)*. Change the words in the layout to match your partition you want to mount. For the Directory, make one up.
*You have to navigate using the arrow keys

4.) Now you have to make your directory. Type: sudo mkdir /[whatever you called it].

5.) Now mount that directory. sudo mount /[whatever you called it]

Now you should be able to see the partition in the file system. You can check by finding the directory or typing 'df' in the terminal and looking for it. :D 

I hope that helps clarify...

---

