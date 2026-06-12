---
title: "Login failed"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by aabento on 2007-12-16
Hello
When I try to login appears to me the following window with the following fault:


[I]User's $HOME.dmrc file is being ignored. This prevents the default session and linguages from being saved 
File should be owned by user and have 644 permissions.
User's $HOME directory must be owned by user and not writable by others users.[/I]

*OK* :(

The only option I have this small window is press OK

----
After this another window appears with the following:

[I][I]your session only latest less than 10 seconds. if you have not logged out yourself this could mean that
there is some installation problem or that you may be out of diskspace.[/I]
*try logging in one of failsafe session to see if you can fix this problem.*
[/I]
OK

Again I have only the option of pressing OK :(:(:(

This is repeated consecutively and not allow me to login. :mad:
I used the Live CD and saw that there is problem of space on disk. I have 13 Gb free disk space.

What can I do? :confused: :confused:

Arnaldo

PS : This is **Ubuntu 7.10**

---

### Post by thelatinist on 2007-12-16
Boot into the live CD.  Open a terminal.  Use the following commands, replacing username with your username:

```
sudo chown username:username /home/username
sudo chmod o-w /home/username/.dmrc
sudo chown username:username /home/username/.dmrc
sudo chmod 644 /home/username/.dmrc
```

---

### Post by aabento on 2007-12-16
Hello thelatinist

Eu start live CD mas when I run the commands that you suggest always get the message that 

*username: username invalid user*        :(:confused:

PS - username=my username!!!

Other ideas?

Thanks.

Arnaldo

---

### Post by thelatinist on 2007-12-16
Remove the Live CD and boot from your hard drive.  When you get to the login screen on Ubuntu, use ctrl + alt + F1.  A terminal should open.  Try those commands there.

When you are done, type exit and then use ctrl + alt + F7 to get back to the standard GDM login screen.

---

### Post by aabento on 2007-12-16
Sorry disappoint you but I did everything that you suggest in your help but still with the same problem. :(
Should be a  /  at the end of each command?  :confused:

In the terminal I can login with usual user and password. 
The problem happens when I am in graphic mode.

More ideas...:confused:


Arnaldo
Thank you in any way :)

---

### Post by aabento on 2007-12-16
And....

In the second window and pressing the option details I can read:

***Refusing to initialize GTK+***

This can help in the solution? :confused:

Arnaldo  :-k

---

### Post by thelatinist on 2007-12-16
> **aabento said:**
> Sorry disappoint you but I did everything that you suggest in your help but still with the same problem. :(
Should be a  /  at the end of each command?  :confused:

In the terminal I can login with usual user and password. 
The problem happens when I am in graphic mode.

More ideas...:confused:


Arnaldo
Thank you in any way :)

Are you still receiving the same error messages?  Those commands should have fixed the problems with chmod and ownership mentioned in those error messages.

---

### Post by aabento on 2007-12-16
In terminal mode I followed your instructions as root and user but none of the options resulted.

As I said in one of the posts I can read the details

**Refusing to initialize GTK+**

This is relevant?

Excuse me but everything remains the same. ](*,)   ](*,)    ](*,) 

Other helps?

Thanking in advance.

Arnaldo

---

### Post by Achetar on 2007-12-16
login to a Failsafe Terminal Session (from the sessions menu on the login screen). Enter the following into the terminal:
```

sudo chmod 644 $HOME
sudo chmod 644 $HOME/.dmrc

```

---

### Post by thelatinist on 2007-12-16
> **aabento said:**
> And....

In the second window and pressing the option details I can read:

***Refusing to initialize GTK+***

This can help in the solution? :confused:

Arnaldo  :-k

Are you still getting the same error messages you got before?  Everything we're telling you has been based on the error messages you said you've been getting, namely:

[I]User's $HOME.dmrc file is being ignored. This prevents the default session and linguages from being saved
File should be owned by user and have 644 permissions.
User's $HOME directory must be owned by user and not writable by others users.[/I]

The next step depends entirely on the answer to that question.

---

### Post by seventhc on 2007-12-16
reboot your computer, when at the login screen...before you log in click on options then sessions and choose fail safe terminal click change session..if it asks to make it default say no and then try the commands mentioned above.

---

### Post by aabento on 2007-12-16
Hello 
After making a session *Failsafe Terminal*  I just faced this error. 
Now each time I enter with user and password I see the following error message and back to the login window.

:confused::confused:

[I]your session only latest less than 10 seconds. if you have not logged out yourself this could mean that
there is some installation problem or that you may be out of diskspace.
try logging in one of failsafe session to see if you can fix this problem.[/I]

Now I only have one error window. 
Better but not enough!

Thanks for trying.

Arnaldo

---

### Post by seventhc on 2007-12-16
Sorry it didn't work. :(

---

### Post by aabento on 2007-12-17
Hello

Someone has other ideas. Do I have to come back to another clean installation?

It is here that I feel the greatest difficulties.  :(

Almost always find someone who is able to solve the problem without new installation, however this will be the fourth reinstallation.

Did I create major problems so that nobody can find the solution? :confused:  :confused:  :confused:

Thanks.
Arnaldo

---

