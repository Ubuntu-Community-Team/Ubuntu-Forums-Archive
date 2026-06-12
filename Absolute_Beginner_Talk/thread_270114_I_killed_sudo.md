---
title: "I killed sudo"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Iron-Monk on 2006-10-02
I installed dapper on my laptop, after I installed it I used the faster-dapper script.  After i launched faster dapper had some problems it's an older laptop w/ 64 mb of ram. I think i killed faster dapper once or twice  
with contol +C  I was looking @ the script wilst i was running it saw things I didn't want done so i killed the script before this could happen. But since I have ran the script my sudo has been messed up, now anytime I run any command with sudo it never ask me for my password I don't really know what happened I used this command from the faster dapper script "sudo sed -ie '/NOPASSWD/s/NOPASSWD: //' /etc/sudoers"  to try to get it to work again and it still doesn't ask me for my pw.  

thnx for any help,               
Joseph

---

### Post by scrattox on 2006-10-02
I think you're going to have to edit your "/etc/sudoers" file manually.

If you use the 'visudo' command to do this, it will check your syntax before it saves the file, so use this command rather than editing it directly.

If you're comfortable with the command line and simple text editors, this should be easy, if not, it might be more challenging!  :)

Since I don't know what editor your system is set up to use, let's explicitly tell it to use 'nano' since I can more easily describe how to do it.

Type this:
```
EDITOR=nano sudo visudo
```

Here is the contents of my /etc/sudoers file:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults    !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```

(This file is actually from an Edgy Eft beta install, but it is probably the same, and will almost certainly work fine.)

The lines which start '#' are comments, so you may ignore them.

Edit the file (using arrows keys, delete etc., just like most other text editors) so that all the important parts match mine above.  Then press Ctrl-X and then 'Y' to confirm that you wish to save the changes on exit.

Now, sudo should work as you expect (but note that there may be a short timeout to elapse before it starts asking you for a password.  This is to make it more convenient to execute several sudo commands in succession.)

---

### Post by Iron-Monk on 2006-10-02
thanx for the help yet i screwed up. I have a habit of saving a file when i edit it i did that and screwed up bad, i now have an error in sudoers file I cannot edit it because of the error sudo no longer works here's teh error.

~$ sudo
>>> sudoers file: syntax error, line 19 <<<
sudo: parse error in /etc/sudoers near line 19

here is that line from my file i forgot teh ALL @ the end of the file

# Members of the admin group may gain root privileges
%admin ALL=(ALL)

---

### Post by aysiu on 2006-10-02
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo) should help.

---

### Post by Iron-Monk on 2006-10-02
Thnx for your help i finally got it fixed. I feel like a  moron i forgot about having recovery mode.  heh

Thnx. again,
Joseph

---

