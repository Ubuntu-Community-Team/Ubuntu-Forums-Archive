---
title: "Fstab Question"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-14
Can anyone tell me how to edit the last two lines of my fstab so that these file systems will be mounted during boot?  The directories are network shares.  After some hair-pulling I finally got write access to them with the uid in fstab.  (Neither chmod or chown would do it.)  But I've tried a lot of different entries on their lines in fstab with no success for automounting.  I have to think the fstab lines are not completely out of whack because a mount -a command mounts them right away.  I'll include the whole fstab file in case it might help.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=3e8a8a7c-ed6b-46de-9fa8-8d108de0018c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb4
UUID=2b9f0dd0-eb0f-410d-bc05-64c00627666f /home           ext3    defaults        0       2
# /dev/hda1
UUID=07D5-0416  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=10643FFF643FE5DE /media/hda2     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       /media/hda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=A8D40520D404F1FC /media/hdb1     ntfs-3g    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=2205ac7b-2906-499e-b2c6-4a7d6572c367 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
//fezzik/SharedDocs /mnt/fezzik/SharedDocs  smbfs  auto,nodev,umask=007,uid=1000    0    0
//maria/My_Documents /mnt/maria/My_Documents  smbfs  auto,nodev,umask=007,uid=1000   0    0
```
Thanks,
Buck

---

### Post by chrisfay on 2006-12-14
Was it permisson settings on your remote location that required the uid settings? All I have in my fstab to mount and write to my Samba share with full access is:

```
//CHRIS/ubu_backups  /mnt/share smbfs 0   0
```

---

### Post by marx2k on 2006-12-14
My samba shares look like:

```

//192.168.11.8/MyMusic1 /home/marx2k/SambaShares/Music/Collection1   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.11.8/MyMusic2 /home/marx2k/SambaShares/Music/Collection2   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.11.8/MyMusic3 /home/marx2k/SambaShares/Music/Collection3   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.11.8/MyMusic4 /home/marx2k/SambaShares/Music/Collection4   cifs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0

```

my credential file looks like:
```

username=marx2k
password=<password here>

```

The directories I set up for samba look like:
```

SambaShares/
&#9500;&#9472;&#9472; [drwxr-xr-x]  Documents
&#9500;&#9472;&#9472; [drwxr-xr-x]  Music
&#9474;   &#9500;&#9472;&#9472; [drwxr-xr-x]  Collection1
&#9474;   &#9500;&#9472;&#9472; [drwxr-xr-x]  Collection2
&#9474;   &#9500;&#9472;&#9472; [drwxr-xr-x]  Collection3
&#9474;   &#9492;&#9472;&#9472; [drwxr-xr-x]  Collection4
&#9500;&#9472;&#9472; [drwxr-xr-x]  Pictures
&#9492;&#9472;&#9472; [drwxr-xr-x]  ReadWrite

```

The directories inside those have the same permissions

I hope that helps you somewhat

---

### Post by Buck2348 on 2006-12-14
> **chrisfay said:**
> Was it permisson settings on your remote location that required the uid settings?

Yes--I could not write to it and when I tried to change permissions the terminal said they were changed...but they weren't.

Thank you both for your help.  I'll report on success.

Thanks,
Buck

---

### Post by chrisfay on 2006-12-14
This is probably super round-about  but, since you said it works if you manually mount it you could give this a try. Create a simple bash bootup script that checks if your share is mounted. If its not, then it will do it for you.

Something like:

```
#!/bin/bash
SHARE="/mnt/share/myshare"

# Let's test to see if share is mounted
if test -d $SHARE
  then
        echo "Share is already mounted."
  else
        echo "Share is not mounted, proceeding to mount it."
        sudo mount /mnt/share/myshare
        echo "Share has now been mounted."
