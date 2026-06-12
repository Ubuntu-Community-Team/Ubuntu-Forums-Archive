---
title: "The GNOME session amager was unable to lock '/home/**/.ICEauthority.'"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by hazira on 2007-10-02
Guys,

I am a new hand on Linux - Ubuntu 7.04. I have a problem to boot my laptop. When input user name and password, it showed "The GNOME session manager was unable to lock the file '/home/hazira/.ICEauthority.' Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable. you could try logging i via the failsafe session and ensuring that it is." I logged into failsafe session and it showed "This is failsafe session. you will be logged into the "Default" session of GNOME without the startup scripts being run. This should be used to fix problems in your installation." Then click "ok", it showed "The GNOME session manager was unable to lock the file '/home/hazira/.ICEauthority.' Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable. you could try logging i via the failsafe session and ensuring that it is." 

What should I do? I guess the reason to cause the problem might be I changed the permission on Drive D(Fat32) from "Read and write" to "Access file". Am i right?

---

### Post by overdrank on 2007-10-02
> **hazira said:**
> Guys,

I am a new hand on Linux - Ubuntu 7.04. I have a problem to boot my laptop. When input user name and password, it showed "The GNOME session manager was unable to lock the file '/home/hazira/.ICEauthority.' Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable. you could try logging i via the failsafe session and ensuring that it is." I logged into failsafe session and it showed "This is failsafe session. you will be logged into the "Default" session of GNOME without the startup scripts being run. This should be used to fix problems in your installation." Then click "ok", it showed "The GNOME session manager was unable to lock the file '/home/hazira/.ICEauthority.' Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable. you could try logging i via the failsafe session and ensuring that it is." 

What should I do? I guess the reason to cause the problem might be I changed the permission on Drive D(Fat32) from "Read and write" to "Access file". Am i right?

HI and welcome, is this a fresh install? Did you check the disc for errors with checksum? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If all else you may just try and reinstall gnome. Good luck!

---

### Post by hazira on 2007-10-02
I installed it for about 2 weeks. And used it well. Suddenly I could not run today. Thanks for ur help!

---

### Post by hazira on 2007-10-03
I used "ls -al" at session terminal, it showed: ".xsession-errors"

??

---

### Post by davbslim on 2007-11-06
> **hazira said:**
> Guys,

I am a new hand on Linux - Ubuntu 7.04. I have a problem to boot my laptop. When input user name and password, it showed "The GNOME session manager was unable to lock the file '/home/hazira/.ICEauthority.' Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable. you could try logging i via the failsafe session and ensuring that it is." I logged into failsafe session and it showed "This is failsafe session. you will be logged into the "Default" session of GNOME without the startup scripts being run. This should be used to fix problems in your installation." Then click "ok", it showed "The GNOME session manager was unable to lock the file '/home/hazira/.ICEauthority.' Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable. you could try logging i via the failsafe session and ensuring that it is." 

What should I do? I guess the reason to cause the problem might be I changed the permission on Drive D(Fat32) from "Read and write" to "Access file". Am i right?

