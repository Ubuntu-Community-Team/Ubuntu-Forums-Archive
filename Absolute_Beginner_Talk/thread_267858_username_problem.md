---
title: "username problem"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by hiena on 2006-09-29
While in System/admin/USers & groups I thought it was a good idea ( and stupid in the end) to change the name of my 'root' user from 'root admin' to 'root'.
After rebooting I realized that I had lost all access to my drivers and most of the menu options including changing the username back.
Tried to find a command line to do that but nothing in the forums so here I am.
Thanks in advance.

---

### Post by Ben Sprinkle on 2006-09-29
Can you go in the users manager, or type "su" in the terminal?

---

### Post by hiena on 2006-09-29
Yeap I can use the terminal but the User manager as all admin menus are gone...
I haven't got any permissions in GUI.

---

### Post by Ben Sprinkle on 2006-09-29
Well can you use "su" and it will let you type in your password?
I am not at my linux computer right now but try to find the name of the user manager so you can run it in the terminal via:
su=>sudo username manager name.

---

### Post by hiena on 2006-09-29
I can use sudo no problem.
what's the command to find out user manager????

---

### Post by Ben Sprinkle on 2006-09-29
I am not sure as I am not at my ubuntu computer, type aptitude and browse the installed apps to see.

---

### Post by hiena on 2006-09-29
Would that be adduser??

---

### Post by Ben Sprinkle on 2006-09-29
Aptitude is in your terminal, it is like the synaptic manager but text based. You may be able to see the usermanager install and what the name is for it. Try it out. ;)

---

### Post by hiena on 2006-09-29
Adduser is one of the packages and the only one that I found related to users. 
Tell the truth I don't know where to start in there as there are so many packages. But I think the solution to my problem might be on the command line.
If I am wrong just say.

---

### Post by Ben Sprinkle on 2006-09-29
Hmmm, did you use the search feature in aptitude?

---

### Post by hiena on 2006-09-29
ok. good one.
Might it be user-setup or kuser?

---

### Post by Ben Sprinkle on 2006-09-29
Like I said, not at the linux comp. :p
Try typing sudo appname for everything that has user in it to see what it does.
(appname=the name of the thing)

---

### Post by hiena on 2006-09-29
Ok good one.
Might it be user-setup or kuser?

---

### Post by dannyboy79 on 2006-09-29
You don't need a gui for this, see below, i copied it from this link, [http://www.linux.com/guides/sag/x2424.shtml](http://www.linux.com/guides/sag/x2424.shtml)

11.3. Changing user properties
There are a few commands for changing various properties of an account (i.e., the relevant field in /etc/passwd): 

chfn
Change the full name field. 

chsh
Change the login shell. 

passwd
Change the password. 

The super-user may use these commands to change the properties of any account. Normal users can only change the properties of their own account. It may sometimes be necessary to disable these commands (with chmod) for normal users, for example in an environment with many novice users. 

Other tasks need to be done by hand. For example, to change the username, you need to edit /etc/passwd directly (with vipw, remember). Likewise, to add or remove the user to more groups, you need to edit /etc/group (with vigr). Such tasks tend to be rare, however, and should be done with caution: for example, if you change the username, e-mail will no longer reach the user, unless you also create a mail alias. [1]

---

### Post by Ben Sprinkle on 2006-09-29
> **dannyboy79 said:**
> You don't need a gui for this, see below, i copied it from this link, [http://www.linux.com/guides/sag/x2424.shtml](http://www.linux.com/guides/sag/x2424.shtml)

11.3. Changing user properties
There are a few commands for changing various properties of an account (i.e., the relevant field in /etc/passwd): 

chfn
Change the full name field. 

chsh
Change the login shell. 

passwd
Change the password. 

The super-user may use these commands to change the properties of any account. Normal users can only change the properties of their own account. It may sometimes be necessary to disable these commands (with chmod) for normal users, for example in an environment with many novice users. 

Other tasks need to be done by hand. For example, to change the username, you need to edit /etc/passwd directly (with vipw, remember). Likewise, to add or remove the user to more groups, you need to edit /etc/group (with vigr). Such tasks tend to be rare, however, and should be done with caution: for example, if you change the username, e-mail will no longer reach the user, unless you also create a mail alias. [1]

If you do not have root properties you can't edit them.
But since he can get in aptitude I think he has them.

Also, you have to copy the /etc/passwd to like /home/user/Desktop then edit.
Then type su, then type:
cp '/home/user/Desktop/passwd' '/etc'
:)

---

### Post by hiena on 2006-09-29
none of it works.
Just keep getting command not found.

---

### Post by hiena on 2006-09-29
think that my problem is really the lack of root properties.
Somehow I managed to loose it. Inside /etc/passwd everything looks ok. The user name is still there.

---

### Post by hiena on 2006-09-29
ok. So what about creating a new user with all the root permissions? Would I get my menus and drivers access back?

---

### Post by Ben Sprinkle on 2006-09-29
> **hiena said:**
> ok. So what about creating a new user with all the root permissions? Would I get my menus and drivers access back?
Lad, it sounds like your F-ED in the A.
I suggest just copying or uploading all your shit you need and reinstall.
I once did the same thing as you and found it easier to just reinstall then go through the aggrevation of trying to fix.

---

### Post by hiena on 2006-09-29
Bloody hell.
I even got through a frozen screen before using the command line.
The problem is that I don't even have a clue of what went wrong.
I could have done that reinstall by now...
Anyway, guys thanks for trying.
Cheers

---

### Post by dannyboy79 on 2006-09-30
alright, I am confussed. you stated that you could sudo?? If you can use sudo, then you can certainly bring up the user and group gui using sudo from a command line! then change it from there. just go to a termianl and type in gksudo users-admin and you should be able to change your root users name back to root.

---

### Post by hiena on 2006-10-02
Yeah I did that and nothing...still no access to all root menus and stuff.
Tell the truth I already reinstalled the whole thing.
and I am not going there again..
Thanks anyway.

---

