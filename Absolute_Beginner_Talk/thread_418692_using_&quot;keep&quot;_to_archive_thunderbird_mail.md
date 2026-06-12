---
title: "using &quot;keep&quot; to archive thunderbird mail"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Ba66e77 on 2007-04-22
I'm running feisty and am trying to use keep to make backups of my thunderbird mail files but I'm getting an error.  Actually, I'm getting the same error no matter what I try to back up. 

 I've set the source directory to "/home/barrett/.mozilla-thunderbird/2ps4l6qm.default/Mail/", which I've verified is where mozilla stores my mail, and the target to "/media/share/Archives/Thunderbird/", an archive directory on my network drive with permissions of 777.

The error I'm getting is below.  Can anyone tell me what I'm doing wrong?  I can't locate a manual or users' guide for "keep".  Is there another archiving tool that you'd recommend?


An error occured making /home/barrett/.mozilla-thunderbird/2ps4l6qm.default/Mail/ backup:
Exception '[Errno 1] Operation not permitted: '/media/share/Archives/Thunderbird'' raised of class '': File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 295, in error_check_Main try: Main(arglist) File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 315, in Main take_action(rps) File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 271, in take_action elif action == "backup": Backup(rps[0], rps[1]) File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 324, in Backup backup_set_rbdir(rpin, rpout) File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 381, in backup_set_rbdir rpout.chmod(0700) # just make sure permissions aren't too lax File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 826, in chmod self.conn.os.chmod(self.path, permissions & Globals.permission_mask) Traceback (most recent call last): File "/usr/bin/rdiff-backup", line 23, in rdiff_backup.Main.error_check_Main(sys.argv[1:]) File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 295, in error_check_Main try: Main(arglist) File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 315, in Main take_action(rps) File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 271, in take_action elif action == "backup": Backup(rps[0], rps[1]) File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 324, in Backup backup_set_rbdir(rpin, rpout) File "/var/lib/python-support/python2.5/rdiff_backup/Main.py", line 381, in backup_set_rbdir rpout.chmod(0700) # just make sure permissions aren't too lax File "/var/lib/python-support/python2.5/rdiff_backup/rpath.py", line 826, in chmod self.conn.os.chmod(self.path, permissions & Globals.permission_mask) OSError: [Errno 1] Operation not 
permitted: '/media/share/Archives/Thunderbird'

---

