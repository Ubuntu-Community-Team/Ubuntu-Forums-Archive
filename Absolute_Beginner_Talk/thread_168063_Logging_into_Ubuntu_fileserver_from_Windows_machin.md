---
title: "Logging into Ubuntu fileserver from Windows machines"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by Karisson on 2006-04-29
I've set up an old box running Ubuntu as a fileserver for my Windows computers to access. I installed Samba, create a public folder, made user accounts, etc.When I try to access the Ubuntu machine by typing \\server in Windows Explorer, I am prompted for a username/password as usual, but even when I enter the correct username and password, it will not log me in. The login window just flashes and pops up again. Any ideas?

I was following this tutorial: [http://www.pcworld.com/reviews/article/0,aid,124162,pg,10,00.asp](http://www.pcworld.com/reviews/article/0,aid,124162,pg,10,00.asp)

---

### Post by cilynx on 2006-04-29
login user/password is not the same as smb user/password

look into the 'smbpasswd' utility to setup your smb user/password

If that doesn't do it for you, do your smb logs show anything?

---

### Post by Karisson on 2006-04-29
I honestly don't know how to do any of those things. :(

---

### Post by Karisson on 2006-04-29
Edit: Crap, double post.

---

### Post by teasum on 2006-04-29
In the tutorial you posted, there is a step that uses smbpasswd to set up accounts and passwords for Windows login on your Ubuntu box.  

Code:

sudo smbpasswd -a username


This was the step that got my setup (similar to yours--old box running Ubuntu and Samba as a file server, and two XP laptops) working.  Of course, substitute the 'username' you want to use to log in to your Ubuntu box from your Windows box. You'll be prompted to enter a password for the new user. Then, use the username and password to log in from your Windows box.

As I said, I had a very similar problem to yours--the Windows login appeared not to work.  After clicking 'ok', the login window would just flash and reappear.  After using smbpasswd on the file server, I was able to login with no problem.

Let us know if this solves the issue.

---

### Post by Karisson on 2006-04-29
Hm. A weird thing happens when it asks for my password after I type sudo smbpasswd -a username. The cursor is on the line that says "Password:", but the cursor is solid black and flashing. It won't let me type anything. If I hit enter to go the next line and type anything, then it says "Sorry, please try again." So I'm not able to enter the password...

---

### Post by cilynx on 2006-04-29
You have to type in the current user password first.  This gives you access to input the new SMB password for that user.  You don't see any of what you type because you're working with passwords.  Linux is just secure like that.

---

### Post by Karisson on 2006-04-29
Oh, I see. I set up the user account and password, it now shows up under System > Administration > Users and Groups. However, I still can't log into the server on my other computers. :(

---

