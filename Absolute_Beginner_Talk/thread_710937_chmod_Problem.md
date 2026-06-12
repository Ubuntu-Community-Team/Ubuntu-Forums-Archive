---
title: "chmod Problem"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by renova on 2008-02-29
I have a permissions issue that is driving me crazy!

I have ubuntu lamp server running virtually on my vista box. I have a website that I'm creating on the linux server and accessing it from vista. I have a photo gallery folder that I upload jpgs to using a simple php script. I ran 'chmod 777' on my gallery folder. I can upload jpgs fine with the php script, but once they are there windows can't open them. The uploaded jpg permission is:

-rw------- 1 www-data www-data

Windows can see the jpgs I upload, but can't open them (access denied)

The pictures that I copy there manually through windows with samba show up as:

-rwxrwxrwx 1 renova renova    (renova is my username)

but when they are uploaded with my php script they are

-rw------- 1 www-data www-data

What is this newbie doing wrong? Thanks for your help!

---

### Post by Rocket2DMn on 2008-02-29
you need to use recursive chmod on the folder
```
chmod 755 -R /path/to/dir
```
You don't want 777 or somebody can overwrite them who shouldn't.  Also, adding new files later may need to have permissions applied to them separately.  You might be able to implement that in your php script by having it execute the chmod command through whatever means php allows you to run shell commands.

---

### Post by renova on 2008-02-29
Thanks for your help!

OK I ran that chmod on my directory, but now my upload script gets access denied when it tries to write the file:

Warning: move_uploaded_file(../assets/gallery/2402.JPG) [function.move-uploaded-file]: failed to open stream: Permission denied in /var/www/rh2/mgmt/uploader.php on line 14

---

### Post by Rocket2DMn on 2008-02-29
That would be because the script is not the same owner as the files.  The script should be owned by the user running the apache server and should have permissions 755 as well.  You may need to "chown" some files - the script has to be owned by the same user that the uploaded files belong to or else it can't write them.
As a matter of fact, the jpg's should probably just have 644 permissions since they are not executables.

---

### Post by igknighted on 2008-02-29
Off topic, but how powerful is that system to run a virtualized web server over vista?

---

### Post by renova on 2008-02-29
OK now the permissions for my php script are:

-rwxr-xr-x 1 www-data www-data

I still get the same error

---

### Post by renova on 2008-02-29
> **igknighted said:**
> Off topic, but how powerful is that system to run a virtualized web server over vista?

Core 2 duo 6600 2 gigs ram

I only use it to build and test sites before uploading them to the host on the internet. It runs plenty fast virtually for my purposes (since no one is hitting it but me). I've never noticed any lag whatsoever.

---

### Post by Rocket2DMn on 2008-02-29
Your "/var/www/rh2/mgmt/uploader.php" file should have the same owner as the directory you are trying to write to.  You may want to chown all your apache stuff to the user that apache is running under (it shouldn't be root!).  For security reasons, the apache server should be running under a limited user, and (don't quote me on this) that user should own the apache directory recursively.  Therefore with permissions like 644 for non-executable files and 755 for executable files (like your php scripts) means the script will have write permissions, but nobody else will.

---

### Post by renova on 2008-02-29
Problem SOLVED!!!

Everything you suggested helped get me closer and then the final hurdle was this:

The path referenced in my upload script was the samba share path /home/htdocs instead of /var/www

Changing ownership, permissions, and the path fixed the problem. I can now upload jpgs through my script and thumbnails are automatically generated.

Thank you SO MUCH for your help!!! I racked my brain for 5 hours straight on this before I asked for help. Next time I'll turn to the awesome ubuntu forums community sooner for support.

Thanks again!!!

---

