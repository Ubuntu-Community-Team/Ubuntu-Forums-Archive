---
title: "Thunderbird password question"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-11
I just started using Thunderbird, and after setting up a gmail account with it, I'm having a problem getting it to require a password.

When I open up Thunderbird, it asks me for a password, but it shows all of the email subjects and senders underneath that box. Is there anyway to set it up so that a password is required before any private information is shown?

---

### Post by x-ray vision on 2007-04-11
Anyone?

---

### Post by x-ray vision on 2007-04-11
Someone here must be using Thunderbird without others in their household seeing who has emailed them, no?

---

### Post by aysiu on 2007-04-11
> **x-ray vision said:**
> Someone here must be using Thunderbird without others in their household seeing who has emailed them, no?
Generally, if you have a group of people using one computer, and you're worried about privacy, your best bet is to set up separate user accounts--then everyone would have her own Thunderbird profile. I know that's not the solution you're looking for, but I'm specifically addressing this last part of your question.

---

### Post by wormser on 2007-04-11
> **aysiu said:**
> Generally, if you have a group of people using one computer, and you're worried about privacy, your best bet is to set up separate user accounts--then everyone would have her own Thunderbird profile. I know that's not the solution you're looking for, but I'm specifically addressing this last part of your question.

Aysiu is right about setting up separate user accounts.

But, you can set a master password for Thunderbird.  
[http://kb.mozillazine.org/Master_password](http://kb.mozillazine.org/Master_password)

---

### Post by aysiu on 2007-04-11
> **wormser said:**
> Aysiu is right about setting up separate user accounts.

But, you can set a master password for Thunderbird.  
[http://kb.mozillazine.org/Master_password](http://kb.mozillazine.org/Master_password)
I think the OP's issue, though, is that you can still see subjects and senders before entering the Master password.

Personally, I don't mind people seeing subjects and senders. Message bodies--that's a different story. My own personal preference--not the OP's.

---

### Post by RKCole on 2007-04-16
Hello, x-ray vision.

My personal preference is that of aysiu's as well.  The main issue here, though, is that if others have access to a computer which only has one user account, they could simply open Thunderbird (by accident or by means of some cruel intention), cancel out the password request, and they would have access to all saved messages.

Here is a method to keep your privacy without setting up multiple user accounts.  Please note, however, that anyone with strong computer skills could view your e-mails; if it is just family members in question, however, this should be just fine.

Before proceeding, make sure that Thunderbird is not running.

**Accessing Thunderbird Profile Manager**
1)  Enter a terminal via (**Applications->Accessories->Terminal** (in GNOME/Ubuntu).
2)  Use the command:
```

gksudo mozilla-thunderbird -profilemanager

```
(enter your password when prompted) to open Thunderbird's profile manager.
3)  The profile created by default in Thunderbird (can you guess) is called **default**.  If you are going to set up multiple profiles, I'd recommend using the **Rename Profile** button to change the name of the default profile (your profile) to your name or whatever you would prefer.
4)  Create additional profiles for other users if other users will be using Thunderbird.
5)  **Make sure to uncheck the option reading "Don't ask at startup".**  This will ensure that a box containing the created profiles appears so that the current user can select his/her profile.

**NOTE:**  This will create separate profiles for Thunderbird.  Each user will have to configure his/her own settings and accounts via his/her respective profile.  Also, this will not password protect the profiles listed; a user can simply select and start Thunderbird under a selected profile and then enter the requested password (or cancel the password request), and the contents of the account will be visible.  Not to worry, though.

**Password Protecting Profiles**
1)  Click on [this link]("http://www.extensionsmirror.nl/index.php?showtopic=1801") to go to the page of the ProfilePassword extension. (This extension also works with profiles on SeaMonkey, Mozilla Suite, and Firefox, apparently)
2)  **DO NOT** left-click on the **Download** link/button ( :) ).  I learned a long time ago that you coudl directly install extensions in Firefox by left-clicking on the download button, but this does not work for installing extensions on Thunderbird.  You must right-click on the Download link/button and use the option **Save Link As...** to save the link (extension) to your desktop or folder of choice.
3)  Open Thunderbird (under your profile) and enter your password as you usually do.
4)  Click on **Tools->Extensions** to open up the Extensions dialog box.
5)  Click the **Install** button.
6)  Navigate to wherever you saved the ProfilePassword extension (link) and double-click on it.
7)  A dialog should open asking what you want to do.  Click **Install now** to install the ProfilePassword extension.
8)  Restart Thunderbird.
9)  Click on **Tools->ProfilePassword->Password manager** to open the Password manager dialog.
10)  Click on the **Set/Change Password** button.
11)  Enter a password **for your profile** and confirm it.

**NOTE:**  You do not have to have multiple profiles for this to work.

Now, when you open Thunderbird, you will be asked for the password to your profile.  The password request box is the only thing that will show, and Thunderbird will not be displayed until the password is entered.  You will then have to enter your account password as usual.

One precaution, however:  If you open Thunderbird in Safe Mode, all extensions will be disabled, thus there will be no password protection for your profile.  For normal home use, though, this method should work just fine.

I hope that this is of some help to you, and fi you have any further questions, please post back.

For more information on Thunderbird profile security, [see here]("http://kb.mozillazine.org/Protect_the_profiles_contents").

Take care.

---

