---
title: "Is online backup really complicated?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by sam_uk on 2006-11-12
OK I want set up an automated online backup - and i want it to be free!

I have read this [http://www.ubuntuforums.org/showthread.php?t=240326](http://www.ubuntuforums.org/showthread.php?t=240326) and will try to get all those steps worked out (I have never edited a script before)

What I would like to know is how do I use [http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem.html) as the backup path?

Also would it be possible to have 2 backup paths? I would ideally like to use [http://amd.streamload.com/](http://amd.streamload.com/) as well so that if either of the backups get taken down i have a spare..

If anyone can give me pointers to a simple how-to that would be really appriciated.:-k 



It surprises me a little that you still have to hack scripts in ordeer to get a working offsite backup.  Free and simple programs exist for windows; [http://weblogs.asp.net/nleghari/articles/gmailbackup.aspx](http://weblogs.asp.net/nleghari/articles/gmailbackup.aspx) Its a shame no one has had the time/inclination to port/develop it for Linux. 

Many thanks

--------------edit--------------------------------------

OK after spending a hour or two trying stuff out this is what i have found out so far. DISCLAIMER - this is the first script i have ever edited, following these instructions may well break, or open up security holes in your system...

To get gmailfs + duplicity is easy in edgy . 

[INDENT][FONT="Courier New"]sudo apt-get install gmailfs duplicity[/FONT][/INDENT]

Getting a gmail account is also easy;
[https://www.google.com/accounts/CreateAccount](https://www.google.com/accounts/CreateAccount)

[INDENT][FONT="Courier New"]cd /Desktop[/FONT][/INDENT] 
 
[INDENT][FONT="Courier New"]gedit backup.sh[/FONT][/INDENT] 

Paste in the following after changing the passphrase + gmailuser + gmailpass  and name of your home folder to your actual details.

[FONT="Courier New"]#!/bin/sh
sudo mount -t gmailfs /usr/local/bin/gmailfs.py /mnt/ -o username=gmailuser??,password=gmailpass??,fsname=zOlRRa 
export PASSPHRASE=SomeLongGeneratedHardToCrackKey??
duplicity /home/?? file:///mnt/
unset PASSPHRASE[/FONT]

Click 'save'

[INDENT][FONT="Courier New"]chmod 700 backup.sh[/FONT][/INDENT] 

[INDENT][FONT="Courier New"]./backup.sh[/FONT][/INDENT] 

The rest of the detail i just copied from here
[https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto)

---

### Post by sam_uk on 2006-11-12
It seems to be working, I get files added to my gmail account anyway..

I will update this thread with any further info..

---

### Post by sam_uk on 2006-11-14
hmm it writes the files to the gmail account OK  (listfiles script works) but when i try to restore files it says 'signature ok but no backups found' Anyone more experienced help me out?

---

### Post by jimhaddon on 2006-11-18
Iv tied SO hard to get this working! Its impossible!

I just get this:

Ignored option :rw
11/18/06 11:02:26 ERROR      Unable to find GMail account configuration
11/18/06 11:02:26 WARNING    Using default file system (Dangerous!)
11/18/06 11:02:26 WARNING    mount: warning, should mount with username=gmailuser option, using default
11/18/06 11:02:26 WARNING    mount: warning, should mount with password=gmailpass option, using default
11/18/06 11:02:26 WARNING    mount: warning, should mount with fsname=name option, using default
Traceback (most recent call last):
  File "/sbin/mount.gmailfs", line 164, in ?
    main(mountpoint, namedOptions, useEncfs)
  File "/sbin/mount.gmailfs", line 90, in main
    gmailfs.main(mountpoint, namedOptions)
  File "/usr/local/bin/gmailfs.py", line 1130, in main
    server = Gmailfs(mountpoint, **namedOptions)
  File "/usr/local/bin/gmailfs.py", line 602, in __init__
    self.ga.login()
  File "/usr/local/lib/python2.4/site-packages/libgmail.py", line 317, in login
    raise GmailLoginFailure("Login failed. (Wrong username/password?)")
libgmail.GmailLoginFailure: 'Login failed. (Wrong username/password?)'
11/18/06 11:02:27 ERROR      gmailfs child died, exiting...

---

### Post by sam_uk on 2006-12-04
I think you just need to set a valid gmail account. everywhere there is a ?? in the script you need to add your valid user info.

---

