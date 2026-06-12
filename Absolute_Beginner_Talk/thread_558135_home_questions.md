---
title: "/home questions"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by tolremeno on 2007-09-23
I've got a few very easy questions that I couldn't quite find the answers to, even though the topics are common enough.

- if you have a separate /home partition and you want to go from feisty to gutsy, do you just install over feisty, or do you reformat that partition first?

- then if you want to go back to feisty or forward to the final 7.10 release, is it wash, rinse, repeat? is upgrading from the alpha or beta to the final even possible?

- once you have your new os with your old /home partition, how does the os know about the /home partition? do you just change the new user's home directory to /home/username, or do you just have to give your new user the same name as your old username? or I guess you have to remount the home partition at /home first?

Thanks!

---

### Post by cmnorton on 2007-09-23
I don't think OS-specific stuff is installed under /home. You would probably upgrade anyway over re-installing.

---

### Post by Lord Illidan on 2007-09-23
> **tolremeno said:**
> 

- if you have a separate /home partition and you want to go from feisty to gutsy, do you just install over feisty, or do you reformat that partition first?


You just mount that partition as /home with the Installer. No need to reformat.

> 
- then if you want to go back to feisty or forward to the final 7.10 release, is it wash, rinse, repeat? is upgrading from the alpha or beta to the final even possible?


Well, it is, but I'd beware of doing it too often, as the new applications will store configuration files in your home directory, which might lead to glitches or even things not working, or settings being erased. Upgrading from the alpha to the final is usually just a matter of staying upgraded, and waking up one day to find you're running gutsy final!

> 
- once you have your new os with your old /home partition, how does the os know about the /home partition? do you just change the new user's home directory to /home/username, or do you just have to give your new user the same name as your old username? or I guess you have to remount the home partition at /home first?
Thanks!
Mount the home partition at /home first, and yes, keep the same username.

---

