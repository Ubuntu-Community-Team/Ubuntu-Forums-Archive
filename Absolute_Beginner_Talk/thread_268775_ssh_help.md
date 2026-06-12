---
title: "ssh help"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by djchintu on 2006-09-30
I recently switched from Fedora Core to Ubuntu.

I use ssh to connect to the linux at my college using the terminal.

ssh [email]username@linux.######.edu[/email]

When I used ssh in fedora core, it used to lauch all application in graphical mode. 

For example, if i tried to open a file using emacs on the remote linux, the terminal would launch a graphical mode of the emacs to edit the the file.

My question is how could you make ubuntu terminal do that? When ever i try to open a file or somethign on remote linux, it does not lauch the graphical version of the emacs, instead i get an emacs editor in the terminal in command line mode.

---

### Post by ewl1217 on 2006-09-30
Try running the ssh command with the -X command (UPPERCASE, NOT LOWERCASE!). You can use that to tunnel X connections over ssh, which lets you launch X applications on the remote computer. Either that, or edit files on your own computer with your preferred editor and then transfer them to the server with scp (although that could be a bit of a hassle).

---

### Post by djchintu on 2006-09-30
Thank you!!.. That worked.. i should have done man ssh before posting this question.. thanks again

---

### Post by David_T on 2006-09-30
You could look into installing sshfs if what you mainly want to do is edit/move/copy files that are on the remote host, but run all your programs on the local system.

---

