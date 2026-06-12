---
title: "Gparted how do I use unallocated space"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-04-13
New to Gparted, I've resized my XP partition to allow more space for my Linux partition.  The resizing of the XP partition appears to have worked ok and I'm now left with 70 GB of unallocated space which I want to add to the Linux partition. How do I go about this please. 

I've added two images of before the XP re-partition and another showing it after I've resized the XP partition. 

[ATTACH]29634[/ATTACH]

[ATTACH]29635[/ATTACH]

---

### Post by Seisen on 2007-04-13
You should be able to take all that unallocated space and add it to your linux partition. Try to resize you linux partition and see if it will add it to it.

---

### Post by laidback on 2007-04-13
Suggest you move your /dev/hda2 to the left to occupy the space, then resize hda2 to take up the extra space, which will now be on the right of hda2. If you have any space left over it can just sit there until you need it. Or you could move the swap partition to the left as well leaving the unallocated space on the rhs. BACKUP precious files first. And remember that you can only alter unmounted partitons, so use Ubuntu Live of Gparted Live, but you probably know that already.

I have a question, how do you get those screen shots in your post?

---

### Post by a.v.l on 2007-04-13
> **a.v.l said:**
> New to Gparted, I've resized my XP partition to allow more space for my Linux partition.  The resizing of the XP partition appears to have worked ok and I'm now left with 70 GB of unallocated space which I want to add to the Linux partition. How do I go about this please. 

I've added two images of before the XP re-partition and another showing it after I've resized the XP partition. 

[ATTACH]29634[/ATTACH]

[ATTACH]29635[/ATTACH]

Thanks for the information I'm in the process of resizing the Ubuntu partition as I write.  To get the screen shots I took the image using a camera, resize it and saved it to the desktop of another PC. To add it to my post I click on the attachment icon as can be seen above this post (in the tool bar)  Its the one to the right of the smily face black and white in colour, then search for the image on your desktop, select it and upload it. Once this is done left click on the arrow to the right of attachment icon and choose the image to attach. Make sure the curser is where you want the image to appear on the page. The image will not show up in your message but a reference to it will, when you send the post the image will appear with it.

Just realised the toolbar can't be seen when the post has been sent. You will see it when you start a post to the list though.

---

### Post by a.v.l on 2007-04-13
> **Seisen said:**
> You should be able to take all that unallocated space and add it to your linux partition. Try to resize you linux partition and see if it will add it to it.

I did as you suggested and it worked fine, I now have both partitions resized as I had hoped and without a loss of data, plus I found out how to use Gparted brilliant, many thanks.

---

