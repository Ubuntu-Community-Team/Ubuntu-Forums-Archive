---
title: "Need Root Login (temporary)"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Whhpssh on 2006-09-28
Hi all,

First off, thanks for creating and maintaining a great, helpful community.  I'm impressed.  I've been able to find a great deal of information about Ubuntu and most of my questions are answered before I even ask them.

Now I have one that has me completely stumped.  I read through [THIS](http://www.ubuntuforums.org/showthread.php?t=267104) thread and found various ways to enable the root login, but none of them work for me.  Here's what happened.

Yesterday, I was looking for a way to start Firestarter at bootup.  I like to have the icon active next to my clock so I can click on it and see statistics.  So I found a page that described how to do this and I made some changes.  One of the changes was to add the line [color=red]username ALL= NOPASSWD: /usr/bin/firestarter[/color] to my /etc/sudoers file, using my login name.

When I tried to save the file, even though I was using sudo, it said the file was read only.  I then changed the permissions on the file so I could save it, saved it, and rebooted.  Ever since then, I've had problems starting any application under my System menu and today I receive [color=red]sudo: /etc/sudoers is mode 0660, should be 0440
[/color] any time I try to use the sudo command.  Obviously I screwed up and forgot to make the file read only again.

So, since I can't change the password of the root account under the system menu (it tries to start then doesn't), can't change my login screen to allow root login (also tries to start, then doesn't), can't run any sudo commands, and can't change the permissions on the file without being root, is there a way I can get root access long enough to change the permissions back to read only?](*,) ](*,) ](*,) ](*,) ](*,) 

Any help is appreciated.  Thanks.  :D

---

### Post by hyper_ch on 2006-09-28
try

```

sudo -i

```

---

### Post by scrattox on 2006-09-28
I'm guessing that 'sudo -i' won't work if /etc/sudoers mode is incorrect, but I'm not near enough to a PC I can test it on.

You could try booting into single user mode.

(From memory, so it may not be entirely accurate:)

Reboot, and when you see the "grub" bootloader menu, go to your normal boot option and press "e" to edit.
Then go to the line which start "kernel" in the next menu and press "e" again.  Go to the end of the line you are editing with the arrow keys and enter the word "single".

Once you are finished editing, boot with these settings (I think by pressing "b" but look on the screen for commands) and you should boot to a shell (no X window stuff) and you'll be logged in as root without having to enter a password.

Then you can correctly chmod /etc/sudoers and reboot!

Hopefully!  :)

---

### Post by DennShin on 2006-09-28
I would think using "gksudo nautilus" would work.  You should be able to edit any files in that window from my understanding.

---

### Post by Whhpssh on 2006-09-28
> **sjau said:**
> try

```

sudo -i

```


Doesn't work.  Any time I type "sudo", I get the error I listed in my main post.

---

### Post by scrattox on 2006-09-28
No "sudo" or "gksudo" commands are going to work, as the OP says.
His modification to the permissions of /etc/sudoers has broken the whole sudo mechanism.

---

### Post by Whhpssh on 2006-09-28
> **DennShin said:**
> I would think using "gksudo nautilus" would work.  You should be able to edit any files in that window from my understanding.

user@ubuntubox:~$ gksudo nautilus
sudo: /etc/sudoers is mode 0660, should be 0440
user@ubuntubox:~$

---

### Post by aysiu on 2006-09-28
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

You need to boot into recovery mode

---

### Post by Whhpssh on 2006-09-28
> **scrattox said:**
> I'm guessing that 'sudo -i' won't work if /etc/sudoers mode is incorrect, but I'm not near enough to a PC I can test it on.

You could try booting into single user mode.

(From memory, so it may not be entirely accurate:)

Reboot, and when you see the "grub" bootloader menu, go to your normal boot option and press "e" to edit.
Then go to the line which start "kernel" in the next menu and press "e" again.  Go to the end of the line you are editing with the arrow keys and enter the word "single".

Once you are finished editing, boot with these settings (I think by pressing "b" but look on the screen for commands) and you should boot to a shell (no X window stuff) and you'll be logged in as root without having to enter a password.

Then you can correctly chmod /etc/sudoers and reboot!

Hopefully!  :)



How do I get into the Grub bootloader menu?  I'll try it but I think my machine just boots straight to Ubuntu (it's a standalone installation).

---

### Post by scrattox on 2006-09-28
> **Whhpssh said:**
> user@ubuntubox:~$ gksudo nautilus
sudo: /etc/sudoers is mode 0660, should be 0440
user@ubuntubox:~$

Try my "single user boot" suggestion then!  :)

---

### Post by bswilson on 2006-09-28
You can only edit the /etc/sudoers file with the command **visudo**.  You can't do gksudo or sudo -i on this special file.

---

### Post by scrattox on 2006-09-28
> **Whhpssh said:**
> How do I get into the Grub bootloader menu?  I'll try it but I think my machine just boots straight to Ubuntu (it's a standalone installation).

Even with a standalone, I'd think you'd see the menu.
It also offers a "memtest" option on my (xubuntu) installation.
If not, look for any hints very early in the boot.  It will probably tell you how to activate the menu.

---

### Post by aysiu on 2006-09-28
If you're not dual-booting, I believe you have to press Escape to see the boot menu.

---

### Post by Whhpssh on 2006-09-28
> **scrattox said:**
> Even with a standalone, I'd think you'd see the menu.
It also offers a "memtest" option on my (xubuntu) installation.
If not, look for any hints very early in the boot.  It will probably tell you how to activate the menu.

> **aysiu said:**
> If you're not dual-booting, I believe you have to press Escape to see the boot menu.


Correct.  I found this out when I tried his suggestion.

Scrattox, you officially ROCK!  There's only one change I'd make to your instructions since I had to try it a couple times before it worked.

> **scrattox said:**
> Reboot, and when you see the "grub" bootloader menu, go to your normal boot option and press "e" to edit.
Then go to the line which start "kernel" in the next menu and press "e" again.  Go to the end of the line you are editing with the arrow keys and enter the word "single". [color=red]Make sure you put a space between the end of the line and the word single[/color]

Once you are finished editing, boot with these settings (I think by pressing "b" but look on the screen for commands) and you should boot to a shell (no X window stuff) and you'll be logged in as root without having to enter a password.

Then you can correctly chmod /etc/sudoers and reboot!

Hopefully!  :)


I now have sudo access again and my administrative commands also work.  Thank you all for your suggestions and help.  Hopefully my experience here will answer somebody else's question.  That's why I love this community.  You post a question and it gets answered in mere minutes   :D

---

### Post by Whhpssh on 2006-09-28
> **bswilson said:**
> You can only edit the /etc/sudoers file with the command **visudo**.  You can't do gksudo or sudo -i on this special file.

Good to know if I ever decide to edit it again...  :)

Thanks.

---

### Post by scrattox on 2006-09-28
Glad to help!

Actually, first question I've answered.  I was inspired by the "help ubuntu in 30 minutes" (or whatever it is) wiki page.

:D

---

