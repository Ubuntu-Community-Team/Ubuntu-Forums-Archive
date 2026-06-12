---
title: "Not root...can't sudo"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by Jonah21 on 2005-12-10
First of all, I apologise if this has been asked a million times over, but I tried some searches and couldn't find a thing.

I've dabled with Linux before, mostly Ubuntu, but never stuck with it because of trouble getting my Speedtouch 330 modem to work. Well, this time I gave it one more go, and I'm pretty sure I've cracked it...except...

I was using the guide at [http://linux-usb](http://linux-usb), and for the first time the firmware was split. The only problem now is that I can't use the terminal properly;  I can't use sudo, nor do I have certain permissions.

And when it asks my password in the terminal, I type but nothing comes up.

I think I've heard of something like this happening before, but I can't remember.

     Also; I want to make Microsoft XP Pro the default loader for my family, and I know to change the "default 0" to "default 4", but I can't remember the line of shell code to access the menu.lst file...If anyone knows, please tell.


Any help'd be great! Thanks in advance.

---

### Post by invalid on 2005-12-10
> And when it asks my password in the terminal, I type but nothing comes up.
This is a normal security feature. Nothing shows up on the terminal screen, but whatever you type *does* go in. This, by default, is your first users password.

---

### Post by Jonah21 on 2005-12-10
So do I just type in "mypassword" when it asks and press enter?

---

### Post by invalid on 2005-12-10
[QUOTE=Jonah21]So do I just type in "mypassword" when it asks and press enter?[/QUOTE]
Correct

---

### Post by 23meg on 2005-12-10
Do you mean that no action is taken at all whenever you enter a command with a sudo prefix?

[QUOTE=Jonah21]
     Also; I want to make Microsoft XP Pro the default loader for my family, and I know to change the "default 0" to "default 4", but I can't remember the line of shell code to access the menu.lst file...If anyone knows, please tell.
[/QUOTE]
It's /boot/grub/menu.lst

---

### Post by Jonah21 on 2005-12-10
It goes a bit like this:

I put in: "sudo whatever"
return: "Password:"
I put in: "mypassword", and press enter, but sometimes I leave it.
return: "incorrect"

---

### Post by 23meg on 2005-12-10
Are you 100% sure that you're entering the correct *user password* that you set up during installation and not a *root password* that you may have enabled manually later on?

---

### Post by Jonah21 on 2005-12-10
Yeah. I have no fear of security, as this is just a test, but I made a user named "admin" with the same username, and "wmxx" as a password.

---

### Post by gord on 2005-12-10
if you want to get your speedtouch modem working you should follow [http://speedtouchconf.sourceforge.net/](http://speedtouchconf.sourceforge.net/) it will handle everything for you. the speedtouch modem is an arse to get working but its possible (i'm using one right now)

---

### Post by Jonah21 on 2005-12-10
I think I can get it working with the other tutorial; but I would probably have to get sudo to work for that, too?

---

### Post by Jonah21 on 2005-12-10
Sorry for double-posting; just wanted to say that what was said in the second post was true, and I am now online in Linux!

Thanks to you all, I wall now stay and help those with whatever knowledge I have. :D

---

### Post by Jonah21 on 2005-12-10
Sorry...posting here AGAIN.

But...what's the exact command line to open a text file, in this case menu.lst? That is; use a sudo command and edit a line to make windows my default choice for booting.

Once again I apologise...n00b.

---

### Post by gord on 2005-12-10
gedit <file>

or for root priviliges
sudo gedit <file>

---

### Post by Jonah21 on 2005-12-10
Thanks; "nano" worked as well.

---

