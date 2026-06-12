---
title: "copying accross the network"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by michael_besselman on 2007-05-20
I am trying to copy an entire folder from a mounted drive on my desktop computer to laptop computer.  I have SSH installed and I can see the folder on the desktop from the laptop, but I can't seem to get the correct command line for the scp command to copy the entire folder.

Thanks

---

### Post by chamberlain2006 on 2007-05-20
You can use the connect to server option in the Places menu, and select SSH.

---

### Post by michael_besselman on 2007-05-20
My laptop has Xubuntu.  There is no Places.  How do I get it on that machine?

---

### Post by chrisven on 2007-05-20
To copy a folder from hostB to hostA, while logged in to hostB first cd to the directory on HostB which contains the folder you want to copy:

bash$ scp -r folder [email]username@hostA.com[/email]:.
(creates new folder if the folder does not exist, again in user's home directory)

Note the period after the : it denotes the users home dir.
So try this logged into your workstation sending the file to your laptop?

---

