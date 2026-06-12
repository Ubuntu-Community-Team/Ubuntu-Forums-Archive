---
title: "Trying to save a corrupted USB drive"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by ___ on 2007-04-20
Hello.  This is the first time that I have ever used Linux.  I installed Ubuntu 6.06 LTS on my computer for the sole purpose of trying to save a corrupted USB drive that is no longer recognized by Windows.  I am trying to follow the this article 
[http://www.linuxjournal.com/article/8366](http://www.linuxjournal.com/article/8366)
as a guide, but everything is like a foreign language to me.  

I realize that I'm nowhere close to being able to retrieve data and burn it onto CD.  For now, all I want to do is see if Ubuntu sees any data on the USB drive.  Clicking on "Places", "Computer", and selecting the USB drive yielded the following message, "Unable to mount the selected volume".  

The author of the article used a different method, using several commands under "Root".  Is this the same as Sudo? And do I access Sudo by clicking on "Applications", "Accessories", "Terminal"?  And would I use the same commands as the author of the article (who used SuSE 8.0)?
# tail -f /var/log/messages
# dd if=/dev/sda of=/tmp/r1 bs=512

I would appreciate your assistance.

---

### Post by goldaryn on 2007-04-20
Yes, firstly you need to go into terminal, as you described, before you can type in any commands.

Now, the sudo command is for carrying out commands with admin privileges. This obviously carries risks! So be careful.

You can either type 'sudo <command>' to execute one command as root (aka admin/superuser)

or you enter a root shell (i.e. root as the guy refers to it) for a while by typing "sudo su", and do what you need to, then "exit" when you are done.

Make sure you know what you are doing before attempting random commands in root!

g.

---

### Post by ___ on 2007-04-20
when i type in: 
sudo # dd if=/dev/sda of=/tmp/r1 bs=512

i get the following message: 
usage: sudo -K | -L |-V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
                  { -e file [...] | -i | -s | <command> }

do i have to enable my account to use the sudo command? any ideas on what i'm doing wrong?

---

### Post by Nik_Doof on 2007-04-20
drop the #, the command should be in the format of:

> sudo dd if=/dev/sda of=/tmp/r1 bs=512

---

