---
title: "/home folder messed up; can not boot"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Majin Zero on 2008-03-28
Ok, a little back ground; my system was set up with the home folder on a second HDD.

I changed my /home folder using the users > /home location thing, to a folder on the first HDD.

After this, I removed the second HDD from my computer. It can not be put back in.

After restarting my computer this happens:

when I boot up I get this:

efsck: cannot continue, aborting

fsk died with exit status 8

*file sytem check failed

Please repair the file system manually
control-D will terminate this shell and resume boot.

If I do ctrl+D it boots and when I go to log in I get this:

User's $HOME.dmrc file being ignored. File should be owned by user and give 644 permisions. User's $HOME directory must be owned by user and not writable by other users.

and there's an OK button, I click OK, and get this:

This session only lasted 10 seconds. If you have not logged out yourself, there may be an installation problem. Try using failsafe mode to see if you can fix this problem.

There is an OK button, and clicking it brings me back to the log in screen.


Failsafe mode gives me the same log in error. I am able to boot in recovery mode fine, however I can not access any system configuration, so no network access.

---

### Post by Tatty on 2008-03-29
try this:

1. put your other hard drive back in
2. boot with a live cd
3. copy your /home/{your user name} folder from your second hard drive to wherever you specified it should be on your first hard drive.  (whever you changed it to in the users section)
4. reboot into your system.

---

### Post by perce on 2008-03-29
> **Majin Zero said:**
> 

This session only lasted 10 seconds. If you have not logged out yourself, there may be an installation problem. Try using failsafe mode to see if you can fix this problem.



I usually get this type of error when I cannot write on the disk. Have you tried to login in textmode? try Ctrl-Alt-F1 to log in in text mode.

You should also try to understand for what filesystem the check fails, and run the command fsck manually when it asks you to check the filesystem manually,

---

### Post by Majin Zero on 2008-03-29
I can not replace that disk, long gone.

The file system check failed, because I obviously didn't configure my new /home folder right.

that's what keeps messing everything up.

I suppose I'm gonna have to boot with a live CD.

I need to get about 11 gigs off this computer; I can't afford to lose those 11 gigs, so I'll use a live CD to send them to my NAS.

Unless there is a way to get internet access in failsafe mode.

---

### Post by dsauxier on 2008-03-29
Go to one of the consoles by pressing <CTRL><ALT><F1>
sign in, then go to the /home directory 
(alternatively, you could boot in "rescue" mode, then you'd be root and you can drop the "sudo" from the commands below)

I'm using "userxyz" for your username, so you'll need to change it to whatever your username really is
```

sudo chown userxyz:userxyz /home/userxyz
sudo chmod 755 /home/userxyz

sudo chown userxyz:userxyz /home/userxyz/.dmrc
sudo chmod 644 /home/userxyz/.dmrc

sudo chown userxyz:userxyz /home/userxyz/.ICEauthority
sudo chmod 600 /home/userxyz/.ICEauthority

sudo chown userxyz:userxyz /home/userxyz/.Xauthority
sudo chmod 600 /home/userxyz/.Xauthority

```

now you can either reboot or re-login 
<CTRL><ALT><F7> gets you back to your gui login

---

### Post by dsauxier on 2008-03-29
You'll probably be left with some permission problems on the other files in your home directory.  It's your choice wethor you want to fix those one-by-one or en masse.
It's a safe bet that owner and group should both be set to userxyz : 

```

sudo chown -R userxyz:userxyz /home/userxyz

```

(I should have thought of that first... the chown commands in my previous post are redundant)

Anyway, I'd start with that and fix any remaining permission problems file-by-file

---

### Post by Majin Zero on 2008-03-29
> **dsauxier said:**
> Go to one of the consoles by pressing <CTRL><ALT><F1>
sign in, then go to the /home directory 
(alternatively, you could boot in "rescue" mode, then you'd be root and you can drop the "sudo" from the commands below)

I'm using "userxyz" for your username, so you'll need to change it to whatever your username really is
```

sudo chown userxyz:userxyz /home/userxyz
sudo chmod 755 /home/userxyz

sudo chown userxyz:userxyz /home/userxyz/.dmrc
sudo chmod 644 /home/userxyz/.dmrc

sudo chown userxyz:userxyz /home/userxyz/.ICEauthority
sudo chmod 600 /home/userxyz/.ICEauthority

sudo chown userxyz:userxyz /home/userxyz/.Xauthority
sudo chmod 600 /home/userxyz/.Xauthority

```

now you can either reboot or re-login 
<CTRL><ALT><F7> gets you back to your gui login

I'm in recovery mode, so I'm at command line, root.

I did the first command; got "no such file or dir" so I made it.

next command same thing. so I'lll need to create those other 3 files.

How do I?

---

### Post by om1 on 2008-03-29
did you replace userxyz with your user name?

---

### Post by Majin Zero on 2008-03-29
Yes I did replace it with my user name.

---

### Post by dsauxier on 2008-03-29
> **Majin Zero said:**
> Yes I did replace it with my user name.

OK, if you had to create the folder, you'll want to get rid of it or it may cause problems later.
It's safest to just rename it, but you want it out of the /home directory 
```
sudo mv -i /home/userxyz /uxerxyz_save
```

Now please post the following info : 
Verify what filesystems you've got mounted.
```
df -h 
```

And let's take a look at how /home is being mounted on bootup
```
cat /etc/fstab | grep home
```

---

### Post by Majin Zero on 2008-03-29
too be honest; this is getting to time consuming; I'm just going to use a live CD to grab the files I need, and I'll reformat after.

---

