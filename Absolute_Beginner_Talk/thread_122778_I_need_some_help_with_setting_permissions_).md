---
title: "I need some help with setting permissions :)"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by synapticjelly on 2006-01-28
Hi, let me first just hi and Ubuntu is pretty cool, i've never used linux before so im kinda lost when it comes to getting help, i normally dont ask for help on a forum because i generally know what to look for so im really sorry if this is a really simple problem to solve :)

Anyway i've been trying to install a custom DesktopIDE i created but for some reason i don't have permission to place files in /usr/share so im a bit lost as to what i should do :-k 

Cheers for any help

Gordon

---

### Post by HJThis on 2006-01-28
Hello,synapticjelly & Welcome

Well this link here is the first one you should be looking at
go there what your looking for is on Page 5

[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

Best of luck

---

### Post by DonQuixote on 2006-01-28
Linux has a permissioning system that allows or disallows modification to files and directories.

If you open a teminal window (looks a bit like a DOS window) type : ls -l

You will see a listing of files and directories that may look something like this:

lrwxrwxrwx  1 root root       9 2006-01-17 16:09 maelstrom -> Maelstrom
-rwxr-sr-x  1 root games 160200 2004-10-07 08:28 Maelstrom
-rwxr-xr-x  1 root root    9720 2004-10-07 08:28 Maelstrom-netd
-rwxr-sr-x  1 root games  83444 2005-10-03 16:15 mahjongg
-rwxr-sr-x  1 root games 295480 2005-06-01 14:26 moria
-rwxr-sr-x  1 root games  64948 2005-10-03 16:15 same-gnome
-rwxr-xr-x  1 root root   93068 2005-10-03 16:15 sol

The column on the left are the permissions.
I don't know what the second column is where "1" is listed.
Column 3 is the owner of the file or directory.
Column 4 is the group.

As a user you don't have permission to modify any file that you do not own.

root can change anything

So, lets change ownership of the directory /usr/share

In the terminal type this:

"sudo chown [your username] /usr/share [enter]"

You will be asked a password, enter your user password.

If you are not already in the /usr directory, change to it with this command:

cd /usr [enter]

Then type:

ls -l

Your user name should be listed in column 3 next to /share

HTH

John
ps. I'm no expert either. :)

---

### Post by aysiu on 2006-01-28
[QUOTE=synapticjelly]
for some reason i don't have permission to place files in /usr/share so im a bit lost as to what i should do :-k [/QUOTE] Read the third link of my signature.

---

