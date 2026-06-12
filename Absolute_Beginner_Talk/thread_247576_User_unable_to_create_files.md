---
title: "User unable to create files"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by goSteelers on 2006-08-30
I have recently installed PHP and I am having trouble creating files.  I am able to create a file if I am root but not as a user.  I have added myself to the 'www-data' group and it still doesn't work.  I have also used root to try and change the permissions to the directory, but nothing.  Does anyone have any ideas?  Thanks.

---

### Post by grimmson on 2006-09-01
Since your a first cup user I'm going to ask some insulting qusetions and hopefully you won't be insulted. Whats your user id and group (system>admin>users & groups)? Secondly are you creating a folder in your home folder or elsewhere on the drive? Last insulting question, who's the group/owner of the folder your trying to create a folder in?  If sudo can do it and you can't it sure seems like a permission's problem or a big piece of the puzzle is missing. Have you created any/several different users? Are you shareing a drive between distros?

---

### Post by goSteelers on 2006-09-02
Thanks for your reply but I finally managed to figure it out.

---

