---
title: "Changing the &quot;Owner&quot; of a file"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by antsen on 2006-09-03
Hello.

I have a shared partition (FAT32) mounted in /home/anthony/Shared and I am not the "Owner" and I would like to be, because I'm fed up with it changing my file attributes.  I have tried
> 
sudo chown anthony:anthony /home/anthony/Shared

and got 
> 
chown: changing ownership of `/home/anthony/Shared': Operation not permitted

I also tried the same with "user" added to the appropriate column of the appropriate drive in /etc/fstab and then a reboot, and got the same results.

Can someone help please?  I'm really keen to get this OS right!

Cheers,

Anthony

---

### Post by greyash99 on 2006-09-03
Does sudo work?
EDIT:nvm

---

### Post by PriceChild on 2006-09-03
you need to add in a "-R" to directories which aren't empty

Stands for "recursive"

So for example:
```
sudo chown anthony:anthony -R /home/anthony/Shared
```
And its a capital R!!!

---

### Post by Omnios on 2006-09-03
Hi I used to have problems and about a year ago or so I came uo with this fstab entry that I have been using ever since which seems to work very well.
```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0

``` 
Also there is a link to tuxfiles in my sig that has a indepth article on fstab that really explains fstab.

 ALso there was a few old threads where I was playing around with fstab.
[http://ubuntuforums.org/showthread.php?t=49830&highlight=fstab](http://ubuntuforums.org/showthread.php?t=49830&highlight=fstab)

---

### Post by antsen on 2006-09-03
```
sudo chown anthony:anthony -R /home/anthony/Shared
```
went through and changed all the files.  Thanks for that! Now I know how to change all the files quickly!

The problem is it still throws the error and doesn't change them:
> Operation not permitted
for every file!

What should I do? ](*,)

---

### Post by Omnios on 2006-09-03
> **Omnios said:**
> Hi I used to have problems and about a year ago or so I came uo with this fstab entry that I have been using ever since which seems to work very well.
```

/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0

``` 
Also there is a link to tuxfiles in my sig that has a indepth article on fstab that really explains fstab.

 ALso there was a few old threads where I was playing around with fstab.
[http://ubuntuforums.org/showthread.php?t=49830&highlight=fstab](http://ubuntuforums.org/showthread.php?t=49830&highlight=fstab)

Bump from above

---

### Post by PriceChild on 2006-09-03
```
pricechild@linbeast:~$ ls
amsn_received  Desktop    gaim-2.0.0beta3.tar.gz  vmware
cache          downloads  PicasaDocuments
pricechild@linbeast:~$ sudo chown pricechild:pricechild -R /home/pricechild/downloads
Password:
pricechild@linbeast:~$
```

Can i see your equivalent as i can't understand exactly what's not working here...

---

### Post by antsen on 2006-09-03
Omnios: thanks I'll try that.  Presumably a reboot is needed?

PriceChild:
```

anthony@anthony-laptop:~$ ls
amsn_received  Linux Scripts         Picture 1.jpg  Transfer        xchat asks
Desktop        Picture 1 (copy).jpg  Shared         wireless stuff
anthony@anthony-laptop:~$ sudo chown anthony:anthony /home/anthony/Shared
chown: changing ownership of `/home/anthony/Shared': Operation not permitted
anthony@anthony-laptop:~$

```
If I use -R it duplicates this error for as many files as I have ~9000. :-D

---

### Post by PriceChild on 2006-09-03
Are you sure that you have sudo permissions?

---

### Post by antsen on 2006-09-03
I am as sure as I can be that I have sudo permissions: using sudo I have managed to do everything I've needed to do (created directories, done, or at least attempted, manual installs, edited & backed-up xorg.conf, etc etc).  Is that what you mean?

---

### Post by antsen on 2006-09-03
```
/dev/hda2       /media/documents     vfat    rw,users,gid=users,umask=000,       0       0
```
Omnios: many thanks for that fstab line.  I inserted the fourth-column part instead of my own, and it's much better: everyone now has full read, write, and execute access.

