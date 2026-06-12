---
title: "Keyring manager"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by muddler on 2008-01-21
Is it safe to delete each keyring and establish new ones?:confused: All are locked now and I can't get online with ubuntu and am making this post using Windows XP. I don't know what I did to get into this mess.

---

### Post by muddler on 2008-01-21
After setting up a new network connection, I can get on line.

---

### Post by zorkerz on 2008-01-27
does anyone have a good link that explains how to use the keyring manager. Im trying to do a few things.

for starters I don't want it to ask me for a password for some wireless networks.

---

### Post by emarkd on 2008-01-27
I don't have a link for you, but a search for pam-keyring or something like that my turn up some good information.  I've got no experience with it personally.

---

### Post by zorkerz on 2008-01-27
I will try that where does the pam come from. The about info for it just says keyring manager and gives a link to the main gnome page, but I cant find it there either.

---

### Post by emarkd on 2008-01-27
A quick Synaptic search returns a package named libpam-gnome-keyring.  Don't know if that's what you're looking for or not.

---

### Post by zorkerz on 2008-01-27
some quick searching for libpam-gnome-keyring is not turning up much either. I get alot of ubuntu pages but have not found the projects page or anything directly dealing with it yet.

---

### Post by euler_fan on 2008-01-27
[This might be helpful.]("http://live.gnome.org/GnomeKeyring") Woo for Google.

I use KeePassX for my passwords and Seahorse for PKE/SSL Keys. There's a way to program KeePassX to automatically insert keys securely too, but in FF "Secure Login" works just fine.

---

### Post by zorkerz on 2008-01-27
Thanks Im looking at that link now. Seahorse does seem pretty cool. I have played with it a little bit  only because it comes default in hardy.

---

### Post by Majorix on 2008-01-27
I am assuming you are on Hardy since you talk about it (part of this might be only available on Hardy, I am not sure, that is why I have to assume). Install libpam-gnome-keyring through Synaptic or whatever you use to install packages (apt-get, adept etc) and then when it asks you for a key next time, click the checkbox under the textbox (I am not sure if this textbox was there with Gutsy) and the next time you boot off, you shouldn't be asked for a key for that specific network.

Hope it helps.

---

### Post by zorkerz on 2008-01-27
libpam-gnome-keyring is installed (I think this is a hardy thing but as I upgraded from feisty it could just be a leftover)

It has already stored my wireless network password in the default keyring. Every time I start up it asks for the password to the default keyring (which i think defaults to your login password??). There is no checkbox for this.

Two possibilities:
-there could be a checkbox when I first enter in wireless password.
-i have ubuntu set to autologin possibly if this is not set it will not ask for the default keyring password

I will report back.

---

### Post by zorkerz on 2008-01-27
-when i do not automatically login it does not ask for the default keyring password likely because i have already entered it in to login

-when creating a new key (ie the first time i enter in my wireless password) this is no checkbox option to not ask for the password in the future

So it appears that as of now there is no way to avoid entering in a password (either to login or to access the default keyring) when you first start up the network.

I understand from a security perspective this is a good thing and is a good way for the defaults to be setup but I am disappointed in the lack of custom ability.

My ideal  setup would be  to automatically login the computer and have a separate keyring for my home wireless and possibly other passwords with a simple password that my friends can use. This would enable trusted others to use the computer and access internet without my presence and without me giving up my root password but also have some means of protection if someone unwanted gets ahold of it.

Thanks for the help all

---

