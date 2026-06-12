---
title: "Keyring Manager"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by GaryLittlemore on 2007-10-16
On every boot I do, I get the keyring manage asking for my password because a keyring is lock. How do I stop it from asking everytime a boot my machine or set the keyring to unlocked.

I'm not even sure what the keyring is.

---

### Post by rich.bradshaw on 2007-10-16
Upgrade to Gutsy.

Keyring is where all passwords for things are stored. Firefox doesn't use it, but everything else in Gnome stores passwords in the keyring.

This includes wireless keys, email in evolution, that sort of thing.

In gutsy you aren't asked for it for wireless passwords, so you won't see it on boot all the time.

---

### Post by Martin Witte on 2007-10-16
see this thread [http://ubuntuforums.org/showthread.php?t=463621](http://ubuntuforums.org/showthread.php?t=463621), page 2

---

### Post by ghost_ryder35 on 2007-10-16
When using Feisty Fawn with Network Manager controlling your wireless it adds the WEP and WPA code to the keyring manager, in some cases this causes problems and is annoying since you want to be able to log into your computer and be connected automatically to the internet. With the keyring manager you have to manually enter your keyring password every time before you are allowed to connect to the wireless network. To remove this keyring password prompt,

sudo apt-get install libpam-keyring
sudo gedit /etc/pam.d/gdm
and add this line:
@include common-pamkeyring
to the bottom of your /etc/pam.d/gdm file, Then reboot and enjoy.

---

### Post by Mazza558 on 2007-10-16
I'm on Gutsy and it doesn't remember the default keyring.

---

### Post by bliffle on 2007-10-16
How can I change the password for the default keyring? Must I make a new keyring, make it the default, then copy/move everything there?

---

### Post by ghost_ryder35 on 2007-10-16
> **Mazza558 said:**
> I'm on Gutsy and it doesn't remember the default keyring.
mine does

---

### Post by ghost_ryder35 on 2007-10-16
> **bliffle said:**
> How can I change the password for the default keyring? Must I make a new keyring, make it the default, then copy/move everything there?

delete the key in the key ring manager and then make a new one

---

### Post by leona on 2007-10-16
Thank you, I was wondering what the heck was going on with this Keyring thing, all my wireless machines keep asking for passwords, I mean you've already logged in, why it ask again, madness, glad its sorted in next release, only 2 days to wait :)

---

### Post by GaryLittlemore on 2007-10-16
> **rich.bradshaw said:**
> Upgrade to Gutsy.

Keyring is where all passwords for things are stored. Firefox doesn't use it, but everything else in Gnome stores passwords in the keyring.

This includes wireless keys, email in evolution, that sort of thing.

In gutsy you aren't asked for it for wireless passwords, so you won't see it on boot all the time.

I am already on Gutsy...

> **ghost_ryder35 said:**
> When using Feisty Fawn with Network Manager controlling your wireless it adds the WEP and WPA code to the keyring manager, in some cases this causes problems and is annoying since you want to be able to log into your computer and be connected automatically to the internet. With the keyring manager you have to manually enter your keyring password every time before you are allowed to connect to the wireless network. To remove this keyring password prompt,

sudo apt-get install libpam-keyring
sudo gedit /etc/pam.d/gdm
and add this line:
@include common-pamkeyring
to the bottom of your /etc/pam.d/gdm file, Then reboot and enjoy.

Done this and it still asked for the password after a reboot.

---

### Post by MattPalmer on 2007-10-20
I upgraded to Gutsy and it also prompted me for the keyring password for the network after rebooting.  Then I noticed that there is a checkbox at the bottom of the keyring prompt for the network manager to not prompt again once logged in.  Problem solved!

---

### Post by leona on 2007-10-20
> **MattPalmer said:**
> I upgraded to Gutsy and it also prompted me for the keyring password for the network after rebooting.  Then I noticed that there is a checkbox at the bottom of the keyring prompt for the network manager to not prompt again once logged in.  Problem solved!
Noticed that too after upgrading the notebook, was just about to post saying this dam box came up again and then  like you noticed the "automatic log in" box, ticked and its gone away, Thanks :)

---

### Post by joshzam on 2007-10-21
I'd like to share what took me a few hours to figure out on my own. Maybe it'll spare someone else the hair-pulling that I've suffered.

I've got a clean Gutsy install on my laptop. I didn't want to have to enter my login or keyring passwords at startup. Auto login for Ubuntu worked fine but I kept getting asked for my keyring password to connect to my WiFi router. I searched the forums and followed about a dozen different suggestions involving:
- install Pam
- install Wicd
- edit the /etc/pam.d/gdm file
- configure the Keyring manager
- etc. etc.

Then I found this thread and i thought that my prayers were answered. What a fool I was for not noticing the checkbox at the bottom of the keyring prompt to log in automatically! I rebooted and... there was no checkbox!!

search... search... search... answer :)

The default network configuration for my wireless modem was set to 'roaming' (as indicated by the WiFi strength meter as the network icon). I removed the roaming option and configured my network manually (the network icon changed to the double LCD monitors). After the next reboot, I wasn't asked for either my Ubuntu login or my keyring password. It just worked.

I hope this helps others with the same problem.

---

### Post by markp1989 on 2007-10-24
> **rich.bradshaw said:**
> Upgrade to Gutsy.

Keyring is where all passwords for things are stored. Firefox doesn't use it, but everything else in Gnome stores passwords in the keyring.

This includes wireless keys, email in evolution, that sort of thing.

In gutsy you aren't asked for it for wireless passwords, so you won't see it on boot all the time.

i have gusty installed and i keep getting asked my keyring password every boot

---

### Post by NilsE on 2007-10-24
markp1989

