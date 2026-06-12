---
title: "Help with Evolution"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-08-28
Well, I just installed Ubuntu and I absolutly love it, but I want to set up Gmail for evolution, like I had on thunderbird but I dont know how, I cant find any instructions on how to, please help.

---

### Post by TwistesdTexan on 2006-08-28
Unless you just love evolution, You can still install Thunderbird.:)
You can install Thunderbird through Automatix.

---

### Post by Drakkor on 2006-08-28
You could install Thunderbird on Ubuntu ,but someone may have an answer for Evolution.

---

### Post by xyz on 2006-08-28
Try these...hope it helps

> 

   

In Evolution:

   1. Select Edit->Preferences
   2. Select the “Mail Accounts” tab and click “Add”
   3. Fill in the required fields, when asked for e-mail address, input USERNAME@HOSTNAME (where USERNAME is your username and HOSTNAME is the hostname of the machine (try “localhost” if you aren’t sure)
   4. For “Server Type in Receiving Email”, select “Local Delivery”. 
   4. input box Path enter: /var/spool/mail/USERNAME (replace USERNAME with your username).
   5. Follow throw and complete creating the account

You’re done. Now you can read the local system mail using Evolution.

I got this from: [http://ubuntu.wordpress.com](http://ubuntu.wordpress.com)

Also: [http://ubuntuforums.org/showthread.php?p=1052483](http://ubuntuforums.org/showthread.php?p=1052483)

---

### Post by Anonii on 2006-08-28
> **Narcoleptic_Insomniac said:**
> Well, I just installed Ubuntu and I absolutly love it, but I want to set up Gmail for evolution, like I had on thunderbird but I dont know how, I cant find any instructions on how to, please help.

IF YOU DONT have evolution already , fire up: "sudo apt-get install evolution" in terminal, to easily install it.

Now, you can follow this guide:
[http://ubuntuforums.org/showthread.php?t=127448](http://ubuntuforums.org/showthread.php?t=127448)
to easily configure your evolution.
Good luck, and dont forget to report back here.

---

### Post by jimrz on 2006-08-28
> **Narcoleptic_Insomniac said:**
> Well, I just installed Ubuntu and I absolutly love it, but I want to set up Gmail for evolution, like I had on thunderbird but I dont know how, I cant find any instructions on how to, please help.

login to Gmail website...then on your page @ top right corner (next to your login name) click link for "setting"...on settings page click on "Forwarding and PoP"   make sure you enable PoP then save changes...go back to settings page / Forwarding and PoP and click on "Configuration instructions"...then click on "other", will open Gmail help page listing the settings you need to get evolution working with it...enter these in evolution via Edit > Preferences > Mail Accounts > "your Gmail" (or add this acct if not already started).

---