I am however still not the "owner".  How can I sort this?

---

### Post by Omnios on 2006-09-03
K this is from the old linke where I was trying to mount the vfat partition as the user as I was trying to set up a wine fake drive on my partition. This mounts the partition as the user

> 
IN fstab instead of this:
/dev/hda2 /media/vfat vfat rw,users,auto,gid=users,umask=0200, 0 0
put this:
/dev/hda2 /media/vfat vfat rw,users,auto,uid=XXX,gid=users,umask=0200, 0 0

where XXX is your userid. To look up your userid goto System.->Administration->Users and Groups.

One done, unmount the vfat drive:
>> sudo umount /media/vfat

then reload fstab:

>> sudo mount -a

This will mount all files and dirs in /meda/vfat with you as owner.

HTH
AM
                                                                                                                                          
 
> 
That did the trick! Thanks. But one little problem Now I am the owner but it booted as a no exe wich means I can't run executables as owner on the drive which was ok when it was owned by root as the exe is only affecting the owner. Also I couldn't unmount even with sud it ran the unmount in sudo but nothing happened. Seems it only wan't to do changes with reboots, which isnt realy that big of a problem for me as long I get it working.
                                                                         [RIGHT]                                                                                                                                                                
[/RIGHT]
                                   Omnios
                  [View Public Profile]("http://ubuntuforums.org/member.php?u=14126")
                  [Send a private message to Omnios]("http://ubuntuforums.org/private.php?do=newpm&u=14126")
                            [Find all posts by Omnios]("http://ubuntuforums.org/search.php?do=finduser&u=14126")
              [Add Omnios to Your Buddy List]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=14126")
          
                                                                                                                       #[**13**]("http://ubuntuforums.org/showpost.php?p=260639&postcount=13")                                                                              
                                            [IMG]http://ubuntuforums.org/images/statusicon/post_old.gif[/IMG]                              July 18th, 2005                                                
                                                                                                                                                [amohanty]("http://ubuntuforums.org/member.php?u=27414")                     [IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]                        vbmenu_register("postmenu_260639", true);                                       
                                  Dark Roasted Ubuntu

                                                                                                                Join Date: Jun 2005
                     Location: Berkeley, CA 
                       Beans: 1,090
  Ubuntu Breezy 5.10 User
                                                                        
                 
                                                         
  
                                                                                             **Re: Need help trying to install wine on a primary Vfat partion.**             
                                                                                 add exec to the list of options in column 4 rw,users,exec....
also a complete explanation of fstab options:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

if it does not allow a umount as sudo, in a teminal type:
>> su

it will respond:
Password:

type in password and then do your mount an unmount. Also as a precaution, I have setup my root password differently than my usual password by:
>> sudo passwd

and I do all things via the method mentioned above. There are certain things you cannot do with sudo.

HTH

AM

 
> 
Look at the umask option. Its the complement of what the permission will be so if umask=0 then all file perms will be 777, a umask of 0200 means it will be 500 which means r-x------ for all files so figure out what you want and set it to that. Also theres an option called dmask for directories.

AM

Edit: oops a umask of 0200 means it will be 500  sorry I mean 577 r-xrwxrwx.


---

### Post by antsen on 2006-09-03
Aha yes. I saw that! But I miss-read "uid=XXX" as "gid=XXX" Doh!

Also is there anything I can look at to explain the relationship between r-xrwxrwx (presumably Read, Write, and eXecute for Owner, Group, and Others respectively) and the numbers that are written in the "umask" part?

I'll try instering 
```
uid=1000
```
into the fstab now.

Cheers.

---

### Post by Omnios on 2006-09-03
This is a really good fstab article. 
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by antsen on 2006-09-03
Omnios: I can't thank you enough for all your help. I've been trying to do this for so long! Maybe now Azureus will work properly....

Regards,

Anthony

---