Next time it asks you look for the check box on the popup to stop it from asking every time.

---

### Post by markp1989 on 2007-10-24
> **NilsE said:**
> markp1989

Next time it asks you look for the check box on the popup to stop it from asking every time.

there is not one i have checked, does it make any difference that i am using xubuntu?

---

### Post by NilsE on 2007-10-24
> **markp1989 said:**
> there is not one i have checked, does it make any difference that i am using xubuntu?
Oooops, could be.  See if you can find the pam keyring manager equivalent for xubuntu and follow it's instructions.

---

### Post by Don Cox on 2007-10-25
> **NilsE said:**
> markp1989

Next time it asks you look for the check box on the popup to stop it from asking every time.

How can this procedure be reversed? 

Don Cox

---

### Post by GaryLittlemore on 2007-11-15
Mine doesn't give me an option to tick to stop asking next time, Can someone help please.

---

### Post by tact on 2007-11-15
Not sure if this relates to some of the problem that some people are seeing...

In normal use when you first install gutsy and first log in the gnome keyring (where wifi passwords are stored) will just use your log in password...  with login and gnome keyring passwords the same (in gutsy) you do not get asked for the gnome keyring password after logging in.

If you change your log in password for any reason...  that does NOT change your gnome keyring password.  This breaks the way it is supposed to work as above...  cos the two passwords are now different.

You can reset the gnome keyring to be same as login password again by deleting this file:
/home/username/.gnome2/keyrings/login.keyring

I notice (but never tried) that in gutsy you can go Applications>Accessories>Passwords & Encryption keys...then Edit>Preferences>Gnome keyring and change the password there.  See if that works.

For those with different passwords for login and gnome keyring - make them the same and then you should not be asked for the gnome keyring password after log in

---

### Post by GaryLittlemore on 2007-11-15
> **tact said:**
> I notice (but never tried) that in gutsy you can go Applications>Accessories>Passwords & Encryption keys...then Edit>Preferences>Gnome keyring and change the password there.  See if that works.

Mine hasn't got this in Accessories??? Please someone help me, this is doing my nut in.

---

### Post by bergamot on 2007-11-15
It was doing my nut in too, but I've worked it out now.

Xubuntu doesn't have the keyring manager application installed unlike the full-fat Ubuntu*, so you have to go to Synaptic, search for and install gnome-keyring-manager. Then you will find it in applications -> system. You can then tell it to stop asking for the password (in fact, if I remember correctly, I didn't really have to do anything much apart from open the application)

Hope that stops you pulling your hair out!

*Xubuntu is semi-skimmed

---

### Post by KOTAPAKA on 2007-11-15
> **rich.bradshaw said:**
> Upgrade to Gutsy.

Keyring is where all passwords for things are stored. Firefox doesn't use it, but everything else in Gnome stores passwords in the keyring.

This includes wireless keys, email in evolution, that sort of thing.

In gutsy you aren't asked for it for wireless passwords, so you won't see it on boot all the time.

You actually are asked on every single reboot. I have to find a way to switch it of - it is very annoying.

---

### Post by tact on 2007-11-15
> **GaryLittlemore said:**
> Mine hasn't got this in Accessories??? Please someone help me, this is doing my nut in.

Check/install seahorse from the repos...  then you will have the application in Accessories.

Its not needed tho.  Just delete the file I mentioned.  It is safe to do so.  Then when you log out and back in the file is created again and when it is recreated gnome-keyring will again have the same password as login

There are other posts in these forums about deleting this file..  and it being safe to do so.

/home/.gnome2/keyrings/login.keyring

If you dont want to delete it then 
```
mv /home/.gnome2/keyrings/login.keyring /home/login.keyring.bak
```

This will only ensure that the password for gnome keyring is the same as login keyring.  (They must be the same or else you will be asked for the password for gnome keyring after login every time).   

Once you are sure this is correctly set then we look for other problems.

---

### Post by IagainstI on 2007-11-18
I have the keyring manager installed with gutsy ubuntu, and I couldn't get the keyring problem resolved; however, I found a workaround.  There is no way that I can find to turn off Xubuntu's asking for a keyring password through the keyring manager or editing the pam file.  But, I went into Settings ==> Sessions and Startup Settings, opened the Advanced tab, deselected the "Launch Gnome services on startup" option, and on the next startup I was not asked for my keyring password.  I don't know exactly why this works or whether it is an appropriate solution for many users, but it works for me.  I was about to switch to WICD.

---

### Post by GaryLittlemore on 2007-11-19
Hi

Where is this 'Settings', I can't find it anywhere?

---

### Post by GaryLittlemore on 2007-11-20
Can anyone tell me where Settings ==> Sessions and startup settings is please?

> **IagainstI said:**
> I have the keyring manager installed with gutsy ubuntu, and I couldn't get the keyring problem resolved; however, I found a workaround.  There is no way that I can find to turn off Xubuntu's asking for a keyring password through the keyring manager or editing the pam file.  But, I went into Settings ==> Sessions and Startup Settings, opened the Advanced tab, deselected the "Launch Gnome services on startup" option, and on the next startup I was not asked for my keyring password.  I don't know exactly why this works or whether it is an appropriate solution for many users, but it works for me.  I was about to switch to WICD.

---

### Post by GaryLittlemore on 2007-11-21
Anyone???

---

### Post by TheDilettante on 2007-11-28
I can't find exactly what he's talking about either; what might be close, though I have no way of turning off GNOME in Ubuntu 7.10, is the 'Sessions' option in the System=>Preferences tab at the top of the screen.

Hope this helps at all.

---

### Post by st33med on 2007-11-29
nvm

---

