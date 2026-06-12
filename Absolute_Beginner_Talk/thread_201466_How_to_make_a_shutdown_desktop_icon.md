---
title: "How to make a shutdown desktop icon"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Frank Golden on 2006-06-21
Hi All,
    Anyone know how to create a desktop shortcut (icon) to shutdown computer.
I know about using 'sudo halt' in a launcher but it causes filebrowser to open and display on restart. I just want a desktop icon I can click that will just close Ubuntu
normally and shut down machine like using the multi-choice icon in the panel but without the choice window.

---

### Post by nalmeth on 2006-06-21
It makes nautilus open when you turn it back on?

did you make the command:
gksudo halt

or something else?

---

### Post by Frank Golden on 2006-06-21
[QUOTE=nalmeth]It makes nautilus open when you turn it back on?

did you make the command:
gksudo halt

or something else?[/QUOTE]
Yeah,
   Annoying huh.
command was 'sudo halt'. What does the 'gk' in your command mean?

---

### Post by nalmeth on 2006-06-21
gksu will bring up a little password prompt display window, pretty nice looking. 

You probably had to check "run in terminal" for the sudo halt right?

Try gksudo and see if it does anything different.

---

### Post by Frank Golden on 2006-06-21
[QUOTE=nalmeth]gksu will bring up a little password prompt display window, pretty nice looking. 

You probably had to check "run in terminal" for the sudo halt right?

Try gksudo and see if it does anything different.[/QUOTE]
Tried gksudo no dice.
BTW don't know if it makes a difference but I have password for sudo disabled (yeah,
I know it's unsecure but I am only user and behind a NAT router).
When I click icon a black screen with white letters and password prompt appears for a few seconds then the second half of the shutdown gui appears then the machine powers down. When I reboot the last thing that happens is File Browser opens to my 
home folder. I don't have to check run in terminal.

---

### Post by aysiu on 2006-06-21
Add this line to your /etc/sudoers file: ```
frankgolden ALL = NOPASSWD: /sbin/shutdown
``` Then create a launcher for the command ```
shutdown -h now
```

---

### Post by Frank Golden on 2006-06-21
[QUOTE=aysiu]Add this line to your /etc/sudoers file: ```
frankgolden ALL = NOPASSWD: /sbin/shutdown
``` Then create a launcher for the command ```
shutdown -h now
```[/QUOTE]

Okay aiysu,
      Just got done breaking my /etc/sudoers file. Tried using sudo gedit /etc/sudoers
to add line you suggested.  Got an error message when tried to save about not being able to save to a read only file. So I 'sudo chown frankgolden /etc/sudoers'
to change permissions and save new line. Figured to change back afterwards.
Now after setting back to original permissions and trying to 'sudo chown root /etc/sudoer' I get message "sudo: /etc/sudoers is owned by uid 1000, should be 0"
It apparently won't let me change file back. I don't know what I am doing here or if
I broke my install of Ubuntu. This must be a special file, with special needs.
Any thought aysiu.

---

### Post by RRS on 2006-06-21
Just tried "sudo gedit /etc/sudoers" myself for same purpose and noticed this line;
"# This file MUST be edited with the 'visudo' command as root."

Tried reopening file with visudo instead of sudo and got a list of options instead so I guess its time to find the link I have explaining sudo, root ,etc. and do my homework.

Posting because it may be related to the error message you got.

BTW, interested in same final result as you, "one click shutdown", but I don't have sudo password dissabled.

---

### Post by aysiu on 2006-06-22
Frank, try booting into recovery mode. This will make you root. Then ```
chown root:root /etc/sudoers
``` That should make it owned by root.

---

### Post by Frank Golden on 2006-06-22
[QUOTE=aysiu]Frank, try booting into recovery mode. This will make you root. Then ```
chown root:root /etc/sudoers
``` That should make it owned by root.[/QUOTE]

Hi aysiu, 
    Thanks to your tutorial about partimage and the fact that I had made an up to date image of my Ubuntu install. I chose the "easy" way  and Just restored my image file.
     I guess I should have edited /etc/sudoers with this command "export EDITOR=gedit && sudo visudo" (without the "") . LOL
Anyway no dice. BTW for anything to happen I had to add sudo to front of launcher command. Works great to shut down but boot up still starts and displays File Browser open to /home/frankgolden.?
     There must be a command that the panel icon uses that I can shortcut to.
Don't know where it is.
     I'm glad I know how to use partimage on the Recovery CD. 

P.S. What's so special about /etc/sudoers?

---

### Post by aysiu on 2006-06-22
Yeah, I guess instead of saying "add this to your /etc/sudoers," I probably should have given you more specific instructions about how to edit the file.

Apologies.

What's special about it? It's the key to security. It says who can do what and with what commands.

---

### Post by Frank Golden on 2006-06-22
[QUOTE=aysiu]Yeah, I guess instead of saying "add this to your /etc/sudoers," I probably should have given you more specific instructions about how to edit the file.

Apologies.

What's special about it? It's the key to security. It says who can do what and with what commands.[/QUOTE]
Well I should have read the warning at the top of file and remembered that this is 
the file I modified earlier to allow sudo without password. Got the command from
Unofficial Dapper Guide.
BTW, When I try to access KrazyPenguin.net for the Ubuntu Dapper Drake 6.06 Guide I get an error message

"You don't have permission to access /Ubuntu_Dapper_Drake_6.06_Guide on this server.

Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
Apache/1.3.33 Server at AppStuff Port 80"

Up until recently I had been able to view this site any idea what's up here.

I get the same result in XP.

---

### Post by aysiu on 2006-06-22
That's not your problem. It's KrazyPenguin's.

---

