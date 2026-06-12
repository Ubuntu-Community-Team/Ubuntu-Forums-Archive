---
title: "Long list of files to copy, going insane."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by octoberdan on 2007-04-12
I have two removable hard drives, both formatted to NTFS. The first hard drive, call it Hard Drive "A", has a few thousand images that need to be copied to the second hard drive, call it Hard Drive "B". With some command line magic I was able to comprise (and refine) a list of over 3,000 images that need to be copied. In the backup directory on Hard Drive "B" I need to preserve the directory structure found on Hard Drive "A". The list I made has several thousand entries like:
"./Documents and Settings/All Users/Documents/My Pictures/pics/10_16_2005/DSCN0018.JPG
./Documents and Settings/All Users/Documents/My Pictures/pics/10_16_2005/DSCN0001.JPG"
I've tried using tar --files-from, but after a point I get "File size limit exceeded." I've had this person's computer/hard drive for awhile now and they're anxious to get at least their pictures back. I fear I may have bit off more then I could chew. Although I've learned a lot about Linux trying to solve this problem, I've come to endless dead ends and irritating IRC misunderstandings. If another person tells me to cp -Rf... Thank you for at least reading this, I appreciate your time.

I beg you for your input

Thanks again,
Dan.

---

### Post by RomeReactor on 2007-04-12
Hi. If making a .tar file is not possible due to the size, you could try making an ISO image with the Nautilus Burning application or K3B; copy that over and extract it by right-clicking it (i think) or with the Archive Manager.

EDIT: Reading your post more closely, it seems to me that you don't have a GUI. Am I mistaken?

---

### Post by Arndt on 2007-04-12
> **octoberdan said:**
> I have two removable hard drives, both formatted to NTFS. The first hard drive, call it Hard Drive "A", has a few thousand images that need to be copied to the second hard drive, call it Hard Drive "B". With some command line magic I was able to comprise (and refine) a list of over 3,000 images that need to be copied. In the backup directory on Hard Drive "B" I need to preserve the directory structure found on Hard Drive "A". The list I made has several thousand entries like:
"./Documents and Settings/All Users/Documents/My Pictures/pics/10_16_2005/DSCN0018.JPG
./Documents and Settings/All Users/Documents/My Pictures/pics/10_16_2005/DSCN0001.JPG"
I've tried using tar --files-from, but after a point I get "File size limit exceeded." I've had this person's computer/hard drive for awhile now and they're anxious to get at least their pictures back. I fear I may have bit off more then I could chew. Although I've learned a lot about Linux trying to solve this problem, I've come to endless dead ends and irritating IRC misunderstandings. If another person tells me to cp -Rf... Thank you for at least reading this, I appreciate your time.

I beg you for your input

Thanks again,
Dan.

I don't know why 'tar' should complain about a file size, but the program 'cpio' can perhaps be of some help.

---

### Post by octoberdan on 2007-04-12
I will ultimately be decompressing any archive I create. Is there a way to get around that step and still get what I've described wanting? Thank you for the quick response.

---

### Post by justleen on 2007-04-12
i might not understand you right.. but why not just use the cp command??
```

cp ./Documents and Settings/All Users/Documents/My Pictures/pics/* /driveb/backupfolder -r

```

the -r will copy recursivly, (go into the folders..)

edit:  soryr, i was to quick reading and replying.. why doenst this work for you, the cp -rf?

---

### Post by octoberdan on 2007-04-12
I don't want to copy *everything* I only want to copy the pictures listed in the file I mentioned. Thanks though anyways

---

### Post by justleen on 2007-04-12
does the file you have contain the full path, or just the file names?

---

### Post by justleen on 2007-04-12
sorry lad, i had a bad nights sleep, and im @work.. recipe for misinterpertation..

try this on for size
cat file.lst |while read line; do cp "${line}" /driveB/backupdrivepath ; done

---

### Post by orb9220 on 2007-04-12
Does tar do ntfs? I know for a fact that I cannot backup to a fat32 partition.
Tar does not support backing up to fat32 due to not being able to set date,and file permissions.

Don't know about ntfs?

---

### Post by AtrejuT on 2007-04-12
you could also consider rsync which AFAIK can take a file containing a list of files to be copied, but I don't know the exact syntax right now.

---

### Post by poscogrubb on 2007-04-12
Hi. Take a look at the man page for **xargs**. It takes as input a list of files and then executes a command (which you supply) for each file. Actually, the input is a list of arguments, not necessarily filenames. Let us know how it goes...

---

### Post by poscogrubb on 2007-04-12
For example, if your list of files is in "my_list.txt", try this command:

cat my_list.txt | xargs -I {} cp {} /whatever/the/destination/is

Disclaimer: read the man page, and try it on a small batch of test files first!

---

### Post by octoberdan on 2007-04-12
> **AtrejuT said:**
> you could also consider rsync which AFAIK can take a file containing a list of files to be copied, but I don't know the exact syntax right now.

Can I use rsync locally?

Thank you all for the response. I'd use xargs, but that doesn't solve my problem of needing to recreate directory structure... or does it? Is it possible to copy ./bar/baz/foo.qux to /media/usbdisk/ and have /media/usbdisk/**bar/baz/ ** created automatically?

---

