---
title: "changing username"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by domromer on 2007-09-05
My copy of ubuntu was installed by another person so I still have their username on my computer. I was able to change the password, but after reading a few other threads I am still not sure how to change username. Also if I do change the username will I still have access to all the files I've created using the previous username? Thanks again for all the help,  be gentle I'm a long time windows slave...I mean user.

---

### Post by eentonig on 2007-09-05
fill access is defined by the users UID (User ID). 

I really don't know how to change your username, but in theory, you should be able to create a new user. Add it to the sudousers group,  move all files under /home/<old user> to /home/<new user> and then chown them all to let the new user take ownership.

But there must be a way to just change the username as well.

---

### Post by nowshining on 2007-09-05
if nothing is yours - then I would suggest downloading and burning an ISO image or ordering a cd copy then doing a format. :) - that would be the best way..

---

### Post by domromer on 2007-09-05
no it's all my stuff, I just don't want the installers username to be there.

---

### Post by penguinv on 2007-09-06
Please notice: this Los Angeles based person has solved their own problem before the end of this post but still has a request for a Dutch penpal, maar te schrijven in Nederlands.
    +++++++++++++++++++++++++++++++++++++++++++++++ Van Penguin
> **eentonig said:**
> fill access is defined by the users UID (User ID). 

I really don't know how to change your username, but in theory, you should be able to create a new user. Add it to the sudousers group,  move all files under /home/<old user> to /home/<new user> and then chown them all to let the new user take ownership.

But there must be a way to just change the username as well.
----------------------------------------------------------------------------------------------------
I just installed Ubuntu on a random old P3. Looks like it works (but the holland.com webpage doe not look so good), heh.
---------------------------------this was how the thing that is inthe QOOTE brackets looked different when I read the post. It looked like this -------------------------------------
 Re: changing username
fill access is defined by the users UID (User ID).

I really don't know how to change your username, but in theory, you should be able to create a new user. Add it to the sudousers group, move all files under /home/<old user> to /home/<new user> and then chown them all to let the new user take ownership.

But there must be a way to just change the username as well.
__________________
How do I install <program X> || I want a script!! || Chinese isn't ready for the desktop || Automatix???
'Eentonig' means boring in Dutch 
--------------------------------------------------------- end look of original post ---------------------------

WHAT i WANT TO DO IS:

Make another not-an-administrator user.
I go to administration, user. 
it asks for a password.
1. I try OK (no password)    
    I go back where I started
2. I try my password
    I go back to where I started.
3. After that I try going to Administration, Users and groups (again)
    It asks for a password.

Your instructions do not empower me because I cannot get there.
I need step by step.

BTW, I am not stupid. I can do things in windows. I can use a tsch shell. I can fix peoples set ups. I have done DOS and CLI in Amiga. I can use a Mac since the classic was not yet the classic. I was a programmer on mainframes in FORTRAN long long long ago. 

AND I just notice that OPTIONS button on the taskbar and SOLVED my own problem.

BUT SINCE YOU ARE DUTCH, please write to me.
Ik prober het nederlands to praten en vind het PRIMA --to haev a penpal in Dutch.
Ze schriven me. OK?

---

### Post by mikeyandmary on 2007-09-15
It can be done easily... (BTW I'm using ubuntu feisty)

YOU WILL NEED A ROOT PASSWORD TO MAKE THE CHANGES!!!

1. Go to System, Administration, Users and Groups

2. Click on the username you want to change

3. Click on the Properties button on the right hand side

4. Change the Username and Real Name as desired. You can also change the password if you like. 

5. Click on the Advanced tab at the top and in the top box change the name of the home directory from /home/oldname to /home/newname it needs to be the SAME as the username WRITE THIS NAME DOWN you'll need it later

6. Click Ok then click Close.

7. Press "ALT+F2" A small window will open. Enter gksudo nautilus and click Run. 

8. Double Click on File System on the left hand side

9. Double click on the Home folder in the main section

10. There will be a folder with the name of the old username. Click once on this and press F2. Change the name of the folder to EXACTLY the same as you entered in step 5 (hopefully you wrote it down)

11. Log out and you should be able to login using your new username. You should be able to access you home folder as normal... 

Hope this is helpful. 

Have a great day...
Michael

---

### Post by uglykigjoe on 2007-09-15
good day..
i guess the requester already solved his problem..
but thanks to you now i can solve mine 
:)
thanks a million.

---

