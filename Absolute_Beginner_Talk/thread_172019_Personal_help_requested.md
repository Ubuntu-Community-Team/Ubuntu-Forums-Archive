---
title: "Personal help requested"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by Reprobate on 2006-05-07
I posted a question to one of the Aboslute Beginners threads and rather than an answer, was told not to post there. 

Specifically "This is not the appropriate place to solicit help for individual problems.  The purpose of this thread is to provide general information on how a person can go about helping themselves to solve a problem."

So this thread is to seek help with MY problem.  If I am still incorrect on how, where, or what to post, feel free to tell me (again).

My problem is that I have loaded Ubuntu on one of my laptops.  I was religious about writing down the username and password that I was prompted for.  I was never asked for a root password for the system as it loaded.  Did I miss that step?  In any case, I am at the login screen.  Nothing I enter works.  I can not get in as root, I can not get in with the username/password that I did enter.  Not being able to get in is... well, fundimental to getting to use sudo or any other command.  Am I missing something?  Is there some way to get to a command line to 'work' on the problem from there (bypassing the windows based interface)?

My original intent in asking for help was to avoid whatever parts of reloading the system that I could.  If starting from scratch is the answer, please tell me so.  If there is some other way on a freshly loaded system, to access things and 'correct' my problem, THAT is what I really want to do.

At present, this is what I see:
 a login screen with ubuntu,
the username/password entry box,
a language button, a session button
a reboot button a shutdown button and lastly, the system name and the time.

Should I reload the system or is there a 'shortcut' to rebiuld the password files or whatever is preventing me from getting access to my machine?

Any help would be greatly appreciated.

Thanks.

---

### Post by n3tfury on 2006-05-07
Perhaps you accidentally have/had the CAPS lock on?

---

### Post by unbuntu on 2006-05-07
[QUOTE=Reprobate]Is there some way to get to a command line to 'work' on the problem from there (bypassing the windows based interface)?
[/QUOTE]

I think you can get access to your hd with a live cd.

---

### Post by harisund on 2006-05-07
OK, there is no 'root' user per se. The user name and password that was prompted for while system installation is what you will need to log in at the login screen. 

Next, you are not installing on a FAT partition are you? I was informed somewhere that you if install on a FAT partition, crazy things might happen short of the sky falling on our heads. (And I am guessing not being able to log in is one.) 

If you want to avoid the GUI, you could press the keys Ctrl, Alt and F1 all together and you will be presented with the deadly console. Again you will have to login, and if you couldn't login into the GUI, chances are you are not going to be able to login into this either. 

By the way you do remember the username and password you had set when installing, right?

---

### Post by nalmeth on 2006-05-07
He said he wrote it down on paper right away.
I don't get why you're not able to log in, and sorry you might have been discouraged to ask for help, people become irritated when you "hijack" threads. :rolleyes:
I agree it is annoying, but people are sometimes just a little too *curt* with their responses.
You're definately posting in the right forum now, don't be afraid to start your own threads.
Not having your username/password work is quite a nuiscance to being able to work!! Try rebooting the computer, and when you see "GRUB" loading, pick recovery mode.
Then when you drop into the command line type: 
"passwd"
(enter a password)
this create's the "root" user and password, which we generally don't need, but this will work for now, if you don't want to install fresh.
Reboot again
"reboot"
and try to log in as root with the password you set.
Then when you've logged in, go to SYSTEM --> ADMINISTRATION --> USERS
and you can edit the password for the user you created.


Post back if this works/fails

---

### Post by Nequeo on 2006-05-07
From the boot menu, select the (Recovery mode) option. This will give you command-line access as root. 

Then type 'passwd user' where 'user' is the name of the user account you created when you installed Ubuntu. Then you can put in a new password.

You can make sure it works by typing 'su - user' where, again, 'user' is your user account. 

If it lets you login in that way, then just type 'exit' to get back to the root prompt, then 'init 2' to get back into normal graphical mode. (No need to reboot).

Hope that helps,

---

### Post by nalmeth on 2006-05-07
Nequeo's advice is best, avoid my suggestion of creating the root user.
I couldn't remember how to set user passwd, thanks for refresh Nequeo

---

