---
title: "[SOLVED] run script automaticaly AFTER logon"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Kilarin on 2007-08-16
I'm very new to Ubuntu and Linux, but, trying to kick the microsoft habit. :)

I want to mount a truecrypt volume every time I log in.  I've got a script that works, and I've recently learned (here) how to create a launcher that works even better.  

BUT, I'd like the script to run automatically as soon as I log in.   So that I enter my user name and password into ubuntu, and the very next thing that pops up is the trucrypt window asking for it's password.

In Windows, I simply put a batch job into the startup folder and it ran every time I logged on.  How would I do the same thing in linux?     

Thank you VERY much for your assistance!

---

### Post by st33med on 2007-08-16
Go to System>>Preferences>>Sessions and add you script name to the additional startup programs.

Also, if you want to make it an executable, make sure the script has something like this at the top:
```
# /bin/sh
```

and do this in the terminal:
```
 sudo chmod +x  /path/to/program 
```

---

### Post by Kilarin on 2007-08-17
thank you for your help!  But I'm still doing something wrong.

I've got a script located on my usb external hard drive.  The owner of the script is root (I'm not certain how that happened), but it IS set to be executable in the permissions.

The script looks like this:
# /bin/sh
truecrypt -u /media/disk/DCH/evol/dch /media/tc1

(I'm not certain what the /bin/sh is for, but I put it there!) :)
Now this script will mount my drive just fine if I simply double click it and select "run in terminal".

So I went into System/Preferences/Sessions   and added this script to the list.  It even shows up in the "current session" tab.  (order 50, style:settings, status question mark)

But when I logon, I don't get a prompt to enter my password for the encrypted volume, and, of course, the truecrypt volume is not actually mounted.

Could it be because the truecrypt volume and the script are both on a usb external hard drive?  surely that drive is mounted before these startup scripts are run?

OR, is there some setting I've goofed up that is making this not run "in terminal", so it can't actually prompt for the password?

Or is it something else?

Again, any help is appreciated.  I'm loving Ubuntu!   Thanks!

---

### Post by mattmole on 2007-08-17
I suspect that the drive is not mounted until you log into gnome.

To check it out:

1) Switch on the PC and let it boot to the login screen
2) Ctrl-Alt-F1 and this will drop you to a terminal
3) Login
4) nano /etc/mtab
5) If your memory stick does not appear in there then it is likely not mounted

If this is the case, then maybe you need to run a script on the local hdd that mounts the device and then runs the other script

mattmole

---

### Post by Kilarin on 2007-08-17
It's actually an external USB Hard Drive, but I don't know if that makes any difference.
I tried the cool nano command, and the mount point for my USB external hard drive DID show up.  So I'm still a bit baffled why the script won't run.  <sigh>

thanks!

---

### Post by mattmole on 2007-08-17
Can you post the line with the info about your mounted external hdd please?

Is the script on the external drive? Im wondering if the 'exec' option is missing from your mounted drive, and then scripts wouldn;t be able to run.

mattmole

---

### Post by Kilarin on 2007-08-17
I'm an idiot.  closer examination proved that I was misreading one of the other drives as my usb drive.  You are correct, the usb drive is NOT mounted when I do the nano command.

so, since the usb external hard drive is not mounted when the "session" commands are run, no chance of mounting my truecrypt volume that is on that external hard drive.  Ok, no problem, I'l just have to keep clicking the button.

BUT, I'm still worried I'm doing something wrong setting up the sessions.  Since I was playing with them I tried setting up firestarter to run at boot, as detailed here: [http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

I have the session set up with the command: gksudo firestarter --start-hidden
and yet, not tray icon for firestarter.  So perhaps I have something ELSE wrong as well?

Anyway, thank you for your assistance!  I'm learning.  slowly, but learning.

---

### Post by stchman on 2007-08-17
> **st33med said:**
> Go to System>>Preferences>>Sessions and add you script name to the additional startup programs.

Also, if you want to make it an executable, make sure the script has something like this at the top:
```
# /bin/sh
```

and do this in the terminal:
```
 sudo chmod +x  /path/to/program 
```

He needs the first line of the script to be the following:

#!/bin/sh (tells the terminal which shell to use)

Then he should do this:

chmod 755 <script> (makes the script executable)

---

### Post by Kilarin on 2007-08-17
ok, just to eliminate the issue of the usb drive, I copied my script and truecrypt vol into my home directory and tried it from there.  I how have:

Script: /home/donald/truecrypt-test.sh with permissions -rwxr-xr-x 

contents of script:
#!/bin/sh
truecrypt -u /home/donald/dch /media/tc1

and, again, this script WORKS if I just double click it and select "run in terminal"

I then go to System/Preferences/Sessions where I set up a session that has a command of:
/home/donald/truecrypt-test.sh

And yet, when I do a restart, and log in, no truecrypt prompt for the password to my volume appears, and, of course, the volume does not mount.

I'm a bit baffled.

---

### Post by nemequ on 2007-08-17
I'm guessing the password prompt appears in the terminal window, not in a popup window or something? If so, you need to run in a terminal. Put this in the startup programs for your session:

```
/usr/bin/gnome-terminal -x /usr/bin/truecrypt -u /home/donald/dch /media/tc1
```

Obviously, /usr/bin/truecrypt will need to be the correct path to your truecrypt exexutable

I'm surprised you don't need superuser privileges for this, but you say it's working without them (you're not running your script as root)?

---

### Post by Kilarin on 2007-08-17
> ```
/usr/bin/gnome-terminal -x /usr/bin/truecrypt -u /home/donald/dch /media/tc1
```
thank you!  that works!  It was just a matter of getting the program to run in a terminal!!!!

> I'm surprised you don't need superuser privileges for this, but you say it's working without them (you're not running your script as root)?
If I'm understanding how it works, truecrypt issues the sudo itself, and the user is prompted for their user password before asking for the volume password, and then the volume is mounted.

BUT, I added truecrypt to my sudoers file and now truecrypt can run and only prompts me for the volume password.  

thank everyone VERY much for thier help.  I am learning.  bit by bit.

Now, if I could just figure out why firestarter won't show up in my tray.  I've followed the instructions and added to my sessions start programs the command:
gksudo firestarter --start-hidden

But no firestarter in the tray.

---

### Post by BartInTN on 2008-01-15
Thank you, guys.  I gave up on Forcefield when it refused to remember my history or favorites... and it prompted me 10 times for every volume I wanted to mount.  So now I just have simple scripts to mount and unmount my truecrypt columes, as you described above.  I just put them in my application menu.

---

### Post by Kilarin on 2008-01-15
Good news is that Truecrypt says a GUI for Linux is coming very soon!

[http://www.truecrypt.org/future.php](http://www.truecrypt.org/future.php)

I won't use it that much, I prefer setting up scripts.  BUT, it will increase the ease of use for new users, and will provide a tool that I can use whenever I'm doing something unusual like mounting a backup, changing a password, or creating a new header.

They are ALSO promising Windows System partition encryption.  That should be interesting for the seldom used windows half of my dual boot machine.

---