When you access your files as a root user, the owner becomes root.  You will have to change the owner back to hazira
in the command prompt type
cd /
sudo chown -R hazira /home/hazira/*
That should work.  You may have to use a liveCD if you cannot access the laptop

---

### Post by timcredible on 2007-11-06
i see this quite often on unix machine where people login as root (rule #1 in computer security, don't login as root).  as the previous poster said, you have to change the permissions on that file to get back in to the system.  however, about the fat32 partition, what do you mean by 'D drive?'.  the only partition that matters here is the / partition, and i don' t think there's any way to install linux on a fat32 partition, so no, that shouldn't have affected anything.

---

### Post by jimsmith80220 on 2007-11-06
I have a similar problem with "unable to lock .ICEauthority" or read it, or an error stating the permissions are not 644 or not the correct owner.

The screen is displayed in large format letters that I cannot read more of and must reboot. Booting not in persistent mode I can see the permissions are only rw for owner, which is ubuntu, and upon changing them to 644 it will then reboot ok, but then is changed back on the next boot and I must fix it again outside of persistent mode.

I have seen mention in the forums of previous .ICEauthority issues but never a fix; please reference a thread or repost any help that is available. 

I am running persistence from a 2Gig flash, not installing on a hard drive, and it works great otherwise.
Thanks.

---

### Post by stevenrushing on 2007-11-08
Thanks Dav, I am also on a persistent thumbdrive, and this worked for me!  =)


> **davbslim said:**
> When you access your files as a root user, the owner becomes root.  You will have to change the owner back to hazira
in the command prompt type
cd /
sudo chown -R hazira /home/hazira/*
That should work.  You may have to use a liveCD if you cannot access the laptop

---

### Post by davbslim on 2007-11-08
> **jimsmith80220 said:**
> I have a similar problem with "unable to lock .ICEauthority" or read it, or an error stating the permissions are not 644 or not the correct owner.

The screen is displayed in large format letters that I cannot read more of and must reboot. Booting not in persistent mode I can see the permissions are only rw for owner, which is ubuntu, and upon changing them to 644 it will then reboot ok, but then is changed back on the next boot and I must fix it again outside of persistent mode.

I have seen mention in the forums of previous .ICEauthority issues but never a fix; please reference a thread or repost any help that is available. 

I am running persistence from a 2Gig flash, not installing on a hard drive, and it works great otherwise.
Thanks.

This may work, but there will be no security.  I have stopped using persistent due from the fact that mine changes also.  Big headache
Method 1
1.  Create a new user called john
2.  Go to the command prompt.  Make sure you are in ubuntu's directory
     Change the owner of the directory to John  ** sudo chown -r john ***
3.  Change the permissions to allow everyone to read, write, and execute
    **  sudo chmod -r 777 ***
Mine for some reason changes owner to 999.  I use Ubuntu Gutsy.

Method 2
  Create a new user john.  If the system locks you out of ubuntu, it should bring you to a login screen.  Login as john and use this as your account.

---

### Post by davbslim on 2007-11-09
I have done some testing and found a solution that may work.  Many of you maybe using your flash drive on more than one computer.  This will cause problems.  This is my solution.  Logging into ubuntu user causes problems, but when I logout and login as a user for the specific computer, it works.

1.  Create a user for each and every computer and make each one an administrator.
     Create a spare administrator account in case you want to add another computer later.
2.  Create a directory in / that is called z_common
3.  Change the permissions for z_common to be accessible by everyone.
4. ** DO NOT** access another Linux partition on any other computer or access this Linux partition.
5.  Put files that you want used in the z_common folder.  Wallpaper, documents, etc.
6.. **Have one main user** that will update, copy files, add stuff, delete stuff, etc.  Checking for updates increased the users home by over 6 mb.

The settings for each and every user will be saved, but making changes in ubuntu causes serious problems.  **NEVER** make any changes to the default ubuntu account.

Use either a fat16, fat32, or Internet drive to share files with other Linux OS's.
Administration->Login Window->Local->Happy Gnome with Browser
This will change the login screen to something easier to use.  This is what I have found.

---

### Post by braindonor23 on 2007-11-23
> **davbslim said:**
> I have done some testing and found a solution that may work.  Many of you maybe using your flash drive on more than one computer.  This will cause problems.  This is my solution.  Logging into ubuntu user causes problems, but when I logout and login as a user for the specific computer, it works.

1.  Create a user for each and every computer and make each one an administrator.
     Create a spare administrator account in case you want to add another computer later.
2.  Create a directory in / that is called z_common
3.  Change the permissions for z_common to be accessible by everyone.
4. ** DO NOT** access another Linux partition on any other computer or access this Linux partition.
5.  Put files that you want used in the z_common folder.  Wallpaper, documents, etc.
6.. **Have one main user** that will update, copy files, add stuff, delete stuff, etc.  Checking for updates increased the users home by over 6 mb.

The settings for each and every user will be saved, but making changes in ubuntu causes serious problems.  **NEVER** make any changes to the default ubuntu account.

Use either a fat16, fat32, or Internet drive to share files with other Linux OS's.
Administration->Login Window->Local->Happy Gnome with Browser
This will change the login screen to something easier to use.  This is what I have found.

Hi, I'm new.  I have consistently had the .ICEauthority problem since I started using ubuntu.  I tried your solution method, and it seems to have stopped the very annoying .ICEauthority issue.  It was all pretty easy, since I only use one computer, and I'm the only ubuntu user on it too. there is one issue, though.  when I'm logged into the user account I created, I can' login to the network.  It starts logging in and then it just feezes without sending or recieving anything.  does anyone know why this could happen? It doesn't even ask me for the password like before.  any help would be appreciated, thanks.

---

### Post by davbslim on 2007-11-27
> **braindonor23 said:**
> Hi, I'm new.  I have consistently had the .ICEauthority problem since I started using ubuntu.  I tried your solution method, and it seems to have stopped the very annoying .ICEauthority issue.  It was all pretty easy, since I only use one computer, and I'm the only ubuntu user on it too. there is one issue, though.  when I'm logged into the user account I created, I can' login to the network.  It starts logging in and then it just feezes without sending or recieving anything.  does anyone know why this could happen? It doesn't even ask me for the password like before.  any help would be appreciated, thanks.

Logging into what network.  I know it should work with the network cable.  Wi-fi maybe a problem.  If you are using wifi, you may need to reinstall it using that account.  I use the accounts with a wired network.  Wireless I have never tried.  

If I were you, I would do 3 things with this problem.  
First, Do a search.  Somebody may have had the same problem
Second, if the first does not help, make a brand new post stating the problem that you have in the Ubuntu Forums.  
Third, I would make another post on [http://www.linuxquestions.org/questions/index.php](http://www.linuxquestions.org/questions/index.php)

The reason for thethird is because the problem you are having could be a more general problem and they may be able to help you out if nobody here can.

---

### Post by seren6ipity on 2007-12-22
> **davbslim said:**
> When you access your files as a root user, the owner becomes root.  You will have to change the owner back to hazira
in the command prompt type
cd /
sudo chown -R hazira /home/hazira/*
That should work.  You may have to use a liveCD if you cannot access the laptop

You response helped me zero down on the problem however I had to use a bit different command.

I had to change the owner of my folder. I used following command and it worked - 
sudo chown -R seren6ipity /home/seren6ipity

Also I changed the group ownership - 
sudo chgrp seren6ipity /home/seren6ipity

---

### Post by mohi on 2008-05-30
I had the same problem here, I did the following:

press: Ctrl+ALT+F1, and enter username and pass, then:

```
sudo chmod 600 ~/.ICEauthority
sudo chown mohi:mohi ~/.ICEauthority
```

you have to replace "mohi" with your username.
this fixed my problem.

---

### Post by Thug14 on 2008-07-04
<bump>

---

