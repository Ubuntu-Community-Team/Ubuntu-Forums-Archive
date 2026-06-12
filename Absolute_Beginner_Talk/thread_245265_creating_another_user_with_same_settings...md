---
title: "creating another user with same settings..?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by juicymixx on 2006-08-27
Hey everyone,  after a couple of weeks, I have my Dapper install looking/acting like I want it to.   Now I'd like to have my wife give it a try.   I noticed when I create a new user that the new user doesn't have any of my customizations (like SLAB menu, different background, access to some programs, etc.)   Is there some quick way to get my wife's account up to speed without having to try to retrace my customizing steps?   Kind of like clone the preferences of my user account for her?

Thanks!:???:

---

### Post by editrix on 2006-08-28
Just a thought: Since all your personalizations and customizations are kept in your home folder, what about copying that to her home folder? I'd make a backup of her home folder before you try this, just in case.

---

### Post by aysiu on 2006-08-28
Try this: ```
sudo cp -R /home/juicymixx/* /home/juicyswife
sudo chown -R juicyswife:juicyswife /home/juicyswife
```

---

### Post by juicymixx on 2006-09-03
Thanks aysiu,

This mostly worked!   There are a few preferences that are odd or didn't work at all, but for the most part this did it!:mrgreen:

---

### Post by jalanbuntu on 2006-09-03
See this post [http://ubuntuforums.org/showpost.php?p=1458363&postcount=2](http://ubuntuforums.org/showpost.php?p=1458363&postcount=2)

---