### Post by Reprobate on 2006-05-07
[QUOTE=nalmeth]He said he wrote it down on paper right away.
I don't get why you're not able to log in, and sorry you might have been discouraged to ask for help, people become irritated when you "hijack" threads. :rolleyes:
I agree it is annoying, but people are sometimes just a little too *curt* with their responses.
You're definately posting in the right forum now, don't be afraid to start your own threads.
Not having your username/password work is quite a nuiscance to being able to work!! Try rebooting the computer, and when you see "GRUB" loading, pick recovery mode.
Then when you drop into the command line type: 
"passwd"
(enter a password)
this create's the "root" user and password, which we generally don't need, but this will work for now, if you don't want to install fresh.
Reboot again
"reboot"
and try to log in as root with the password you set.
Then when you've logged in, go to SYSTEM --> ADMINISTRATION --> USERS
and you can edit the password for the user you created.


Post back if this works/fails[/QUOTE]
Thank you Nalmeth, for the encouragement as well as the tech advice.

How do I "..pick recovery mode" when I see GRUB loading?  It wisses by fairly quickly and, while I think I see a prompt for input, I am not able to make out any other option but '0'.  Is that what I am looking to enter?

Thanks again.

---

### Post by nalmeth on 2006-05-07
Yeah, it does fly by pretty fast, though it is rarely needed to pick another kernel.
People complain a lot about boot-times, so this must be an area they wanted to skim a bit off.
As soon as you see the GRUB list (right after it say's loading GRUB), hit up or down on the keyboard to stop the 3 second timer.
You should see 2 or 3 different kernel selections, the bottom one should say recovery mode on the right.
EDIT:
Again use Nequeo's advice, and type:
passwd user
(with your username of course) rather than just 
passwd
It is unneccessary to create the root user, so just do this to reset your password for the user you created.

---

### Post by Reprobate on 2006-05-07
[QUOTE=Nequeo]From the boot menu, select the (Recovery mode) option. This will give you command-line access as root. 

Then type 'passwd user' where 'user' is the name of the user account you created when you installed Ubuntu. Then you can put in a new password.

You can make sure it works by typing 'su - user' where, again, 'user' is your user account. 

If it lets you login in that way, then just type 'exit' to get back to the root prompt, then 'init 2' to get back into normal graphical mode. (No need to reboot).

Hope that helps,[/QUOTE]
I am equally apprieciative of Nequeo's advice and assistance.  I am confuswith though as to where the boot menu is to be found.  Rather than repeat the screen that I see with its limited options (no 'root menu' to be seen), I have opted for the 'long way'.  I am starting from scratch (sort of) and am loading the system fresh.  My question at this point is this; when I am partitioning the  disk, there were 2 options that looked ok and I don't know which is the 'correct' one.  The options are as follows:

        Resize IDE1 master, partition #1 (hda1) use freed space
        Erase entire disk: IDE1 master (hda) - 8.2 GB  IBM-DYLA-28100
        Erase entire disk and use LVM: Ide1 master (hda) - 8.2 gb IBM-DYL
        Manually edit partition table

The first time, I selected option #3 "Erase... use LVM...".  Might this be the 'mistake' that I made?  And, which SHOULD I select here?  Also, I am sorry to be acronym deficiant but what is LVM?

Thank you guys again, very much for your understanding and your assistance.

---

### Post by nalmeth on 2006-05-07
Ahh, yes unless you know what you're doing, you should just select the second option, which will erase the entire disc and (though it won't say here) will install on a EXT3 filesystem.
I don't think this has anything to do with your logging in problem, but I wouldn't rule it out.

Again, pick the second option, not the LVM option.

Also, when you're done, you might like to check out [automatix]("http://www.ubuntuforums.org/showthread.php?t=138405")

---

### Post by Reprobate on 2006-05-07
[QUOTE=nalmeth]Yeah, it does fly by pretty fast, though it is rarely needed to pick another kernel.
People complain a lot about boot-times, so this must be an area they wanted to skim a bit off.
As soon as you see the GRUB list (right after it say's loading GRUB), hit up or down on the keyboard to stop the 3 second timer.
You should see 2 or 3 different kernel selections, the bottom one should say recovery mode on the right.
EDIT:
Again use Nequeo's advice, and type:
passwd user
(with your username of course) rather than just 
passwd
It is unneccessary to create the root user, so just do this to reset your password for the user you created.[/QUOTE]
Nalmeth, slight correction, since I read your posting prior to selecting to repartition, to stop the 3 second timer one must hit the esc key.  The boot menu is available then.

I'll let you know how I fair.

Thanks again.

---

### Post by nalmeth on 2006-05-08
Well, whaddya know. I'll have to remember that. I think it shows grub list when you've installed another OS, giving you time to pick. That's where I think I went wrong.
Good luck with your install

---

