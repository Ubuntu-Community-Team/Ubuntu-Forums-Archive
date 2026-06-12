---
title: "ipod+amarok problems"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by szac9 on 2008-04-16
Hello,
Up until recently I decided to clean out my amarok collection that was full of duplicate files and folders. This turned out to be successful and my collection was finally organized.

However, problems came shortly after:
1. Pressing the disconnect button in amarok does not disconnect my ipod from amarok

2. Pretty much all of my music has the same album cover (Let it Bleed by the Rolling Stones) which is kind of funny because...

3. My music from R to Z will not sync with the ipod (Rolling Stones on). I will place it in the queue, hit the transfer button, and it will claim to have succesfully made the transfer. Then upon closing amarok and ejecting the ipod, the music I supposedly transfered is not on there.

I have over 4000 songs but my ipod will not let me upload more than 3023.

I feel I may have done damage when I forced amarok to abort an earlier upload and didn't give it adequate time to flush.

In addition, I've been getting the message about iTunes Control Lock needs to be removed.

I feel like a mess. Please I need help, with any of this. Thank you so much!

---

### Post by philliptweedie on 2008-04-16
1. Pressing the disconnect button in amarok does not disconnect my ipod from amarok

I'm not too sure about your other problems but Amarok is configured to eject devices in kde and not gnome so the command is wrong.  (I'm just assuming you're using Ubuntu and not Kubuntu)

It's in the device settings as post-disconnect command. You need to change it. There are other threads here about it, just search for "post-disconnect command" should get you some more info.

Unfortunately I was never able to get it to work with my ipod.

Good Luck

P.S. I vaguely remember one of the proposed disconnect commands included a rm something command which helped remove the ipod lock (I think!). Don't hold me to that but it may end up killing two birds with one stone so to speak.

---

### Post by Tom--d on 2008-04-16
I have an Ipod and when I press Disconnect it disconnects from amarok, not the pc then after you can just right click the ipod and press eject. 

With the album cover, thats easy to sort out. 
Go to your music collection in natulias (gotta learn how to spell it xD) then to the picture. It will be there somewhere.. its not hidden, well, it shouldn't be. Just in case. Press CTRL + H in the music folder. My guess its in the rolling stones folder. Once you have found the picture. Delete it. (There might be more than one. Delete them all).

Update collection in Amarok and the picture should disappear :)

---

