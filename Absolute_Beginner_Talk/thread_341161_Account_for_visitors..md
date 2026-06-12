---
title: "Account for visitors."
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Oki on 2007-01-18
Hi

I want to make a new account for visitors, so I can have my privacy. I just want people how want to use the Internett, write, listen to music or whatever to be able to use the computer. 

But I dont want to give the visitor a password, I just want them to be able to click the &#8220;Visit&#8221; account and then get logged in. If I give them a password they would need to ask for it each time, and then(I guess) they could use the Sudo command witch I dont want them to. And I also dont want to share bookmarks, history and so on with my account.   

Is this possible? When lokking at the System>Administration> Users and Groups I have to set a password for this new account. 

Thanks for any help

---

### Post by apunc1 on 2007-01-18
i think you have to set up a password for the visitor account but you can set it to automatically login so they won't have to enter it each time.

---

### Post by taurus on 2007-01-18
Why not create an account guest with the same password guest.  That way, they have their own $HOME directory and you have your own $HOME directory.  And if they don't belong to groups adm & admin, they can't run sudo, period.

---

### Post by Oki on 2007-01-18
I did think about the automatically login option, but when you have two accounts, men and the visitor, then it wouldn’t go (as I understand it). 

I will go for taurus suggestion, perhaps stick a post-it in front of the screen with the password for visitors on it. 

“And if they don't belong to groups adm & admin, they can't run sudo, period.” 
Ok, good to know – I guess I can find these options under “Users and Groups” dialog. And then I could test to be “a visitor” in the new account.


Thanks again for you help :-) 


This forums is so good!!

---

### Post by taurus on 2007-01-18
Just tell that person the login name is the same as the password.  And if you want to disable that account later, you don't have to remove it.  Just lock it in /etc/passwd.

---

### Post by Oki on 2007-01-24
Hmm

I have made one more account witch are going to be for “visitors”. But there is one problem; The language on my Ubuntu is English cus thats makes it easier for me to read/understand tutorials/guides and so on. But I am from Norway, and want to spell “Visitors” on Norwegian, witch is “besøk” - but Ubuntu will not take the letter Ø. I could(perhaps?) install the Norwegian language pack but I have read that those can make the system buggy... Is there a solution on this?

---

