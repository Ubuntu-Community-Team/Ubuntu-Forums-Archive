---
title: "Installing"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by B_Ran on 2008-03-19
Im trying to install ubuntu on my computer from the Live cd
When I go to install I get to the step where you select a partition to install it on but then it doesnt let me proceed
I have two partitions as of now, C: and D: in windows and I can tell which is which from the amount of space left
When I select the what would be D: partition it tells me it cant because theres no root directory

Can anyone explain to me what I need to do to make Ubuntu install?

And also, after I do get it installed, how do I make it so Ubuntu loads up when I turn my computer on instead of Windows? and whats the button when you turn on your computer so you can pick either or?

Sorry if this is a lot in one post, but thanks in advance!

---

### Post by alzie on 2008-03-19
[COLOR="Blue"][http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")[/COLOR] 
Is a good guide to doing a dual boot.

When you boot up you'll get a Grub Menu which will give you the choice of OS's

Hope this helps :)

---

### Post by B_Ran on 2008-03-19
That guide answered most of my questions about Dual Booting, thanks : >.
BUT im still confused about the partition thing
I already have two but it wont let me use one 
and I dont want to use that resizing tool because I dont want to mess with my Windows partition if I can help it : /

Any more ideas?

---

### Post by sowelie on 2008-03-19
If you're going to use the second partition completely you need to delete it and create an ext 3 and swap partitions with the freed space.  Gparted is pretty reliable but I would definitely back up your stuff if you can first.

---

### Post by B_Ran on 2008-03-19
Ah this is starting to get intimidating to me.
Can I do all of this from Gparted?
If someone knows a guide to this, that would help tremendously
Im kinda hesitant to do this because I have no way of backing up info on my Windows parition, and if my Windows partition gets messed up ill be in a hole : /

---

### Post by sowelie on 2008-03-20
I found a pretty good video that shows how to use gparted.

[http://video.google.co.uk/videoplay?docid=-2369893842637434537]("http://video.google.co.uk/videoplay?docid=-2369893842637434537")

---

