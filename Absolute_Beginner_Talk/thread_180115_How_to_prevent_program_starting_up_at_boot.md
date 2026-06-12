---
title: "How to prevent program starting up at boot?"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2006-05-21
Every time I boot up my laptop, Open Office starts up, without my doing anything. I have checked system > preferences > sessions > startup, and Oo isn't in the list of programs there. Why else would it start up automatically? It's driving me crazy because it takes quite a while to load on my slow laptop, thus keeping me from getting on with what I really want to do!:confused:

---

### Post by JNowka on 2006-05-21
Ok try this.  Make sure everything is closed out.  

Goto System->Logout.

Click the Save Setup box on the top left.

And Log out.

Now log back in.

Let me know if this works

---

### Post by JNowka on 2006-05-21
If that doesn't work then goto System->Preferences->Sessions->Current Session.

Scroll down until you find a line that has openoffice in its Program Discription.

Click on it.

Click Remove

Click Apply

And Close

Make sure everthing is closed

Goto System->Logout

Click the Save Setup box on the top left

And log out.

Log back in.

This should work

---

### Post by SteveHoffmanUK on 2006-05-21
J Nowka wrote:
> Ok try this. Make sure everything is closed out.
Goto System->Logout.
Click the Save Setup box on the top left.
And Log out.
Now log back in.
Let me know if this works

Whoops, sorry; forgot to say that I'm using Dapper Beta, which doesn't offer the "Save Setup" option at Logout. <embarrassed> :oops: 

Any suggestions, or should I not be in this forum, using Dapper?

---

### Post by userundefine on 2006-05-21
As said above, 

System->Preferences->Sessions->Startup Programs.  If OO.o is there, remove it.

This is on Dapper.

---

### Post by SteveHoffmanUK on 2006-05-21
But I said in my first message that Oo ISN'T there! That's the problem -- it's not in the list, yet it starts up whenever I boot. Why?

---

### Post by it.henrik on 2006-05-21
System-preferences-sessions .. check the box about saving sessions.

This is a bit buggy .. sometimes it doesnt save your session .. 95% of the time it does :)

---

### Post by SteveHoffmanUK on 2006-05-21
it.henrik

Many thanks. I ticked the box and restarted and Oo didn't appear, so it looks like it worked!

---

