---
title: "editing files over sftp"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by SamYoung on 2007-03-12
I am trying to connect to a sftp server to edit files on the remote computer.

When I try to connect using places->connect to server the systems hangs forever while trying to connect.

gftp is very dificult to use, since you either have to close the editor in order to save your changes, or download the file and refresh the list every time you want to upload the changed file.

In windows I used winscp, which allows easy editing of the remote files. Is there a similar program for ubuntu?

Thanks for any help.



ubuntu edgy eft, amd64

---

### Post by thingy on 2007-03-12
Re: Places->Connect to server hanging... hmm are you sure the remote side is providing SFTP? Some FTP Server programs like Filezilla provide SSL FTP which is very different to SFTP! Can you tell us what happens when to try to ssh into the remote machine from the command line?

Re: A text editor which allows remote editing of files, see if this thread helps: [http://www.ubuntuforums.org/showthread.php?t=165904&highlight=remote+file+edit+sftp](http://www.ubuntuforums.org/showthread.php?t=165904&highlight=remote+file+edit+sftp)

---

### Post by ashonline on 2007-03-27
Hey peoples

I'd like to bump up this thread as I'm also looking for a WinSCP equivalent app for Ubuntu.

I SSH into my uni account ok from the CLI no probs.

Any ideas?

Any help much appreciated!

Cheers

Ash

---

### Post by cephlon on 2007-04-27
I am also looking for a winscp equivalent. nautilus used to be sufficient, but no longer works with ssh or sftp on feisty.

---

### Post by Najand on 2007-04-27
"Connect to server" works fine on my feisty!

---

