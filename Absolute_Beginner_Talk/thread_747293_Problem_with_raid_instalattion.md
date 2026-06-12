---
title: "Problem with raid instalattion"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by rgotten on 2008-04-06
Finally i am ready to install ubuntu server edition and even though the motherboard is raid enable evidently is a fakeraid and will not work under ubuntu. After researching is my impression the the sofware raid will work well and even sometimes it is better than the hardware and less expensive. This is  my question in the event i need to buld from a crash ( i will still make backups of the server), But in regards to the raid this are my questions:

Originally i was going to do a raid 5, but then reading all over the internet found that i should have to do boot in raid 1 and the rest for storage in raid 5, so if the boot section is damage i can still boot up. I have (3) 500 gb hd then:
        a) how big should the boot partition be for the raid 1? 
        b) Since i have the 3 hard drive, should i have the same boot partition areas on each of this 3 hd? and can this 3 partiton be on read 1 
        c) can i have raid 1 in this 3 equal size partitions, and then do the rest of the partition for each one of the hd for the raid 5 so evrything is on equal sizes?

Remember i am completely new to Ubuntu server, and instructions will be well apreciated

Thanks rgotten

:guitar:

---

### Post by Repus on 2008-04-09
[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

This is not a perfect match to your questions but it is more information along the lines of what you are looking for, I just did my first linux software raid a few months ago and found this article to be very clear and easy to follow. Again, it isnt quite what your looking for but my guess is it may help you. I think it will answer at least two of your questions.

---

