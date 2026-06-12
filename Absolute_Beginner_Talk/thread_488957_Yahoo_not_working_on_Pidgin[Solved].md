---
title: "Yahoo not working on Pidgin[Solved]"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by ftmichael on 2007-06-30
For the past couple of weeks or so, inexplicably, Yahoo will not let me log in via Pidgin.  It isn't having any trouble connecting; it's telling me that my password is incorrect.  I've checked and re-checked it, and it is absolutely entered correctly, and I used the same password to log into my account on yahoo.com with no problems.  I've been trying and re-trying for two weeks with absolutely no success.  What is going on?  Has anyone else had this happen?

**EDIT: Fixed!** See my final post on this thread.  It was definitely a Pidgin problem, not Yahoo.  [http://developer.pidgin.im/ticket/970](http://developer.pidgin.im/ticket/970) has the bug report.

Michael

---

### Post by EXCiD3 on 2007-06-30
The other day i couldnt log into my yahoo account but then i rebooted and then tried to connect later and it worked. I think it is a problem with yahoo's servers, not pidgin.

---

### Post by wolfen69 on 2007-06-30
try Gyachi (in synaptic). it is a yahoo messenger (only) clone. supports webcam, voice, etc. you just have to pick the right server to connect with. i believe the 3rd or 4th one from the top works fine. you can access your yahoo mail through it too.

---

### Post by ftmichael on 2007-07-01
I have Gyachi, but it sops up my resources and I don't like it generally - I just use it when I want to cam.

Could you possibly check and tell me which server you use when connecting via Gyachi, and what port?

Michael

---

### Post by sailor2001 on 2007-07-01
yahoo didn't allow me in a few minutes ago (password) and after about 2 minutes tried again and it worked,.. Must be a yahoo problem

---

### Post by viralbug on 2007-07-01
there was a problem with the yahoo servers. many people couldnt login.

---

### Post by stmiller on 2007-07-01
Yahoo had a major security update on their end, perhaps that threw 3rd party clients out of whack.

---

### Post by ftmichael on 2007-07-07
This was the most roundabout fix ever.  It was definitely a Pidgin problem, because GyachE logged me in with no problems at all.  I went into my Yahoo account info on their website, created a second public profile - just my regular Yahoo ID with some numbers tacked on the end - and logged in with that, using my same Yahoo password.  It logged me in with no complaints.  (Just a moment earlier, I had tried to log in with my regular Yahoo ID and password, and still got the password error.)  Once I was logged in with the alternate screen name, I attempted to log in via my normal screen name again, and it worked immediately.  Completely bizarre.

Interesting note: When I added the account for my alternate Yahoo screen name, it automatically removed the other Yahoo account.  When I re-added my regular one and it finally logged me in, it automatically removed the alternate one.  Since they're linked to the same account, Pidgin won't let you have more than one screen name at the same time, which makes good sense.

Michael

---

