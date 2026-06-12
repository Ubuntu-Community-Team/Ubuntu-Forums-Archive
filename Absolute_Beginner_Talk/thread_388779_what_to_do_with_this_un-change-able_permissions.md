---
title: "what to do with this un-change-able permissions ?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by medya on 2007-03-19
hey guys I am installing phpBB 3 , on ubuntu (I have installed LAMP apache-mysql server )
it is driving me crazy, 
in my phpBB folder I need some directories to be Write-able , 

I go to nautilus file manager and I right l click on the folder which I want to be write-able ,then choose "properties" then I choose "permissions" and then I change the Read-only things to Read and Write  and then I click on "Apply permissions to enclosed files" 

but after I click on OK, ubuntu is like nothing has  happened and everything goes back to whatever it was.
and SOME times it just changes the permission , ubuntu acts like a child (a bad child which refuses to do things)

I tried to do it with ROOT Nauttilus , but still the same...

it is really making me crazy ,how can I change a folder to be write-able easily?
:(:(

---

### Post by bruenig on 2007-03-19
```
sudo chmod a+w /path/to/directory
```

---

