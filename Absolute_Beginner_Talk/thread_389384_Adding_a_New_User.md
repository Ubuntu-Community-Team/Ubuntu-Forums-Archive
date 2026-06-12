---
title: "Adding a New User"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by JimmyTheSaint on 2007-03-20
Hi

I am fairly new to Linux and have thus far managed to install Edgy, configure my wirless setup and access Windows shares on another computer and get Mp3's working. My problem is in trying to add another user. After I add the user through the System -> Administration -> Users and Groups option and try to login as that user the Mouse and Keyboard are completely unresponsive. Also the prompt for a password to access the Wireless network does not happen either.

I have had a bit of a scout about but I can't seem to find anything that indicates where I might be going wrong. Everything seems AOK whilst logged in as me (user I installed Ubuntu with).

If it's of any interest I have installed on a Compaq Evo N800v laptop.

Thanks

James

---

### Post by Dr. Nick on 2007-03-20
I am on windows now so cant be to specific, but it sounds like your new user is not a member of the correct groups. Log in as your default/working user and go to the user&groups configuration dialog and look to see what groups your working user is in and then add the non working user to them. I imagine that will solve your problems.

---

### Post by zvacet on 2007-03-20
[https://help.ubuntu.com/community/AddUsersHowto?highlight=%28add%29%7C%28user%29]("https://help.ubuntu.com/community/AddUsersHowto?highlight=%28add%29%7C%28user%29")

---

### Post by JimmyTheSaint on 2007-03-21
Hi

I will check out the groups setup again - I did think of that and was sure they were the same but maybe I missed something.

I did follow the guide on setting upa new user by the way so that link doesn't really tell me anything that's going to help with this particular problem.

Thanks

James

---

### Post by JimmyTheSaint on 2007-03-22
Hi

I have checked the Group membership on this and ensured that my user and the new user are in the same groups (only admin and specific name of login anyway). Still any additional login I set up will not work as the mouse and keyboard are unresponsive.

Can anyone give me any other help on this, are there any file permissions I could check that may mean something is not being run at startup by another users login that is during mine? I've been scouring the internet for clues but I am draing a blank so far. :confused: 

James

---

### Post by seshomaru samma on 2007-03-22
I had the same problem with a Xubuntu machine but unfortunately couldn't find a solution.
One thing you can try to do is assume that there is a bug in the GUI application that adds user and add a user with the command line. It might work. I haven't tried . I switched to Debian

---

