---
title: "Ubuntu server as a domain controller?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by Louisme2 on 2007-04-13
Hi,

I have only just installed my first Linux box today and am very new to Linux so please forgive any silly questions!

I have installed Ubuntu Server 6.10 and wondered how I could use it as a file server for Windows based pc’s, someone suggested Samba which I have now installed and configured (with much online help!). A windows user with an account on a remote XP pc can now log on and access their Linux home directory – hurray!

I want the Windows users to be able to access files (work and email folders) from any pc. Is it possible to setup Ubuntu as a domain controller like NT4 where users can logon to the domain which would automatically create a share to their home directory?  I am trying to avoid creating multiple local users on PC’s – any advice as to where I should start?

You help would be much appreciated!

Thanks,

Louis

---

### Post by lamalex on 2007-04-13
search how to set up LDAP.

---

### Post by Steven Heuser on 2007-04-13
Actually I've got samba set up as a domain controller for a small home network (3 dual boot Win XP Pro / Ubutnu Fiesty clients and 1 Edgy server). Setting up samba as a domain controller was pretty easy to do. LDAP is much more powerful but can be pretty hard to set up. Don't ask me about LDAP though - I looked into and decided to use NIS (yellow pages) for authentication of my Ubuntu clients.
-Steve

---

