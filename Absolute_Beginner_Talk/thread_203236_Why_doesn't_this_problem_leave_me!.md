---
title: "Why doesn't this problem leave me!"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by linuxfreaks on 2006-06-24
Here is a problem related to the sudo command.
My Sudo command doesn't work.. Why?:confused: 

For eg: To edit the /etc/hosts file 

1) If i write

```
gedit /etc/hosts
```

then gedit opens as a read only file 

2) If i want to edit it then i write

```
sudo gedit /etc/hosts
```

and then nothing happens

I also have changed the /etc/hosts file  to

```
127.0.0.1 localhost.localdomain localhost ubuntu 
```

PLease Help me!

I also have reinstalled ubuntu but nothing happens!](*,)

---

### Post by prash@linuxitarian on 2006-06-24
[QUOTE=linuxfreaks]Here is a problem related to the sudo command.

If i write

```
gedit /etc/hosts
```

then it opens as a read only file 

If i want to edit it then i write

```
sudo gedit /etc/hosts
```

and then nothing happens

PLease Help me!

I also have reinstalled ubuntu but nothing happens![/QUOTE]


Have you tried
sudo -s
and then
gedit /etc/hosts....?

---

### Post by fdrake on 2006-06-24
check the permission of the file.
are you running as a root?

---

### Post by linuxfreaks on 2006-06-24
Nah!! I am running as the user that was created during installation.
However sudo give root permissions to the command .. isn't it.

And ya!

How do i use the sudo -s.

PLease give the command for it cuz i am new to ubuntu.

---

### Post by prash@linuxitarian on 2006-06-24
[QUOTE=linuxfreaks]Nah!! I am running as the user that was created during installation.
However sudo give root permissions to the command .. isn't it.

And ya!

How do i use the sudo -s.

PLease give the command for it cuz i am new to ubuntu.[/QUOTE]
just type
sudo -s 
at the prompt...
This will ask you for your password...like
password:

enter YOUR password....(i.e. the one you use to login)..

You will then be root...try editing your file after that...

to exit this mode just type
exit
at the prompt and you will be back to user mode...

Let me know if this works :)

---

### Post by catlett on 2006-06-24
Is it just graphical applications you are having problems with or is it sudo. To troubleshoot stop using gedit and use nano. Nano opens in the terminal window. run this and see if you can edit ```
sudo nano /etc/hosts
``` If you can edit that file run gedit as a different user. You should always run graphical applications like this in Ubuntu. The command to run as a different user, sudoer is gksudo. So run it like this and see if gedit opens```
 gksudo gedit /etc/hosts
``` Post any errors so we can see where your issue lies. 

The next step is to create another user and see if the same problem occurs.

---

### Post by linuxfreaks on 2006-06-24
I think that the problem is with the sudo command.

I tried the sudo-s command and here is the erooe message that i get

> avinash is not in the sudoers file. This incident will be reported.

Avinash is the user that was created during the installation.

---

### Post by prash@linuxitarian on 2006-06-24
[QUOTE=linuxfreaks]I think that the problem is with the sudo command.

I tried the sudo-s command and here is the erooe message that i get



Avinash is the user that was created during the installation.[/QUOTE]
have you tried catlett's suggestion....nano or gksudo?

Could you post the errors from these too please?


Also this shouldn't be the case in ubuntu (your error normally happens in something like fedora where one has a separate root account)..also try apt-get install sudo (i think)...

paste the errors here

---

### Post by presentt on 2006-06-25
*Please someone correct me if this information is wrong, it is based on something I *think* I remember from a while back.

[quote=linuxfreaks]```
127.0.0.1 localhost.localdomain localhost ubuntu 
```[/quote] 
Try changing this back, and using ```
hostname
``` to make changes to this file (check the man).  You need to have root privelidges to change /etc/hosts, but doing so seems to mess with sudo, which you need to edit another file to completely change the hostname and fix sudo.  You'll probably have to boot Ubuntu in recovery mode to fix this file, as doing so will put you in root automatically.

---

### Post by linuxfreaks on 2006-06-25
I tried both nano and gksudo but neither an eroor came nor anything happened.
Still the sudo is not working.
And ya I am using Ubuntu version 5.10 . Dows it make  any differnece

---

### Post by fdrake on 2006-06-25
try this :
"sudo passwd root"
(now enter your user password)
(enter the root password)
(re-enter the root password)

and now "sudo gedit /etc/hosts"
 let me know

---

