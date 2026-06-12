---
title: "[SOLVED] Partition, Bad Sector"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by siciliancasanova on 2007-03-08
Hello, I'm new to Ubuntu/Linux and have spent the last 24 hours trying to figure out my problem.

Thanks in advance to any responses to this problem.  I really like the community here and the response time I see on posts.

I'm running Windows XP and want to do a dual boot with Ubuntu.

I have never partitioned before so the manual route seems a little daunting.

I load Ubuntu fine off the disk and start the installation, I get to the partitioning part.  If I make the first selection of the auto partition, it just sits there with the load icon.  From what I understand on the forums this should take only a couple of minutes.  

I did the defrag.

When I manually try to resize the NFTS partition, I am receiving the error that there is 1 bad cluster on that partition.

I downloaded and ran the latest version of Gpartition like I saw in the forums.  I didn't try to resize anything with the gpartition.  I only ran the check on the partition and it gave me the same message.  There is 1 bad cluster or sector in my partition.  

I have ran chkdsk several times and rebooted the machine several times after each chkdsk and the problem continues to persist.

I did notice that there was a suggestion in Gpartition, after running chkdsk several times to override the bad cluster when I do the resize.

I'm not really sure how I begin to go about this or if there is a way to override this.  Like I said, I've never manually partitioned anything before and although it doesn't seem terribly difficult, I'm still treading carefully.

Thanks again for any help.

---

### Post by overdrank on 2007-03-08
> **siciliancasanova said:**
> Hello, I'm new to Ubuntu/Linux and have spent the last 24 hours trying to figure out my problem.

Thanks in advance to any responses to this problem.  I really like the community here and the response time I see on posts.

I'm running Windows XP and want to do a dual boot with Ubuntu.

I have never partitioned before so the manual route seems a little daunting.

I load Ubuntu fine off the disk and start the installation, I get to the partitioning part.  If I make the first selection of the auto partition, it just sits there with the load icon.  From what I understand on the forums this should take only a couple of minutes.  

I did the defrag.

When I manually try to resize the NFTS partition, I am receiving the error that there is 1 bad cluster on that partition.

I downloaded and ran the latest version of Gpartition like I saw in the forums.  I didn't try to resize anything with the gpartition.  I only ran the check on the partition and it gave me the same message.  There is 1 bad cluster or sector in my partition.  

I have ran chkdsk several times and rebooted the machine several times after each chkdsk and the problem continues to persist.

I did notice that there was a suggestion in Gpartition, after running chkdsk several times to override the bad cluster when I do the resize.

I'm not really sure how I begin to go about this or if there is a way to override this.  Like I said, I've never manually partitioned anything before and although it doesn't seem terribly difficult, I'm still treading carefully.

Thanks again for any help.

Hi maybe this thread could help you. Good luck
[http://www.ubuntuforums.org/showthread.php?t=360784&highlight=partition+bad+sectors](http://www.ubuntuforums.org/showthread.php?t=360784&highlight=partition+bad+sectors)

---

### Post by siciliancasanova on 2007-03-08
It seems as though after searching the above thread the best thing to do would be to just repair that sector.  Since chkdsk doesn't do it, does anyone have any suggestions for a free program that will repair this.  If there are any?

---

