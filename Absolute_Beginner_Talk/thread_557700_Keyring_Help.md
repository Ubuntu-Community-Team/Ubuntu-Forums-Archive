---
title: "Keyring Help"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by dellis.gjc on 2007-09-23
I guess I don't understand how to use Gnome Keyring.  I've used password managers in Windows (Roboform) and Mac OS X (Keychain), but Keyring is another matter.  I searched for how-to's, but nothing seems to locate anything of value.

I'm using Ubuntu 7.04, 64-bit.  I can open Keyring Manager and the default keyring OK.  If I enter username and password on a web site, the Keyring doesn't notice.  Obviously I'm missing something.

Dale :confused:

---

### Post by dwhitney67 on 2007-09-23
What are you trying to do?  Your post was not too clear.

I recently helped out someone with a 'keyring' problem in that she was annoyed at having to type in the password everytime she logged in.  The solution I gave her was to delete the keyring file in ~/.gnome2.

Since I cannot comment on your issue perhaps you should consider supplying more information so that perhaps I, or someone else on the forum can help you.

---

### Post by lisati on 2007-09-23
If you're annoyed at entering a password every time you log on, you might try the following, which is based in information at [http://ubuntuforums.org/showthread.php?t=463621&highlight=keyring](http://ubuntuforums.org/showthread.php?t=463621&highlight=keyring)

Step 1: Type the following at the terminal:
```

sudo apt-get install libpam-keyring
sudo gedit /etc/pam.d/gdm

```
Step 2: Add the following lines to the end of the file:
```

# use session pw for gnome-keyring
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
@include common-pamkeyring

```
Step 3: save the file, and exit

Hope this helps!

---

### Post by lisati on 2007-09-23
Oh, by the way, to the best of my knowledge (perhaps someone can correct me if I'm mistaken)  the keyring manager has little (if anything) to do with saving passwords for websites.

---

### Post by mcduck on 2007-09-23
> **lisati said:**
> Oh, by the way, to the best of my knowledge (perhaps someone can correct me if I'm mistaken)  the keyring manager has little (if anything) to do with saving passwords for websites.

That's right. Only programs that are made to use Gnome's keyring store their data with it. And Firefox doesn't do that, it has it's own password manager.

---

### Post by dellis.gjc on 2007-09-23
> **mcduck said:**
> That's right. Only programs that are made to use Gnome's keyring store their data with it. And Firefox doesn't do that, it has it's own password manager.

Ahhh.  Now I know why my Firefox entries didn't show up in the keyring.  So, is there a password manager, other than Firefox itself, that will store passwords entered in Firefox?

Dale

---

### Post by dellis.gjc on 2007-09-23
> **dellis.gjc said:**
> Ahhh.  Now I know why my Firefox entries didn't show up in the keyring.  So, is there a password manager, other than Firefox itself, that will store passwords entered in Firefox?

Dale

I found Gorilla, and I am testing this now.  If anyone has experience with it, or knows of a better manager, I'd appreciate hearing about it.

Thanks.

Dale

---

### Post by mlentink on 2007-09-23
You might want to take a look at KeepassX, which is in the repo's

---

### Post by dellis.gjc on 2007-09-23
> **mlentink said:**
> You might want to take a look at KeepassX, which is in the repo's

Thanks -- I'll do that!  :)

---

### Post by jqball2u on 2007-09-25
> **mcduck said:**
> That's right. Only programs that are made to use Gnome's keyring store their data with it. And Firefox doesn't do that, it has it's own password manager.

Ok, you sort of answered the question I came here to look for; specifically, "What the heck is a Keyring / Keyring Manager for?". What (Gnome) programs use Keyring / Keyring Manager? (and why) :lolflag:

I am new to Ubuntu ... I've used several different distro's of Linux in the last several years (as well as MS' Windows ... which sucks! :). I really like Linux a lot and, so far, I really like Ubuntu! I've been thinking of checking out Edubuntu (I am an electrician and we've been remodeling / adding-on to some local schools; I've been thinking that Edubuntu might be a better alternative for them than MS Windows?), as well as Xubuntu, & Kubuntu, etc. Also, I want to bring Linux to other MS Windows users & educate them in using Linux; although, I do not know how to use the Unix 'command prompt', yet! (sigh) That's in the (near?) future, I hope! :)

Thanks all & I look forward to getting to know ya'll,
James

---

### Post by mcduck on 2007-09-25
> **jqball2u said:**
> Ok, you sort of answered the question I came here to look for; specifically, "What the heck is a Keyring / Keyring Manager for?". What (Gnome) programs use Keyring / Keyring Manager? (and why) :lolflag:

I am new to Ubuntu ... I've used several different distro's of Linux in the last several years (as well as MS' Windows ... which sucks! :). I really like Linux a lot and, so far, I really like Ubuntu! I've been thinking of checking out Edubuntu (I am an electrician and we've been remodeling / adding-on to some local schools; I've been thinking that Edubuntu might be a better alternative for them than MS Windows?), as well as Xubuntu, & Kubuntu, etc. Also, I want to bring Linux to other MS Windows users & educate them in using Linux; although, I do not know how to use the Unix 'command prompt', yet! (sigh) That's in the (near?) future, I hope! :)

Thanks all & I look forward to getting to know ya'll,
James

For example the Network Manager stores your wireless network keys in the keyring. It's also used by GPG to store your signing/encryption keys, and I remember that keys for repositories would be there as well.

The point is that every application shouldn't have to implement their own way of storing keys. It would be easier for both application developers and the end user if all keys were stored in one place, and accessed with single password (in best case the at the time you log into desktop, without asking for the keyring password separately).

Only problem is that all applications don't use the Gnome Keyring, for example Firefox has chosen to use it's own system for storing keys instead.

---

### Post by nebbe on 2007-09-25
So f*cking annoying!

My /etc/pam.d/gdm:

#%PAM-1.0
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password
## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so
@include common-pamkeyring

Doesnt work :(

Ive sudo apt-get --purged removed gnome-keyring-manager gnome-keyring libpam- and those..  Updated system, Reinstalled them, Doesnt do it for me. Still that god damn irritating popup-window :(

Suggestions? Couse its driving me MAD. I changed to "wicd" for a while.. but then other things that i needed for my network didnt work, and i really want network-manager.

system: x64 AMD

cheers.

---

