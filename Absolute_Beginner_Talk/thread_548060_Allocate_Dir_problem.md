---
title: "Allocate Dir problem"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by capera on 2007-09-10
I am having a problem.....and would appreciate some help.

When I execute a torrent file and point the download location to a directory on my HD, I get this error :


Could not allocate Dir
[Errno 30] Read Only file System


It is my guess I have to change permissions on my drive but now sure how to do this. I have opened my "Places" folder and brought up the properties on my drive, and can see where you change permissions from "read Only" to "Read and Write".......but it will not let me. It says it cannot change the permissions.

Can someone help?

---

### Post by diatribe on 2007-09-10
is the drive formatted in ntfs?  if so you will need to install ntfs-3g from the repos

---

### Post by Maestro23 on 2007-09-10
Have you tried saving it in your [COLOR="Red"]/home/username[/COLOR] dir?

---

### Post by capera on 2007-09-10
> **Maestro23 said:**
> Have you tried saving it in your [COLOR="Red"]/home/username[/COLOR] dir?

It works to this directory......but it is another drive that I want to save it to (a NTFS drive)


What is ntfs-3g from the repos?

---

### Post by diatribe on 2007-09-10
you need to open synaptic package manager, it is in your system->administration directory, and search for ntfs-3g and ntfs-config I believe, these will allow you read/write access to ntfs drives

---

### Post by Maestro23 on 2007-09-10
> **diatribe said:**
> you need to open synaptic package manager, it is in your system->administration directory, and search for ntfs-3g and ntfs-config I believe, these will allow you read/write access to ntfs drives

Yeah, use this.  Here is the site for it so you can read about it: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

---

### Post by James.Dedon on 2007-09-10
NTFS 3G works good as long as you are reading and writing from Ubuntu, but if it's an external drive and you use it with both linux and windows you might run into some problems with windows not reading the files that you wrote (even though they show up with Ubuntu).  Your best bet is to back up the disk and reformat it into a FAT file system that is easily read and writeable with Linux and Windows without any add-ons.

---

### Post by capera on 2007-09-10
Thank guys   

:)

---

### Post by Maestro23 on 2007-09-10
> **James.Dedon said:**
> NTFS 3G works good as long as you are reading and writing from Ubuntu, but if it's an external drive and you use it with both linux and windows you might run into some problems with windows not reading the files that you wrote (even though they show up with Ubuntu).  Your best bet is to back up the disk and reformat it into a FAT file system that is easily read and writeable with Linux and Windows without any add-ons.

Yeah, I have a share partition formatted in FAT. Jjust beware of the 4GB file size limit on FAT32.

---

