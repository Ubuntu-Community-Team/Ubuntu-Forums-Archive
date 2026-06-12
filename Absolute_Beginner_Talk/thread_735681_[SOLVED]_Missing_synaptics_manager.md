---
title: "[SOLVED] Missing synaptics manager"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by skrap on 2008-03-25
I have installed ubuntu gutsy and I do not have a synaptics package manager link under system admin
or there is no add/remove link under applications.  Also when I tried to install thunderbird  after I downloaded to desktop using sudo apt-get thunderbird in terminal  and it asks for my password which I enter and nothing happens.

Another problem I am having is when I try to run update manager and I enter password I get error message and nothing happens.

---

### Post by glennric on 2008-03-25
Type
```
sudo apt-get update
```
and then
```
sudo apt-get install thunderbird
```
in a terminal and post the output of these commands here.

---

### Post by Hospadar on 2008-03-25
can you start synaptic from the command line?  what error messages do you get when you try to update? could you post the output of "which synaptic", "which dpkg" and "which aptitude"

---

### Post by ad_267 on 2008-03-26
It sounds to me like you don't have administrator privileges and aren't in the sudo list, sorry but I don't have the knowledge to confirm this and help out more.

You will probably need to boot into recovery mode to get a root login and add yourself to the sudo list

---

### Post by Oldsoldier2003 on 2008-03-26
> **ad_267 said:**
> It sounds to me like you don't have administrator privileges and aren't in the sudo list, sorry but I don't have the knowledge to confirm this and help out more.

You will probably need to boot into recovery mode to get a root login and add yourself to the sudo list
```

id <yourusername>
```

will ist your groups. if you aren't in the admin group you usually won't have rights to install software unless the groups have been modified.

---

### Post by skrap on 2008-03-26
uid=1001(skrap) gid=1001(skrap) groups=1001(skrap),4(adm),20(dialout),
24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin)

This is the result from id skrap (username) it does not look like I have adm privileges

---

### Post by skrap on 2008-03-26
OK thanks for the replies.  I have found out that my username is not in the sudoers files
How do I add and get admin privileges?

---

### Post by N1N31NCHN41L5 on 2008-03-26
command line - is that the terminal??

and how would you open a program in command line say camstream, that you dont know where synaptics installed it at

---

### Post by northern lights on 2008-03-26
> **N1N31NCHN41L5 said:**
> command line - is that the terminal??
Pretty much. The gnome-terminal is a commandline interface. In KDE it's the "Konsole". Same thing.

> **N1N31NCHN41L5 said:**
> and how would you open a program in command line say camstream, that you dont know where synaptics installed it at

The correct command (i.e. name of the executable) should do it, as your OS should "know" where it is located. If you wanna find out, open a terminal and type ```
whereis camstream
```
Linux is damn intuitive...

---

### Post by N1N31NCHN41L5 on 2008-03-26
i downloaded it in synaptics manger i dont know the executable

or is it what glenrick wrot in the second post????

---

### Post by northern lights on 2008-03-26
mkey, I've installed this package now.

Guess what? The command to start camstream is - suspense... - "camstream"!

So, in the terminal, konsole, shell, commandline (or whatever you prefer to call it) or the "Alt+F2" dialog type "camstream" and hit Enter.

After typing "cams" the "Alt+F2" dialog completes the entry automatically, hitting TAB in the terminal will do the same...

> **northern lights said:**
> Linux is damn intuitive...

---

### Post by ad_267 on 2008-03-27
Ok. . . . 
Back to the original post:
> OK thanks for the replies. I have found out that my username is not in the sudoers files
How do I add and get admin privileges?

You need to boot up your computer and in the boot loader, you need to select to boot in to recovery mode. If you aren't dual booting and GRUB usually doesn't appear I think there's a key you need to press to get it.

Once in recovery mode you have a command line with root access so can add yourself to the admin group. To do this type:
```
adduser YourUserName admin
```

And do you know how you came to not have admin privileges in the first place? When you install Ubuntu the first account you create will automatically have admin privileges.

If you are just using a different login and still know the login details for the original user then you don't need to do what I mentioned above. You can log in as that user and add yourself to the admin group by going to system - administration - users and groups, then click on your user, select properties, click on the privileges tab and tick administer the system.

---

### Post by ad_267 on 2008-03-27
Also, I just found this here: [https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes)

If this sounds like what might have caused your problem you might need to follow these steps instead:

> If the mail-server task is selected during installation and "No configuration" is selected in response to the question "General type of mail configuration:", then the initial user will be set up without sudo access. To repair this, boot in recovery mode and run:

addgroup --system admin
adduser USERNAME admin
echo '%admin ALL=(ALL) ALL' >>/etc/sudoers

where USERNAME is the name of the initial user created during installation. Selecting any other answer to the "General type of mail configuration:" question will avoid this problem. Bug #158952 [https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/158952](https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/158952)

---

### Post by skrap on 2008-03-27
Thanks ad_267 

The adduser line did the trick I can now move on to the next adventure.

---

