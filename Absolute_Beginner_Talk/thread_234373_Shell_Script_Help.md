---
title: "Shell Script Help"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by brownjl on 2006-08-11
Hi,

I have a console based application which when ran prompts the user for a password does something and then exits.

I wish to write a shell script which will execute the application, and then fill out the password when prompted then wait for the application to quit, how can then be done?

Cheers,

James

---

### Post by moma on 2006-08-11
#!/bin/bash

your_program.exe
wait $$
passw=$(zenity --title "Passwd" --entry --text "Enter your password:")
echo "Done"

---

### Post by kebes on 2006-08-11
Automating password entry is generally a security risk for obvious reasons. It is discouraged to do so. However there are ways to accomplish this if you need to.

First off, if the password arises in the context of an SSH login, you can set up key pairs on the two machines to allow for password-less secure logins. The procedure for doing this is well documented:
[http://www.astro.caltech.edu/~mbonati/WIRC/manual/DATARED/setting_up_no-password_ssh.html](http://www.astro.caltech.edu/~mbonati/WIRC/manual/DATARED/setting_up_no-password_ssh.html)
[http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/advanced/node74.html](http://rcsg-gsir.imsb-dsgi.nrc-cnrc.gc.ca/documents/advanced/node74.html)

If the password is appearing in a different context (like telnet or interactive programs), you can use a scripting program called "expect" (based on the "tcl" scripting language) to automate the process. In expect, you can launch an application ("spawn") and then wait for a given piece of text (such as "password:") using a special command (called "expect") and then return some text ($pass or whatever). This might be what you want. Some info:
[http://expect.nist.gov/](http://expect.nist.gov/)
[http://en.wikipedia.org/wiki/Expect](http://en.wikipedia.org/wiki/Expect)

I've used expect to automate complicated telnet and ftp sessions and file transfers. It works quite well when the input/output behavior of all programs is very reproducible. The passwords are stored as plain text, which is totally insecure, so this is not a good idea for important passwords.

---

### Post by kitus on 2006-08-11
there's really simple way to get an bash script working on linux, in fact, i think this one of the best tools that linux do..

check this link out...

[http://www.powered-by-linux.com/docs/?doc=/docs/es/Programacion-Bash-COMO](http://www.powered-by-linux.com/docs/?doc=/docs/es/Programacion-Bash-COMO)

this is in spanish lenguage.. cuz i'm from mexico.. but find out about english lenguage... good look... never give up..

---

### Post by brownjl on 2006-08-11
Cheers for the help,

What I am trying to do is write a Kdialog wrapper around 

"sudo cryptsetup LuksOpen /dev/sda1 usb-crypto"

so instead of dropping to the console I could do it via kde, so I would run it from kde and it ask me for my passphrase in a kdialog and then pipe it to the above command, not the best for security really..

James

---

### Post by kebes on 2006-08-12
I'm guessing you're using KDE, right?

Wouldn't it be simplest to make an application shortcut that gets run as root?

Try this:
1. Right-click on desktop, go "Creat New" > "Link to Application..."

2. On the "Application" tab, enter the command as:
cryptsetup LuksOpen /dev/sda1 usb-crypto

3. Under "Advanced Options" set the "Run as different user" to "root".

4. Fill in the other info (Name, description, etc.).

Now when you click on this shortcut, it will open up a dialog asking for the password for user "root". You could make it any other user if that's more appropriate.

Now that it's a shorcut you can put it in a menu, assign it a shortcut, etc.

Does that do what you need?

---

### Post by brownjl on 2006-08-13
:( no the actually application wants a Pass Phrase as well as the root/admin password to open the encrypted drive so as you suggested I can write a script and run it as root and it will ask me in kde for the admin password but then it needs the console for me to type in the pass phrase for the encrypted drive so i was hoping to write a kde dialog wrapper around that..

Cheers,

James

---

### Post by kebes on 2006-08-13
This tutorial:
[http://developer.kde.org/documentation/tutorials/kdialog/t1.html](http://developer.kde.org/documentation/tutorials/kdialog/t1.html)

Explains how to launch KDE dialogs from the commandline. It actually uses "entering a password" as an example of how you would do it. Looks to me like you could have a shell script that asks the user for a password, and then passes this as an argument to the function you need. You could also use the kdialog to grab the password, and store it in a temporary file (probably a file that exists only memory is safer), and then use the "expect" programming environment that I already mentioned to pass this variable onto the command that requires it (when the program writes "Enter Passphrase:" expect returns the value of the password...).

I think that would work, although of course the details may be a bit complicated. The trick will be storing the passphrase in some kind of sane way and passing it to the function.

---

