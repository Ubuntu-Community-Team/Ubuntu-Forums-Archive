---
title: "Building Ubuntu File Server for Home Win Network"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by wildsnail on 2007-07-01
I recently bought a laptop as my wife and kids are hogging the desktop far too much and I've set up a workgroup so that I can access files on the desktop. But I'm finding it annoying that both machines have to be on as we tend to boot up and shutdown as we need to use the desktop rather than leaving it on. So I'm thinking of building a simple file server using older hardware that I can hide away and leave running and use VNC to control it (as I have most of the parts, this will work out cheaper than buying a NAS box).

I have an empty hard disk on which I can install Ubuntu but I would also like to remove the 2nd disk from my desktop and use this in the file server as well. This is a 250GB drive formatted with NTFS which already has a lot of data on it which I don't want to lose but I do want to share. So, do I need to convert the drive to another file system in order to read and write? Also, where should I mount this drive in the linux file system - under /mnt ?

TIA.

---

### Post by chamberlain2006 on 2007-07-01
Wow, nice idea.  My preferred method of doing this would be to use FTP.  It will be a lot easier to explain the whole process once you've gotten it all set up.

---

### Post by ayenack on 2007-07-01
Hello wildsnail (love that name). Take a look at this [site]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") and scroll down to Servers 1.22 from here there are instructions on how to build many different servers. SAMBA might be a good option for you.

Best of luck. ayenack.

---

### Post by Raineer on 2007-07-01
If you are serious about the "hide away" part of being a file server, checkout the link in my sig for setting up a FreeNAS system. You could keep your NTFS data intact, but it would be _safer_ in my opinion to move the data off and back on if you can spare any temp space, just to get it in a more linux-friendly format.

---

### Post by wildsnail on 2007-07-02
Thanks for the advice, guys. I've been reading the Ubuntu Guide and a few posts here and I felt pretty confident about setting up Ubuntu with Samba although I don't think I'd keep the drive as NTFS as a few people are have difficulties and I've got enough new things to learn without risking the project on something potentially frustrating.

BUT all this has changed since I took a look at FreeNAS - cheers Raineer, this looks perfect :D I'm downloading this now and all I'm waiting on is a CPU as I have all the other comps ready and waiting. Hopefully I'll be ready to try it out next weekend.

---

### Post by P86 on 2007-07-09
Here is the link I used to set up FreeNAS:

[http://www.howtoforge.com/network_attached_storage_with_freenas](http://www.howtoforge.com/network_attached_storage_with_freenas)

Installation was really simply, and the webGUI is fairly intuitive. I had some initial problems that turned out to be file corruption, and had nothing to do with FreeNAS. I haven't fully put the box to the test, but so far everything has been good. 

I would also suggest you convert your NTFS drive to UFS. FreeNAS warns that using any other filesystem may cause corruption (unlikely, but still scary).

Let us know how things are going.

---

