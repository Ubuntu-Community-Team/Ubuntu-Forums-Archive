---
title: "Locked out of system - need to access system"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by newguy90 on 2007-11-29
I am totally new to UBUNTU and had never heard of it before yesterday, when a friend asked me to look at her PC. 
I found an intro screen for UBUNTU and did a web search on it. 

So now, I would like to ask if there is a way to logon if we do not know any of the user account info. It was her ex-husbands PC and so she does not have any of the user id info. But she would like to use the computer.

Is there a way into the system?

thanks in advance.

respectfully,

Dave

---

### Post by Chilli Bob on 2007-11-29
I can't help you with logging in, but a live CD of Puppy Linux or Knoppix would let you mount the hard drive and access data on the home directory.  You could then save this to an external drive and re-install Ubuntu.  It's not an ideal solution, but may help.  Let me know if you need instructions on doing this.

You can probably do this with a live Ubuntu CD too, but I've never tried.

---

### Post by anaconda on 2007-11-29
Just boot to recovery mode (from the boot menu) and you would get to terminal with admin rights.

In terminal you could type eg. "startx" and you would end up to graphical environment with admin rights.. 

If there isn't recovery mode on the boot menu you can still get to recovery mode by editing the "kernel" boot line and adding 
single
to the end of the line..

one other thing you could do in the recovery mode is to type:
adduser new_username

and then 
adduser new_username admin

That would create a new user "new_username" and the second line would then add the new_username to admin group. Then just reboot and log in with the new_username....

---

### Post by fineas on 2007-11-29
> **Chilli Bob said:**
> 

You can probably do this with a live Ubuntu CD too, but I've never tried.

Yes, you can do this with a live Ubuntu CD too.

---

### Post by mcduck on 2007-11-29
From the boot menu select the recovery mode (if you can't see the boot menu you should at least see a message that tells you to press a key to show it, the key is Esc, if I remember right..).

This will log you into text mode with full admin rights. Now, run 'ls /home'. This will list all directories inside the /home directory, and as every user has one, and it has the same name as the username is this will tell you the username.

Next, run command 'passwd username' (replace the username with the one you got in the precious step). This will allow you to set a new password for the user.

Finally, run 'reboot'  to restart the computer. Now you should be able to log in normally, using the username you found out and the password you set.

---

### Post by newguy90 on 2007-11-29
Good morning,

Please forgive me, but I am stuck and don't know anything about UBUNTU.

Yesterday, a friend asked me to take a look at her PC, because she could not logon to it. So she brought it over and when I powered it up, bingo, my first experience w/ UBUNTU.

The PC was her ex-husband's, so she does not have any idea what the user account info is, and so can not log on to use the PC.

Is there a way to logon w/ a default ID or reset somehow, so she can use the system?

Thank you in advance and hope you can help me.

Respectfully,

---

### Post by newguy90 on 2007-11-29
Good morning,

Please forgive me, but I am stuck and don't know anything about UBUNTU.

Yesterday, a friend asked me to take a look at her PC, because she could not logon to it. So she brought it over and when I powered it up, bingo, my first experience w/ UBUNTU.

The PC was her ex-husband's, so she does not have any idea what the user account info is, and so can not log on to use the PC.

Is there a way to logon w/ a default ID or reset somehow, so she can use the system?

Thank you in advance and hope you can help me.

respectfully,

---

### Post by PmDematagoda on 2007-11-29
Please do not start duplicate threads as it is not allowed on the forums especially at the Forum Feedback and Help section where help or answers concerning the forums itself is only given.

Anyway, solutions have already been given for your problem in your [ first thread]("http://ubuntuforums.org/showthread.php?t=626559")about this. Personally I believe mcduck has given the best solution.

---

### Post by newguy90 on 2007-11-29
Thank you so much for the terrific help.

that is exactly what I needed.



Now the I loged on, I must say that the system is actually pretty amazing. Wow ! 

Certainly faster and cleaner than Bill's Windows's OS's.

Very Nice.

I think I might start looking into how to set up one of my PC's to dual boot to start using this OS.

I like it.

Thank you again
:)

---

### Post by meindian523 on 2007-11-29
Please mark thread solved.

---

### Post by cdenk on 2007-12-02
I have newly fresh installed V7.1 desktop including GRUB as dual boot with WINXP, which I updated, and added numerous addons including to end up with Kubuntu. Kubuntu was working well, and then suddenly (this also happened with an earlier install) it wants a user password, which nothing is recognized.

I followed instructions per mcduck, was able to log into root, ls /home to determine the user name which is the same as shown on the Kubuntu log in screen. Then I was able to "passwd <username>" and confirm, which was accepted a changed. Restarted system, and at Kubuntu password screen, the new password was not accepted. 

2 questions:
1: Where now to get into Kubuntu?
2: Any ideas how I got to where I am?

Thanking in advance. )

---

### Post by cdenk on 2007-12-03
I Did Anaconda's suggestion to add user with a password, rebooted, and at KUBUNTU login screen, selected new-user and entered password, and enter.  Screen goes blank for a moment, and then comes back to the KUBUNTU login screen. Selecting the original user, entering a password results in the red wrong password message. This is progress I guess. Now at least it tries to get to the next step. 

Is this the correct way on this form, to pick up a close thread and add to it, or should of I started a fresh tread? 
Thanks again. :)

---

### Post by cdenk on 2007-12-03
Worked on problem some more, here's more info: In particular Bug #93360 seems to be an issue, but don't know if that is the cause of my issue.

Tried a few more things:
1:$ sudo chown -R username.username /home/username/

> $ sudo /etc/init.d/kdm restart

Commands were accepted, but no change

2:

/var/log/syslog  and /var/log/Xorg.0.log

was able to save in Word format on XP machine these 2 files. I can attach these files to a private message, you can ask at [email]cdenk@alltel.net[/email] The Syslog has some suspicious items, including:
Dec  3 21:48:44ubuntu dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name

Dec  3 21:48:45 ubuntu NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))

and in XORG.0.LOG

(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x00000000 (pgoffset 0)

(WW) intel(0): xf86AllocateGARTMemory: allocation of 1024 pages failed

      (Cannot allocate memory)

(II) intel(0): No physical memory available for 4194304 bytes of DCACHE

(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x00800000 (pgoffset 2048)

(II) intel(0): Allocated of 4096 bytes for HW cursor

(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x00801000 (pgoffset 2049)
(II) intel(0): Allocated of 16384 bytes for ARGB HW cursor

In googling for "ubuntu dhcdbd", I find a bug "Bug #93360 in dhcdbd (Ubuntu)" and the fix is to install the latest updates (I can get to the web). How do I running the live CD download and install these? I don't know if this will solve my problem, but it's a start, seems to be a network install issue.

3: I tried: 
$ sudo chown -R username.username /home/username/
$ sudo /etc/init.d/kdm restart

but wasn't succesful, tried with and without sudo, and "username", and "carl" the user

4: Now the Kubuntu login responds the same to the 3 users avaiable there, the brief blank screen followed by return to the login screen. Entry of an incorrect password does trigger the red message.

Thanking in advance for help

---

