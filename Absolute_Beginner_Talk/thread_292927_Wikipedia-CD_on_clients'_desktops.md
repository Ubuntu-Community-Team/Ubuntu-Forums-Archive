---
title: "Wikipedia-CD on clients' desktops"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by CastleMaster on 2006-11-04
I volunteer at a non-profit where we have installed Edubuntu 6.1 Server on a PC. We also have some thin client workstations which boot from the server, and set up some 'student' user accounts. All is fine and dandy.

Wikipedia-CD is a hand selection of about 2000 articles taken from a snapshot of the Wikipedia site. 

[http://fixedreference.org/2006-Wikipedia-CD-Selection/](http://fixedreference.org/2006-Wikipedia-CD-Selection/)

I would like to make this Wikipedia CD (the folder I have downloaded) available on each clients desktop, without their
having to access the net. How would I go about doing this?

Is there a top level folder for general user read-only access?

How do I create a quick launcher or menu item for all users to access?

Thanks for any responses.

---

### Post by 23meg on 2006-11-04
Just copy the folder somewhere under their home folders, and drag and drop the index.html file (I assume you have one?) to the GNOME panel to create a panel shortcut, or middle-click and drag it to the desktop and hit "Link here" to create a link to it on the desktop.

---

### Post by CastleMaster on 2006-11-04
Thanks for you answer 23meg.

I would like to avoid duplication. If you have, say 20 users in
the classroom, that's 20 * 200 mb = 4 GB of space.

I would also like to take advantage of the whole server-client
thing Edubuntu has going. This means being able to make a single
change on the server and have it propagate to all the users.

I'm hoping there is a way to do this with a common folder and the proper permissions in place.

---

### Post by CastleMaster on 2006-11-06
Well I figured out the first part. This may
be more commands than needed, but it works.

Commands run from the /home directory

mkdir public
sudo chmod 777 public
cp -Rv admin1/Desktop/SOS/ public/SOS
(This copied files from admin1 desktop.)
sudo chmod 755 public
(This sets files to read only for user access.)

I now have a directory accessable to all users.

Now hopefully with one modification to the menu system
all users can have access to the index.htm located
in 'public/SOS' Anyone have any hints?

---

