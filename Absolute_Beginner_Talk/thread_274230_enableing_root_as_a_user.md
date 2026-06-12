---
title: "enableing root as a user"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by fnordportland on 2006-10-09
how would i enable root as a user?i used root as my user name when i installed now it wont let me log in to the gui with root as  user name i set up another acount but none of the normal options under system/administration options are availible so i need to go into a terminal and chaNGE THE USER PRIVS/GROUP PRIVS SOMEHOW BUT THE DOCUMENTAION ON THE UBUNTU SITE ISNT BEING HELPFULL oops sorry about the caps

---

### Post by bodhi.zazen on 2006-10-09
Use sudo

sudo <command>

You will be asked for a password, enter you user password. You will not see text on the screen as you type.

You can also ```
sudo su
```

---

### Post by Kateikyoushi on 2006-10-09
It is intentional that no root account is created during an ubuntu installation, use the sudo command instead.

[Reasons]("https://help.ubuntu.com/community/RootSudo").

---

### Post by fnordportland on 2006-10-09
whats the commands for giving a user admin privs?sudu su dosent help because i still dont have acssess to the admin menu under the gui,so i have to give another acount admin privs

---

### Post by bodhi.zazen on 2006-10-09
> **fnordportland said:**
> whats the commands for giving a user admin privs?sudu su dosent help because i still dont have acssess to the admin menu under the gui,so i have to give another acount admin privs

The first user has full admin privileges. If you are not the first user, talk to your sys admin.

It is **sudo** not sudu.

If you want to start a graphical program:

gksudo <graphical command>

ie. ```
gksudo nautilus
```

---

### Post by Delkster on 2006-10-09
> **fnordportland said:**
> how would i enable root as a user?i used root as my user name when i installed now it wont let me log in to the gui with root as  user name i set up another acount but none of the normal options under

Can you login to a text console, though? You can try it by pressing Ctrl+Alt+F1 (for the 1st console) and attempting to log in. If you're able to do it, you could try entering the following command to enable administrative privileges through sudo for your normal user account:
```
adduser <username> admin
```
where you should replace <username> with that of your normal user account. The command will add the user to the admin group, and members of that group have rights to sudo by default. I guess that should also give you the administrative menu items for the normal user account.

---

### Post by cilynx on 2006-10-09
Nice find...using "root" as your username should be caught and disallowed by the installer.  

Just in case anyone finds this looking for how to add privileges:

"go to the command line and..." is never a good answer in "Absolute Beginner Talk".

To add admin privileges to a user:

Click on System->Administration->Users and Groups
Select your user
Click Properties
Click the User Privileges Tab
Check the boxes for the abilities you need

On my non-important systems, I just check them all.

Hope this helps --

---

### Post by aysiu on 2006-10-09
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) should help--make sure you add your new user to the *admin* group, not the old user you called *root*.

---

### Post by timnoc1456 on 2006-10-09
cilynx's method I thk is best for beginners like us. Though trying to get used to, the terminal and all those commands is quite intimidating for toddlers in Linux like us.

---

### Post by aysiu on 2006-10-09
> **timnoc1456 said:**
> cilynx's method I thk is best for beginners like us. Though trying to get used to, the terminal and all those commands is quite intimidating for toddlers in Linux like us.
Except that if I'm understanding the situation correctly, that won't work.

In order to go to System > Administration > Users and Groups, you have to be either root or a user with *sudo* privileges.

Since the first user created has *sudo* privileges but can't be logged into, and the second user does not have *sudo* privileges, no user on fnordportland's system can go to System > Administration > Users and Groups

This icky situation has to be solved from the command-line.

I'm really surprised that the installer let you pick *root* as a username...

---

### Post by cilynx on 2006-10-09
Sorry about the confusion.  The point-and-click walkthrough I posted will only work if you have sudo privileges working.  I was trying to clear up the manually-running-gksudo type of hack, as opposed to getting sudo privs working in the first place.

As an asside:

If you were to choose "root" as your username in the installer, should it:

1) Throw a scary error and tell you that you can't do that and explain why.
2) Proceed as normal and let you log in as root
3) Throw a scary error, but allow you to override sic 2)

My gut thought is 3), however, It just might be a better idea to do 1).  That keeps people who aren't comfortable enough to do 'sudo passwd' from logging in as root and that's probably a good thing.

---

### Post by timnoc1456 on 2006-10-09
So is it that, one should never use, "root" as username on one's first install of Ubuntu. Seems all the prob started from  fnordportland's using root as username in the first time.

---

### Post by aysiu on 2006-10-09
> **timnoc1456 said:**
> So is it that, one should never use, "root" as username on one's first install of Ubuntu. Seems all the prob started from  fnordportland's using root as username in the first time.
Yes.

But not only should you not pick *root* as your username--the installer itself should not *allow* you to pick root as your username.

Of course, since this is the first time in the past year and a half of my using Ubuntu that I've heard of anyone doing this, I doubt this bug would get a critical priority rating...

---

### Post by Madpilot on 2006-10-09
Critical or not, it should be filed - remember that the Ubuntu developers don't have the spare time to poke around the Forums much!

[http://bugs.ubuntu.com/](http://bugs.ubuntu.com/)

File it against 'ubuntu' as a whole; or poke around to find the installer package name and file against that.

I'd go with Option #1 (forbid, and throw scary explanatory error) on cilynx's list of options, myself.

---

### Post by fnordportland on 2006-10-09
got it fixed,im going with option 3.the more choices the better but i dont see why anyone would want to

---

### Post by timnoc1456 on 2006-10-09
folks!,
        Sorry but I've a query myself arising out of this post. Since I did'nt always wanted to use sudo in my terminal for every administertative tasked (though almost nil, but sometimes), I enabled/created "root" account through the GUI User Management. Now when I swicth user in the terminal> su -i command" I can do "cp", "mv", "rm" or ./configure so and so forth without bothering to sudo again. The thing I am not sure still now is that, is this "root" user I enabled/created, the same as the one created during the first install by "fnordportland".

---

### Post by fnordportland on 2006-10-09
not unless  "root" was the name you put in when you installed

---

### Post by Delkster on 2006-10-10
> **fnordportland said:**
> got it fixed,im going with option 3.the more choices the better but i dont see why anyone would want to

How did you fix it? Usually it's a good idea to let people know how you resolved your issue so that others can possibly learn from it, too.

---

