---
title: "[SOLVED] deleting user home folder"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Xoanan on 2007-06-29
Hi All

About a month ago, I had to deleted one of the profiles; the process did not delete the users home folder, which doesn't surprise me in particular.  

Would there be any harm in deleting that users home folders with all of its contents?

---

### Post by Seisen on 2007-06-29
As long as you don't use that user anymore, I don't see a problem with that.

---

### Post by kleo skywalker on 2007-07-22
I deleted a profile, but now I can't delete the user's home folder. The msg I get is that I don't have permission to do it. How do I delete it?
Thanks.

---

### Post by girard on 2007-08-13
same here. i was successful in removing the Desktop and Examples, and all it's contents, but the hidden folders are stubborn. already chmod the folder to 0777, but it's still there. apparently, what we should have done was to use deluser .... <after five minutes>

ok i got it. if we have the same scenario, we deleted the account in the GUI, so the home folders were left behind. i recreated the user.  and then i ran:

```

sudo deluser --remove-all-files

```

this successfully removed all files owned by that user. but i would think that you'd have to be careful to make the duplicate user exactly the same - that's what i did - username, name, password and all.

you might not want to remove all the files associated to that user, so you might opt for the --remove-home option only.

see man deluser for details. 

hope this works for you.

---

