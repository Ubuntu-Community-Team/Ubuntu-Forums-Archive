---
title: "Sleep on g4 laptop"
date: 2008-03-22
forum: Apple PPC Users
---

### Post by somethingkindawierd on 2008-03-22
I have successfully installed 7.10 on a G4 17" aluminum PowerBook.  Ubuntu does not appear to support sleep or hibernate.  They are not even an option thru the gui - I can only shutdown.

In the Power Manager I can only select "Blank Screen" when the laptop lid is closed.  When I close the lid the screen blinks off and then immediatly back on.

Is there any way to enable sleep/hibernate?

-jon

---

### Post by slacka-vt on 2008-03-22
The best I have been able to accomplish on my PowerBook G4
as far as Power Management goes
-is get the machine to sleep after 30 minutes of inactivity.
I have the display set to "go blank" when I shut the lid.
So essentially the display sleeps when i close the machine and
the machine sleeps 30 minutes after that.

There is definetly a need for some improvements there.

One thing I do like though
-in Power Management, I can have my machine shut down
when I close the lid and am on Battery Power.
As far as I can remeber,
I couldn't do this with Mac OS X

~s

---

### Post by stream303 on 2008-03-24
> **somethingkindawierd said:**
> I have successfully installed 7.10 on a G4 17" aluminum PowerBook.  Ubuntu does not appear to support sleep or hibernate.  They are not even an option thru the gui - I can only shutdown.

If that Powerbook is using an Nvidia card, I believe that there is currently no way to sleep or hibernate due to lack of Nvidia info...

---

### Post by somethingkindawierd on 2008-03-24
No, it is not using an Nvidia card.

I have tried setting the LapTop to at least make its screen blank, but it blinks off and instantly turns back on again.

I can see in the system logs that the policy does not allow for hibernate/sleep/suspend, but cannot find where this policy is actually defined. 

Is it possible to edit the policy file?  Or is there a terminal command that I can use to test sleep?

---

### Post by spaetz on 2008-03-25
Suspend/Hibernate is also broken on a G4 with the new hardy heron beta, upgrading will you probably not help with this specific issue.

---

### Post by Gen2ly on 2008-03-25
Have you tried using hal to suspend?

```
sudo /usr/libexec/hal-system-power-pmu sleep
```

works on my gentoo ibook, not sure it will get around the nvidia problem though.

---

