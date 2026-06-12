---
title: "Showing Passwords In Terminal (while typing)"
date: 2016-04-11
forum: Assistive Technology &amp; Accessibility
---

### Post by annaek on 2016-04-11
Hi.  I'm wondering if there is any way to show passwords while typing in terminal.   
 
I have a physical disability that makes it difficult and painful for me to type.  While I can type my own passwords, I make a lot of mistakes, and I don't always realize when I have made a mistake if I can't see the text on the screen.  I usually circumvent the problem by making my (user) passwords extremely short.  (I know, bad security.  But good security doesn't count if I can't physically use my computer!)  Recently, though, I'm needing to use ssh and sftp quite a bit, and the organization governing those accounts has strict requirements on how long passwords need to be.  I find myself trying to enter the password 20+ times at the terminal before I manage to get it right, which is very painful given my disability.  Is there any way to make the terminal show me the password so that I can correct my mistakes?
 
Also, I did try typing the password into gedit and then using copy and paste.  And it does work but requires a right click, which is also challenging for me.  Since every keystroke and mouse movement is painful, I'd like to minimize them by typing directly in the terminal. 
 
Any pointers would be much appreciated!  Thanks! 

(I'm pretty familiar with Ubuntu; I've been a user for about 6 years.  Limited programming experience due to my disability, but a good theoretical understanding of computer science.)

---

### Post by TheFu on 2016-04-12
Don't know of any way to enable passwords to show up, but perhaps a different option?  Maybe a 2FA device like a YubiKey could work?  Use the static part for initial data entry and add something to the beginning and end so it isn't just "something you have."  This can be used to unlock ssh key access (ssh-agent) and gpg keys too.

BTW, any organization requiring passwords for ssh is just stupid.  They/you should use ssh-keys for authentication.  More convenient AND more secure.  Why aren't you using key-based authentication?  I've never seen that blocked anywhere. Not at any government facilities where I've worked.

A place that allows 20 attempts has some pretty big security issues too. 3 times, then the account should be locked.

Please don't use gedit for passwords. Use a password manager and setup auto-type.  KeePassX does this.

---

### Post by annaek on 2016-04-14
Ssh keys! That's what I need.  Thank you!  (I've been using Ubuntu for years, but ssh is new territory for me.) 
 
By the way, I totally recognize the issues with storing passwords as plain text.  I was just commenting that it is possible to type into an application which does display the entered characters (like gedit) and then paste into the terminal (which, I guess, could still be an issue if there was a bug or something with the text editor...).  I was never proposing keeping a plain text list of passwords! 
 
I would still be interested in an answer to the original question if anyone has ideas, mainly because it just feels like an accessibility hole to me.  (After all, my cell phone, which has an error-prone input device in the on-screen keyboard, gives me the option to show passwords as I enter them.  Ubuntu really should do the same for people whose fingers are themselves error-prone!)  Also, I could pick a stronger root password.  Which would be a good thing.

---

### Post by sudodus on 2016-04-15
It is a good idea to use keys to login via ssh and sftp.

But you need a tool for other log in scenarios too. So I made a small shellscript, that you should run in a terminal window. I have tested it, and it works for passwords in ssh and sftp as well as for sudo. You should run the program that wants a password in another window. I hope it will help you (and maybe other people too) :-)

This script works for ***sudo***, but there is another script for that purpose - and it is more convenient to use. See the next post.

I use the name ***show-only*** for the shellscript.

```
#!/bin/bash

# Copyright 2016 Nio Wiklund
#
# GPLv3: GNU GPL version 3
# <http://gnu.org/licenses/gpl.html>.
#
# This is free software: you are free to change and redistribute it.
# There is NO WARRANTY, to the extent permitted by law.
#-----------------------------------------------------------------------
# author sudodus alias nio-wiklund at launchpad
#
# date        editor   comment
# 2016-04-15  sudodus  created

cursorup="\0033[A"

function select_text {

/bin/echo $* | xsel -pi
/bin/echo $* | xsel -bi
}

# ----------------------------------------------------------------------
# main
# ----------------------------------------------------------------------

# Do it

echo "Enter passphrase (finish with the Enter key) "
read ans
select_text "$ans"

# Overwrite text string (variable and on screen) and prompt to use it

ans="1234567890qwertyuiopasdfghjkl*zxcvbnm,.-1234567890qwertyuiopasdfghjkl'"
ans=""

/bin/echo -e "${cursorup}In another window: Pull-down menu: Edit -- Paste (or middle-click) ..."
read -p "... clear the selection buffers afterwards (finish with the Enter key) " ans

# Overwrite selections

ans="echo '1234567890qwertyuiopasdfghjkl*zxcvbnm,.-1234567890qwertyuiopasdfghjkl'"
select_text -n "$ans"
ans=""
select_text -n "$ans"

```

