---
title: "Macbook with Cinema Display Blank Video Issue."
date: 2010-07-17
forum: Apple Hardware Users
---

### Post by hyper84 on 2010-07-17
Hello all, I just installed Lucid on a Macbook circa 2007 and it is working beautifully now that the sound and bluetooth mouse issues are fixed thanks to the members of this forum. I was surprised how easily my network printer was to install too! However, I do have one issue that I was hoping the experts could help me with. Hence, here I am. I have a 20" Cinema Display connected to my Macbook, and it works well but when I play a movie file, the sound works but the video is blank inside Movie Player. I can turn the Cinema Display off via the Monitors menu and the movie reappears in Movie Player. Everything else works fine, the video just goes blank when the Cinema Display is running. Does anyone have any ideas? If you need more information just let me know, and thank you so much for your help.

---

### Post by davidryderuk on 2010-07-17
Hi,
You need to check what graphics processor you have by running the following command in terminal.

```
sudo lshw -short
```

If you have one of the "intel GMA 950" graphics cards (which was in one of two Macbooks sold in 2007) then your computer is likely to have the same bug as my netbook.

In my case I can get the video to work on the external display by opening up the Monitors menu and arranging the screens vertically (i.e. drag the second display around so that it is located above the first).

---

### Post by hyper84 on 2010-07-20
Thanks a lot your workaround worked for me. I also tried setting up to use the external display only with the laptop display off, but my external display looked like it was seizing for lack of a better term. My external display will also do that with OSX sometimes when I plug the display back into my macbook. In OSX it requires a restart to fix it, but I don't know how to fix a seizing monitor in Ubuntu sadly.

---

### Post by davidryderuk on 2010-07-21
I'm glad you have some way of getting the video to work. 

The seizing display is reported elsewhere, however there doesn't seem to be many fixes suggested other than restarting the computer with the lid closed. In addition unlike the video problem, this one seems to be fairly specific to macbook owners.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/377598](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/377598)

> 

I have found the solution to this tiring problem. I am running the final Ubuntu 9.10 on a MacBook 2,1 and I can successfully fix this issue with a 100% success.

You need to do the following (remember to disable mirrored monitor first):
1. Plug in your external monitor
2. Start your MacBook and start boot into Ubuntu
3. Close the lid of your MacBook
4. You have now booted in and logged in (the flickering is now present)
5. Now, restart your machine and boot into Ubuntu (DO NOT OPEN MACBOOK LID!!)
6. Your now booted into Ubuntu again, the flickering is gone!

This I am able to do with success.

I have an SyncMaster 226BW and my MacBook is a revision 2,1.

I hope this helps others as well as it helped me!


---

