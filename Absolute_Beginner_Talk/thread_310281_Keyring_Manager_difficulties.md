---
title: "Keyring Manager difficulties"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Frijolie on 2006-11-30
hey all,

I, after much tribulation, was finally able to get my Intel Pro/Wireless 2200BG wifi card to connect to my router with WPA+PSK security.

However, now on each and every logon I get a Keyring Manager popup which asks for my password. **see attached screenshots** I'm assuming the password is required for the keyring manager to give the network-manager my passkey for my wireless router, right? Is there not a way where you can allow the keyring manager to automatically give the network-manager my network passkey without me having to give it permission? There isn't anywhere, that I saw, that says "remember this password", "allow", "always allow", or even "deny". Any ideas? You don't have to write a script do you?

what is this keyring manager really used for? I guess is it just a secure place to put your username/password combos?

---

### Post by jsage on 2006-12-01
> **Frijolie said:**
>  now on each and every logon I get a Keyring Manager popup which asks for my password. 


try the instructions here:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo")

scroll down to the section entitled "Avoiding password nagging" for instructions on integrating pam-keyring.

jsage

---

### Post by Tulsapoke on 2007-02-23
Those instructions look pretty complicated.  I hope the get this fixed in the next version so it wont require this fix.  Using Suse or even XP all I had to do was leave the password blank in the key keeper and no more nags.

---