I would copy and paste from this code window to ***gedit*** and save it into **~/bin**

```
cd  # brings you 'home'
mkdir bin
gedit show-only  # copy and paste the shellscript code, save it and exit from gedit.
```

Then I would make it executable

```
chmod ugo+x show-only
```

and the next time you reboot it should be in PATH, so that you can run it with

```
show-only
```

See ```
man xsel
``` for more details.

***Example:***

Type in window #1:
```
[COLOR="#0000FF"]$ show-only[/COLOR]
Enter passphrase (finish with the Enter key) 
[COLOR="#0000FF"]echo 'Hello Anna'[/COLOR]
```

[COLOR="#0000FF"]Press Enter[/COLOR] in window #1:

```
$ ./show-only 
Enter passphrase (finish with the Enter key) 
In another window: Pull-down menu: Edit -- Paste (or middle-click) ...
... clear the selection buffers afterwards (finish with the Enter key) 
```

Use the pull-down menu: [COLOR="#0000FF"]Edit -- Paste (or middle-click)[/COLOR] in window #2:

```
$ echo 'Hello Anna'
Hello Anna
$ 
```

[COLOR="#0000FF"]Press Enter[/COLOR] in window #1:

```
$ ./show-only 
Enter passphrase (finish with the Enter key) 
In another window: Pull-down menu: Edit -- Paste (or middle-click) ...
... clear the selection buffers afterwards (finish with the Enter key) 
$ 
```

Check that the selection buffers are empty in any window:

1. Use the pull-down menu: Edit -- Paste

2. Middle-click

Nothing should happen, now that the selection buffers are empty.

---

### Post by sudodus on 2016-04-15
I had the time, and enjoyed making a dedicated shellscript for ***sudo***, which needs no mouse actions at all. It should make system tasks more convenient :-)

```
#!/bin/bash

# Copyright 2016 Nio Wiklund
#
# GPLv3: GNU GPL version 3
# <http://gnu.org/licenses/gpl.html>.
#
# This is free software: you are free to change and redistribute it.
# There is NO WARRANTY, to the extent permitted by law.
#-----------------------------------------------------------------------
# author sudodus alias nio-wiklund at launchpad
#
# date        editor   comment
# 2016-04-15  sudodus  created
#
# This script assumes that sudo allows the user to run sudo again for a
# period of time (15 minutes) without requiring authentication according
# to the policy used in Ubuntu. See 'man sudo' for details.

cursorup="\0033[A"

# try without a password

sudo -n echo $(pwd) > /dev/null 2>&1

if [ $? -ne 0 ]
then
 read -p "write passprase: " ans

# port the password to sudo
 echo "$ans" |sudo -S echo $(pwd) > /dev/null 2>&1
 res=$?

# overwrite text string on screen
 /bin/echo -e \
 "${cursorup}-------------------------------------------------------------------------------"

# overwrite text string variable
 ans="1234567890qwertyuiopasdfghjkl*zxcvbnm,.-1234567890qwertyuiopasdfghjkl'"
 ans=""

 if [ "$res" != "0" ]
 then
  echo "show-sudo: bad password, please try again"
  exit 1
 fi
fi

sudo $*
```


I suggest that you call it ***show-sudo*** and treat it in the same way as ***show-only***:

```
cd  # brings you 'home'
mkdir bin
gedit show-sudo  # copy and paste the shellscript code, save it and exit from gedit.
```

Then I would make it executable

```
chmod ugo+x show-sudo
```

and the next time you reboot it should be in PATH, so that you can run it with

```
show-sudo commands
```

Examples:

```
show-sudo lsblk
show-sudo lsblk -o NAME,MODEL,FSTYPE,LABEL,MOUNTPOINT,SIZE,NAME /dev/[^f]d?
```

---

