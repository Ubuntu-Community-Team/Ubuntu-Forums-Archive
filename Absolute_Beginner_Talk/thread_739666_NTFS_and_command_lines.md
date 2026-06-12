---
title: "NTFS and command lines"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by jcasemd on 2008-03-29
I am totally new to linux. I loaded Ubuntu (Hardy) onto an older computer and am wanting to try to use it as a music server. My music files are on a portable hard drive formatted in NTFS (of course). I searched for what to do and downloaded a program ntfs-3g-1.2310.tar and loaded it onto my linux computer. The directions say to type the following commands: ./configure, make, make install. 
However, I am not even sure how to start entering commands. I went to 'terminal', attempted to change directories to the one I had loaded the program into (cd /home/j/Documents) and this worked. The I tried typing ./configure. Nothing happened. Then every permutation I could think of (eg ntfs-3g-1.2310.tar./configure, etc.). I have no idea what I am doing because nothing works. Help!

---

### Post by ad_267 on 2008-03-29
You shouldn't need to do anything, Hardy Heron can read and write to ntfs by default. The package ntfs-3g should already be installed. If you open up the synaptic package manager and search for ntfs-3g it should be there.

Edit: But if you did want to compile this you would need to first extract the files from the tar archive. To do this you would type "tar -x ntfs-3g-1.12310.tar" or just right click on it in the file browser and select extract and then you could type ./configure etc. You would also need to install the build-essential package which contains a compiler and other required software. **But you don't need to do any of this as ntfs can be read and written to by default**

---