fi
```
Replace 'myshare' with a file or folder on your networked share...Just an idea.

---

### Post by Buck2348 on 2006-12-14
Hey, that's great--thank you very much!  I actually thought about that yesterday but didn't really know how to do it.  While I'm here, let me ask you another question.  What is the purpose of that first line  #!/bin/bash?  I understand the # means a comment and the contents of the line are ignored.  But every script I've seen begins with that and it looks like a purposeful line.

Thanks again for taking the trouble to write that up.

Regards,
Buck

---

### Post by chrisfay on 2006-12-14
> Thanks again for taking the trouble to write that up.

No problem....

> What is the purpose of that first line #!/bin/bash? I understand the # means a comment and the contents of the line are ignored

Normally that is true, but in the case of bash programming the first line tells the system which program to use to run the file.  Otherwise known as a "sha-bang".

---

### Post by hal10000 on 2006-12-14
The first line in a shell script is a comment, but it's the only comment  that exert influence on the script.
It indicates that your shell script has to work under bash. If you write e.g. a perl script, then the first line would be #!/usr/bin/perl or in case a script which shoul be run under the korn-shell it was #!/bin/ksh
You see, you can control in which shell the script has to be run.

---

### Post by Buck2348 on 2006-12-14
> **hal10000 said:**
> 
You see, you can control in which shell the script has to be run.

OK, got that.  Thanks.

chrisfay, I still can't figure out why my network shares won't mount at boot, but your script fixed it.  Still being a noob, I had to do some study (through Google) to get the script to run at boot.  I didn't know it needed an .sh extension, and I put it in /etc/init.d to make it work.  Reading an elementary tutorial I got the idea it ought to go when placed in ~/bin.  That directory is not in the list of PATH, and I still don't know why that is, since the script ~/.bash_profile is supposed to add it.  Maybe that script isn't running, since it is not in a $PATH?

Anyway, I'm very pleased to have that working, and I thank you again.  Maybe you can answer one more question for me.  Is it possible just to mount each computer on the network to get to their shares, rather than mounting a directory in them?  I know it must be but I don't have a clue.  One of the computers on my network got mounted once without any help from me.  No idea how it happened.

I really appreciate the help.

Buck

---

### Post by chrisfay on 2006-12-14
> Anyway, I'm very pleased to have that working, and I thank you again.

No problem, I suppose I should have also told you how to add the script at bootup. My bad.

> Is it possible just to mount each computer on the network to get to their shares, rather than mounting a directory in them?

I assume you intend to mount an entire Windows partition/drive to your Ubuntu file system.  I have never tried to do this but, it seems you would have to share your entire Win drive and mount it as you would a specific folder. Depending on your network configuration and access level locally it may not be a security risk, but I'd think it would be bad practice to open up your entire system like that. 

There may be more efficient and secure ways to do it but, like I said, i've never needed to. Let me know what you find out...

Chris

---

### Post by Buck2348 on 2006-12-15
Right, as impatient as I often am with system security measures, I don't want to share a whole drive or partition on the network.  I just discovered how a remote machine on my network got "mounted" if that is the correct term.  You no doubt know that when you go Places > Connect to Server you get that machine's icon on the desktop and you can access it there instead of Network Servers.  (It stays there after rebooting too.)  I say "Mounted" because right-clicking on it and choosing Unmount Volume seems to be the only way to get rid of it.  But in use it seems to be essentially the same as using "Network Servers."  It doesn't show up in the list given by the "mount" command.  When In Nautilus I toggle the "text-based location bar" it shows the same path:  "smb://servername."  My need to mount the network shares stemmed from the inability to access them using that text pathname.  Do you know if there is a way to write a path to the network shares without first mounting them?

One other thing--I'd still like to know why putting your script in ~/bin, and adding it to the list in System > Preferences > Sessions > Startup Programs (with full path) didn't work.  It's when seemingly simple things like that don't work that I tend to start pulling out my hair.

Once again, thanks for your help.

Regards,
Buck

---

### Post by Buck2348 on 2006-12-15
I just remembered one other question I'd very much like to have answered.  How can I permanently add to the list of paths in $PATH?  I saw some instruction on adding to it within a session with the export command, but it's gone after a reboot.

Buck

---

### Post by chrisfay on 2006-12-15
> It doesn't show up in the list given by the "mount" command

The mount command initiates all mount points specified in /etc/fstab. Samba can obviously access shares not listed in this file and therefore would not show up via 'mount'. 

> Do you know if there is a way to write a path to the network shares without first mounting them?

You can always see available samba network locations using the command:
```
sudo smbtree
```

This will display a 'tree' of locations on all networked systems. 

> One other thing--I'd still like to know why putting your script in ~/bin, and adding it to the list in System > Preferences > Sessions > Startup Programs (with full path) didn't work.

Since all my Ubuntu systems are servers, I only have knowledge using terminal commands. I'm not sure about the method you are using to get the script to initiate at boot but, assuming your script was called foo.sh usually all you would do is:

Create the script foo.sh 
```
sudo mv foo.sh /etc/init.d/foo.sh
```
```
sudo update-rc.d foo.sh defaults
```
```
sudo chmod +x foo.sh
```

Check out the man file for more info on update-rc.d:
```
man update-rc.d 
```

I'm not familiar with what you are referring to regarding $PATH....Sorry

Chris

---

### Post by Buck2348 on 2006-12-15
Chris, thanks once again for your full and informative reply.  I hope you won't mind me quoting this info about $PATH.
> the shell maintains a list of directories where executable files (programs) are kept, and just searches the directories in that list. If it does not find the program after searching each directory in the list, it will issue the famous "command not found" error message.

This list of directories is called your path. You can view the list of directories with the following command:

[me@linuxbox me]$ echo $PATH

This will return a colon separated list of directories that will be searched if a specific path name is not given when a command is attempted. In our first attempt to execute your new script, we specified a pathname ("./") to the file.

You can add directories to your path with the following command, where directory is the name of the directory you want to add:

[me@linuxbox me]$ export PATH=$PATH:directory

A better way would be to edit your .bash_profile file to include the above command. That way, it would be done automatically every time you log in.

Most modern Linux distributions encourage a practice in which each user has a specific directory for the programs he/she personally uses. This directory is called bin and is a subdirectory of your home directory
When I do
```
buck@argos:~$ export PATH=$PATH:/home/buck/bin
buck@argos:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/home/buck/bin
```
it works like the man said; my path is added to $PATH.  But I have the following in ~/.bash_profile, 
```
PATH=$PATH:/home/buck/bin
export PATH
```
which seems to have no effect.  A command for that purpose was already in the file anyway
```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
```
in a different form, which also doesn't seem to work as advertised.

marx2k:  Thanks for the help you posted yesterday.  I'd like to know how you produced that nifty tree of your SambaShares.  I'm sure it's quite simple once you know but I can't figure it out on my own.

Edit:  Never mind about the tree--for once I did figure it out.  I installed "tree."

Thanks again to all for the replies.

Buck

---

### Post by Buck2348 on 2007-01-07
After reinstalling my system, I was unable to get the script to work automatically any more.  I finally ran onto the solution in these forums:  [here]("http://www.ubuntuforums.org/showthread.php?t=103274")  My Windows machines have only one user and no password.  In my /etc/samba/smb.conf file I have a line:  security=share
In my fstab line for each share I had to add in the option field:
"username=share,password="
Now it works fine.

Buck

---

