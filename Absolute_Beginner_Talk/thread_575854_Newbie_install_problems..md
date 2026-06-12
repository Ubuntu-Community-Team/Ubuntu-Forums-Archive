---
title: "Newbie install problems."
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by rotcon on 2007-10-14
hi im new to the forums and was not sure how to start a new thread etc so i thought id reply here!

having a problem when i try and update my newly installed xubuntu

applications/system/synaptic package manager

when i try to enter synaptic package manager it does not allow me and says

''failed to run /usr/sbin/synaptic as user root. unable to copy user's Xauthorisation file.''

can anyone help? :)

---

### Post by rotcon on 2007-10-14
hi im new to the forums and was not sure how to start a new thread etc so i thought id reply here!

having a problem when i try and update my newly installed xubuntu

applications/system/synaptic package manager

when i try to enter synaptic package manager it does not allow me and says

''failed to run /usr/sbin/synaptic as user root. unable to copy user's Xauthorisation file.''

can anyone help?

---

### Post by rotcon on 2007-10-14
having a problem when i try and update my newly installed xubuntu

applications/system/synaptic package manager

when i try to enter synaptic package manager it does not allow me and says

''failed to run /usr/sbin/synaptic as user root. unable to copy user's Xauthorisation file.''

can anyone help?

this also happens when i try to go on other applications?

---

### Post by Frak on 2007-10-14
> **rotcon said:**
> hi im new to the forums and was not sure how to start a new thread etc so i thought id reply here!

having a problem when i try and update my newly installed xubuntu

applications/system/synaptic package manager

when i try to enter synaptic package manager it does not allow me and says

''failed to run /usr/sbin/synaptic as user root. unable to copy user's Xauthorisation file.''

can anyone help?
Make sure you are not running sudo, su, or any other root program in the background.

Also, use "Make New Post" in orange just over the stickies to create a new thread.

---

### Post by bapoumba on 2007-10-14
Moved to its own thread.
Could you please open a terminal (Accessories > Terminal) and run:
```
 ls -la .Xaut*

```
Please paste the output in here.

---

### Post by rotcon on 2007-10-14
how can i check if i am running sudo?

and how can i stop it?

cheers! :)

---

### Post by rotcon on 2007-10-14
how do i stop any of those root programmes? like sudo?

---

### Post by rotcon on 2007-10-14
-rw------- 1 root   root   0 2007-10-14 18:56 .Xauthority
-rw------- 2 lawrie lawrie 0 2007-10-14 19:07 .Xauthority-c
-rw------- 2 lawrie lawrie 0 2007-10-14 19:07 .Xauthority-l


this appeared when i typed that?

---

### Post by bapoumba on 2007-10-14
> **rotcon said:**
> -rw------- 1 root   root   0 2007-10-14 18:56 .Xauthority
-rw------- 2 lawrie lawrie 0 2007-10-14 19:07 .Xauthority-c
-rw------- 2 lawrie lawrie 0 2007-10-14 19:07 .Xauthority-l


this appeared when i typed that?
Yes. Please rename the file, another one will be created.
```
sudo mv .Xauthority .Xauthority_bak
```
and logout from your session, then log back in.

---

### Post by rotcon on 2007-10-14
sorry which file am i renaming?

and how do i rename it?

---

### Post by bapoumba on 2007-10-14
> **rotcon said:**
> sorry which file am i renaming?
The .Xauthority file.
Please open a terminal, and paste the line I provided in my previous post. You'll have to enter your own password (it won't appear on screen, which is normal), then hit <enter>.

Logout from your session and log back in.

---

### Post by rotcon on 2007-10-14
sorted! lol...cheers! *thumbs up*

---

### Post by bapoumba on 2007-10-14
> **rotcon said:**
> sorted! lol...cheers! *thumbs up*
Glad to see you got it to work!
And welcome to the ubuntuforums :)

---

