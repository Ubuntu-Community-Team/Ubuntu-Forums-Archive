---
title: "How do I verify .ISO in Windows?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by henkk78 on 2006-06-02
I've downloaded the Kubuntu ISO. I've burnt it to CD and booted off it, but the CD check failed and it also wouldn't boot into live mode or install. 

Before I try burning onto another CD, how would I verify the integrity of the ISO? 

I know it has something to do with MD5 Checksums, but I'm clueless as to what to do. 

Please note I'm using Windows.

Thanks,

Henk

---

### Post by lapsey on 2006-06-02
[http://losrivas21.blogspot.com/2006/04/how-to-verify-md5-checksum-of-ubuntu.html](http://losrivas21.blogspot.com/2006/04/how-to-verify-md5-checksum-of-ubuntu.html)

---

### Post by Almighty on 2006-06-02
download MD5summer and run the software. It will verufy if the MD5 checksum is correct.
[http://www.md5summer.org/about.html]("http://www.md5summer.org/about.html")

---

### Post by henkk78 on 2006-06-02
No luck so far. The blogpost refers to a context menu that doesn't even come up.

I have no idea how to use MD5Summer. 

Henk

---

### Post by henkk78 on 2006-06-02
Okay, I've managed to use FastSum to CREATE an md5sum of the ISO. 

Now what?

---

### Post by henkk78 on 2006-06-02
Figured it out! 

For anyone who comes across this post, here's how to do it:

1. Download the ISO
2. Use FastSum or MD5summer to CREATE an md5sum of the ISO. (Note: an md5sum is sort of like a 'key')
3. Look at the file MD5SUMS that you will find at the bottom of the page from where you downloaded ubuntu or kubuntu
4. That file MD5SUMS will list a whole bunch of MD5 'sums' or 'keys'
5. Compare the md5sum you created with the one displayed on the MD5SUMS page.
6. If they're the same, your ISO is fine and ready for burning! If they're not the same, burn again!

Good luck!

Henk

---

### Post by Irony on 2006-06-02
md5summers don't create the sum of the .iso - they read the md5 sum which you then compare to the sum published.

---

### Post by user1397 on 2006-06-02
Just follow this guide: [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

