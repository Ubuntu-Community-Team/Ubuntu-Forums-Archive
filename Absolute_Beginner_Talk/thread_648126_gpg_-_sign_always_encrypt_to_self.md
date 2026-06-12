---
title: "gpg - sign always encrypt to self?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by yeehi on 2007-12-23
When using public key encryption to communicate, for every email, should we:

sign it?
encrypt to self?

When roaming terminals, should we export the private key to usb drive, and take it with us?

---

### Post by MalfunctioningMartian on 2007-12-28
If you think there's a chance that someone will try to impersonate the person you're communicating with or change the message, sign it. Ask yourself, if someone impersonates the sender and/or changes the message what kind of damage would it do?

For encryption, ask yourself, what would happen if the worst possible person who could read it reads it what kind of damage would it do?

For carrying it around on a USB drive. You could do that, but make sure that:

A Nobody who shouldn't reads the key on the drive.
B Nobody changes the key. 
C You have a revocation certificate.
D You use a *strong* password.

I don't know too much about ways to secure the key on a USB drive, but encrypting it with truecrypt and storing truecrypt travellers version on the drive sounds like a good idea. If you're extra paranoid use a hidden volume.

If you decide to use truecrypt tell me and I'll give you a walktrough.

---

### Post by Chayak on 2007-12-28
> **yeehi said:**
> When using public key encryption to communicate, for every email, should we:

sign it?
encrypt to self?

When roaming terminals, should we export the private key to usb drive, and take it with us?

This is a question that first you need to assess your risk.  If you go to security cons like Defcon and such I'd suggest even more security including LUKS encryption on your harddrive and booting your system from a usb key that you have an encrypted spare hidden on your body.  Then set up a bluetooth proximity monitor [http://gentoo-wiki.com/TIP_Bluetooth_Proximity_Monitor]("http://gentoo-wiki.com/TIP_Bluetooth_Proximity_Monitor") so whenever the laptop gets out of the range of your phone it will lock itself down or when you walk away for more than thirty seconds.  Tunnel to a secure system whenever you travel, don't trust public wifi.

If you want to open your sent messages later encrypt it to yourself.  You should sign any message you care about so people on the other end can verify that it's from you and hasn't been changed.  There are situations where you may want to send an unsigned encrypted message to someone to get important data across that can't be confirmed to come from you.

Then there are backups... are your backups encrypted?  They should be if they're not thats a huge hole in security.  If you don't make backups then you really really should.  It's only a matter of time before a hard drive fails or gets corrupted. (I learned the hard way, loosing three drives in one month).  There are methods for doing this, truecrypt works well as you can create a dvd size image, copy everything you need into it and then burn it to disk.

Oh and forget passwords use a ***passphrase*** with rainbow tables in wide use longer passwords are much less secure.  Pick a phrase you remember and mix a number or two into it such as *#Y0u should really tru$t n0 on3!* Yes it can be a pain but how serious are you about protecting your data? That's just an example but you should at least use something with 20 characters or more now and if you can throw another authentication method in the mix do it!  The works great on wifi routers using WPA/WPA2.  With a good passphrase they are extremely difficult to crack.  Avoid WEP like the plague.

I can go on, but I hope you get the general idea.  It depends on how much threat you realistically can assess for yourself.

---

### Post by yeehi on 2008-01-06
Cool posts! Very cool, chayak! How do I thank you? There is some button or something...

---

