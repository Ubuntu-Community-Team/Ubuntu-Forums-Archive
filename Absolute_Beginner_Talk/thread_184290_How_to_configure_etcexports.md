---
title: "How to configure /etc/exports"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-05-29
Here is my problem I want to configure /ect/exports but I don't know how.  I go into vi /ect/exports but it is asking me to input the client and it's information but I don't know exactly how to input it.  Here is an example:
[B]/home @myclients(rw,sync)
/usr/local @myclients(rw,sync)[/B]

Does @myclient the name of the host computer? For instance at the terminal mode prompt I have this on this computer:
**neogreen@ubuntulinux:/$**

Is ubuntulinux, myclient? and is usr neogreen? 
So I would input the information like this:
[B]/home@ubuntulinux(rw,sync)
/neogreen/local @ubuntulinux (rw,sync)[/B]

And where would I place it on the file?  

Please Help.

---

### Post by kzutter on 2006-05-29
A host name is a name of a computer.
You are setting up a server (hostname = ubunulinux) and it wants to know the hostname(s) of the clients that will be connecting to use its services.

The @ symbol is used here to denote a 'netgroup', unless you have set up netgroups, don't use the @ symbol.

Please read the man file.  Type 'man exports' at the command line.

Here is an example:
/home/neogreen     clientbox(rw,sync)

It says: Share folder /home/neogreen with someone connecting from a different computer that has the hostname of clientbox , allow reads and writes,  and syncronize changes.

Yes neogreen is your username, but we do not put usernames in the exports file.
In your example 'usr' is referring to a system folder - it does not mean user, it stands for Unix System Resources. Ignore it unless you 'want' to export your /usr folder.

Put the lines anywhere in the file.

Lines that start with # are ignored as well as blank lines.

Good luck,
-Ken

---

### Post by NeoGreen on 2006-06-07
Okay thanks, sorry it took me a while to reply:D

---

### Post by dvarsam on 2006-06-08
[QUOTE=NeoGreen]Okay thanks, sorry it took me a while to reply:D[/QUOTE]

Another way to see an example is the following:

1. From the Menu, select "System\Administration\Shared Folders"

2. Click on the button named "Add"

3. Under "Path:", select the Folder you want to share.

4. Under "Share with:", select "NFS"

5. Click on the button named "Add host"

6. Click on the button named "OK"

7. Click on the button named "OK"

8. Click on the button named "OK"

To see the example you created above, launch a Terminal window & type the following:
> cat /etc/exports

You should now see the following entry added:

> /home/dimitris/Desktop 192.168.1.0/255.255.255.0(rw)

However, I do NOT know how someone can add that "sync" command after the "(rw)" to get an "(rw,sync)" output...

Hope I helped.

---

