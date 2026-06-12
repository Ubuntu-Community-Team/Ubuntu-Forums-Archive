---
title: "Problem Adding New Software"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by mattforni on 2007-12-25
I have been trying to add new programs to my system.  I select 'Applications' from the menu bar and then 'Add/Remove...' and the Add/Remove Applications window appears.  The problem occurs when I try to select something to add.  

For example, when I check the box next to any of the applications not currently installed I get a message telling me that 'The list of applications is not available' and it asks me to refresh the list.  However, when I click refresh I get a message telling me that it is downloading and installing six files.  Then after this has completed I try again to check the box next any of the currently not installed applications, but receive the same message, and so on in a constant loop.  What do I do?

Thanks!

---

### Post by taurus on 2007-12-25
Close Add/Remove window.  Then, click System -> Administration -> Synaptic Package Manager -> Settings -> Repositories.  Make sure you check everything _except_ Sources code (last option) and CDROM.  Close that window.  Then, press Refresh and you can install whatever you want from there.  Or close synaptic and use Add/Remove if you wish.

---

### Post by overdrank on 2007-12-25
> **mattforni said:**
> I have been trying to add new programs to my system.  I select 'Applications' from the menu bar and then 'Add/Remove...' and the Add/Remove Applications window appears.  The problem occurs when I try to select something to add.  

For example, when I check the box next to any of the applications not currently installed I get a message telling me that 'The list of applications is not available' and it asks me to refresh the list.  However, when I click refresh I get a message telling me that it is downloading and installing six files.  Then after this has completed I try again to check the box next any of the currently not installed applications, but receive the same message, and so on in a constant loop.  What do I do?

Thanks!

HI and welcome you may want to make sure your repos are enabled. This link may help 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by mattforni on 2007-12-27
thanks guys, that did it!

---

