---
title: "Former Kubuntu User Wants Replacement for Smb4k"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by LaneLester on 2006-12-14
I have a home LAN on which my (K)Ubuntu machine connects to several Win XP boxes. When I run Kubuntu on a different partition, I use the KDE app Smb4K for easy connection to the Windows shares. Now that I've switched (or am switching) to Ubuntu, I'm trying not to use any KDE apps.

Some other newbie asked for help and was told to read all the documentation on Samba. I'm hoping for something less exhaustive and exhausting. :) 

Lane

---

### Post by deadgobby on 2006-12-14
Is there a reason why you do not want to run KDE apps? You can run both.
Gobby

---

### Post by LaneLester on 2006-12-14
It's just an experiment: is it possible to have a user-friendly experience with Ubuntu without KDE? Surely there are some true believers on here who can provide a positive answer. :) 

Lane

---

### Post by gunksta on 2006-12-14
Does Nautilus work for you?

Places --> Network Servers

or, if it's all locked up and such

Places --> Connect to Server...

This works for me at the office I work in. I'm the only 'nix box in the house.

--andy

---

### Post by meng on 2006-12-14
> **LaneLester said:**
> It's just an experiment: is it possible to have a user-friendly experience with Ubuntu without KDE? Surely there are some true believers on here who can provide a positive answer. :) 
Lane
As a pure GNOME user, I'ld say yes it is possible to have a great KDE-free experience. Surely there are many KDE users who don't miss GNOME. Now is it possible for YOU to have a great experience without KDE? Time will tell.

---

### Post by LaneLester on 2006-12-14
> **gunksta said:**
> Does Nautilus work for you?

Places --> Network Servers

Andy, it scans for a long time, and then finds "Windows Network," so far, so good.

I then click that entry, and my workgroup name "simbiosys" is substituted. More progress.

When I click the workgroup item, I get this error:
[INDENT]Couldn't display "smb:///simbiosys".
The location is not a folder.[/INDENT]

It may be need a username and password, but I don't know how to supply it.

> or, if it's all locked up and such
Places --> Connect to Server...

Trying this approach, I choose "Windows share" as the Service type. Then I need help. I presume the Server is the name of the computer I want to connect to. But do I need any slashes or anything else in addition to the name?

And is "Share" simply the name of the share?

What's with "Folder"? The share is a folder.

OK for the User Name, but how do I supply the password?

I guess I leave Domain Name blank, since I have a workgroup.

I know I'm asking a lot, but I'd sure appreciate getting this taken care of. It's the only thing remaining for a completely-useful Ubuntu installation.

Lane

---

### Post by meng on 2006-12-14
I find I have to enter the IP address, or else have the hostname and IP address linked in the /etc/hosts file.

---

### Post by LaneLester on 2006-12-14
> **meng said:**
> I find I have to enter the IP address, or else have the hostname and IP address linked in the /etc/hosts file.

I already had the hosts entries, but that wasn't sufficient. But your tip about the IP was exactly what I needed. Thank you very, very much.

Lane

---

