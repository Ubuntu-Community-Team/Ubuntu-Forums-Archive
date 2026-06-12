---
title: "new users won't save (no &quot;ok&quot; button)"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by bps4484 on 2007-10-05
Hello,

I'm new to ubuntu and trying to add another user.  I've looked online and have seen that I go to system -> administration -> users and groups.  That's all fine, but when I add a user, after clicking "ok" for the user's information, all the instructions I have seen say that I then need to click "ok" on the users settings console for the new user to be created, however I don't have an "ok" button on my screen.  I don't know if I'm doing something wrong, but it's not appearing for me.  As a result, my new user is not being saved.

Has anyone had this problem?

Thanks.

---

### Post by zvacet on 2007-10-05
[https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

---

### Post by BillDozer on 2007-10-05
Hi,

And welcome to the Ubuntu community. If I should make a guess, you are using a low resolution 800x600 or less. Then you cannot see the OK and Cancel button in the bottom of the screen because of standard panels.

You can set these to autohide by right clicking them and choosing the properties menu item and then check the autohide check box.

Instead of doing this you can also press enter (simulates click on the default button, which in this case is the OK button).

---

### Post by bps4484 on 2007-10-07
HI,

thanks for your help, unfortunately my system seems to be different than the posted solutions' systems.  Pressing "enter" hasn't worked, and as you can see from this screen shot, there isn't even an "ok" or "cancel" button as shown in the link posted, just a "close" button.

[IMG]http://www.sherald.dyndns.org/Screenshot-Users%20settings.png[/IMG]

so I'm still stuck on what to do.

Thanks for your help.

---

### Post by Dr Small on 2007-10-07
Try this:
```
sudo adduser *username*
```

---

### Post by FuturePilot on 2007-10-07
If you want to add a new use, click on Add User. Enter the info and click OK. Then just click the Close button. The information will be saved. You can check it by opening it back up again.

---

### Post by bps4484 on 2007-10-08
Dr Small - I actually originally tried doing it that way, but it didn't create a home directory and allow me to log in as that user.  I could ssh but it acted a little funny.  Do you know the arguments I have to give in order to create a full user account?

FuturePilot - unfortunately that's what I've been doing all long, but the account information doesn't save.  In my screenshot example, kevtrice was the user I added, but when I click close and then open users and groups back up:

[IMG]http://www.sherald.dyndns.org/Screenshot-Users%20settings-2.png[/IMG]

I'm out of luck.

---

### Post by BillDozer on 2007-10-09
Sound really weird. Just tried to create a few users, no problem, no OK button. Have you tried to create the same user each time, maybe something hangs in the system, try another username.

Have you checked /var/log/auth.log whether there were reported some errors there?

---

### Post by zvacet on 2007-10-09
In terminal

```
sudo adduser <username>
```

---

### Post by bps4484 on 2007-10-09
zvacet, as I said before when this was suggested, that doesn't seem to create a full user with the appropriate folders and the ability to sign into ubuntu.  Do you know the arguments to do that?  I can't seem to find it online.

---

### Post by BillDozer on 2007-10-10
Have you checked the permissions for the /home folder?

---

### Post by bps4484 on 2007-10-25
I think I found out my problem.  I had tried at one point to do:

sudo adduser <username>

and had created 2 accounts but as I said in a previous post this didn't create a full ubuntu user with the ability to sign in.  I then deleted them and tried to create a new user with the same name using the GUI way described above.  I think because I was using the same name this caused problems and for some reason wasn't getting saved, because when I finally tried a different username it saved properly and now works.  I guess something happened with me not deleting the user account properly.

Thanks for everyone's help with this.

---

