---
title: "User (log in) and sudo question"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by uputer on 2007-07-29
I will search the forum but can anyone inform me how to use the traditional super user method so that sudo is not needed?   

Also, even more important, how do you avoid having to log in as other users when you use applications such as mythtv (permissions issue)?  

That's all.   I think (my) Ubuntu experience will improve if I can set it up to utilize those two systems.   

Thanks to anyone who can inform me.   I'll do a search though and hopefully, I'll find the answers.   But, it would be great if I could find it in this thread or answers could supplement any potential answers I might find.   It would be good to have a guide.

---

### Post by rillip on 2007-07-29
Keeping in mind, this is very discouraged, you can setup the super user root for use with su by doing the following

```
sudo passwd root
```

You can then go ```
su root
```

But this is really not that good an idea.  You can also set the duration for sudo to last longer, but really what are you doing that fifteen minutes isn't long enough?

As for having to login as other users, I'm not sure how that particular program works, but couldn't use set it up to use a group, and then just add all the users to the group?

---

### Post by carloslosgrande on 2007-07-29
[I][FONT="Comic Sans MS"][I]It sounds like you've setup applications under different users? you don't need a User and Admin like in windows.
I only use sudo when its absolutely necessary, everything else is done in my user.

Not sure if this is really what you asking.

Anyway have a look at this;
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)[/I][/FONT][/I]

---

