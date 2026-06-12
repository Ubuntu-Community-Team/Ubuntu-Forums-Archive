---
title: "win 7 security permissions inheritance error"
date: 2012-12-16
forum: Any Other OS
---

### Post by sdowney717 on 2012-12-16
Error applying security permissions when I try to apply the change.

"Replace all child object permissions with inheritable permissions from this object"

So what is it saying?

What I have is a win7 share which I can access from Ubuntu.
BUT BUT, I can not access ANY subfolders in the shared folder.

What could I do to make it so all subfolders under a shared folder I can open?

---

### Post by 2F4U on 2012-12-16
> "Replace all child object permissions with inheritable permissions from this object"

I think this means that it is going down into the folder structure and wants to apply the settings of the parent folder. The error seems to indicate that your account does not have the necessary rights to access this particular file or folder mentioned in the error message.

---

### Post by Rockstarever on 2012-12-16
try using the administrator account to apply the changes to all users. good luck.

---

### Post by sdowney717 on 2012-12-16
Thing is I am the owner of the shared folder called video, and I can not make the change.

---

### Post by sdowney717 on 2012-12-16
> **Rockstarever said:**
> try using the administrator account to apply the changes to all users. good luck.

How do I open the properties page as an admin?

---

### Post by sdowney717 on 2012-12-16
[http://answers.microsoft.com/en-us/windows/forum/windows_vista-security/how-to-start-windows-explorer-as-administrator/a3cfdd52-695d-46b0-a617-1c9128addf01](http://answers.microsoft.com/en-us/windows/forum/windows_vista-security/how-to-start-windows-explorer-as-administrator/a3cfdd52-695d-46b0-a617-1c9128addf01)

following this, I was able to activate admin login and can make changes without getting error.

selecting the 
"Replace all child object permissions with inheritable permissions from this object"

does not error, but when applied the check mark is removed.

---

### Post by sdowney717 on 2012-12-16
Ok, did a test and it works on opening subfolders.
I log in as admin

I created a new folder sharetest1
Then a subfolder sharetest2
then put a text file

Then I told folder sharetest1 to be shared
Added 'Everyone' 

and I can open it from the ubuntu PC on the LAN

So something about the 'video' folder is not right.

some pics

next test is to log out and back as scott and try a second test.

---

### Post by sdowney717 on 2012-12-16
Ok I logged out and back as scott

Did the same thing with a folder called it share1 then folder share2, put in text files

And can open on the LAN ok.

Ok, copied the folder called Video_TS into share2 and I can open on the LAN, so I can just get rid of the defective folder and make a new one.

So what is goofy about the folder called 'video'??

---

### Post by Dr. C on 2012-12-16
> **sdowney717 said:**
> Ok I logged out and back as scott

Did the same thing with a folder called it share1 then folder share2, put in text files

And can open on the LAN ok.

Ok, copied the folder called Video_TS into share2 and I can open on the LAN, so I can just get rid of the defective folder and make a new one.

So what is goofy about the folder called 'video'??

If this is a default folder in Windows 7 my guess is that DRM is what makes video "goofy".

---

### Post by sdowney717 on 2012-12-16
> **Dr. C said:**
> If this is a default folder in Windows 7 my guess is that DRM is what makes video "goofy".

It's not, I created it myself some time ago. It is just a folder called 'video' in the root of the c drive.

---

### Post by sdowney717 on 2012-12-16
It is working now on video folder.
I turned off sharing and reset everything on the folder back the way it was before I messed with the sharing settings. Then redid sharing and I can open it up on the LAN

"Replace all child object permissions with inheritable permissions from this object"
IS NOT NEEDED, just the line on top of that needs checking.

---

