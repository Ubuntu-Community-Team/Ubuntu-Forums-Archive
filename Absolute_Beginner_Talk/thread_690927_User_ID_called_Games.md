---
title: "User ID called Games"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by cforput on 2008-02-08
I wanted to create a user ID for my kids so they can play games. I thought a great ID for this would be called games. I went in and tried to add it and received an error message that the user ID already existed. It doesn't show up in the user list and I know I never added a user ID called games in the past. 

I tried logging in with the ID but it asked for a password. I tried a few but no luck.

Anyone have any idea what is going on here?

thanks

---

### Post by talsemgeest on 2008-02-08
Same thing happens on my box. Use "game" instead of "games"

Hope this helps :)

---

### Post by cforput on 2008-02-09
I went onto IRC chat in #ubuntu and found the answer for those of you who are curious. In Gusty (not sure if this is true of earlier versions because I am so new to Ubuntu) if you go to the etc/ directory and then edit the passwd file, all users that have a number lower than 1000 are system users. The games id is apparently used more for groups than an actual user ID.

---

### Post by talsemgeest on 2008-02-10
In the groups list, games is a group. Whether you can delete that group or not, I don't know...

---

