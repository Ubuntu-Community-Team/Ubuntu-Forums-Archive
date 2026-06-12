---
title: "vmware server problems, I don't know what to do."
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by BVStang1967 on 2007-07-14
I didn't know where to post this question and I am an absolute beginner so here it is...

I installed vmware server through synaptic package manager and I set it up to use the entire disk it loads grub then I select windows xp it goes to a black screen and says starting up....

It doesn't do anything after that. I set up a virtual profile in xp but I don't know what else to do.

---

### Post by anewguy on 2007-07-14
I don't know squat about using the whole disk, but I do have something for you to try, if you haven't already:

- edit the .vmx file for the virtual machine and change scsi0 to false, then try rebooting.  I had to do that to get it to even begin to start up. 

I'm just a novice, so I don't know if that will help you or not, but it sure helped me!:)

---

### Post by BVStang1967 on 2007-07-14
> **anewguy said:**
> I don't know squat about using the whole disk, but I do have something for you to try, if you haven't already:

- edit the .vmx file for the virtual machine and change scsi0 to false, then try rebooting.  I had to do that to get it to even begin to start up. 

I'm just a novice, so I don't know if that will help you or not, but it sure helped me!:)

Ok... (to show how much of a beginner I am) How would I go about finding that file... and editing it.

---

### Post by anewguy on 2007-07-15
Sorry it took me so long to get back here.:)

I am very new to all of this as well, so hang in there!

For my installation of Vmware-server, it seems to have created the virtual machine files in this path:  
    /var/lib/vmware/Virtual Machines/xxxxxx,  where the "xxxxxx' it the name you gave your virtual machine when you created it.  In my case, it is WinXP.

Try this in a terminal window:

ls "/var/lib/vmware/Virtual Machines"   (I had to use the quotes because of the space in the path)

Hopefully it should show your virtual machine.  If so:

In a terminal window:

sudo gedit "/var/lib/vmware/Virtual Machines/xxxxxx/xxxxxx.vmx"  (again with quotes)

look for the line that says:

scsi0.present = "TRUE"

and change the TRUE to FALSE, then save and exit.

Also, your userid needs to be part of the group "vmware".  To check this, do the following on the main menu line on top:

click "system", then "Administration" then "Users and Groups"

it will ask for your administrative password - just enter the password you used to log in.

You should get a window that is titled "User settings".  On the right hand side of that window, click on "Manage Groups".  This should open a window titled " Groups settings".  Scroll through the list until you find the name "vmware".  Double-click on that and it will show the users who are members of that group (the members have a check by the user name).  If your userid does not have a check in front of it, just click the box, then click "OK" to get back to the "Groups settings" window, click "close" to get back to the "User settings" window and just click "close"  to get out of that.

Now that you have done all of those things, try to run the server again.  If you have more problems, please post back.  I have used VMware Server to set up and run Windows in Ubuntu 7.04, but other than that I'm just a regular new user who got lucky and got it to work!:)

---

### Post by anewguy on 2007-07-16
Hi, please let me know if you had any luck with this and how you did get it to work.  Then we can mark this as "solved" so others could find it for help also.:)

---

### Post by BVStang1967 on 2007-08-06
> **anewguy said:**
> Hi, please let me know if you had any luck with this and how you did get it to work.  Then we can mark this as "solved" so others could find it for help also.:)

Sorry it took me so long, I was on vacation :).... but now I am back and I did try that out unfortunately the first command I tried to find the file didn't bring up anything... I'm going to keep looking around to try and find out what I'm doing wrong.

EDIT: Ok so I found the folder Virtual Machines (it is empty as I deleted the windows XP folders which were failed attempts) when I tried to edit the file using sudo gedit it brings up an empty file there is nothing to be edited in it.. so something is messed up.

---

### Post by anewguy on 2007-08-07
> **BVStang1967 said:**
> Sorry it took me so long, I was on vacation :).... but now I am back and I did try that out unfortunately the first command I tried to find the file didn't bring up anything... I'm going to keep looking around to try and find out what I'm doing wrong.

EDIT: Ok so I found the folder Virtual Machines (it is empty as I deleted the windows XP folders which were failed attempts) when I tried to edit the file using sudo gedit it brings up an empty file there is nothing to be edited in it.. so something is messed up.

If your virtual machine still shows in VMWare Server, try to run it.  If indeed you deleted the files it should not be able to start.  If it does start, then the virtual machine files still exist.  The names of those files will be the exact name of your virtual machine and is case sensitive.  So, for example, if you named your virtual machine Windows XP, then you can find out where those files are by typing the following in a terminal window:

locate "Windows XP"  

If you don't see the .vmx file for your virtual machine, then you will need to go back in to VMWare Server and create it again.  

It should return a list of files, and one of those should be a .vmx file - just drag you mouse over that entire path and file name, then do the following in a terminal window:

sudo gedit xxxxxxx  <- the xxxxxxx is where you paste the path and file name you copied from the locate command.  Then try the things I put in under my previous edit post, then restart your virtual machine.

Let us know what happens!:)

---

