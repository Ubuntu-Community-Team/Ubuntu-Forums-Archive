---
title: "new arch user, horrible nautilus!"
date: 2008-03-19
forum: Arch and derivatives
---

### Post by savagenator on 2008-03-19
Hello everyone.

I just installed Arch64, and Its working great. A lot of control over the system, pretty fun to use I have a problem though. When I used Ubuntu I enjoyed a feature rich nautilus with a sidebar explorer and a bar telling me where I was, now I have none of that in arch, and I do not know why. can anyone point me in the right direction and show me how i can get away from the featureless nautilus?

Also my programs load from the hard disk every time I open them, I  need to fix that somehow...

---

### Post by santaslittlehelper on 2008-03-19
All the features should be there the two I believe your looking for are within View. 

View > Side Pane
View > Location Bar

I don't know about the second one I don't seem to have that problem. 

ps
There's a Arch subforum here in (other OS talk) if you don't know. :)

---

### Post by Sef on 2008-03-19
Moved to the Arch Subforum.

---

### Post by savagenator on 2008-03-19
> **santaslittlehelper said:**
> All the features should be there the two I believe your looking for are within View. 

View > Side Pane
View > Location Bar

I don't know about the second one I don't seem to have that problem. 

ps
There's a Arch subforum here in (other OS talk) if you don't know. :)

Yeah, I forgot about the Arch Subforum

But now, I dont have that option. And I dont have the area where it says "/home/user/Desktop" towards the top

---

### Post by santaslittlehelper on 2008-03-19
Maybe I misunderstood something happens mostly because I am not a native English speaker I think. ;)

I am just going to try again if I did get it right. Don't you have something like -File | Edit | View- in the toolbar when you open nautilus? 
If you do have a look under View I still think that's what you are looking for. No?

---

### Post by justsomedude on 2008-03-19
Edit --> Preferences --> Behavior --> Always open in browser Windows

Tick the box.

Fixed. :)

---

### Post by santaslittlehelper on 2008-03-19
> **justsomedude said:**
> Edit --> Preferences --> Behavior --> Always open in browser Windows

Tick the box.

Fixed. :)
Arhh, forgot about that one :) I should have remembered because I spend a good deal of time looking for it. :D

---

### Post by savagenator on 2008-03-19
thank you very much! That really didn't make any sense, but thank you!

---

### Post by Lu_cas on 2008-08-05
> **savagenator said:**
> I enjoyed a feature rich nautilus with a sidebar explorer and a bar telling me where I was, now I have none of that in arch, and I do not know why. can anyone point me in the right direction and show me how i can get away from the featureless nautilus?


I had the same problem, the solution:

open gconf-editor, go / > apps > nautilus > preferences and check the `always_use_browser`

It worked for me.

---

### Post by handy on 2008-08-05
> **Lu_cas said:**
> I had the same problem, the solution:

open gconf-editor, go / > apps > nautilus > preferences and check the `always_use_browser`

It worked for me.

That's how I have to do it in Sabayon.

I'm using Openbox & a directory utility in under Arch though.

---

