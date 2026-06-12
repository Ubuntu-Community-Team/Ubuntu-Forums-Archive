---
title: "Help with setting super user permits"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by linuxcamayoq on 2006-09-23
Hi folks,

I was an old DOS skilled user when I was a kid, so I faced the challenge to start learning linux without too much fears... but the first steps are always the hardest.

I have found problems trying to install my USB modem in linux since I cannot access internet from Ubuntu so far.  But when I want to issue some important commands through the shell window the system tells me I have no super user rights and asks me for my root user password.  The main problem is that when I installed Ubuntu and followed the menus, I did not see anything about setting a super user, I just created the requested user profile.  And now when I want to get super user rights Ubuntu asks me for a password I never set, and without accessing to super user rights I cannot configure my system as I need.

I am running Ubuntu in my Personal Home computer, I am not part of any LAN and of course I have no "system administrator" but myself.

PLEASE, HOW CAN I CREATE A SUPER USER PROFILE THAT I CAN USE TO PROPERLY SET MY SYSTEM?  Remember I still dont have access to Internet from Ubuntu since I cannot install my USB modem without super user rights.

As a totally new user of linux I will thank any help you can give me with this problem, I hope to improve my linux skills in the future but right now, even my ancient skills to deal with the DOS command line, I feel totally in the dark with the linux shell...!!!!

---

### Post by Henry Rayker on 2006-09-23
In Ubuntu (and linux in general) one key aspect is security. By logging in as super-user all the time, you are not terribly secure.

In order to execute a single command as a super-user, you can type sudo before your command.

for example, to edit your menu.lst file, you would type

sudo gedit /boot/grub/menu.lst

This would open the file with super-user rights, but leave your system secure.

If this isn't good enough, there are ways to allow you to logon as root, but I find the sudo is a small price to pay for a little more security.

---

### Post by æþeling on 2006-09-23
just put

```

sudo

```

In front of the command. Then, you'll be prompted for the password you entered during the installation.

---

### Post by linuxcamayoq on 2006-09-23
Thanks Henry,  I have read about the sude command previous to start trying with the shell window.  But when linux asks me for the administrator password I write down the only password I have set during my Ubuntu installation, but it is not recognized as the super user pass but only as my profile pass...

It seems during some moment of the install process I should have to enter another password but the only requested was the one to create my profile.

I also know it is safer to use linux with a normal user level  and only use the super user rights for more careful managment, but I never set any other user password than the one I use... it is a little bit frustrating to be asked about a high security password I never set... what should I do?  Maybe to install Ubuntu again?  I dont remember any requests about the super user profile during the automated process of installation.

I am ashamed of making so basic questions, but I feel like some one who has the idea of how to drive but doesnt have the key of the car :)

Thanks again for your patience, I am amazed of how fast you answer questions in this forum!

---

### Post by ubuntuuser on 2006-09-23
The root account is disabled by default. The first user you create during your install has superuser privileges via sudo. So when you're asked for a password, enter yours. To get a root shell you could either type ```
sudo -s
``` or you could "enable" the root account with ```
sudo passwd
``` and use ```
su
``` to become root. But this is really not necessary in most cases.

---

### Post by linuxcamayoq on 2006-09-23
Thanks for your tips fellows, this is really a wonderful community.

Greetings

---

### Post by Henry Rayker on 2006-09-23
as Ubuntuuser said, the first account should have superuser rights through sudo. If you are getting an error, it could be one of a couple things.

1) You created a second account. This seems unlikely due to the fact that you remember only giving the installation one password. If you can, in the System menu (in the Applications Places System menubar that is, by default installed on the top left of your screen) go to Administration-Users and Groups, this will show you if you have another user (you may have to enter your admin password and this might not be possible for you)

2) You may be typing the password incorrectly. I was a little weirded out at first when the terminal didn't seem to respond to my keystrokes, so you have to be extra careful when typing the password in. Caps lock can ruin your life in this instance

3) The first time I installed Ubuntu, I actually had a problem similar to this, and couldn't use sudo. I just thought, "this is total BS" and reinstalled. If you haven't done too much configuration, that may be an option for you (if nothing else works). My guess is, without the internet, you can't have done TOO much in getting it up and running thus far.

PS: The speed of replies will vary, but it does tend to be pretty swift...if you'll get a response at all, that is.

---