### Post by linuxfreaks on 2006-06-25
[QUOTE=fdrake]try this :
"sudo passwd root"
(now enter your user password)
(enter the root password)
(re-enter the root password)

and now "sudo gedit /etc/hosts"
 let me know[/QUOTE]

I tried the **sudo passwd root** but also nothing happened.

The first thing that was wrong is that the password was asked only once but according to fdrake it had to be asked thrice.

Finally Nothing happened

---

### Post by SkyNet2029 on 2006-06-25
```
avinash is not in the sudoers file. This incident will be reported. 
```
would be the root of your problems, no pun intended.

Your attempts to run commands using gksudo or su
won't result in any visible actions, since the above message
shows your not allowed to do that.
If you can login as root from a terminal or tty, (ctrl+alt+F1)
run this:
```
#visudo
```

you will probably find that your username is not listed
in this file. Or maybe it is and the permisssions aren't properly set (unlikely, but possible).
Just copy what is listed for your root account, directly under 
the entry for root. That way you will still get the prompt for
a password, but it will ask for YOUR password, and more importantly, your commands will work. :D
Here is what mine is like, as an example:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
insert_user_name_here ALL=(ALL) ALL

```

Hope that helps.

---

### Post by linuxfreaks on 2006-06-25
[QUOTE=SkyNet2029]```
avinash is not in the sudoers file. This incident will be reported. 
```
would be the root of your problems, no pun intended.

[B]Your attempts to run commands using gksudo or su
won't result in any visible actions, since the above message
shows your not allowed to do that.[/B]
If you can login as root from a terminal or tty, (ctrl+alt+F1)
run this:
```
#visudo
```

you will probably find that your username is not listed
in this file. Or maybe it is and the permisssions aren't properly set (unlikely, but possible).
Just copy what is listed for your root account, directly under 
the entry for root. That way you will still get the prompt for
a password, but it will ask for YOUR password, and more importantly, your commands will work. :D
Here is what mine is like, as an example:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
insert_user_name_here ALL=(ALL) ALL

```

Hope that helps.[/QUOTE]


The su command works .....

And yea! the above thing didn't work. Now what shoulld I do to run sudo .

Also the networking and other things in the administrative panel don't open. They prompt for a password but don't open even after putting the passowrd.....

---

### Post by catlett on 2006-06-25
> The su command works . If su works use it to get a root terminal. Which means enter su in a terminal. It will ask for a password. You enter the root password. The terminal will say **root@???: /home/???#** If you can do this then run the following to create a new user with sudo powers.

From a ROOT terminal enter ```
useradd ???
```  (replace ??? with the user name you are creating) Next edit the file mentioned in a previous post to give ??? sudo powers. Open the file ```
visudo
``` then edit the last line to look like this > ??? ALL=(ALL) ALL
Again replace ??? with the user name you created.
Close your terminal and press these keys at the same time "ctrl + alt + backspace" (do not press a key for quotes or +, press control, alt and backspace at the same time)All this does is end the x session and get you back to the login page. Login in as ??? and run a command with sudo to see what happens.

---

### Post by Salarzae on 2007-05-30
Something similar happened to mine also..... 

I did whatever was advised but nothing is happening...  here is what I'm getting in response.

[B]salarzae@Salarzae:~$ visudo
visudo: /etc/sudoers: Permission denied[/B]

upon using su.... this is what happens... 

[B]salarzae@Salarzae:/etc$ su -
Password: 
su: Authentication failure
Sorry.[/B]


Now whats the remedy?

---

### Post by Salarzae on 2007-05-30
Here is a screenshot of the failure to use even the gedit!

---

### Post by drowner on 2007-05-30
> **Salarzae said:**
> Something similar happened to mine also..... 

I did whatever was advised but nothing is happening...  here is what I'm getting in response.

[B]salarzae@Salarzae:~$ visudo
visudo: /etc/sudoers: Permission denied[/B]

upon using su.... this is what happens... 

[B]salarzae@Salarzae:/etc$ su -
Password: 
su: Authentication failure
Sorry.[/B]


Now whats the remedy?

This looks like you've not typed your password correctly.

---

### Post by Salarzae on 2007-05-30
> **drowner said:**
> This looks like you've not typed your password correctly.

I tried it so many times, but still it came up like this.... but thanx god I finally sorted it out.

All you've to do is restart system into **recovery mode** and use the **adduser ***** admin** and bingo! it worked for me..... 

where ******** is u'r userid.

---

