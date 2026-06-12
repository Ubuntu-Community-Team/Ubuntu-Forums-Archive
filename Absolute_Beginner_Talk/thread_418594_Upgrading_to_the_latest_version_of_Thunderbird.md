---
title: "Upgrading to the latest version of Thunderbird"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2007-04-22
I am try to upgrade, but after downloading the compresses file package, I have no idea where to put the files.  They are pre-compiled and the program runs directly from the folder, but of course none of my contacts, or mailboxes exist.  So where is it that I have to move these new files to?

Thanks

---

### Post by RobsterUK on 2007-04-22
Try [this page]("https://help.ubuntu.com/community/ThunderbirdNewVersion")

---

### Post by chris.olsen on 2007-04-23
the installation worked well (the script failed, but manually installing it worked), but the transferring over of my contacts, email and mail filters did not.  and for some reason I cannot access the previous version as is mentioned in the page of the link you provided.

Has anyone else had the same problems?

Update:

There is a mistake in the copy command listed in that post.  If you copy and paste what is there it will copy the current config dir to a sub-dir in the new directory, which is not what you want.  Instead use the below and it will work as it should

cp -r .mozilla-thunderbird/* .thunderbird

---

### Post by myddrin on 2007-04-24
So, I followed the directions to run the script as mentioned in the wiki.  I ran into an issue and solved it. I'm posting the solution here, in case someone else hits the problem.

When I started thunderbird, I had a wierd menu at the bottom that said "<menu id="offlineMenuItem" ... , it was clearly an XML parsing error.  Digging deeper, there was an undefined entity....

After much digging around, I already had a version of thunderbird (1.5) installed in opt from back in the warty days (or hoary, or something).  At any rate, deleting the existing /opt/thunderbird and re-running the script solved the problem.

---

### Post by prasad_bhatla on 2007-04-24
HI

# Using Ubuntu Edgy 6.10 with a slow internet, I downloaded Thunderbird 2.0 tar.gz file  onto a  USB stick on a PC with broadband connection.
                       
# Checking if its really there

cd /media/usbdisk/Ubuntu 
ls

# Moving the file to /opt 

sudo mv thunderbird-2.0.0.0.tar.gz /opt/

# Extracting the tar.gz file  in the /opt directory

sudo tar -xvvzf /opt/thunderbird-2.0.0.0.tar.gz 

# Checking , extracting creates the thunderbird directory in /opt
ls

# List of files extracted

cd /opt/thunderbird
ls

# At this stage if  :

sudo /opt/thunderbird/thunderbird

# Thunderbird is launched fine and I can set up an email profile .

 But I need a launcher on the desktop so right clik on the desktop , Create Launcher, fill in details, for the "Command" enter /opt/thunderbird/thunderbird. Click "Close". This will created an icon to start Thunderbird from the Desktop. 

But when I launch from here , I get a weird error about Profile creation failed as the file could not be written. I have checked permissions in the launcher and the file has read/write permissions for all.

Help !!


Prasad

---

### Post by Bachstelze on 2007-04-24
This is precisely why you should **never** run a GUI app with *sudo*. Your Thunderbird profile is owned by root so no wonder you can't access it. Delete it and try again.

---

### Post by aysiu on 2007-04-24
> **HymnToLife said:**
> This is precisely why you should **never** run a GUI app with *sudo*. Your Thunderbird profile is owned by root so no wonder you can't access it. Delete it and try again. HymnToLife speaks the truth.

Great: ```
thunderbird
``` Okay for upgrading: ```
gksudo thunderbird
``` **Never** do this: ```
sudo thunderbird
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by prasad_bhatla on 2007-04-24
Many thanks HymnToLife  and aysiu for pointing out sudo and gksudo.

U rock  :guitar: 

I deleted the /.thunderbird folder in my home directory and Thunderbird now works fine.

I had to do the same for the /.mozilla folder to get Firefox up and running.

Cheers

Prasad

---

