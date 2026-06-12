---
title: "System &gt; Administration tools won't work"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by Califax on 2006-01-27
I try to do anything in administration, such as add programs, it ask for pass then just starts to load and stops. Then If I try to load anything else in administration it just starts to load then quits w/o asking for pass... I tried rebooting a few times

---

### Post by detyabozhye on 2006-01-27
Your current user is probably not in the sudoers list.

Try this in the terminal:

sudo gedit /etc/sudoers

and add this line at the bottom:

<your user name>	ALL=(ALL) ALL

---

### Post by detyabozhye on 2006-01-27
Wait a sec, that won't work, you can't sudo if your user isn't a sudoer.

Try typing "su" in the terminal, then the password, then try "gedit /etc/sudoers", and then do the other step I mentioned.

---

### Post by Califax on 2006-01-27
I try sudo gedit /etc/sudoers

It does not do anything, just goes to next line [-( 

My su Password apparently isn't same as sudo password because the authentication fails...not sure how that happens

The password works for apt-get etc. and I am on original user I installed Ubuntu with. Not sure exactly what I could have done to cause this except I tried to wine a windows program...

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=Califax]I try sudo gedit /etc/sudoers

It does not do anything, just goes to next line [-( 

My su Password apparently isn't same as sudo password because the authentication fails...not sure how that happens

The password works for apt-get etc. and I am on original user I installed Ubuntu with. Not sure exactly what I could have done to cause this except I tried to wine a windows program...[/QUOTE]
Try booting into recovery mode.  You will have a terminal and will be logged in as root without needing a password.  Then you can edit the /etc/sudoers file with visudo.

---

### Post by YumaJim on 2006-02-10
I put my user ID at the end of the /etc/sudoers file using "visudo" command
as user 'root' using command 'su'. you have to set a passwd for root inorder to do this.

As a regular user, you might try:    $ sudo visudo     if your  sudo passwd is working.

Put this did not help my problem of getting Administration mode to work.
It is still broken.

---

### Post by Madpilot on 2006-02-10
You may well have broken something, YumaJim...

Read [the wiki's root/sudo page]("https://wiki.ubuntu.com/RootSudo") for information. Basically, whenever Ubuntu asks for a password, it wants your own user password - there is no root password in a default install.

---

### Post by YumaJim on 2006-02-13
When I try to use the System Settings tools all the fields are grayed, even after
I login to the admin. mode. It seems that I am getting authentication failures
and I get a message at times that says 'dcopserver' may not be running.
When I do a 'ps -e'. I can see the dcopsever. See the attachments. I sure
would like some help solving this problem.

I will have to add the attachments in another post a little later.

Thanks,
YumaJim

---

### Post by Chappy on 2006-02-13
Califax, fwiw, I am having the exact same problem, and I have not tried to install anything. All I am trying to do is get to Networking which is after Sys/Admin. When I click on System, the Administrator, then Networking, it goes to the taskbar, says "starting network", and then stops w/in 15 secs or so. I can't get any further. I need "Linux for Dummies" or something. Being a newbie is a lesson in patience. Don't throwout Windoze till you have Linux figured out. I have no idea how to do commands. I haven't done them since before w95, about 12 years ago.

---

### Post by detyabozhye on 2006-02-13
Like I said before, try this:

```
su
Password:

gedit /etc/sudoers
```

Add this line at the bottom:

<your user name> ALL=(ALL) ALL

Save it and close the Text Editor.

```
exit
```

---

### Post by YumaJim on 2006-02-15
Her's the error message files that I get.
See attachments. :( 

YumaJim


[ATTACH]6149[/ATTACH]

[ATTACH]6150[/ATTACH]

---

### Post by YumaJim on 2006-02-15
See previous post - sorry about this dup post.

---

### Post by YumaJim on 2006-02-15
I see in Bugzilla that this problem has been reported many times (32) at this date. Do a search on 'systemsettings'.

---

### Post by detyabozhye on 2006-02-15
What are the permissions of "/etc/sudoers"? They should be 440.

---

### Post by YumaJim on 2006-02-15
yes - they are set to 440

---

### Post by detyabozhye on 2006-02-15
hmm, then I don't know what the problem could be, I don't use KDE, btw, so I don't know if it's a KDE specific problem or not.

---

### Post by towsonu2003 on 2006-02-16
[QUOTE=YumaJim]I see in Bugzilla that this problem has been reported many times (32) at this date. Do a search on 'systemsettings'.[/QUOTE]
I would subscribe to each one, and also post a comment as well to get some more attention... until then, you can use [coe]kdesu command[/code] For synaptic (I know kde doesn't have that, but I donno what kde has...), the command would be kdesu synaptic

---

