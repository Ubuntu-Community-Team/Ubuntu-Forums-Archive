---
title: "For those who can't go online"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Mitchlb on 2008-01-25
I don't need help getting online. I'm getting a network card compatible with my 802.11g connection. What i do need, is a way to get files in the meantime.

How to i get programs i could easily get with synaptic. What's the way to go? I tried tarballs (THOSE SUCKED. THEY TAKE FOREVER FOR NO REASON). and i tried .debs..... Better, but it's harder to find them. Any suggestions???

---

### Post by antisocialist on 2008-01-25
debs are easy, just search the debian an ubuntu repos and you will find them in no time
btw, in linux it is a package, not a program

---

### Post by ugm6hr on 2008-01-25
There are ways to get Synaptic packages on your computer:
[http://ubuntuforums.org/showpost.php?p=4202237&postcount=31](http://ubuntuforums.org/showpost.php?p=4202237&postcount=31)

---

### Post by ajgreeny on 2008-01-25
If you know someone else with ubuntu get them to download aptoncd, download the packages you want and then run aptoncd.  This will produce an iso file which they can either burn to cd or just copy to you as the iso.  If the former I think the CD will contain the extracted files they had in their /var/cache/apt/archives folder, not still as the iso but extracted.  If it is still just the iso file, no problem, you can just extract the contents by mounting it as follows.
1  Make a directory to mount to with ```
md /home/username/iso
```Now extract the iso with ```
sudo mount -o loop -t iso9660 <filename>.iso /home/username/iso
```You will now have all the packages from the iso your friend gave you in the Packages subfolder of the folder you just made, and you can use dpkg to install the ones you want.  I suggest you start by installing aptoncd yourself and then run it, pointing it to the iso file again.  After that you will be able to use synaptic as if connected to the internet yourself.

---

### Post by mikewhatever on 2008-01-25
> **Mitchlb said:**
> I don't need help getting online. I'm getting a network card compatible with my 802.11g connection. What i do need, is a way to get files in the meantime.

How to i get programs i could easily get with synaptic. What's the way to go? I tried tarballs (THOSE SUCKED. THEY TAKE FOREVER FOR NO REASON). and i tried .debs..... Better, but it's harder to find them. Any suggestions???

Have you tried [http://nonetdebs.homeip.net/?](http://nonetdebs.homeip.net/?) It seems like a good solution, and I'd appreciate a fit back if you do try it. Don't want to recommend something that might not work.

---

### Post by Mitchlb on 2008-01-25
Um... How do i search the debian/ubuntu repos?

---

### Post by Mitchlb on 2008-01-25
Oh, and i don't know anyone else with Ubuntu... Probably should've said that first.

---

### Post by Mitchlb on 2008-01-25
Thanks mikewhatever and ugm6hr. I just checked out [http://nonetdebs.homeip.net/?](http://nonetdebs.homeip.net/?)
It's really helpful. I think that's all i need.

Though, How do i search the debian/ubuntu repos? I've never heard of them. (Not saying much since i'm new to Ubuntu (though not linux)).

---

### Post by rosegarden78 on 2008-01-25
If your computer needs drivers or restricted files, and you can't connect with wireless because it needs restricted drivers, you can still connect to your modem router with an Ethernet cable.

Otherwise you can download the .deb package from Canonical repositories from your local library or Internet cafe.  Good luck!  P.S.  I had to download the fw-cutter package and save it on my Windows FAT32 partition so when I upgrade, I always have a way to install my wireless.  You can always dual-boot a Windows/Mac partition handy just in case something fails and vice versa.  Never good to keep all eggs in one basket!

---

### Post by Het Irv on 2008-01-25
To search for packages, Open Synaptic Package Manager and use the search feature.  You can also use the Firefox add-on Ubuntu Package Search.

---

### Post by Mitchlb on 2008-01-25
Um... People aren't reading the origional post.... The last two posts didn't address my problem at all....

---

### Post by Mitchlb on 2008-01-25
Oh, actually, 2 ago sorta did. sorry. But the last one didn't.

---

### Post by Mitchlb on 2008-01-25
**The following is from [http://nonetdebs.homeip.net/?q=node/add/status_file&destination=user%2F160](http://nonetdebs.homeip.net/?q=node/add/status_file&destination=user%2F160) **

Submit Status file from target

Select the status file you have brought from the target computer. This file is located in /var/lib/dpkg/status. Generally is is a small file (1 to 5MB, maybe more depending on how much packages you have installed on the target computer. Copy it to a media of your choice (email, USB memory, CD, whatever), rename it to status.txt and select it here for upload.
status_upload
Changes made to the attachments are not permanent until you save this post.
Attach new file:
Please rename the status file to status.txt to be able to upload it. Select it and click "Upload", then "Submit" at the end of this page.
Allowed extensions: txt

**Um... I'm doing this on an xp run computer, because my internet is down, would this still work?**

---

### Post by ugm6hr on 2008-01-25
> **Mitchlb said:**
> **Um... I'm doing this on an xp run computer, because my internet is down, would this still work?**

Yes. Copy the file from your Ubuntu machine to a USB, rename it to status.txt.  Then upload from the Windows machine.

I have used nonetdebs, and it works well.  However, I did find that when trying to use it with a fresh Ubuntu install which had never had its sources updated it didn't seem to work properly.  That was a one off, and I haven't been in that situation since.

---

### Post by Mitchlb on 2008-01-26
k. Thanks for the heads up. I think it's working fine.

---

