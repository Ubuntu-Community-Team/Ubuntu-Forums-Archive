---
title: "[SOLVED] Using visudo"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by drsaamah on 2008-03-31
Okay, before I ask, I need to specify that I am REALLY lost here.  I need like super detailed instructions if that's possible.  Thanks in advance!!
So in order to use ThinkFinger on my computer I need to edit my so-called "sudoers" file.  Exactly what I need to do to this file is outlines [here]("https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/86843/comments/18").  The problem is I tried to do this not ever using visudo before and now I'm totally lost.  I don't know how to edit this file or to save the changes.  I accidentally edited it, but in the process put a whole lot of whitespace into the file (from my understand bash does not ignore whitespace), and now I can't delete it or backspace it.
Furthermore, I didn't know how to save it, so every time I run 'sudo visudo' I get the following:
```

E325: ATTENTION
Found a swap file by the name "/etc/.sudoers.tmp.swp"
          owned by: root   dated: Mon Mar 31 04:21:42 2008
         file name: /etc/sudoers.tmp
          modified: YES
         user name: root   host name: euler
        process ID: 8557
While opening file "/etc/sudoers.tmp"
             dated: Sun Mar 30 13:24:41 2008

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/sudoers.tmp"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.sudoers.tmp.swp"
    to avoid this message.
"/etc/sudoers.tmp" 23 lines, 496 characters
Press ENTER or type command to continue

```
Following this I hit 'Enter' and I get the unedited "sudoers" file again.
I've been using linux for over a year now, so it's kind of embarrassing that this has me completely stumped.  Thanks again for any help!

---

### Post by kellemes on 2008-03-31
It's a vim thing..
confirm your sudoers file is fine by opening the original with gedit..
```
sudo EDITOR=/usr/bin/gedit visudo 
```

Now you can delete the tmp/swp-file I guess..

Always create backups of files like this before editing, surely you know..

---

### Post by drsaamah on 2008-04-02
Alright the good thing is that the original file seems to be unmodified.  I cannot however find the .temp file.  Its not in the /tmp directory, nor in the /etc directory where the 'sudoers' file is.  Can you tell me where this is?  And, can I actually modify the sudoers file using 'sudo EDITOR=/usr/bin/gedit visudo' command? (I was too afraid to even try, hehe).

---

### Post by drsaamah on 2008-04-02
Alright never mind, i decided to man up and take some risks.  I found the temp files (I didn't realize they were hidden) and deleted both of them.  Then I used gedit to edit the sudoers file the way I needed, and all worked just dandy except that the changes were automatically saved to a new temp file!!  So should I just delete the old sudoers file, and rename the temp file accordingly?

---

### Post by brian_p on 2008-04-02
> **drsaamah said:**
> Alright never mind, i decided to man up and take some risks.  I found the temp files (I didn't realize they were hidden) and deleted both of them.  Then I used gedit to edit the sudoers file the way I needed, and all worked just dandy except that the changes were automatically saved to a new temp file!!  So should I just delete the old sudoers file, and rename the temp file accordingly?

A good find. I was about to suggest looking for a hidden file.

To be on the safe side I'd backup the original file, /etc/sudoers-orig (say) and then replace it as you intend to. Check the permissions and test. Then delete sudoers-orig.

---

### Post by drsaamah on 2008-04-02
Alright now the issue is changing the permissions.  The permissions on the original sudoer file was 110, that is, read-only for owner and group.  But I can't seem to change to those permissions.  Here's what (a portion) of ls -al gives me:
```
-rw-------   1 root root       496 2008-03-30 13:24 sudoers
-r--r-----   1 root root       516 2008-04-02 11:28 sudoers-orig

```
Where "sudoers" is the new file, what use to be the temp file.  'sudoers-orig' is the original file backed up, and as you can see the permissions are different.
When I try to change to permissions I get the following:
```
saam@euler:/etc$ sudo chmod -R 110 ./sudoers
sudo: /etc/sudoers is mode 0600, should be 0440
saam@euler:/etc$ 

```
Even if I try to change the syntax:
```
saam@euler:/etc$ sudo chmod o -w ./sudoers
sudo: /etc/sudoers is mode 0600, should be 0440
saam@euler:/etc$ 

```
Any ideas?

---

### Post by brian_p on 2008-04-02
> **drsaamah said:**
> 

Any ideas?

The permissions on /etc/sudoers should be 440.

---

### Post by drsaamah on 2008-04-02
Yeah it says the same thing:
```
saam@euler:/etc$ sudo chmod 440 sudoers
sudo: /etc/sudoers is mode 0600, should be 0440
saam@euler:/etc$ 

```
Any other ideas?

---

### Post by brian_p on 2008-04-02
> **drsaamah said:**
> Yeah it says the same thing:
```
saam@euler:/etc$ sudo chmod 440 sudoers
sudo: /etc/sudoers is mode 0600, should be 0440
saam@euler:/etc$ 

```
Any other ideas?

How do you go if you type 'su' followed by 'sudo chmod 440 sudoers'?

---

### Post by drsaamah on 2008-04-03
'su' command won't authenticate but that's because I don't have my root account enabled.  I would prefer to keep it that way, unless there's no other way around this.

---

### Post by p_quarles on 2008-04-03
> **drsaamah said:**
> 'su' command won't authenticate but that's because I don't have my root account enabled.  I would prefer to keep it that way, unless there's no other way around this.
No, you don't need to enable the root password to get a root shell. The officially supported way of getting a root shell is to boot into recovery mode from the GRUB menu. The other way (officially not recommended, but safe if you don't go crazy) is:
```
sudo -i
```

---

### Post by brian_p on 2008-04-03
> **drsaamah said:**
> 'su' command won't authenticate but that's because I don't have my root account enabled.  I would prefer to keep it that way, unless there's no other way around this.

I see p_quarles has come to your rescue so hopefully you will chmod successfully.

An apology: I should have advised you to have checked the permissions on files before backing up. It had slipped my mind that sudo will not work if /etc/sudoers is not 440.

---

### Post by drsaamah on 2008-04-04
Thank you VERY much p_quarles!  I should have thought of that.  And thank you brain_p for following the thread and being so patient.

---

