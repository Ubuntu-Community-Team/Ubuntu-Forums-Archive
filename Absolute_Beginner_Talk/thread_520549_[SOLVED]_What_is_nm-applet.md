---
title: "[SOLVED] What is nm-applet?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by paker on 2007-08-08
Is it safe to follow the "how to remove nm-applet password screen" threads?

Like many wireless users, I am annoyed by nm-applet requesting password. Apparently, it is not the log-in password. It is not the network password, either. I have always selected "deny" and wireless started right away. I found several threads here and would like to try. But before I do it, I would like to know what nm-applet is and if following the suggested solutions is safe. FYI, my wireless works without entering nm-applet password.

---

### Post by Nexus... on 2007-08-08
Hope this is what you were looking for :) just goto the link there is a walkthrough there.

[http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874)

---

### Post by Inxsible on 2007-08-08
nm-applet is the application that manages your network connections.

if you have a  WEP or WPA enabled network, then nm-applet stores your password(s) in a encrypted file so that you dont have to give the entire key for different wireless networks. The password it asks for is the password for the encrypted file.

Technically it should be a different password than your login password and wireless network password. But you do get the annoying dialog box.

You can follow the threads to get rid of it without any problems.

---

### Post by paker on 2007-08-08
Finding how-to threads is not a problem. One of the methods is appending gdm file. I read a comment that the method was basically replacing keyring password with log-in password.

Inxsible,
Yes, I have WPA-enabled network. According to your post, it needs to be different from log-in or network password. Should I still follow the method? Another comment for another method was that it removed nm-applet password completely, and would be equivalent to opening the network. With these conflicting statements I cannot tell which method to follow.

Nexus,
The link was based on the keyring password and log-in password to be the same. In my case, they are different. I enter log-in password. The nm-applet password screen pops back up. I enter network password. The same. Basically, I don't have the nm-applet password to the keyring. If I knew it, I would enter it.
Thanks.

---

### Post by Inxsible on 2007-08-08
If you are asking me if it is secure...then NO.

if you have a different nm-applet password, then some random person cannot access the internet even if he/she gains access to your computer. So that way it is a bit more secure.

But most times people do away with it, since they are the only users on the computer or they are careful enough to lock their computers if they leave it on their desks or whatever.

Edit: I have 3 passwords. one for login, another for my keyring and yet another for my network

---

### Post by paker on 2007-08-08
Inxsible:

Thanks for the quick reply. Let me ask you a related question.
Since it don't know the nm-applet password, I just hit "deny" and my network starts right away. What is going on? And how do I find the keyring password?

---

### Post by Inxsible on 2007-08-08
> **paker said:**
> Inxsible:

Thanks for the quick reply. Let me ask you a related question.
Since it don't know the nm-applet password, I just hit "deny" and my network starts right away. What is going on? And how do I find the keyring password?

Go to System --> Administration --> Keyring Manager. Delete the key that is present there. Then restart your machine. It will ask you if you want to create a new keyring password. you can then create a completely new password for your keyring, or use your login password (which will help you avoid the dialog on every restart--using all the threads that explain it well)

---

### Post by paker on 2007-08-09
> **Inxsible said:**
> Go to System --> Administration --> Keyring Manager. Delete the key that is present there. When I do System>Administration>Keyring Manager, the same nm-applet password screen pops up. Since I don't know what that is (I have never created one), I choose "deny." Then keyring is locked. I select "vew keyrings" I see two: Default is locked and Session is open. Thanks.

PS: I am not desperately annoyed by the nm-applet password screen. I just want to do the right thing. If I need to create/enter nm-applet password, I will gladly do that.

---

### Post by Inxsible on 2007-08-09
> **paker said:**
> When I do System>Administration>Keyring Manager, the same nm-applet password screen pops up. Since I don't know what that is (I have never created one), I choose "deny." Then keyring is locked. I select "vew keyrings" I see two: Default is locked and Session is open. Thanks.

PS: I am not desperately annoyed by the nm-applet password screen. I just want to do the right thing. If I need to create/enter nm-applet password, I will gladly do that.
If you click on default, does it show you anything to the effect of "Passphrase for the network <your network name>"

If not, it means that you havent created a keyring password and you should(if you want)

About doing the right thing -- well, it all depends on person to person. Some people want an extra layer of encryption, yet others feel that it is redundant if they are careful about it. It all depends on what you want.

---

### Post by paker on 2007-08-09
> If you click on default, does it show you anything to the effect of "Passphrase for the network <your network name>"No, it doesn't. 
I cannot delete or create a keyring. When I attempt to, pop up screen reads: keyring daemon is not running. I guess it's because I did not provide keyring password to begin with.  It is way above my head. Unless someone tells me what to do, I cannot figure it out myself. Thanks.

---

### Post by Inxsible on 2007-08-09
So what do you want to do?

Do you want to create a password or not? If you keep clicking 'Deny', then you wont create a password or on the same dialog box if you enter a new password, that could become your new keyring password.

Choice is yours :)

---

### Post by paker on 2007-08-09
> **Inxsible said:**
> So what do you want to do?

Do you want to create a password or not? If you keep clicking 'Deny', then you wont create a password or on the same dialog box if you enter a new password, that could become your new keyring password.

Choice is yours :)I made myself misunderstood. The dialog box gave me just 2 choices,  Deny or enter the right password and hit Enter. Since I didn't have the password, I could not enter it. 

But the problem is solved. As you posted, in the keyring manager, I selected "Create a keyring." Computer response was "Keyring daemon not working." I gave up and turned off the computer.

I just came home and turned on the computer. Guess what. A different dialog box popped, prompting selection of password. Your instruction worked! Thanks.

Now I have a log-in password to the computer, a network password, and a keyring password. They are only slightly different that they are easy to remember. Thanks for guiding me step by step, and explaining what each step is about. May your God bless you richly.

EDIT: In post #7, you said to restart the computer. Which was what I did above basically, but unknowingly.

---

### Post by Inxsible on 2007-08-10
Glad to know that it worked. Make sure you mark the thread as solved for others with similar problems. :)

---

