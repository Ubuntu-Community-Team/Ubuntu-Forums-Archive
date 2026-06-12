---
title: "sbackup"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by SVWander on 2007-12-30
Has anyone gotten sbackup to work over a network using ssh? I have it running on this laptop right now. It is backing up to a little file server I have running. Today I tried to restore my desktop system from the server but just like with the command line for backing up with ssh the restore command line didn't work. Even when I copied and pasted the command in the backup location . . . I even copied the files from my server to /var/backup/ and although it said it was restoring it never did. Can anyone tell me what the hell I am doing wrong. I have good (I guess) backup in /var/backup/ now but restoring them seems impossible.
tim

---

### Post by toupeiro on 2008-01-01
I myself have not tried it over ssh, but I used to use sbackup and I have had 2 different experiences of corrupt archives.

First things first, If you don't have the hostname of the server, or its IP address, you have to get that before you can do anything else.  if you were ever able to complete a backup using this method, I am assuming that SSH-server is already installed and configured on the server computer.  

Everything outlined here will be done in a terminal window (applications - accessories - terminal)


in your /var/backup folder on the server, you are going to see a directory structure similar to this:


2007-07-28_16.59.38.814049.computername.ful

The first part of the directory name in the example above is obviously the date and time.  The second part, is your computers hostname, and the third part is ful or inc (meaning full backup or incremental).  We want to find the newest full backup on that machine that we can get our hands on.  Assuming you can't sit in front of this server  and verify what that is, type this command, filling in your information

> ssh account_on_server@server_name_or_ip_address ls -l /var/backup

you will be prompted for the password of the account you specified.  This should give you a directory listing of the /var/backup directory on the server.  Find and note the newest .ful directory name.

ok, now we are going to copy the big archive file in this directory to your local system using this command below, filling in your information

> scp [email]account_on_server@server_name_or_ip_address:/var/backup/noted_directory_name/files.tgz[/email] /tmp

copying the file may take some time depending on its size.  Once its completely copied, we are going to open it with root privledges.

> sudo file-roller /tmp/tiles.tgz

This may take some time to open depending on its size.  We are now going to cross our fingers and hope that the file is not corrupt...  If it opens, you can extract these files back to any place on your computer using the file-roller utility.  


Hopefully, this gives you access back to the data you lost.  Next thing to do is to find another backup tool.  The author of[ this tool]("http://ubuntuforums.org/showthread.php?t=613462") is very responsive to feature requests and Quality Assurance.  I don't know if it allows for ssh enabled backups out of the box, but You can probably ask him about the possibility of it.  If not, you can also manually copy your backups made with this tool using the scp command like I did above similar to this:  

> scp file.tar.gz accont_on_server@server_name_or_ip_address:/directory/to/put/it


Best of luck to you!

---

