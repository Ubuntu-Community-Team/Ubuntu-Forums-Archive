---
title: "adding users"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by gmhikin03 on 2006-05-21
as i was going through the installation of breezy this morning.  i came to adding a user.  i did the full name, the username, then the passwords.  then it took me back to enter a full name again.  it seemed to be in a loop.  so i just said go back.  and went to the next part of the installation.  thinking it would ask me to enter a user somewhere else.  i finished the first part of the installation and rebooted.  it told me to enter a user again.  it started the same loop.  so eventually i just said create one later.  it brought me to the login screen.  so i tried the user name that i tried to use.  but wouldn't work.  so i hit crtl+alt+f1 and got logged in as root.  i tried adding a new user and just got this 

root@gregubuntu:~# adduser
Enter username to add: greg
Adding user 'greg'...
adding group 'greg' (1000).
adding new user 'greg' (1000) with group 'greg'.
creating home directory '/home/greg'.
chown 1000:1000 /home/greg: operation not permitted
cleaning up
removing directory '/home/greg'
removing user 'greg'
removing group 'greg'
groupdel: group name does not exist.
root@gregubuntu:~#

im not sure what to do.  any help would be appreciated.

g

---

### Post by it.henrik on 2006-05-21
Were you doing a clean installation or mounting an existing filesystem?

How ever .. the installation of Breezy doesnt work on your computer and since it is only less then 10 days till the next version of Ubuntu, Dapper Drake. I recommend you to either install the BETA 2 of Dapper or just sit back and wait for ten more days :)

---

### Post by Sef on 2006-05-21
Were you doing an expert install?

---

### Post by gmhikin03 on 2006-05-21
no i wasn't doing an expert install.  just a regular install.  could it be from the partioning i did.  im putting it on my second hard drive thats 120 gigs.  i resized my ntfs for windows to 70gigs using the gparted live cd.  then i created the other partions while doing the install. 

fat32 - 25 gigs with the mount point /home
ext3  - 15 gigs with mount point /
swap - 900 MB's or so

i got my cd from shipit.  should i try to use one of the other cds i recieved.

g

---

### Post by gmhikin03 on 2006-05-21
ok, i redid the installation.  i used one of the other cds.  and when it came to partioning i just created an ext3 and swap partion, and left the rest free to create the fat32 later.  so now i have a user set up, and its working great.  now i just need to figure out how to get xserver to work.  i figured it would be a problem because i had to do an expert boot with the live cd.  hopefully ill get xserver working.

g

---

### Post by gmhikin03 on 2006-05-21
ok,  i have gotten everything working.  im writing this from ubutnu.  

g

---

### Post by Mustard on 2006-05-21
Well done. :)

---

