---
title: "GMail FS permissions help"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by Ian505 on 2008-01-04
I would like to use GmailFS with my gmail account... but I am having some trouble setting it up. The instructions on the GmailFS site do not include fetching it from an application such as synaptic, and I couldn't find a help package. 

I stumbled upon a file called gmailfs.conf which I assume is the configuration file... but when I try to edit it with my info, I get an error saying I don't have permission. The permissions tab under properties has root as the user with read/write.

And even if I get the configuration set up... I have no idea how to mount this thing.

Help?

-Ian

---

### Post by Bufke on 2008-01-04
Open a terminal and type 
```
sudo apt-get install gmailfs
```
after installation is should work just like the website describes it.

I prefer using the firefox extension Gspace, it does the same thing, but it's more like using a FTP client.  It's easier to use and you don't need to mount any drives.

Hope that helps

---

### Post by Ian505 on 2008-01-05
Wow... Gspace is MUCH better- and more convenient for me as I use FireFTP anyway! 

Only one problem... I would like to create a label that will filter out any messages sent by Gspace and have them skip the inbox. Do you know how to do this? It is kind of important that I can... for organization.

-Ian

---

### Post by Bufke on 2008-01-05
Yep, just create a new filter and in the Has the words: box put GSPACE.  Mark the skip the inbox, you could also apply a lable for it, in case you need to access without GSPACE.

---

### Post by Ian505 on 2008-01-05
Thanks! Problem solved.

-Ian

---

