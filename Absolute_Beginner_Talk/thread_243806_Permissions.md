---
title: "Permissions"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-08-25
Is there a way to set all permissions to a partition or folder,**and**
everything it contains down to the indiviual file level ? Thanks  :)

---

### Post by TFX360 on 2006-08-25
Uhm, 

```
chown -R user /dir
```

should do the trick. Or even deeper?

Kind regards,


TFX

---

### Post by ciscosurfer on 2006-08-25
Absolutely. Use 'chmod' and modify your permission set to whatever you like...to include all directories below the a specific one, use the "*" (asterisk character).  For example```
sudo chmod 755 testfolder/*
``` Happy chmod'ing \\:D/

---

### Post by ciscosurfer on 2006-08-25
> **TFX360 said:**
> Uhm, 

```
chown -R user /dir
``` 
should do the trick. Or even deeper?

Kind regards,


TFX

This will recursively modify the directory you choose to the owner that you set.  This will not modify permissions.

---

### Post by Drakkor on 2006-08-25
Eeeek ! I guess one step deeper to the indiviual file level, I'm organizing my albums and songs on Amarok and it keeps saying no write permissions. I have been going gksudo nautilus,locating the files and selection properties permissions,but that's a real whole lot of work !! :(

---

### Post by kinematic on 2006-08-25
sudo chmod -R 755 /pathtodirectory will change the permissions recursively to the last file and make it world read/writeable if that's what you want.

---

### Post by ciscosurfer on 2006-08-25
> **kinematic said:**
> sudo chmod -R 755 /pathtodirectory will change the permissions recursively to the last file and make it world read/writeable if that's what you want.

[COLOR=Red]sudo chmod -R 755 /pathtodir[/COLOR] will accomplish the same task as [COLOR=Red]sudo chmod 755 pathtodir/*[/COLOR]

---

### Post by aysiu on 2006-08-25
FYI: Konqueror allows you to do recursive permission changes graphically.

All those command-line suggestions will work, though.

---

### Post by Drakkor on 2006-08-25
drakkor@drakkor:~$ sudo chmod 755  MUSIC/*
chmod: cannot access `MUSIC/*': No such file or directory
drakkor@drakkor:~$

---

### Post by kinematic on 2006-08-25
> **ciscosurfer said:**
> [COLOR=Red]sudo chmod -R 755 /pathtodir[/COLOR] will accomplish the same task as [COLOR=Red]sudo chmod 755 pathtodir/*[/COLOR]

didn't know that one but i guess i would have if i've read your post better :rolleyes: 
put a forward slash in front of it drakkor.
a drectory always starts with a "/"

---

### Post by aysiu on 2006-08-25
A few things here:

1. If you want the changes to be recursive, you need the *-R* option in there: ```
sudo chmod -R 755 MUSIC/*
```

2. File and folder names are case-sensitive. Are you sure it's *MUSIC* and not *Music* or *music*?

3. The way you've written it, you're trying to *chmod* a directory called /home/drakkor/MUSIC
Does that folder exist? If it's really /MUSIC, then you need that slash in there: ```
sudo chmod -R 755 /MUSIC
```

---

### Post by Drakkor on 2006-08-25
Ok,guys, did this: drakkor@drakkor:~$ sudo chmod -R 755 /Foghorn/*
drakkor@drakkor:~$

Now when I open up Foghorn and check permissions of MUSIC folder still can't write to it ! Should it be 777 ?

---

### Post by aysiu on 2006-08-25
Is /MUSIC a FAT32 or NTFS partition?

Or is just a folder?

---

### Post by Drakkor on 2006-08-25
It's inside a folder inside hda6 called Foghorn

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       /media/data     ext3    rw,user,auto,exec    0       0
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /windows        ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       /windows2       ntfs    nls=utf8,umask=0222        0       0
/dev/hda6       /Foghorn        ext3    rw,user,auto,exec    0       0

---

### Post by aysiu on 2006-08-25
Oh, so it's Ext3? In that case, I would advise you just *chown* it (change ownership): ```
sudo chown -R drakkor:drakkor /Foghorn/MUSIC
```

---

### Post by Drakkor on 2006-08-25
Cool ! :D  Thanks, aysiu !

---

### Post by TFX360 on 2006-08-25
Didn't I advice chown in my first post? :D

Kind regards,


TFX

---

### Post by ciscosurfer on 2006-08-25
You did, but from what Drakkor stated initially (the way it was described), chmod'ing the directory made perfect sense.  Because his situation was slightly different than originally assumed (by nearly all of us), using chown worked just fine.  For the record, just because a file or directory changes owners via chown, doesn't necessarily mean that permissions cascade down -- this is why chmod is effective and used as well in certain circumstances.  To be clear, I'm not saying "you were wrong, and I was right."  I'm simply stating that it just depends on the circumstances -- and yes, you did advise Drakkor to use chown in your first post, and your advice in this situation makes good sense. :-D

---

### Post by TFX360 on 2006-08-25
> **ciscosurfer said:**
> You did, but from what Drakkor stated initially (the way it was described), chmod'ing the directory made perfect sense.  Because his situation was slightly different than originally assumed (by nearly all of us), using chown worked just fine.  For the record, just because a file or directory changes owners via chown, doesn't necessarily mean that permissions cascade down -- this is why chmod is effective and used as well in certain circumstances.  To be clear, I'm not saying "you were wrong, and I was right."  I'm simply stating that it just depends on the circumstances -- and yes, you did advise Drakkor to use chown in your first post, and your advice in this situation makes good sense. :-D

Ciscosurfer,


Luckily I'm and I hope we all aren't here to be right but to help. And thats what we did. It's (chown and chmod are) a tad clearer to me now too :D

Sorry if my English isn't quite right. I'm from Holland.


Kind regards,


TFX

---

### Post by Contrid on 2006-08-25
> **ciscosurfer said:**
> Absolutely. Use 'chmod' and modify your permission set to whatever you like...to include all directories below the a specific one, use the "*" (asterisk character).  For example```
sudo chmod 755 testfolder/*
``` Happy chmod'ing \\:D/

Thank you for the helpful information! ;)

---

### Post by ciscosurfer on 2006-08-25
> **TFX360 said:**
> Ciscosurfer,


Luckily I'm and I hope we all aren't here to be right but to help. And thats what we did. It's (chown and chmod are) a tad clearer to me now too :D

Sorry if my English isn't quite right. I'm from Holland.


Kind regards,


TFX

@TFX360
Your English is very good and much better than some people I know ;) And I'm glad we were able to help out a fellow Ubuntunian :D  The UbuntuForums are what keep me going with Ubuntu; the community interaction, the will to want to help other people out; it's what makes Ubuntu such a tremendous success (imo).  What one person knows, another person may not, and vice versa.  It's the collaboration-effect that I love the most...I most certainly have learned a lot about Ubuntu since joining the forums and will continue to participate and hopefully gain more insight(s).  Let's keep up the good work! =D>

De jouwe,
ciscosurfer \\:D/

---

### Post by ciscosurfer on 2006-08-25
> **Contrid said:**
> Thank you for the helpful information! ;)
Glad I (we) could help (others in this thread [TFX360, aysiu, kinematic] have provided additional information that you might find useful as well!)

---

### Post by BiggoCharley on 2006-08-28
I've been following this thread so, as a learning exercise, I ran "chmod -R 755 /etc".(I probably should have created a test folder first --but I neglected to do this)
All seemed ok --no obvious bad effects until somewhat later when I tried to start synaptic from the gui.  It wouldn't start so I openned a terminal and tried to start it from there and got an error message to the effect that the mode for "/etc sudoers" should be 0440 not 0755. After messsing around unproductively for a couple of days off and on, I rebooted in the recovery mode and typed chmod -R 440 /etc.  Again no APPARENT problems so I rebooted into the normal mode and got this message:
INIT: cannot execute "etc/init.d/rcS"
INIT: entering run level 2
INIT: cannot execute "etc/init.d/rc"

the boot process stalled at this point --now I'm unable to boot up in the normal mode (can still boot up in the recovery mode).
How do I extract myself from this mess I've created??

I've been using Ubuntu for one year (dual boot with Windows XP)and gradually weaning myself away from XP and this is the first SERIOUS problem I've had.

Your help will be appreciated

---

### Post by ciscosurfer on 2006-08-28
Oh wow.  Well, if you use backups, I would try that first.  But at the risk of sounding like a complete a-hole, you've hosed your /etc directory and modified all permissions recursively, downward and throughout your /etc directory.  My best advice, and this is going to be painful (sorry), is to boot up another computer with Ubuntu (or use a liveCD on your current machine), write/type/copy down the default permissions for each subsequent directory within /etc, then dive into each directory within /etc to see what their files permissions are set at...this is a tedious process.  It might be a better idea for you to simply backup your important work and then start again fresh (do a fresh install of Ubuntu).  Do you need to do this?  No.  You can follow the instructions I just gave and modify your permissions that way.  Will it take a long time?  Probably so.  Can you backup your important files on a disc or other drive and then start again anew?  Yes, and this solution will probably be the lesser of two evils.  Here's the overall lesson: work with test directories when learning new commands like these; it's just too risky not to.  And remember, the command-line is  an extremely powerful tool (as I'm sure you are now aware).

---

### Post by TFX360 on 2006-08-28
Dear BiggoCharley,

Bummer, good luck with ciscosurfers advice! (I would reinstall Ubuntu).


Kind regards,


TFX

---

### Post by Drakkor on 2006-08-28
Yeah,unfortunately I was thinking the same thing wipe and reinstall Ubuntu, I was going to say it,but I see you have had Ubuntu on there for a year,and probably got it tweaked just the way you want it. :(  I have had to reinstall it also,being a linux noob, but now I cheat a little and make an exact image of my whole Ubuntu drive (when everything's working fine,of course) in Windows with Acronis True Image, so now if I accidently hose it, I just restore with the backup image,and I'm up and running in about 10 minutes,
with everything just like it was before. It sure saves a lot of work later on !! ;)

---

### Post by BiggoCharley on 2006-08-28
> **Drakkor said:**
> Yeah,unfortunately I was thinking the same thing wipe and reinstall Ubuntu, I was going to say it,but I see you have had Ubuntu on there for a year,and probably got it tweaked just the way you want it. :(  I have had to reinstall it also,being a linux noob, but now I cheat a little and make an exact image of my whole Ubuntu drive (when everything's working fine,of course) in Windows with Acronis True Image, so now if I accidently hose it, I just restore with the backup image,and I'm up and running in about 10 minutes,
with everything just like it was before. It sure saves a lot of work later on !! ;)

Actually the install that I use regularly is on my desktop machine. The problem I described is on one of my laptops and (happily) I use this installation for experiments and learning exercises (since I'm self taught I have a lousy teacher):-D.  So I guess the best and quickest remedy is to reinstall Dapper and try to learn from my mistakes.  I really appreciate everyones help and comments. This forum is GRRRREAT!!!
Charley

---

### Post by maansson on 2006-09-02
I'm new to Ubuntu, but have been trying to learn bash scripting for a while.

The first suggestion to boot a CD could work.

1. boot the cd
2. insert a usb keyring or...
3. open a shell and type

sudo -i
cd /etc
find * -printf "chmod %p %m \n" > /your_usb_drive/set_permissions.sh

Now you should have a script that would reset all your permissions to default (I have not tried it).

---

### Post by ciscosurfer on 2006-09-02
@maansson
That's a nice little script...but it will only show what your *current* permissions are...I would say that to make this effective (in terms of resetting one's own permission set on files that have gotten reset) one would need to issue this on a fresh install (or perhaps a liveCD, and copy over the output of said scritpt to a file, and then use those permissions as a guide to reset permissions of another computer that's gotten messed up)

Well done!

---

### Post by TFX360 on 2006-09-02
> **maansson said:**
> I'm new to Ubuntu, but have been trying to learn bash scripting for a while.

The first suggestion to boot a CD could work.

1. boot the cd
2. insert a usb keyring or...
3. open a shell and type

sudo -i
cd /etc
find * -printf "chmod %p %m \n" > /your_usb_drive/set_permissions.sh

Now you should have a script that would reset all your permissions to default (I have not tried it).

Sweet dude. Will try it later!

---

### Post by maansson on 2006-09-02
> **ciscosurfer said:**
> @maansson
That's a nice little script...but it will only show what your *current* permissions are...I would say that to make this effective (in terms of resetting one's own permission set on files that have gotten reset) one would need to issue this on a fresh install (or perhaps a liveCD, and copy over the output of said scritpt to a file, and then use those permissions as a guide to reset permissions of another computer that's gotten messed up)

Well done!
Exactly - I did not get my references straight. One of the first suggestions for fixing the problem was to boot a live cd and go through the permissions manually (and that would take like forever).

But with a little scripting and an USBKEY it could be done.

---

