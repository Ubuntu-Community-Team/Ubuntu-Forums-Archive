---
title: "Ubuntu doesnt ask for password once i log in anymore"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by darkwave80 on 2007-10-17
I looked at a site that said "ubuntu security" and now it looks like the root account is disabled
and my log in can do everything without a password.

How do I set my main user log on to where if i go to do a administrative task, it will prompt me for a password?

I think that whatever that site recommended did a good thing by making root not able to log on remotely even though I thought by default that couldn't happen anyway

but now I just feel like it should be back the other way by asking me when I access certain items.

---

### Post by greenstar on 2007-10-17
Check in System->Administration->Users and Groups for user accounts, then select the desired user, and click properties to see if you have a password set.

Also check System->Administration->Login Window and click the Security tab, and see if Enable Automatic Login or Enable Timed Login are checked, also check to see if Allow local system administrator login is checked. They should all be unchecked.

Greenstar

---

### Post by greenstar on 2007-10-18
Did this solve your problem? If so, please mark your thread solved. Instructions are in my signature block.

Greenstar

---

### Post by jackflap on 2007-10-18
Once you've entered your root password for something, Ubuntu remembers it for that task until you next reboot.

Have you rebooted since the last time you entered your password? If not, try rebooting and checking to see if it asks you again.

Alex

---

### Post by darkwave80 on 2007-10-21
I unchecked the "Allow local admin to log on" on my other computer to help security but the box i mentioned I guess is working right......

IT only asks once for  a admin task.

it used to ask every single time but i guess if it "remembers" that i logged on once per session its ok....but that seems like a security issue still.....

like if you did one thing then something was running or breaches security then it could perform admin things because it "remembered you did it already that session"

maby thats not how it works but thats what it would seem like.

but it seems to be on track, but im just used to it asking every time;/

---

