---
title: "Can't Change Password in User and Groups"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by pmueller on 2007-04-01
Hi,

Going to "users and Groups" under "Administration" I entered a new password. A long time ago I decided to have the same root password as my login thinking that I could change it later.

So, I have entered a longer password  under my user account and hit OK. After rebooting my login only works with my old shorter password. Going back to Users and Groups I find that my longer password is still in the boxes.

I was messing around with root in Users and Groups and I have noticed that my longer password is entered in the Password and confirm password boxes. When I enter my older password which is the same as my older user password that works and close out Users and Groups, my newer longer password that does not work reappears in the boxes for root properties.

Also, I would like to ask, what kind User Privileges should root have? I went to the  User Privileges tab for root and I gave it extra authority. Should I go back and uncheck everything for root. What is the default? 

My intuition is failing me in understanding the Intelligent Design of Ubuntu and I get in trouble often. Recently, I took away my own Administrator privileges as a user thinking that I could log in as root anyway. Wrong! I spent the last few hours getting back on track by looking things up, using the Recovery Mode (My Suse bootloader did not give me this, so I had to edit menu.lst in Suse), and editing the group file with nano so I could get Users and Groups back. 

PM in New Hampshire

---

### Post by bapoumba on 2007-04-01
Hello,
did you hit OK to both the Preference window (the one where you change the password) and to the User and Groups window (to apply changes)?
One more thing: the number of dots in the Preferences window do not represent the number of letters/numbers in the password .

---

### Post by zvacet on 2007-04-01
[http://easylinux.info/wiki/Ubuntu_Edgy#User_Administration]("http://easylinux.info/wiki/Ubuntu_Edgy#User_Administration")

---

### Post by pmueller on 2007-04-01
I got my user password changed by hitting OK, but this changed my root password as well. I would like my root password to be different from my regular login password. Is that possible or is it always the same as the user login password?

I created a new account with a new user login and password. Oddly, when I am trying to open up Users and Groups, the password is the same as the new user account, but it is different from the root password in my old account.  I thought that I would only the same one root password for the different accounts.

When I tried "sudo passwd root", it only changed my Unix password (whatever that controls?). It did not change my root password.[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

Paul

---

### Post by pmueller on 2007-04-01
Any comments? I thought that a second user account should have an unguessable password. Yet, I can login two different accounts and use the same passwords for those accounts' respective logins and access synaptic, users and groups, and any other process that should only be accessed by one Administrator. 

Why is it that I can not change the Administrator's or Root's password and make it different from the User's Account login? Is my system compromised or corrupted?

Paul

---

### Post by pmueller on 2007-04-03
2 days since my last post.  How am I wrong or missing something? Is the default administrator password the user password? Or is it possible that my user and administrator file passwords are cross linked and therefore corrupted? How do I get rid of this file corruption.

Paul

---

### Post by zvacet on 2007-04-04
```
sudo adduser your_name
```

this will create new user but it will procede and ask you for pasword.This is where you put any password you want (diferent from administrator).That is it.

---

### Post by pmueller on 2007-04-04
I still do not get it. I entered in terminal sudo adduser your_name. I created a new username and let's call it login3. Terminal asked me to create a new unix password which I did, let's call it password4. 

I noticed that when I switched users and called up login3. I could not log in. So I went back to one of my older accounts and created, password3. I booted into login3, but I could not get into Users and Groups. Also, I could not use Automatix. Automatix is on the menu, but after I tried once I could not call the program back up again. This is because I have no administrators rights. 

Let's say that I use the login3 account, because it is secure. How can I make a change as an administrator without logging out and logging back in as either login1 with password1 or the login2 created through Users and Groups, where I use password2. 

It seems to me that I should not be able to use both password1 and password2 to change my system. It also seems to me that I should be able to use password4 or something that is tied to root to make a change when I am using login3.

I guess Ubuntu is forcing me to actually use login1 or login2 because these have administrator privileges. To stay safe once I fool around and add and subtract programs from my system, I should logout and switch into the login3 account where I can't make any changes at all.

Is this right? It just seems awkward.

Paul

---

### Post by bapoumba on 2007-04-05
Hello :)

You may be interested in reading [this]("https://help.ubuntu.com/community/RootSudo?highlight=%28rootsudo%29").

Ubuntu does not set up the root account by default. Instead, The first user created during the install is in the admin group, which grants administration priviledges when using sudo in the CLI or gksudo in graphical admin applications.

Any subsequent user created will not be in the admin group, unless a user with admin priviledges add it in:
```
sudo adduser <user_login_here> admin
```
Then this new user will have admin privilidges and will be able to use sudo or gksudo.

Now, I do not understand what is going on with your passwords.

To check which groups a user is in, run 
```
groups
```

In addition, say you are logged in with a basic user that does not have admin priviledges. In CLI, you can switch to another user (say user1 which does have admin rights) and perform some admin tasks:
```
su <user1>
```
(I use this quite a lot onto my kids users who do not have admin priviledges).

"Run as another user" in the graphical sessions never worked perfectly for me. I did not investigate, as I do not use this feature.

Hope this helps.

---

### Post by pmueller on 2007-04-05
Hello,

Thank you for your help. I do not quite have enough time to investigate further because I will have to drive to Pennsylvania. My computer will have a break and I will get back in 5 days.

Switching to a user that has administration rights is not all that hard. It's  tempting to do everything in an account that has these privileges through the use of a simple password. My misreading of Ubuntu was that the user password should be always different from the administrator's password. Instead I can just stay in account that has no rights and switch over when I get the itch to browse synaptic where there are so many programs that I am unfamiliar with. That is why it seems a little clumsy to me. I rather just look at synaptic without switching users  or try any of the other menu choice requiring the use of the password so I can more easily learn this great distribution.

I need to check out a few of the terminal commands in the last post when I get back. I really like the way Ubuntu is so much more secure and that it hardly requires antivirus updates (if any) or firewalls (a good idea anyway). Despite the extra security and the my problems understanding it at times Ubuntu is great, and easier in many other areas than Windows.

Paul

---

